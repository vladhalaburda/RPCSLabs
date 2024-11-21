# Знайомство з GIT

1. Вперше створюємо каталог нашого майбутнього репозиторія
[screen1](screens/screen1.png)
2. Створюємо тестовий index.html файл, та вносимо туди будь який зміст.
[screen2](screens/screen2.png)
3. Далі потрібно ініціалізувати репозиторій (його створити) за допомогою команди
```bash
	git init .
```
Після чого ми побачимо що після нашого каталогу додалося назва гілки (main)
4. Тепер ми будемо додавати наш файл index.html до репозиторію за допомогою команди
```bash
	git add index.html
```
[screen3](screens/screen3.png)
5. Також ми застосували команду 
```bash
	git status
```
Адже для того щоб перевірити те що файл index.html було додано.
6. Тепер створимо коміт наших змін
```bash
	git commit -m "init commit"
```
[screen4](screens/screen4.png)
7. Далі змінемо зміт index.html та подивимось git status
[screen5](screens/screen5.png)
Ми можемо побачити що було ідентифіковано зміну зміста у файлі index.html
Червоний колір означає те що ці зміни не було додано до коміту.
Додаємо
[screen6](screeens/screen6.png)
Та обгортовуємо у новий коміт з назвою Add tags
[screen7](screens/screen7.png)
## Робота з логами
Для доступу у логи дій у GIT використовуємо команду
```bash
	git log
```
[screen8](screens/screen8.png)

Також ця команда має багато параметрів щодо форатування виводу даних
[screen9](screens/screen9.png)
Для більш зручності можна задати параметри форматування логів у конфігу, щоб кожного разу не писати купу операторів
[screen10](screens/screen10.png)
Перевіряємо це, далі використовуємо команду
```bash
	git checkout <hash>
```
Для переходу на коміт який ми побачили у логах.
[screen11](screens/screen11.png)
## Робота з тегами
Для створювання тегів застосуємо команду
```bash
	git tag <tag-name>
```
та подивимося у логи що тег було успішно створенно.
[screen12](screens/screen12.png)
## Можливості тегів
За допомогою тегів ми можемо розділити якусь кількість комітів для того щоб працювати з ними окремо
Наприклад:
[screen13](screens/screen13.png)
Переходимо у коміти з тегом v1
[screen14](screens/screen14.png)
Переходимо у останній коміт з тегом v1
[screen15](screens/screen15.png)
Перелік усіх тегів можна подивитись за допомогою команди ```git tag```
## Можливості checkout
В перше ми перемкнемося на гілку main
```bash
	git switch main
```
У файл index.html я додав HTML-скелет.
[screen15](screens/screen15.png)
Далі перевіряємо статус репозиторія, та відкатуємо зміни у фалі index.html
[screen16](screens/screen16.png)
Також для відкатування використовується команда 
```bash
	git reset
```
[screen17](screens/screen17.png)
## Можливості revert
Тепер розглянемо можливість відкатування змін вже у коміті.
Змінемо зміст index.html
[screen18](screens/screen18.png)
Потім додаємо ці зміни у комміт Oops, та відкатуємось
[screen19](screens/screen19.png)
Усі ці дії можемо побачити у логах
[screen20](screens/screen20.png)
## Можливості reset
За допомогою команди
```bash
	git reset 
```
Ми можемо перемкнутися до того стану HEAD, до котрого потрібно
Наприклад на зображені внизу показано перехід до стану останнього коміту за тегом v1
[screen21](screens/screen21.png)
## Видалення тегу
Видаляємо тег за допомогою оператору d
[screen22](screens/screen22.png)
## Зміна змін коміту
Якщо ми зрозуміли що нам потрібно, у попередньому коміті щось змінити використовуємо команду git commit з оператором --amend
Наприклад:
Ми додаємо у наш файл коментар з позначкою автора
[screen23](screens/screen23.png)
Додаємо його у коміт Added Author name, але потім, загадали що забули додати пошту, та додаємо також пошту.
Та додаємо у останній коміт та зазначемо нове імя коміту за допомогою --amend

[screen24](screens/screen24.png)
## Робота з гілками
Для демонстрації роботи з гілками створемо та одразу перейдемо у гілку style
```bash
git switch -c style
```
за допомогою оператора с ми створюємо гілку.
у ній створюємо файл ```style.css```
додаємо у коміт. Потім підключаємо таблицю стилей у index.html

[screen25](screens/screen25.png)

Потім перейдемо до гілки main, у якій ми не бачимо змін які ми тільки що зробили у гілці style

[screen26](screens/screen26.png)

Потім у гілці style та main додамо README

[screen27](screens/screen27.png)

Перевіремо це у логах

[screen28](screens/screen28.png)

Потім об'єднаємо обидві гілки у одну гілку main за допомогою команди
```bash
git merge <branch-name>
```
[screen29](screens/screen29.png)


Одже давайте тепер створемо конфлікт при об'єднанні гілок.
1. Додаймо у гілці main зміни у index.html додавши HTML-скелет.

[screen30](screens/screen30.png)

2. Потім перейдемо до гілки style та спробуэмо об`єднати.

[screen31](screens/screen31.png)

Ми бачимо що у нас цього не вийшло, та потім у файлі index.html ми можемо побачити саме чому.
Поки що скасовуємо об'єднання за допомогою оператору --abort
3. Змінюємо зміст index.html, а саме додаємо теж самі зміни які були й у гілці style.

[screen32](screens/screen32.png)

Конфлікт було вирішено.

Тепер переходемо до коміту який знаходится на два кроки назад від теперешнього за допомогою команди
```bash
git reset --hard HEAD¬2
```
та перевіряємо логи.

[screen33](screens/screen33.png)

## Можливості rebase

