# gulp-pug-starter
![gulp-pug-starter](https://i.imgur.com/0AG0txq.png)

## Особенности
* сборка предназначена для автоматизации задач в повседневной front-end разработке
* именование классов по [БЭМ](https://ru.bem.info/)
* использование препроцессора [Pug](https://pugjs.org/api/getting-started.html)
* использование препроцессора [SCSS](https://sass-lang.com/)
* использование транспайлера [Babel](https://babeljs.io/) для поддержки современного JavaScript (ES6) в браузерах
* использование [Webpack](https://webpack.js.org/) для сборки JavaScript-модулей
* использование CSS-сетки [smart-grid](https://github.com/dmitry-lavrik/smart-grid) для быстрой адаптивной вёрстки

## Установка
* установите [Yarn](https://yarnpkg.com/en/docs/install)

> Yarn - это современная альтернатива npm. Yarn работает с тем же файлом ```package.json``` и так же скачивает необходимые модули в папку ```node_modules```, но делает это намного быстрее.

* скачайте сборку: ```git clone https://github.com/andreyalexeich/gulp-pug-starter.git```
* установите ```gulp``` глобально: ```yarn global add gulp-cli```
* перейдите в скачанную папку со сборкой: ```cd gulp-pug-starter```
* скачайте необходимые зависимости: ```yarn```
* чтобы начать работу, введите команду: ```yarn run dev``` (режим разработки)
* чтобы собрать проект, введите команду ```yarn run build``` (режим сборки)

Если вы всё сделали правильно, у вас должен открыться браузер с локальным сервером.
Режим сборки предполагает оптимизацию проекта: сжатие изображений, минифицирование CSS и JS-файлов для загрузки на сервер.

## Плагины
* [browser-sync](https://browsersync.io/docs/gulp) - живая перезагрузка веб-страницы при внесении изменений в файлы вашего проекта
* [webpack-stream](https://github.com/shama/webpack-stream) - интеграция Webpack с Gulp 
* [eslint](https://eslint.org/) - линтер для JS-файлов
* [gulp-autoprefixer](https://www.npmjs.com/package/gulp-autoprefixer) — автоматически расставляет вендорные префиксы в CSS в соответствии с сервисом [Can I Use](https://caniuse.com/)
* [gulp-uglify](https://www.npmjs.com/package/gulp-uglify) — минификация JS-файлов
* [gulp-pug](https://www.npmjs.com/package/gulp-pug) — компиляция Pug в HTML
* [gulp-pugbem](https://www.npmjs.com/package/gulp-pugbem) - шорткаты БЭМ в Pug
* [gulp-sass](https://www.npmjs.com/package/gulp-sass) — компиляция SCSS в CSS
* [gulp-group-css-media-queries](https://www.npmjs.com/package/gulp-group-css-media-queries) - группировка ```@media```
* [gulp-clean-css](https://www.npmjs.com/package/gulp-clean-css) — минификация CSS-файлов
* [gulp-sourcemaps](https://www.npmjs.com/package/gulp-sourcemaps) - карта стилей
* [gulp-rename](https://www.npmjs.com/package/gulp-rename) — переименование файлов, добавление суффиксов и префиксов (например, добавление суффикса ```.min``` к минифицированным файлам)
* [gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin) — сжатие изображений PNG, JPG, GIF и SVG (включая дополнительные плагины для оптимизации)
* [gulp-webp](https://www.npmjs.com/package/gulp-webp) - конвертация изображений в современный формат WebP
* [gulp-favicons](https://github.com/evilebottnawi/favicons) — генератор фавиконок для вашего проекта
* [gulp-if](https://www.npmjs.com/package/gulp-if) - запуск заданий только тогда, когда это нужно
* [gulp-replace](https://www.npmjs.com/package/gulp-replace) - замена строк
* [gulp-plumber](https://www.npmjs.com/package/gulp-plumber) — оповещения в командной строке (например, ошибки в SCSS/Sass)
* [gulp-debug](https://www.npmjs.com/package/gulp-debug) — отладка в терминале
* [gulp-watch](https://www.npmjs.com/package/gulp-watch) — отслеживание изменений в ваших файлах проекта
* [gulp-clean](https://www.npmjs.com/package/gulp-clean) — удаление файлов и папок
* [yargs](https://www.npmjs.com/package/yargs) - получение аргументов командной строки в Node.js

## Файловая структура

```
gulp-pug-starter
├── dist
├── src
│   ├── img
│   ├── styles
│   ├── views
│   ├── index.js
│   └── .htaccess
├── gulpfile.babel.js
├── webpack.config.js
├── package.json
├── .babelrc
├── .eslintrc.json
└── .gitignore
```

* Корень папки:
	* ```.babelrc``` — настройка ES6
	* ```.eslintrc.json``` — настройка ESLint
	* ```.gitignore``` – запрет на отслеживание файлов Git'ом
	* ```gulpfile.babel.js``` — настройки Gulp
	* ```webpack.config.js``` — настройки Webpack
	* ```package.json``` — список зависимостей
* Папка ```src``` - используется во время разработки:
	* JS-файл, в который импортируются модули, плагины и содержащий в себе остальные скрипты: ```src/index.js```
	* Pug-файлы: ```src/views```
	* SCSS-файлы: ```src/styles```
	* изображения: ```src/img```
	* конфигурационный файл веб-сервера Apache с настройками [gzip](https://habr.com/ru/post/221849/) (сжатие без потерь): ```src/.htaccess```
* Папка ```dist``` - папка, из которой запускается локальный сервер для разработки (при запуске ```yarn run dev```)

## Рекомендации по использованию
* придерживайтесь изначальной структуры папок и файлов
* придерживайтесь компонентного подхода к разработке сайтов
	* каждый БЭМ-блок имеет свою папку внутри ```src/views/blocks/```. Папка одного БЭМ-блока содержит в себе один Pug-файл, один SCSS-файл и один JS-файл (если у блока используется скрипт)
	* Pug-файл блока импортируется в файл ```src/views/index.pug```
	* SCSS-файл блока импортируется в файл ```src/views/blocks/_blocks.scss```, который в свою очередь импортируется в файл ```src/styles/main.scss```
	* JS-файл блока импортируется в ```src/index.js```
* из всех SCSS-файлов компилируется только ```main.scss```. Остальные стилевые файлы импортируются в него
* компоненты (например, иконки, кнопки) оформляются в Pug с помощью примесей 
	* каждый компонент имеет свою папку внутри ```src/views/components```
	* папка одного компонента содержит в себе один Pug-файл и один SCSS-файл
	* Pug-файл компонента импортируется в файл ```src/views/pages/templates/main.pug```, который в свою очередь импортируется в файл ```src/views/index.pug```
	* SCSS-файл компонента импортируется в файл ```src/views/components/_components.scss```, который в свою очередь импортируется в файл ```src/styles/main.scss```
* все сторонние библиотеки устанавливаются в папку ```node_modules```
	* для их загрузки воспользуйтеcь командой ```yarn add package_name```
	* для подключения JS-файлов библиотек импортируйте их в файл ```src/index.js``` с помощью ```import```, например: 
	```javascript 
	import $ from "jquery";
	```
	* для подключения стилевых файлов библиотек импортируйте их в файл ```src/styles/utils/_libs.scss``` (который в свою очередь импортируется в файл 
	```src/styles/main.scss```) с помощью директивы ```@import```
* в вёрстку подключаются только минифицированные CSS и JS-файлы.

## Именование классов по БЭМ
В сборке используется компонентный подход к разработке сайтов. Для более удобного написания разметки по БЭМ используется плагин шорткатов для препроцессора Pug. Пример 
использования:

**Pug**
```jade
header.header
    nav.menu
        a(href="#")._logo Company
        .list
            a._item.-active(href="#") Home
            a._item(href="#") News
            a._item(href="#") Gallery
            a._item(href="#") Partners
            a._item(href="#") About
            a._item(href="#") Contacts
    h1._title Hello, World!
    .myslider._myslider
        ._slide Content
        ._slide.-active Content
        ._slide Content
    p._text Good weather
```
**Результат**
```html
<header class="header">
    <nav class="menu">
        <a class="menu__logo" href="#">Company</a>
        <div class="list">
            <a class="list__item list__item--active" href="#">Home</a>
            <a class="list__item" href="#">News</a>
            <a class="list__item" href="#">Gallery</a>
            <a class="list__item" href="#">Partners</a>
            <a class="list__item" href="#">About</a>
            <a class="list__item" href="#">Contacts</a>
        </div>
    </nav>
    <h1 class="header__title">Hello, World!</h1>
    <div class="myslider header__myslider">
        <div class="myslider__slide">Content</div>
        <div class="myslider__slide myslider__slide--active">Content</div>
        <div class="myslider__slide">Content</div>
    </div>
    <p class="header__text">Good weather</p>
</header>
```

## CSS-сетка smart-grid
В сборщик включена CSS-сетка [smart-grid](https://github.com/dmitry-lavrik/smart-grid) от [Дмитрия Лаврика](https://dmitrylavrik.ru/). Она позволяет избавиться от 
лишних классов в разметке за счёт использования примесей в SCSS и ускоряет адаптивную вёрстку. Конфигурация уже настроена в соответствии с сеткой [Bootstrap](https://getbootstrap.com/). Пример использования:

**SCSS**
```scss
.items{
    @include row-flex();
    @include md(justify-content, center);
 
    .item{
        @include col();
        @include size(3);
        @include size-md(5);
        @include size-xs(10);
    }
}
```
**Результат**
```css
.items {
    display: flex;
    flex-wrap: wrap;
    margin-left: -15px;
    margin-right: -15px;
}
.items .item {
    box-sizing: border-box;
    margin-left: 15px;
    margin-right: 15px;
    word-wrap: break-word;
    width: calc(100% / 12 * 3 - 30px);
}
@media screen and (max-width: 992px) {
    .items {
        justify-content: center;
    }
    .items .item {
        width: calc(100% / 12 * 5 - 30px);
    }
}
@media screen and (max-width: 576px) {
    .items .item {
        width: calc(100% / 12 * 10 - 30px);
    }
}
```

## WebP 
В сборщик включена поддержка WebP. WebP — это формат графики, разработанный Google в 2010 году. Он был создан как альтернатива PNG и JPG и отличается от них гораздо 
меньшим размером при том же качестве изображения. Подробная информация по использованию [тут](https://vk.com/@vk_it-webp).

## Нужен SCSS без Pug?
Используйте [эту](https://github.com/andreyalexeich/gulp-scss-starter/) сборку.

## Контакты
* ВКонтакте: [@andreyalexeich](https://vk.com/andreyalexeich)
* Telegram: [@andreyalexeich](https://t-do.ru/andreyalexeich)