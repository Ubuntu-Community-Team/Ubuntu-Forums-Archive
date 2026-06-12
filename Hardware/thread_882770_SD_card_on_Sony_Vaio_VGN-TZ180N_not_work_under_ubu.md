---
title: "SD card on Sony Vaio VGN-TZ180N not work under ubuntu 8.04"
date: 2008-08-07
forum: Hardware
---

### Post by nifty8 on 2008-08-07
Hello,

I buy and Sony Vaio VGN-TZ180N and I delete previously installed Vista business and install Ubuntu 8.04, I'm almost happy with this software therefore I cant make work my internal SD card slot. Could somebody help me if there is any posibility how to make it works.

Thank you all in advance for your help. :)

Regards,

Nifty888

---

### Post by matt.taylor on 2008-08-07
Have you tried another SD card? I presume its a Multi Card reader, have you got another card you can try?

---

### Post by eahiv on 2008-09-10
I have the same problem on my 170n. The card and card reader are just never recognized. I can't remember for sure but I think it may have worked before a recent kernel update...

I've tried multiple cards with the same results. Nothing whatsoever happens in dmesg output or /var/log when inserting a card.

---

### Post by IntuitiveNipple on 2008-09-10
If you were to provide some definitive information about the system when asking the question, we might have some idea of what to suggest. At a minimum report the hardware configuration:
```

sudo lspci -vnn

sudo lsusb -v

```
It is always useful to *attach* the most recent [b]/var/log/dmesg[/i]. Also report the output of lshal and lsmod by capturing their output:
```

lshal > lshal.log
lsmod >lsmod.log
tar -czf logfiles.tar.gz lshal.log lsmod.log /var/log/dmesg

```
and attaching the compressed file "logfiles.tar.gz".

---

### Post by forgewire on 2009-05-01
I have Sony Vaio VGN-TX2HP and has never managed card reader to work on Ubuntu 9.04
When I used SUSE card reader worked and showed inserted card in fdisk -l. I even didn't do anything particular to set it up on SUSE

---

### Post by karlhutt on 2011-09-13
i'm using ubuntu 11.04 on a Sony Vaio VGN-TZ25FN, and i can't make the integrated SD card reader to work. 
using an external SD card reader it works fine, but i'd really like to have the integrated slot working. it's so practical! 
any ideas?

---

