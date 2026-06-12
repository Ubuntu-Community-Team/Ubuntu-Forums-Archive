---
title: "Install from USB thumb drive from Windows"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by zooplibob on 2009-11-02
Im trying to use a USB thumb drive to install Ubuntu 9.10 on my netbook which has no cd drive. I am looking at these instructions from [https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)
> **From Windows**

 burn the iso file or use use virtual clone drive to access the files within the image. 
usb-creator.exe is located in the CD image already for you! 
You won't be able to select the USB drive if it wasn't formatted in a way that windows can see it. You may have to format it using explorer, then it will show up in the creator tool Unfortunately there is no "usb-creator.exe" anywhere within the image. Can you tell me where I can find this program? Otherwise how can I install Ubuntu without a CD drive?

---

### Post by Bluehaze65 on 2009-11-03
For Windows I use the Fedora usb creator:

[http://en.wikipedia.org/wiki/Fedora_Live_USB_creator](http://en.wikipedia.org/wiki/Fedora_Live_USB_creator)

Things may have changed in the 9.10 release but the Ubuntu usb creator was Linux only.

---

### Post by ojobson on 2009-11-03
zooplibob, did you manage to get this to work? I used unetbootin to create my usb boot disc in windows.

The installer runs form the usb disc, but then it looks for a cd-drive to mount but I don't have one so it fails. Not sure what I can do now..

---

### Post by jaduvet on 2009-11-06
Seems youre right. At least i havent found a solution to the same problem. andthere is some other threads reporting same problem in different ways

the problems aplies also if you try to use unetbootin 

but still no explanation if this is a user (you, me and her rest) error or a ubuntu error (embarasing then)

threads:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008)
[http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508](http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707)
[http://ubuntuforums.org/showthread.php?p=8257120](http://ubuntuforums.org/showthread.php?p=8257120)
[http://newyork.ubuntuforums.org/showthread.php?t=1313987](http://newyork.ubuntuforums.org/showthread.php?t=1313987)

---

### Post by duanedesign on 2010-01-02
Guide to creating a Llive USB:
[http://ubuntuforums.org/showthread.php?t=1193680](http://ubuntuforums.org/showthread.php?t=1193680)

**Known Issues**
The 9.10 CDs and DVDs are [COLOR="Red"]missing the usb-creator.exe program[/COLOR]. To install to a flash drive from a disk image on Windows, use the incredibly easy process described at:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) 
-
-
-

---

