---
title: "Gammu config"
date: 2008-11-07
forum: General Help
---

### Post by unclejac on 2008-11-07
Hi there, needing a bit of help from someone with a bit experience setting up the Gammu config file. 

Connecting an old Sony Ericsson K800i via USB cable 

(since my bluetooth is non functional at the moment in 8.10) 

So far I've got:
```

[gammu]

port = /dev/ttyUSB001
model = auto
connection = at
;synchronizetime = yes
;logfile = gammulog
;logformat = textall
;use_locking = yes
;gammuloc = locfile
startinfo = yes
;gammucoding = utf8
;rsslevel = teststable
;usephonedb = yes
```

So I know this is wrong as when I type "gammu --identify" it gives me:

```
betai@beta:~$ gammu --identify
gammu: /build/buildd/gammu-1.20.0/common/device/serial/ser_unx.c:159: serial_close: Assertion `d->hPhone >= 0' failed.
Aborted

```

I am thinking the connection type is way wrong, but unsure what to change it to? 

```
betai@beta:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 062a:6728 Creative Labs 
Bus 001 Device 004: ID 046d:c313 Logitech, Inc. 
Bus 001 Device 003: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 001 Device 002: ID 0fce:d039 Sony Ericsson Mobile Communications AB 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thanks in advance to anyone who can spare a moment to help!

---

### Post by unclejac on 2008-11-09
bump

---

### Post by surapat on 2008-11-17
[FONT="Arial"]I also face with some problem on gammu, anyway you may try
(on my machine i use "port=/dev/ttyACM0")[/FONT]

[gammu]
port = /dev/ttyUSB001
connection = at19200
model = at

or

[gammu]
port = /dev/ttyUSB001
connection = at19200
model = obex

or 

[gammu]
port = /dev/ttyUSB001
connection = at19200
model = auto

---

### Post by Akuma_s on 2009-10-19
Same issue, connected in the USB port.
I used the last set up option for my k610 and it worked really nice!! 
Just amazing...

```

[gammu]
port = /dev/[FONT=Arial]ttyACM0[/FONT]
connection = at
model = 

```

Now its time to learn how to use it...
Niice! :)

Thanks for the help!

---

