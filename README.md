# Проект Kittygram
С помощью данного сервиса пользователи могут добавлять своих котов, их достижения, выбирать цвет питомца и даже прикреплять их фотографии!

## Задачи, выполненные с помощью сервиса GitHub Actions:
- Настройка и запуск проекта Kittygram в контейнерах
- Настройка автоматического тестирования и деплой этого проекта на удалённый сервер
 ## При пуше в ветку main:
- Проект тестируется
- В случае успешного прохождения тестов образы обновляюься на Docker Hub
- На сервере запускаются контейнеры из обновлённых образов.

# Запуск проекта в контейнерах
### Выполните последующие действия:
- Подключитесь к удалённому серверу
- Создайте директорию kittygram:
```
mkdir kittygram
```
- Установите Docker compose:
```
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin
```
- Создайте .env файл и наполните его по примеру:
```
touch .env
```
```
SECRET_KEY=...
DEBUG_STATUS=True
ALLOWED_HOSTS=...
POSTGRES_DB=...
POSTGRES_USER=...
POSTGRES_PASSWORD=...
DB_NAME=...
DB_PORT=5432
DB_HOST=db
```
- Скопируйте docker-compose файл и запустите его:
```
scp -i path_to_SSH/SSH_name docker-compose.production.yml username@server_ip:/home/username/kittygram/docker-compose.production.yml
```
```
sudo docker compose -f docker-compose.production.yml up -d
```
- Примените миграции:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```
- Соберите статику:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
# Разработчик: [Аринов Данияр](https://github.com/vegitobluefan)