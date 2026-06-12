---
title: "HP X2 210 G1 built in card reader not working on ubuntu mate 16.10."
date: 2016-06-15
forum: Hardware
---

### Post by jagdtigger on 2016-06-15
Greetings.

I just got my new laptop mentioned in the topics name and im trying to install ubuntu onto the micro SD to dualboot with windows. But when i try to modify the partitions with gparted i cant see card. The reader and the card works fine on windows but when i boot the freshly downloaded yakkety build it doesn't work. In windows i see three intel SD host controller. And here is the dmesg output:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/dmesg.txt](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/dmesg.txt)

Have someone any idea what is the problem here?

Thanks in advance for the help :) .

/EDIT
lsusb and lspci:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/lsusb-lspci.txt](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/lsusb-lspci.txt)

HW ID from windows hardware manager: ACPI\VEN_8086&DEV_0F14&REV_0001

---

### Post by jagdtigger on 2016-06-20
Bump...

---

### Post by jagdtigger on 2016-08-10
Bump2

Tried yesterdays build, no luck. And here is some more info on the damn thing:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/hp-x2-210.HTM](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/hp-x2-210.HTM)

---

### Post by jagdtigger on 2016-09-16
BUMP3.....

No luck with todays build. I looked at dmesg again and i noticed this:
card never left busy state
error -110 whilst initializing SD cad

On windows the card works just fine :/ .

---

