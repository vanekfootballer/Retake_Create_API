# Веб-приложение резюме

Этот проект представляет собой простое веб-приложение на Flask для отображения резюме. Оно получает данные об авторе из переменных окружения (.env), а также список репозиториев из GitHub API.

## Функциональность

*   Отображение личной информации (имя, город, Telegram, университет, программа, курс).
*   Отображение списка репозиториев из GitHub.
*   Использует `.env` файл для хранения конфиденциальных данных (токен GitHub).

## Необходимые условия

*   Python 3.6+
*   Установленный pip

## Установка

1.  Установите зависимости:

    ```
    pip install -r requirements.txt
    ```
    Чтобы записать все установленные библиотеки в файл requirements.txt, можно использовать команду:

    ```
    pip freeze > requirements.txt
    ```
   
3.  Настройте переменные окружения:

    *   Создайте файл `.env` в корневой директории проекта.
    *   Добавьте необходимые переменные:

        ```
        FULL_NAME="Ваше имя"
        CITY="Ваш город"
        TELEGRAM="Ваш Telegram никнейм"
        UNIVERSITY="Ваш университет"
        PROGRAM="Ваша программа обучения"
        COURSE="Ваш курс"
        GITHUB_TOKEN="Ваш GitHub токен"
        ```

        Замените значения на свои.  **Важно:** Получите GitHub токен с правами на чтение информации о репозиториях (см. раздел "Как получить GitHub токен").

## Запуск
С помощью команды python app.py запустите приложение

Приложение будет запущено на `http://127.0.0.1:5000/`.

## Структура проекта
|-- app.py # Основной файл приложения Flask
|-- templates/
|  |-- resume.html # Шаблон HTML для отображения резюме
|-- requirements.txt # Список зависимостей Python
|-- .env # Файл с переменными окружения


## Зависимости

*   Flask
*   python-dotenv
*   requests

## Как получить GitHub токен

1.  Перейдите на сайт GitHub и войдите в свою учетную запись.
2.  Перейдите в **Settings** -> **Developer settings** -> **Personal access tokens** -> **Tokens (classic)**.
3.  Нажмите кнопку **Generate new token (classic)**.
4.  Укажите описание токена (например, "Resume App").
5.  **Важно!** Выберите необходимые разрешения (scopes) для токена.  Для данного приложения требуется разрешение **`read:repo`** или **`repo`** (дает полный доступ к приватным/публичным репозиториям).  **ВНИМАНИЕ: Предоставляйте только необходимые разрешения, чтобы обеспечить безопасность вашей учетной записи.**
6.  Нажмите кнопку **Generate token**.
7.  Скопируйте сгенерированный токен и вставьте его в файл `.env` в переменную `GITHUB_TOKEN`.  **Важно: Этот токен будет показан только один раз.  Сохраните его в безопасном месте.**

## HTML Шаблон (resume.html)

HTML-шаблон `resume.html` использует движок шаблонов Jinja2, который предоставляет Flask.  Он получает данные из контекста, переданного функцией `resume` в `app.py`, и отображает их на странице.

## Конфигурация

Настройки приложения, такие как личная информация и GitHub токен, хранятся в файле .env. Это позволяет избежать жесткого кодирования конфиденциальных данных в коде.
