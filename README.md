# Набор правил для Sublime Text 3 для проверки CodeStyle

_Сам CodeStyle находится тут https://www.notion.so/odva/PHP-Code-style-O-b84dcd527e3f46b895d0c9cba3f5cb21_

_**Внимание! В системе должна быть установлена `nodejs`**_

## Установка
- склонировать проект, желательно в домашнюю директорию
- Установить npm-пакеты (`npm i` внутри склонированной папки)
- Установить в Sublime три плагина (нажимаем `command+shift+p`, вводим `install package`, находим пункт установки пакетов, после подгрузки списка пакетов вводим название и выбираем нужный плагин)
  - SublimeLinter
  - SublimeLinter-phpcs
  - SublimeLinter-eslint
- Открыть настройки плагина SublimeLinter (Sublime Text > Preferences > Package Settings > SublimeLinter > Settings) и вставить следующие настройки

```json
{
	"show_panel_on_save": "view",
	"linters": {
		"phpcs": {
			"executable" : ["~/linter/phpcs"],
			"args"       : [
				"--standard=~/linter/rules/phpcs.xml"
			]
		},
		"eslint": {
			"executable" : [
				"node",
				"~/linter/node_modules/eslint/bin/eslint.js"
			],
			"args": [
				"-c",
				"~/linter/rules/eslintrc.json"
			]
		}
	}
}
```

_Если репозиторий клонировали в другое место, надо подправить пути в настройках. И естественно можно дополнить настройки своими =)_

Вот и все. Теперь Sublime должен показывать ошибки  CodeStyle



## Конфликты

SublimeLinter привязывает к комбинации клавиш `ctrl+command+a` открытие окна с ошибками. А это комбинация выравнивания кода из плагина **Alignment** (который у нас почти у всех установлен). Поэтому есть смысл переназначить эту комбинацию у SublimeLinter на другую. Например,`ctrl+command+z` вроде свободен.

Настройки горячих клавиш находятся тут Sublime Text > Preferences > Package Settings > SublimeLinter > Key Bindings
