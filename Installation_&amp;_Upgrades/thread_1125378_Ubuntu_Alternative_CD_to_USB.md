---
title: "Ubuntu Alternative CD to USB??"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by jznomoney on 2009-04-14
Is there a way to place the alternative cd image to a usb key to install from it.  I tried using the Unetbootin program and when i tried install it says it cannot find the cdrom drive.

---

### Post by wpshooter on 2009-04-14
Is your system capable of booting from a USB device ?

Look at your options in the BIOS boot order section ?

---

### Post by logos34 on 2009-04-14
try this tut:

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

(I think you can use either the live or alternate iso--"Jon-Paul" in the comments sections says he used it to install Hardy alt to webbook)

---

### Post by jznomoney on 2009-04-14
my motherboard supports usb boot.  I can boot the live cd of a usb drive.  I just want to find a way to put the alternative cd image to a usb drive and boot it.

---

### Post by tamas305 on 2009-04-14
So I'm guessing that you want basically a live USB not a full install of Ubuntu on your USB drive. If you you start up the live CD and begin a demo session. Once you are logged in as a generic user, you can navigate to System --> Administration --> Create a USB startup disk. This copies all the contents of the live CD onto the USB drive, making it basically a live USB drive. Note this is not a full install of Ubuntu, if you want that than e-mail @ [email]tamas305@gmail.com[/email]

-tamas

---

### Post by jznomoney on 2009-04-14
i just want the alternative cd image able to install to my main computer.  I have a raid setup but no cdrom drive and only the alternative cd will able to install to a raid setup.  I have windows vista on my primary partition and i want to put ubuntu on my secondary one.

---

### Post by jznomoney on 2009-04-15
<bump>

---

### Post by ahbart on 2009-04-15
Best way to create a Buntu alternative cd usb stick is using the
> System --> Administration --> Create a USB startup disk
and select the alternive iso.
You can do this from a live cd (on another computer?)
I have trouble using Unetbootin with Ubuntu iso's too.

---

### Post by jznomoney on 2009-04-15
that worked ahbart.  I was just hoping someone knew a way to do it from within windows.

---

### Post by ahbart on 2009-04-15
Well, there are ways to do that under windows. You have to make the disk bootable and copy the right files and folders to the right place on the usb stick. No don't ask. ;)

---

### Post by jeffdp78 on 2009-04-15
download iso...
[FONT=Verdana][SIZE=2]Alternate installer[/SIZE][/FONT]
*[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)*


install this...
[FONT=Verdana][SIZE=2]Ubuntu LiveUSB[/SIZE][/FONT]
*[http://klik.atekon.de/liveusb/#download](http://klik.atekon.de/liveusb/#download)*


and howto's from here...
[FONT=Verdana][SIZE=2]LiveUsbPendrivePersistent[/SIZE][/FONT]
*[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)*

;)
---

---

### Post by ahbart on 2009-04-15
You are a little bit to late. :D
See post #9

---

### Post by jeffdp78 on 2009-04-15
if you want to easily create one from windows, try [B]Cd2usb

[/B]an open source windows program, designed to make Live USBs of [Ubuntu]("http://hacktolive.org/wiki/Ubuntu") 8.10+
[http://hacktolive.org/wiki/Cd2usb](http://hacktolive.org/wiki/Cd2usb)

---

---

### Post by jeffdp78 on 2009-04-15
@ahbart // lol!, I didn't notice that :p ...my silly internet connection bugs me today!

---

---

### Post by ahbart on 2009-04-15
@jeffdp78, well this cd2usb windows tool is good to remember for another time!

---

### Post by logos34 on 2009-04-15
> **ahbart said:**
> Best way to create a Buntu alternative cd usb stick is using the

and select the alternive iso.
You can do this from a live cd (on another computer?)
I have trouble using Unetbootin with Ubuntu iso's too.

good to know.  Thought it allowed only live usb option

---

