# Гайд по курсу "Основы работы с Git"*
* *гайд во втором разделе, в первом разделе демонстрирую какой я ~~умный и находчивый~~ скромный*


# Полезное предисловие

## Учимся в дороге

### Нудное напутствие (по заданию разные возможности MARKDOWN использовать нужно, так что терпите)

Ученье - свет, а неученых - тьма.
Сказано давно, не нами, и не так, но чертовски верно.
Как быть, если отсутвие свободного времени не позволяет идти к свету? 
Для жителей больших городов, подолгу находящихся в дороге между офисом и домом (только не за рулем!!! тем более не за рулем электропоезда!!!), готов поделиться рецептом, как учиться в пути, включая выполнение практических заданий.
Испольуйте свой смартфон. Даже старенький смартфон c ОС Android сгодится для прохождения этого курса.
Рекомендации ниже успешно опробованы на Xiaomi Redmi Note Pro 6, но уверен, доступны и на других смартфонах.

### К делу...

Итак, что вам понадобится для успешного освоения курса "Основы работы с Git" от Yandex Практикум на смартфоне:

1. Приложение [Yandex Практикум](https://play.google.com/store/apps/details?id=ru.yandex.practicum.flutter_practicum "Я укажу тебе дорогу к свету!"), с помощью которого легко и удобно учиться в дороге.

![Yandex Практикум](./ypractice_ico.png "Ученьесвет...")

2. Приложение [Termux](https://play.google.com/store/apps/details?id=com.termux "Нисы, *япон.*, означает "Я так 100 раз уже делал!"), приложение, котрое позволяет превратить телефон в мини-станцию Linux с терминалом.

![Termux](./termux_ico.png "Дапребудетсиластобой...")

3. Браузер, любой, обычно установлен по умолчанию.

Рецепт на самом деле прост:

1. Берем в руки телефон, устранвливаем из Google Play приложение Yandex Практикум, выбираем бесплатные курсы, среди них найдется и тот самый, "Основы работы с Git".
2. Регистрируемся на курсе.
3. Устанавливаем Termux из Google Play
4. Запускаем Termux и устанавливаем в консоли:
    
    -Git*:
    
    ```bash
        $ pkg install git
    ```
    * *главный герой этого романа*
    
    -OpenSSH*:
    
    ```bash
        $ pkg install openssh
    ```
    * *с этим пакетом установится утилита ssh-keygen, используемая в курсе*
    
    -Nano*:
    
    ```bash
        $ pkg install nano
    ```
    * *консольный текстовый редактор с подсветкой синтаксиса различных ЯП. Можно при желании использовать любой графический редактор с GUI и подсветкой синтаксиса, но работать в одном консольном окне (терминал + редактор) по мне удобнее и быстрее, чем перемещаясь между несколькими приложениями. "У каждого свой вкус" - как бывало говаривал кот Васька...*

5. Определяем домашний каталог* пользователя:

    ```bash
        $ echo ${HOME}
    ```
    * *у меня это /data/data/com.termux/files/home, у вас может быть другой путь к домашнему каталогу, важна суть - здесь создаем тренировчные каталоги для курса, которые будем использовать как репозитории git (большой привет от git init), а также каталог .ssh для хранения ключей SSH (такой же большой привет от ssh-keygen)*

    ![Домашний каталог](./home.jpg "Мойдомоякрепость...")

6. Создаем* в домашнем каталоге скрытый каталог .ssh:

    ```bash
        $ cd ~
        $ mkdir .ssh
        $ ls -al
    ```
    * *первая команда - переход в домашний каталог, вторая команда - создание скрытого каталога .ssh, третья команда - убедиться, что не показалось...*

7. Открываем приложение Yandex Практикум и поехали!

### P.S. пара-тройка советов, которые мне сэкономили немало времени:

1. Присмотритесь к возможностям консольного терминала Termux, они позволяют очень споро работать при небольшом навыке:

![Интерфейс Termux](./termux.jpg "Айлбибек...")

Несколько удобств*:

-CTRL + a - переход в начало строки
-CTRL + e - переход в конец строки
-CTRL + c  - прервать выполнение любой комады
    ...
ALT + d - удалить целиком слово, расположенное за курсором
    ...
TAB - двойной клик по клавише дополняет команды и пути
Стралка вверх - переход по логу команд терминала к предыдущим (вверх)
Стрелка вниз - переход по логу команд терминала к последующим (вниз)

* *я указал здесь те клавиатурные комбинации, которые испольую в работе регулярно сам, но если интересно - найдете много других интересных комбинаций, которые возможно подойдут именно вам*

2. Присмотритесь к возможностям консольного редактора Nano, они тоже здорово ускоряют работу:

![Интерфейс Nano](./nano.jpg "Айнанэ..")

Несколько удобств*:

CTRL + a - переход в начало строки
CTRL + e - переход в конец строки
CTRL + \ - заменить любое слово в тексте на другое
CTRL + o - сохранить изменения в редактируемом файле
CTRL + x - закрыть редактируемый файл (с сохранением или без)
    ...

* *я указал здесь те клавиатурные комбинации, которые испольую в работе регулярно сам, но если интересно - найдете много других интересных комбинаций, которые возможно понравятся вам*

3. Когда будете создавать SSH-ключи (при помощи команды ssh-keygen) не выдумывайте пожалуйста для создаваемых ключей никаких собственных названий!!! Трижды проклянете эти названия, когда у вас и соединение по SSH с GitHub вроде работает, и одновременно синхронизация репозитория на тот же GitHub не проходит из-за проблем с ключами. Оставьте параметры по умолчанию - нервы крепче будут :) 

---------------------------------------------------------------------------------------------------------------------------------

$ git init # создать репозиторий в текущей папке

$ git init "repo_name" # создать новую папку с именем "repo_name" и создать в нем репозиторий

$ git init /path/to/repo/ # создать репозиторий в указанную директорию

$ git clone "/path/to/repo/" # скопировать локальный репозиторий в текущую директорию

$ git clone "https://repository_link" # скопировать удаленный репозиторий в текущую директорию


Работа с ветками

$ git branch #отображение существующих веток
$ git branch "branch_name" #создание новой ветки с именем "branch_name" (без кавычек)
$ git checkout "branch_name" # переключение на ветку с именем "branch_name"


Удаление коммита (для GitHub)

$ git reset --hard "commit-code"
$ git push --force


Просмотр статистики репозитория

$ git log # показывает историю коммитов текущей ветки 
$ git status # статус файлов в текущем репозитории


---------------------------------------------------------------------------------------------------------------------------------
