---
title: "Install hangs at same spot"
date: 2004-10-17
forum: Installation &amp; Upgrades
---

### Post by uratewl on 2004-10-17
I am trying to install Ubuntu and am unable to run through the installer. I get to the same spot each time I run the installer. It will get to the "Loading Components of the Ubuntu Installer" screen at 34% complete and the component it's loading is "Retrieving nic-extra-modules-2.6.8.1-3-386-di.

The machine is an older Dell with a PII 400mhz pro and 256 mb of ram. The hard drive is a Maxtor 40 GB. 

Any help will be greatly appreciated.

---

### Post by uratewl on 2004-10-18
I'm trying to install from the Warty iso. Just downloaded yesterday.

---

### Post by etitor on 2005-03-29
Same problem here in Madrid.

Trying to install Ubuntu Warty Spanish from boot CD. When reaching 34% of  "Cargando los módulos del instalador de Ubuntu", just in the middle of retrieving  "nic-extra-modules-2.6.8.1-3-386-di", the screen begins to flash, the progress bar freezes at 34% (I think I can see very briefly the 34% changing back and forth to 0%), and it all ends there.

Machine is a 330 MHz P III, 64 MB RAM, 6 GB HD.

By the way, our German friends also know the problem. For those who can read German please see [http://www.ubuntu-forum.de/artikel/10/sid14e98438272757f47102a2f9f718723d/Installation-CD-Rom-Laufwerk-wird-nicht-eingehangen.html](http://www.ubuntu-forum.de/artikel/10/sid14e98438272757f47102a2f9f718723d/Installation-CD-Rom-Laufwerk-wird-nicht-eingehangen.html)


Any advice someone?

---

### Post by blabla on 2005-03-31
I've had the same problem every time I go for a normal "enter" install. 

However, if I do an F1 first, go to F2 for requirements and then click my way through it appears to work fine.

Have a go at that one, it might work for you, too.

Cheers

Ingo

---

### Post by Ubuntu_User on 2005-06-07
Yeehaa...
I had the same problem when trying to install Ubuntu (5.04) on a 32 MB Laptop. I decided to try it in a virtual machine (where I can change available RAM at will) and clearly, the problem goes away once you have more memory.

So, what to do? Make more memory available. How to do this?
Create a swap partition *before* installing Ubuntu, then make the installation use it. Unfortunately, you'll need some other way to boot your machine to create the swap partition, because fdisk is not available on the Ubuntu install CD :?  (hint to the Ubuntu creators: maybe this should be included in future versions...). Anyway, boot some minimal linux (I used hal91, fits on a single floppy, you could also use some LiveCD or something), use fdisk to create a swap partition (Label 0x82, just so you know; I made it 512MB in size). Don't forget to write your changes to the disk...

Then, start booting. Wait for the system to load the drivers and find the CD-ROM, then use Alt+F2 to get a console. Now:
mkswap /dev/hdaX
swapon /dev/hdaX

... and your installation works  :D 
At least here, it seems to install it at this very moment.
Hope this helps some of you :)

---

