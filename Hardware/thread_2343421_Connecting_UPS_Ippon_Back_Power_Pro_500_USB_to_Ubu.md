---
title: "Connecting UPS Ippon Back Power Pro 500 USB to Ubuntu server 16.04"
date: 2016-11-16
forum: Hardware
---

### Post by shindax on 2016-11-16
Hallo. I have a problem with UPS to Ubuntu server connection. Did by google answers. Installed a nut. Config files contents:

[COLOR=#000000][FONT=&amp]nuf.conf
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]MODE=standalone

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]upsd.conf
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]LISTEN 127.0.0.1 3493

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]upsd.users
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]password  = password[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]actions = SET[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]instcmds = ALL[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]upsmon master

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]upsmon.conf
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]RUN_AS_USER nut[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]MONITOR ippon@localhost 1 user password master[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]MINSUPPLIES 1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]NOTIFYCMD /sbin/upssched[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]POLLFREQ 5[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]POLLFREQALERT 5[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]HOSTSYNC 15[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]DEADTIME 15

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]type and get:

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]#lsusb
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 003 Device 003: ID 4242:0008 USB Design by Example[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 003 Device 004: ID 0665:5161 Cypress Semiconductor USB to Serial[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]#upsc ippon@localhost
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Init SSL without certificate database[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Error: Driver not connected

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]#service nut-server status
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]&#9679; nut-server.service - LSB: Network UPS Tools initscript[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Loaded: loaded (/etc/init.d/nut-server; bad; vendor preset: enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Active: active (running) since &#1055;&#1085; 2016-11-14 09:18:20 +07; 25min ago[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]     Docs: man:systemd-sysv-generator([/FONT][/COLOR][IMG]http://forum.ubuntu.ru/Smileys/webby/cool.gif[/IMG]
[COLOR=#000000][FONT=&amp]  Process: 12519 ExecStop=/etc/init.d/nut-server stop (code=exited, status=0/SUC[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Process: 12528 ExecStart=/etc/init.d/nut-server start (code=exited, status=0/S[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    Tasks: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Memory: 436.0K[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]      CPU: 90ms[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   CGroup: /system.slice/nut-server.service[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]           &#9492;&#9472;12539 /lib/nut/upsd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer upsd[12538]: Can't connect to UPS [ippon] (blazer[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer upsd[12539]: Startup successful[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer nut-server[12528]:    ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer systemd[1]: Started LSB: Network UPS Tools initsc[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:26 shubuntuServer upsd[12539]: User [/FONT][/COLOR][EMAIL="user@127.0.0.1"]user@127.0.0.1[/EMAIL][COLOR=#000000][FONT=&amp] [/FONT][/COLOR][COLOR=#000000]logged into UPS [ippon][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:23:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:28:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:33:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:38:21 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:43:21 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]lines 1-22/22 (END)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9679; nut-server.service - LSB: Network UPS Tools initscript[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Loaded: loaded (/etc/init.d/nut-server; bad; vendor preset: enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Active: active (running) since &#1055;&#1085; 2016-11-14 09:18:20 +07; 25min ago[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]     Docs: man:systemd-sysv-generator([/FONT][/COLOR][IMG]http://forum.ubuntu.ru/Smileys/webby/cool.gif[/IMG]
[COLOR=#000000][FONT=&amp]  Process: 12519 ExecStop=/etc/init.d/nut-server stop (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Process: 12528 ExecStart=/etc/init.d/nut-server start (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    Tasks: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Memory: 436.0K[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]      CPU: 90ms[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   CGroup: /system.slice/nut-server.service[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]           &#9492;&#9472;12539 /lib/nut/upsd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer upsd[12538]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer upsd[12539]: Startup successful[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer nut-server[12528]:    ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:20 shubuntuServer systemd[1]: Started LSB: Network UPS Tools initscript.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:18:26 shubuntuServer upsd[12539]: User [/FONT][/COLOR][EMAIL="user@127.0.0.1"]user@127.0.0.1[/EMAIL][COLOR=#000000][FONT=&amp] logged into UPS [ippon][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:23:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:28:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:33:20 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:38:21 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:43:21 shubuntuServer upsd[12539]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]# service nut-server restart[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]# service nut-server status
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]&#9679; nut-server.service - LSB: Network UPS Tools initscript[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Loaded: loaded (/etc/init.d/nut-server; bad; vendor preset: enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Active: active (running) since &#1055;&#1085; 2016-11-14 09:44:31 +07; 3s ago[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]     Docs: man:systemd-sysv-generator([/FONT][/COLOR][IMG]http://forum.ubuntu.ru/Smileys/webby/cool.gif[/IMG]
[COLOR=#000000][FONT=&amp]  Process: 13407 ExecStop=/etc/init.d/nut-server stop (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Process: 13416 ExecStart=/etc/init.d/nut-server start (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    Tasks: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   Memory: 440.0K[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]      CPU: 24ms[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]   CGroup: /system.slice/nut-server.service[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]           &#9492;&#9472;13426 /lib/nut/upsd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer systemd[1]: Starting LSB: Network UPS Tools initscript...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer nut-server[13416]:  * Starting NUT - power devices information server and drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer upsd[13425]: listening on 127.0.0.1 port 3493[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer upsd[13425]: Can't connect to UPS [ippon] (blazer_usb-ippon): No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer upsd[13426]: Startup successful[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer nut-server[13416]:    ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#1085;&#1086;&#1103; 14 09:44:31 shubuntuServer systemd[1]: Started LSB: Network UPS Tools initscript.

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]/lib/nut/blazer_usb file presents. Sometimes get a message : Broadcast from [/FONT][/COLOR][COLOR=#000000][FONT=&amp]nut@shubuntuServer (UPS ippon@localhost is unavailable[/FONT][/COLOR][COLOR=#000000][FONT=&amp]

[/FONT][/COLOR][FONT=Ubuntu Beta][COLOR=#000000]I tried to do the same with another UPS different model, but with the same connection chip, and got same results. 
What i do wrong? 
What means user@127.0.0.1? [/COLOR][/FONT]One user registered in system. 
[COLOR=#000000]What is a blazer_usb-ippon file, and where i can find it?[/COLOR]
In system [FONT=Ubuntu Beta][COLOR=#000000]T[/COLOR][/FONT]hank you in advance.

---

