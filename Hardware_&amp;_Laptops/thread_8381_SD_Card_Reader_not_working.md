---
title: "SD Card Reader not working"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by vontez on 2004-12-16
I am trying to get my built-in SD card reader on my HP zt3000 working.  I compiled the 2.6.9 kernel and patched it with the patches from [here](http://projects.drzeus.cx/wbsd/) and everything went smoothly.  I can modprobe wbsd with no problems, but when I put in my SD card nothing happens.  I've tried following the instructions to mount the drive that are on the page listed above, but I have had no success.

Has anyone had any luck with an SD card reader built into a laptop?

---

### Post by mirtux on 2005-02-27
Hi,
   i'm trying to get some results.. but still nothing...

---

### Post by smtanner on 2005-02-27
The SD card reader built into my laptop (Gateway M675) works ok.  When I put a card in, a window opens up displaying the contents.  I don't get desktop icon though due to this bug:


[https://bugzilla.ubuntu.com/show_bug.cgi?id=6355](https://bugzilla.ubuntu.com/show_bug.cgi?id=6355)

---

### Post by briguy on 2005-03-16
I've got a PCI SD card reader and this is how I made it work:

enter the following line in /etc/fstab:
/dev/hde5	/media/smart 	auto	noauto,user,exec 0 0

create the folder /media/smart:
sudo mkdir /media/smart

Put the card in, desktop icon appears and window opens!

You will probably have to change hde5 to hde1in fstab - my card has a goofy partition.

---

### Post by briguy on 2005-03-16
I've got a PCI SD card reader and this is how I made it work:

enter the following line in /etc/fstab:
/dev/hde5	/media/smart 	auto	noauto,user,exec 0 0

create the folder /media/smart:
sudo mkdir /media/smart

Put the card in, desktop icon appears and window opens!

You will probably have to change hde5 to hde1in fstab - my card has a goofy partition.

---

### Post by mirtux on 2005-03-16
Thanks for your hint but my problem is that i don't have any hde devices... only hdax which are referring to my hard disk partition.

However thanks again,
MC

---

### Post by briguy on 2005-03-16
Plug the SD card in and then do dmesg | grep hd or just dmesg and you should see what device it should be.  Plug that into your fstab.

---

### Post by mirtux on 2005-03-16
Thanks i'll check for sure..... ;-)

Regards,
MC

---

### Post by mirtux on 2005-03-21
[QUOTE=briguy]Plug the SD card in and then do dmesg | grep hd or just dmesg and you should see what device it should be. Plug that into your fstab.[/QUOTE]

Hi,
  definitely it is not working since i've got nothing in /var/log/messages or dmesg when i plug in the card!

Regards
MC

---

### Post by thread on 2005-04-16
I have a Dell Inspiron 700m with an sd card reader. I have the same problem. Nothing shows up in the logs when I insert the SD card. Also, I don't see a /dev/sd* or anything becides /dev/hda and /dev/hdc (hard drive and optical drive).

However, HAL does appear to pick it up:

```
$ lshal | grep SD
...
info.product = 'PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. and SD/MS-Pro Sockets'  (string)
...
```

I am unfamilliar with sysfs, but it appears that the linux.sysfs_path is

```
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.3
```

now... how do I mount it?

---

### Post by ilmw on 2005-08-03
I got exactly the same problem. Is there any workaround? Or shall we wait for the new kernel? :-(

[QUOTE=thread]I have a Dell Inspiron 700m with an sd card reader. I have the same problem. Nothing shows up in the logs when I insert the SD card. Also, I don't see a /dev/sd* or anything becides /dev/hda and /dev/hdc (hard drive and optical drive).

However, HAL does appear to pick it up:

```
$ lshal | grep SD
...
info.product = 'PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. and SD/MS-Pro Sockets'  (string)
...
```

I am unfamilliar with sysfs, but it appears that the linux.sysfs_path is

```
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.3
```

now... how do I mount it?[/QUOTE]

---

### Post by mirtux on 2005-08-04
Hi,
  because do you think that in the next kernel there will be support for it? I don't think so because it needs some proprietary drivers..... I've contacted the manufacturer but still no drivers from their side...

Regards,
MC

---

### Post by ilmw on 2005-08-06
[QUOTE=mirtux]Hi,
  because do you think that in the next kernel there will be support for it? I don't think so because it needs some proprietary drivers..... I've contacted the manufacturer but still no drivers from their side...

Regards,
MC[/QUOTE]

I agree. This is always a problem, though it is getting better and better.

---

### Post by thread on 2005-08-08
I decided to have another look into this today, and found this site:

[http://projects.drzeus.cx/wbsd/](http://projects.drzeus.cx/wbsd/)

This kernel patch will make some card readers work, but unfortunately, if my Inspiron 700m has the same controller (Ricoh R5c576A) as the Inspiron 6000 (and I suppose it does) there really is no driver for it in linux yet.

So I guess I just have to wait.

And here's the dude with the Inspiron 6000 who sounds like he knows what he's talking about:

[http://www.math.ucla.edu/~jimc/insp6000/p-proc.html](http://www.math.ucla.edu/~jimc/insp6000/p-proc.html)

---

### Post by mirtux on 2005-08-08
Thanks,
   unfortunately my O2 Micro reader is not  (yet?) supported ](*,)....

Regards,
MC

---

### Post by =]MESSIAH[= on 2005-11-22
Hi, I have a winbond sd slot on my notebook (presario x1000 exactly like zt3000 and the nx7000) and i got it to work but only with mmc cards. All ypu have to do is load the mmc_block module

> modprobe mmc_block

when you insert the card the green light will go on and you will now have
mmcblk0
mmcblk0p1
in /dev. you can now mount the partition manually or add it to your fstab.

The thing is i can't find the kernel patches to get sd support (looked in [http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd))
if anybody can give them to me i would be very thankfull

---

### Post by ilmw on 2005-11-25
btw, I bought a PC Card Reader which supports SD, MMS, xD, and MS. It does work with my 700m and so far it successfully recognized both SD and xD (I don't have others to test) cards.

---

### Post by Copter on 2005-11-30
word!

---

### Post by ilmw on 2006-06-28
[QUOTE=ilmw]btw, I bought a PC Card Reader which supports SD, MMS, xD, and MS. It does work with my 700m and so far it successfully recognized both SD and xD (I don't have others to test) cards.[/QUOTE]

my pc card does not work any more since i upgraded to dapper. :( The system will significantly slow down after i insert SD card to the pc card reader. Anyone has the same problem?

---

