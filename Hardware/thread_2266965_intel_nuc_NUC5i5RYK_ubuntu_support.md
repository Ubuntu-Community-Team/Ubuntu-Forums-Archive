---
title: "intel nuc NUC5i5RYK ubuntu support"
date: 2015-02-26
forum: Hardware
---

### Post by kominato on 2015-02-26
Hi,
Bought a  new intel nuc the nuc5i5ryk which has the 5th generation Intel® Core™ i5-5250U and latest HD 6000 intel graphics.
I can't install 14.04 or 14.10 on it.
it loads grub then loads the installer but the graphics are broken .. windows only have bars, no text, no menus, no buttons at all ... when I pass the mouse inside windows suddenly buttons appear etc
Does this means I have to wait because its a too new product?
I would greatly appreciate any help

---

### Post by Yellow Pasque on 2015-02-26
In your case, you'll probably be better off with an Ubuntu 15.04 snapshot.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by kominato on 2015-02-26
yes it seams it is working with 15.04 .. i am already at the installation process

---

### Post by kominato on 2015-02-26
yes everything worked fine with 15.04thank you.do you know if ubuntu 14.04 will be supported?

---

### Post by Yellow Pasque on 2015-02-26
I have no idea, but I suspect updated graphics drivers could help: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=trusty](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=trusty)

---

### Post by kominato on 2015-02-26
tried the ppa on live cd without success

---

### Post by oldfred on 2015-02-26
Supposedly it works, similar new model:
 NUC NUC5i3RYB - openSUSE Tumbleweed vs. Manjaro vs. Debian 8.0 vs. Fedora 21 vs. Ubuntu 14.10
[http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1)

---

### Post by Yellow Pasque on 2015-02-26
> **kominato said:**
> tried the ppa on live cd without success

I think you would have to restart the Xserver. Maybe you can try creating a persistent install on the USB if you want to test it out: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by kominato on 2015-02-27
the nuc5i3ryb has intel graphics HD5500 maybe that's why it worked with 14.10

---

### Post by furioususer on 2015-04-16
Did you solve this? How is it going so far?

---

### Post by furioususer on 2015-04-16
> **kominato said:**
> yes it seams it is working with 15.04 .. i am already at the installation process

How does the 15.04 differ from 14.04 LTS? I have the same issue as OP and I don't want to abandon the 14.04 LTS version and settle for something else.

---

### Post by stratosnn on 2015-04-22
Same here, 
I have tried [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=trusty](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=trusty) ppa on live and restarted lightdm after - no effect.
Would be nice to stick with LTS version of Ubuntu.

---

### Post by gordintoronto on 2015-04-23
At the moment, 15.04 (which should be released today) uses the 3.19.0-15 kernel. I have been running the Xubuntu and Ubuntu Mate versions for about a month with minimal problems. The biggest drawback is that I will have to migrate to 15.10, since 15.04 will expire before 16.04 is released.

---

### Post by dr_squalo on 2015-07-26
> **gordintoronto said:**
> At the moment, 15.04 (which should be released today) uses the 3.19.0-15 kernel. I have been running the Xubuntu and Ubuntu Mate versions for about a month with minimal problems. The biggest drawback is that I will have to migrate to 15.10, since 15.04 will expire before 16.04 is released.

Hi
which minimal problems they are?
I have a severe one in resuming from standby.  Grafic fails. No chance to see any text on buttons nor to navigate. Only remedy is to switch off/on NUC.
Any hints?
(Is Intel HD6000 Grafic anyhow supported by UbuntuMATE 14.05? Or is it still somehow beta?)
(Got latest BIOS)


Thx

---

### Post by albert47 on 2016-03-09
> **kominato said:**
> yes it seams it is working with 15.04 .. i am already at the installation process

Please! I have the same problem than you, but I still can't get it working. 

Can you tell me, where do you get de iso, and wich software did you use to build the Pend drive (USB), Did you use Windows/Mac.., And did you use iso for 32 or 64 bits?

* I tried with 15.10, and did not worked...¿?

Thanks you very much!!

Albert

---

### Post by oldfred on 2016-03-09
You can download 64 bit here, do not use 32 bit.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
      
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Both 14.04.4 and 15.10 are now newer than others that worked as posted in thread above. Should work better.

---

