# Qo'shni.uz backend (to'liq)

## Ishga tushirish (Windows)
    python -m venv venv
    venv\Scripts\activate
    pip install -r requirements.txt
    python manage.py migrate
    python manage.py createsuperuser     (bu foydalanuvchi avtomatik "admin" bo'ladi)
    python manage.py runserver

Django admin: http://127.0.0.1:8000/admin/  (kategoriya qo'shish, do'kon va dillerni tasdiqlash)
Testlar: python manage.py test

## Telegram kanalga avtomatik e'lon (ixtiyoriy)
    set TELEGRAM_BOT_TOKEN=...
    set TELEGRAM_CHANNEL_ID=@kanal_nomi
Yangi aksiya va chegirmali mahsulot kanalga chiqadi. Berilmasa, o'chiq turadi.

## Applar
users, shops, products, notifications, sourcing (diller so'rovlari), exchange (almashish),
chat, orders, groupbuy, discounts (umumiy aksiya), reviews, dashboard (admin API)

## Asosiy API
auth:     POST /api/auth/register/ , /api/auth/login/ ; GET /api/auth/me/ ; PUT /api/auth/dealer-profile/
shops:    /api/shops/ , /api/shops/my/
products: /api/products/?search=&category=&shop=&discounted=1&ordering=price , /api/categories/
sourcing: /api/sourcing/ , POST /api/sourcing/{id}/offers/ , /close/
exchange: /api/exchange/items/ , /items/matches/ , /api/exchange/proposals/ (+accept, reject, complete)
chat:     /api/chat/messages/?public=1|with=ID&after=ID , /chat/threads/ , /chat/people/
orders:   /api/orders/ , POST /api/orders/{id}/status/
groupbuy: /api/groupbuys/ (+join, close)     campaigns: /api/campaigns/ (+join)
reviews:  /api/reviews/?target=ID            notifications: /api/notifications/ , /notifications/read/
admin:    /api/admin/stats/ , /users/ , /users/{id}/toggle/ , /shops/{id}/verify/ , /dealers/
Token: har so'rovda  Authorization: Token <token>
