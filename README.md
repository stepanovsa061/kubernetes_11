# Задание. Необходимо определить требуемые ресурсы
Известно, что проекту нужны база данных, система кеширования, а само приложение состоит из бекенда и фронтенда. Опишите, какие ресурсы нужны, если известно:

Необходимо упаковать приложение в чарт для деплоя в разные окружения.
База данных должна быть отказоустойчивой. Потребляет 4 ГБ ОЗУ в работе, 1 ядро. 3 копии.
Кеш должен быть отказоустойчивый. Потребляет 4 ГБ ОЗУ в работе, 1 ядро. 3 копии.
Фронтенд обрабатывает внешние запросы быстро, отдавая статику. Потребляет не более 50 МБ ОЗУ на каждый экземпляр, 0.2 ядра. 5 копий.
Бекенд потребляет 600 МБ ОЗУ и по 1 ядру на копию. 10 копий.

Исходя из заданных требований, проект будет состоять из следующих компонентов:

1) База данных (DB).
2) Система кеширования (Cache).
3) Фронтенд (Frontend).
4) Бекенд (Backend).
Каждый компонент будет требовать определенное количество вычислительных ресурсов (CPU и RAM), а также иметь специфичные требования к отказоустойчивости и производительности.

# 1) База данных (DB)
Требования:
Отказоустойчивость: 3 копии.
Ресурсы: 4 ГБ ОЗУ, 1 ядро на копию.

Расчет:
Всего ресурсов: 3 копии * 4 ГБ = 12 ГБ ОЗУ, 3 копии * 1 ядро = 3 ядра.

# 2) Система кеширования (Cache)
Требования:

Отказоустойчивость: 3 копии.

Ресурсы: 4 ГБ ОЗУ, 1 ядро на копию.

Расчет:

Всего ресурсов: 3 копии * 4 ГБ = 12 ГБ ОЗУ, 3 копии * 1 ядро = 3 ядра.

# 3) Фронтенд (Frontend)
Требования:

Производительность: Быстрая обработка запросов.

Масштабируемость: 5 копий.

Ресурсы: 50 МБ ОЗУ, 0.2 ядра на копию.

Расчет:

Всего ресурсов: 5 копий * 50 МБ = 250 МБ ОЗУ, 5 копий * 0.2 ядра = 1 ядро.

# 4) Бекенд (Backend)
Требования:

Производительность: Высокая нагрузка на обработку данных.

Масштабируемость: 10 копий.
Ресурсы: 600 МБ ОЗУ, 1 ядро на копию.

Расчет:
Всего ресурсов: 10 копий * 600 МБ = 6 ГБ ОЗУ, 10 копий * 1 ядро = 10 ядер.

Итого:
Всего CPU: 3 (DB) + 3 (Cache) + 1 (Frontend) + 10 (Backend) = 17 ядер.
Всего RAM: 12 ГБ (DB) + 12 ГБ (Cache) + 250 МБ (Frontend) + 6 ГБ (Backend) ≈ 30.25 ГБ ОЗУ (округлим до 32 ГБ).

Упаковка в чарт для деплоя в разные окружения Для упаковки проекта в чарт Helm необходимо описать ресурсы и конфигурации для каждого компонента отдельно. Чарт должен поддерживать различные профили (различные окружения, такие как dev, staging, production), где требования к количеству копий и ресурсам могут варьироваться.

Пример структуры чарта:
1) Chart.yaml: Основной файл чарта, содержащий метаданные (название, версия, зависимость и т.д.).
2) values.yaml: Файл с параметрами по умолчанию для настройки (количество копий, ресурсы и т.д.).
3) templates/: Директория с шаблонами Kubernetes-ресурсов (Deployment, Service, ConfigMap и т.д.).

# Заключение

Проект требует значительного количества вычислительных ресурсов для обеспечения высокой производительности и отказоустойчивости. Общая сумма составляет около 17 ядер CPU и 32 ГБ оперативной памяти.
