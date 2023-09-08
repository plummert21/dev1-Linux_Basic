## Part 1. Установка ОС

- Ubuntu Version \
![Ubuntu Version](img/part1.png)
>Ubuntu Version

## Part 2. Создание пользователя

- Добавление пользователя \
![Add user](img/part2.png)

- Вывод команды `cat /etc/passwd` \
![Users](img/part2_2.png)

## Part 3. Настройка сети ОС

- Изменение hostname \
![Hostname](img/hostname.png)

- Изменение timezone \
![Timezone](img/timezone.png)

- Сетевые интерфейсы \
![Network](img/network_interface.png)
>lo (loopback device) – виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost.

- IP-адрес хоста от DHCP \
![IP](img/ip_host.png)
>DHCP (Dynamic Host Configuration Protocol) – сетевой протокол, позволяющий сетевым устройствам автоматически получать IP-адрес и другие параметры, необходимые для работы в сети TCP/IP. Данный протокол работает по модели «клиент-сервер». Для автоматической конфигурации компьютер-клиент на этапе конфигурации сетевого устройства обращается к серверу DHCP и получает от него нужные параметры.

- Внешний IP-адрес и адрес шлюза (gw) \
![GW](img/ip_gw.png)

- Статичные настройки ip, gw, dns \
![COMMAND](img/edit_ip_settings.png) \
![STATIC_IP](img/static_ip_settings.png) \
![APPLY_SETTINGS](img/apply_settings.png)

- Проверка сетевых настроек, заданных в предыдущем пункте \
![NEW_SETTINGS](img/new_ip_settings.png)

- Ping 1.1.1.1 и ya.ru \
![PING_REPORT](img/ping_report.png)

## Part 4. Обновление ОС

- ОС обновлена. Обновления отсутствуют. \
![IP](img/os_upgrade.png)
>Команда `sudo apt-get update` обновляет списки пакетов, которые доступны для загрузки в системе. \
>Команда `sudo apt-get upgrade` обновляет установленные пакеты (обновляет ОС).

## Part 5. Использование команды sudo

- Добавление пользователя в группу `sudo` и изменение hostname от его имени. \
![USR](img/sudo_usr_change_hostname.png)
>Команда `sudo` предоставляет возможность пользователям выполнять команды `от имени суперпользователя root`.

## Part 6. Установка и настройка службы времени

- Часовой пояс \
![TIMEZONE](img/timezone_check.png)

- NTP включена \
![NTP](img/ntp.png)

## Part 7. Установка и использование текстовых редакторов

- Запись никнейма \
![VIM](img/vim_txt.png)
>VIM - для выхода с сохранением нажать `ESC` для выхода из режима редактирования. После ввод `:wq!` и `<Enter>`

![NANO](img/nano_txt.png)
>NANO - для cохранения нажать `<Ctrl>+O`, для выхода нажать `<Ctrl>+X` или сразу нажать `<Ctrl>+X` и затем подтвердить `<YES>`

![MCEDIT](img/mcedit_txt.png)
>MCEDIT - для cохранения нажать `<F2>`, для выхода нажать `<F10>` или сразу нажать `<F10>` и затем подтвердить `<YES>`

- Изменение содержимого файлов и выход без сохранения \
![VIM](img/vim_change.png)
>VIM - для выхода без сохранения нажать `ESC` для выхода из режима редактирования. После ввод `:q!` и `<Enter>`

![NANO](img/nano_change.png)
>NANO - для выхода без cохранения нажать `<Ctrl>+X` и затем подтвердить `<NO>`

![MCEDIT](img/mcedit_change.png)
>MCEDIT - для выхода без cохранения нажать `<F2>` и затем подтвердить `<NO>`

- Поиск и замена
>VIM \
![VIM_FIND](img/vim_find.png)
![VIM_REPLACE](img/vim_replace.png)

