---
title: "mount compact flash pcmcia adapter?"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by usererror on 2005-06-17
I have a compact flash media card for my digi camera.  i have a pcmcia cflash card adatpor so i can plug in my card w/o using the usb cable and drain my battery during file transfer.

how do I mount my pcmcia flash card device? or set it to auto mount when I insert the card?

thanks in advance! =)

---

### Post by diebels on 2005-06-18
Mounting should be done automatically. Is driver for your pcmcia slot working properly(other cards working). Is the driver for the card working? See /var/log/messages when you put it in.

---

### Post by ericvmazzone on 2005-07-11
This is what I see when I put in a 16MB card.  I can't mount mine or find it anywhere though.

Jul 11 23:24:57 localhost kernel: hde: max request size: 128KiB
Jul 11 23:24:57 localhost kernel: hde: 31808 sectors (16 MB) w/1KiB Cache, CHS=497/2/32
Jul 11 23:24:57 localhost kernel:  /dev/ide/host2/bus0/target0/lun0: p1
Jul 11 23:24:57 localhost kernel: ide-cs: hde: Vcc = 3.3, Vpp = 0.0

---

### Post by leezer3 on 2005-07-12
Mounting won't necessarily be done automatically, especially as this is a PCMCIA adaptor (Additionally it may not be correctly identifying the FS type). Open up a root terminal and type:
```
mount /dev/hde0 -t vfat /mnt/pcmcia
```
This should hopefully mount the card adaptor's contents in /mnt/pcmcia
Good luck, as on my machine this has been notoriously tempermental :P

-Leezer-

---

### Post by flapane on 2006-10-21
gipi@gipinet:~$ sudo mount /dev/hde1 -t vfat /media/pcmcia
mount: /dev/hde1 is not a valid block device

why?
lexar ata flash 128mb

---

### Post by usererror on 2007-10-25
I have since updated to 7.10 and forgot i posted this thread. :(  i'll see if this works automagically on 7.10 tomrrow!

---

### Post by usererror on 2007-10-27
In 7.10 it automatically mounts.  Woo hoo!

---

### Post by rajman on 2007-11-07
I am having problems with mounting an SD card. It's a micro but with an adaptor for regular SD. It's worked before in OS X and in windows XP so i KNOW it has to work in linux. 

Device manager lists it as RL5c476 II and shows Bay1Controller when it's plugged in. 

from dmesg: 
[29611.192000] pccard: PCMCIA card inserted into slot 0
[29611.192000] pcmcia: registering new device pcmcia0.0

/var/log/syslog
Nov  7 00:17:26 zoroaster kernel: [30256.028000] pccard: PCMCIA card inserted into slot 0
Nov  7 00:17:26 zoroaster kernel: [30256.028000] pcmcia: registering new device pcmcia0.0
Nov  7 00:17:26 zoroaster NetworkManager: <debug> [1194412646.984908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 

/var/log/kernlog
Nov  7 00:17:26 zoroaster kernel: [30256.028000] pccard: PCMCIA card inserted into slot 0
Nov  7 00:17:26 zoroaster kernel: [30256.028000] pcmcia: registering new device pcmcia0.0


All saying the same thing basically.
Other than that I see no activity. Any clues ?

---

