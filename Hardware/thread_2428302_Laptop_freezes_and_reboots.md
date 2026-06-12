---
title: "Laptop freezes and reboots"
date: 2019-10-02
forum: Hardware
---

### Post by zampieri on 2019-10-02
[SIZE=2][FONT=arial][COLOR=#141414]Hi everyone, newbie here.[/COLOR]

[COLOR=#141414]I have a problem that has been occurring for one month now:[/COLOR]
[COLOR=#141414]once or twice every other day, my laptop freezes, meaning that the screen starts flickering, and then the laptop reboots. The issue sometimes manifests itself by trying to boot several times, but failing. Sometimes I have to hard reboot after the screen freezes.[/COLOR]
[COLOR=#141414]It usually happened when I tried to move the laptop from below, or when I moved the screen after some time.[/COLOR]

[COLOR=#141414]This issue is 'scientifically' happening also when I am trying to train a machine learning model with FastText on a coprus of 230MB, indipendently from using 1 thread or the default settings. Three times out of three, after some time (usually around 20% of the training), the malevolent event happens.[/COLOR]

[COLOR=#141414]I kept track of the CPU temperatures during the last training, with core-0 being at 65°C and core-1 at 57°C (never above 69°C).[/COLOR]

[COLOR=#141414]My laptop is a Lenovo ideapad 310[/COLOR]
[COLOR=#141414]Intel Core i5-7200U CPU@2.50GHz x 4[/COLOR]
[COLOR=#141414]12GB RAM[/COLOR]
[COLOR=#141414]Intel HD Graphics 620 (Kaby Lake GT2) ---> I have also a dedicated NVIDIA GeForce 920M, 2GB[/COLOR]

[COLOR=#141414]The laptop is 2-years old, the battery is not good (it probably lasts ~1 hour max), the charger is not the original Lenovo one, as it stopped working; I bought a KFD charger that suited the voltage.[/COLOR]
[COLOR=#141414]I opened the laptop a couple of days ago to remove some dust from the case and the fan.[/COLOR]

[COLOR=#141414]Dual boot with:[/COLOR]
[COLOR=#141414]Windows 10[/COLOR]
[COLOR=#141414]Ubuntu 18.04.3 LTS[/COLOR]

[COLOR=#141414]98% of the time I use Ubuntu.[/COLOR]

[COLOR=#141414]From /var/log/syslog, this is the last set of messages before I had to hard reboot:[/COLOR]

[COLOR=#141414]Oct 2 15:44:50 MatteoLenovo wpa_supplicant[978]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-61 noise=-109 txrate=1000[/COLOR]
[COLOR=#141414]Oct 2 15:48:01 MatteoLenovo wpa_supplicant[978]: wlp2s0: WPA: Group rekeying completed with 24:01:c7:db:01:74 [GTK=CCMP][/COLOR]
[COLOR=#141414]Oct 2 15:48:33 MatteoLenovo wpa_supplicant[978]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-66 noise=-109 txrate=1000[/COLOR]
[COLOR=#141414]Oct 2 15:49:37 MatteoLenovo wpa_supplicant[978]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-61 noise=-109 txrate=1000[/COLOR]
[COLOR=#141414]Oct 2 15:51:28 MatteoLenovo wpa_supplicant[978]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-65 noise=-109 txrate=1000[/COLOR]
[COLOR=#141414]Oct 2 15:53:51 MatteoLenovo wpa_supplicant[978]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-60 noise=-109 txrate=1000[/COLOR]
[COLOR=#141414]Oct 2 16:14:56 MatteoLenovo systemd[1]: Starting Flush Journal to Persistent Storage...[/COLOR]

[COLOR=#141414]It happened at 15:54.
[/COLOR]
EDIT:[/FONT][/SIZE]
Just now the laptop rebooted itself without crashing, and this is what is shown in syslog:
Oct  2 22:24:20 MatteoLenovo smartcode-stremio.desktop[24120]: [cplayer] Set property: pause=true -> 1
Oct  2 22:24:20 MatteoLenovo smartcode-stremio.desktop[24120]: (Paused) AV: 00:20:40 / 02:22:11 (14%) A-V:  0.000 Cache:  9s+14MB
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Oct  2 22:26:26 MatteoLenovo systemd[1]: Starting Flush Journal to Persistent Storage...
Oct  2 22:26:26 MatteoLenovo kernel: [    0.000000] microcode: microcode updated early to revision 0xb4, date = 2019-04-01
Oct  2 22:26:26 MatteoLenovo systemd-modules-load[239]: Inserted module 'lp'
Oct  2 22:26:26 MatteoLenovo kernel: [    0.000000] Linux version 4.15.0-64-generic (buildd@lgw01-amd64-038) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #73-Ubuntu SMP Thu Sep 12 13:16:13 UTC 2019 (Ubuntu 4.15.0-64.73-generic 4.15.18)



[COLOR=#141414][FONT=&quot]Do you have any advice on such a matter? Can I post any other log?
[/FONT][/COLOR]A friend suggested it could be:
- drivers
- faulty connectivity with the mother boards
- the mother board itself

[COLOR=#141414][FONT=&quot]Thank you very much for your time and your help [/FONT][/COLOR][IMG]https://ubuntuforums.org/image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7[/IMG]

[COLOR=#141414][FONT=&quot]Cheers[/FONT][/COLOR]

---

### Post by zampieri on 2019-10-03
I reply to my own thread:

Today we opened the laptop and checked the thermal paste, the GPU itself, faulty connections, and the RAM.
It turned out that what caused the laptop to freeze and reboot (or shut down) was the removable RAM bank. At least, without it, the laptop didnt show (and is not showing) any misbehavior. 
We checked the weld joint at the microscope (thanks to the meccatronic lab technicians) and we found no faulty joint. 
We will try with another DDR-4 bank tomorrow, to check whether it could be a problem of momentary pressure when moved or if it was that specific faulty RAM bank.

I am confident to say it was no conflict with drivers or similia.

---