>NANO \
![NANO_FIND](img/nano_find.png) \
>для поиска нажать `<Ctrl>+W`, ввести искомый текст и нажать `<Enter>` \
>для замены нажать `<Ctrl>+\`, ввести искомый текст и нажать `<Enter>`, ввести новый текст и нажать `<Enter>`, выбрать вариант замены

>MCEDIT \
![MCEDIT_FIND](img/mcedit_find.png) \
>для поиска нажать `<F7>`, ввести искомый текст и нажать `<Enter>` \
![MCEDIT_REPLACE](img/mcedit_replace.png) \
>для замены нажать `<F4>`, ввести искомый и новый текст и нажать `<Enter>`

## Part 8. Установка и базовая настройка сервиса SSHD

- Установка SSH \
`sudo apt-get install openssh-server`

- SSH в автозагрузку \
`sudo systemctl enable sshd`

- Конфигурация SSHD \
`sudo vim /etc/ssh/sshd_config` \
![SERVICE_SSHD](img/sshd_config.png)

- SSHD в процессах \
![SERVICE_SSHD](img/service_sshd.png)
> ключ -A - все процессы

- Перезагрузка системы \
`sudo reboot`

- Вывод команды `netstat -tan` \
![SSHD_LISTEN](img/sshd_listen.png)
>`-t` - Отображать TCP подключения\
>`-a` - Показывать состояние всех сокетов; обычно сокеты, используемые серверными процессами, не показываются. \
>`-n` - Показывать сетевые адреса как числа. netstat обычно показывает адреса как символы. \
>`Proto` - Содержит тип протокола \
>`Recv-Q` - Счётчик байтов не скопированных программой пользователя из этого сокета. \
>`Send-Q` - Счётчик байтов, не подтверждённых удалённым узлом. \
>`Local Address` - Адрес и номер порта локального конца сокета. \
>`Foreign Address` - Адрес и номер порта удалённого конца сокета. \
>`State` - Состояние сокета. \
>`LISTEN` - Сокет ожидает входящих подключений. \
>`0.0.0.0` - это немаршрутизируемый адрес IPv4, который используется в качестве адреса по умолчанию или адреса-заполнителя (localhost).

## Part 9. Установка и использование утилит top, htop

### вывод команды top

- uptime, количество авторизованных пользователей, общая загрузка системы, общее количество процессов, загрузку cpu, загрузку памяти \
>команда `top` \
![TOP_UPTIME](img/top_uptime.png)

> перевод в цветной режим - клавиша `<z>` \
> подсветка столбца сортироваки - клавиша `<x>` \
> переход по столбцам для изменения сортировки - клавиши `<Shift> + <` или `<Shift> + >` 

- pid процесса занимающего больше всего памяти \
![TOP_SORTMEM](img/top_sortmem.png)

- pid процесса, занимающего больше всего процессорного времени \
![TOP_SORTCPU](img/top_sortcpu.png)

### вывод команды htop

- сортировка по PID \
![HTOP_SORTPID](img/htop_sortpid.png)

- сортировка по PERCENT_CPU \
![HTOP_SORTCPU](img/htop_sortcpu.png)

- сортировка по PERCENT_MEM \
![HTOP_SORTMEM](img/htop_sortmem.png)

- сортировка по TIME \
![HTOP_SORTTIME](img/htop_sorttime.png)

- отфильтрованному для процесса sshd \
![HTOP_FILTER](img/htop_filter.png)

- с процессом syslog, найденным, используя поиск \
![HTOP_SEARCH](img/htop_search.png)

- с добавленным выводом hostname, clock и uptime
>настройка через Setup `<F2>` \
![HTOP_HOSTINFO](img/htop_hostinfo.png)

## Part 10. Использование утилиты fdisk

- Запуск команды fdisk -l.
>команда `sudo fdisk -l` \
![FDISK](img/fdisk.png)

> Название жесткого диска - /dev/sda \
> Размер жесткого диска - 25 Gb \
> Количество секторов - 52428800

**Раздел swap физически не размечен на жестком диске, но мы можем посмотреть размер программного swap несколькими способами (см.ниже)**
- swap - 2.2 Gb \
![SWAP](img/swap.png)

## Part 11. Использование утилиты df

- Запуск команды `df` \
![df](img/df.png)
> размер раздела - 11758760 Kb \
> размер занятого пространства - 5198300 Kb \
> размер свободного пространства - 5941352 Kb \
> процент использования - 47% 

- Запуск команды `df -Th` \
![dfth](img/dfth.png)
> размер раздела - 12 Gb \
> размер занятого пространства - 5.0 Gb \
> размер свободного пространства - 5.7 Gb \
> процент использования - 47% \
> тип файловой системы - ext4

## Part 12. Использование утилиты du

- Запуск команды `du` \
![du](img/du.png)

- Размер папок /home \
![duhome](img/duhome.png)

- Размер папок /var \
![duvar](img/duvar.png)

- Размер папок /var/log \
![duvarlog](img/duvarlog.png)

- Размер всего содержимого в /var/log, используя * ***(показывает файлы)*** \
![duvarlogall](img/duvarlogall.png)

## Part 13. Установка и использование утилиты ncdu

- Установка утилиты ***ncdu***. \
![ncduinst](img/ncduinst.png)

- Размер папок /home
> `ncdu -x /home` \
![ncduhome](img/ncduhome.png)

- Размер папок /var
> `ncdu -x /var` \
![ncduvar](img/ncduvar.png)

- Размер папок /var/log
> `ncdu -x /var/log` \
![ncduvarlog](img/ncduvarlog.png)

## Part 14. Работа с системными журналами

- Просмотр /var/log/dmesg *(с возможностью прокрутки)*
> `less /var/log/dmesg` \
![logdmesg](img/logdmesg.png)

- Просмотр /var/log/syslog *(с возможностью прокрутки)*
> `less /var/log/syslog` \
![logsyslog](img/logsyslog.png)

- Просмотр /var/log/auth.log *(с возможностью прокрутки)*
> `less /var/log/auth.log` \
![logauthlog](img/logauthlog.png)

- время последней успешной авторизации, имя пользователя и метод входа в систему
> `grep -i login /var/log/auth.log` \
![loglastauth](img/loglastauth.png) \
> время последней успешной авторизации - 13:14:30 \
> имя пользователя - plummert \
> метод входа в систему - локально

- Перезапук службу SSHd
> `sudo systemctl restart ssh`

- скрин с сообщением о рестарте службы \
![logrestartssh](img/logrestartssh.png)

## Part 15. Использование планировщика заданий CRON

### Запуск команды uptime через каждые 2 минуты, используя планировщик заданий

- Настройка задания
> `crontab -e` \
![cronset](img/cronset.png)

- Строчки в системных журналах о выполнении.
> `tail /var/log/syslog` \
> Для отслеживания появления новых записей использвовать `tail -f /var/log/syslog`
![cronlog](img/cronlog.png)

- Список текущих заданий для CRON
> `crontab -l` \
![crontasks](img/crontasks.png)

### Удаление всех заданий из планировщика CRON.

- Удаление всех заданий для CRON
> `crontab -r`

- Список текущих заданий для CRON
> `crontab -l` \
![crontasksno](img/crontasksno.png)
