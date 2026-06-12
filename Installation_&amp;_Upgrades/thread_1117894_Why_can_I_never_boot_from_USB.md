---
title: "Why can I never boot from USB?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-04-06
I used the Create USB Boot Image from the menu at the top of Ubuntu and everything worked fine but when I rebooted with the stick in, it only booted to the following command line:
> boot:
No matter what I type, I get the following:
> <what I type> is not a valid Linux kernel. Please try again.

So last night I downloaded the USB image for the Ubuntu Mobile beta daily release, downloaded the USB Image Create program, installed that and used it to successfully create a boot image on the same USB drive. I reboot with the stick in again and the exact same command line comes up again. I really want to try this Ubuntu Mobile build, what am I doing wrong? The file is 755 megs so I can't burn it to CD and I don't have a DVD burner....yet.

---

### Post by Maheriano on 2009-04-06
Here's the link I was using to do all the downloads:
[http://cdimage.ubuntu.com/ubuntu-mid/daily-live/current](http://cdimage.ubuntu.com/ubuntu-mid/daily-live/current)

---

### Post by 0cton on 2009-04-06
maybe your download has some bad "sectors"\bytes
have you tried md5-ing it and comparing to the provided hash?

---

### Post by Maheriano on 2009-04-06
I don't think that's it. It happens every time I make a USB boot image.

---

### Post by jo4hnc on 2009-04-07
Here's a pretty good guide to installing to a flash drive.

[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)

---

### Post by Maheriano on 2009-04-11
I think I figured out the problem with this. I tried it with a different USB stick last night and it worked fine. I guess it was giving me the boot prompt because there was more than one image installed onto that flash drive. Then it wanted me to choose.

---

