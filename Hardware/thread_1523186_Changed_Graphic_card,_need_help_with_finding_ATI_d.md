---
title: "Changed Graphic card, need help with finding ATI drivers"
date: 2010-07-03
forum: Hardware
---

### Post by Ifaistos on 2010-07-03
Hello :-)

I had an MSI NX8500GT-TD256E graphics card based on an Nvidia chip.  Unfortunately it got burned (I guess) and had to switch graphics cards to my old one, a Gigabyte X800 with ATI chip on board.

It works ok, but I can't make my Ubuntu (10.04) installation re-discover the graphics card and load the appropriate drivers, and enable the desktop effects etc...  It still thinks that I have an Nvidia Graphics card.

For those of you who know the answer I would appreciate to guide me through a graphics menu, and not command line.  If it is not possible I can handle command line, but I would really prefer GUI instructions.

Thank you all in advance :-)
Ifaistos

---

### Post by 73ckn797 on 2010-07-03
I assume you went to System/Hardware Drivers and checked for a driver?

---

### Post by Linuxforall on 2010-07-03
If you had drivers enabled for your previous nvidia, try disabling them via hardware drivers and reboot and see if your ATI gets detected.

---

### Post by Ifaistos on 2010-07-03
Yes, of course I went to system > graphics drivers... but after a while it says that no proprietary drivers are in use in this system.

It shows no drivers at all.

I will try to reboot to see if the "new" graphics card is detected, although I have done this already once...

I am downloading right now the catalyst 9.3 which I found on the AMD.com site, but I am afraid to install it, cause I read that for other users the results were not so "pleasant".

Please let me know, if there is anything else I could do.

Thanks.

---

### Post by cascade9 on 2010-07-03
ATI dropped support for the X800 a while ago, and AFAIK the older versions of the ATI proprietary drivers wont install on newer versions of ubutnu.

---

### Post by Ifaistos on 2010-07-03
That is true... as far as the part of "not installing" is concerned.
The file that I tried to download was a .run file and I can't run it.

So I guess I am stuck with my X800 in low-graphics mode.  Right?
Well my computer is working great now, which is something that wasn't happening with my old nvidia card.

I guess I will have to live without the special desktop effects and without any proprietary drivers.

I don't play games, and although wobbly windows is a nice effect, I guess it's something that i will have to live without, unless someone knows another way.  (other than buying a new gfx card ;-)...

Thank you all for your immediate and helpful answers..

Viva Linux :-)
Ifaistos

---

### Post by notbitmonk on 2010-07-03
Did you gave execution rights to the .run file.  Right click on it and under the permissions tab, at the bottom there is a checkmark to give the file execution rights.  Afterwards, double click it to execute the file and run the installer.

---

### Post by cascade9 on 2010-07-03
> **Ifaistos said:**
> That is true... as far as the part of "not installing" is concerned.
The file that I tried to download was a .run file and I can't run it.

So I guess I am stuck with my X800 in low-graphics mode.  Right?
Well my computer is working great now, which is something that wasn't happening with my old nvidia card.

Even if you do manage to run the file, it wont install.....

There might be some imporvement if you havethe newest ATI open source drivers, but I have no idea if they are up to the point of supporting desktop effects, etc. I also have no idea how you would go about doing that on *buntu.

---

### Post by Ifaistos on 2010-07-03
Ok, I followed your advice and gave it execution rights.
It run, but it didn't do anything.  It created a folder and then nothing.

I rebooted and still nothing.  I believe that this file doesn't do anything on 10.04

Thanks though for your suggestion.
Viva Linux :-)

---

### Post by Yellow Pasque on 2010-07-03
> **Ifaistos said:**
> Ok, I followed your advice
LOL, you did the opposite of the advice (read the post again). Anyway...
```
sudo nvidia-settings --uninstall
sudo /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
Some of the above commands will probably not work or complain. It's ok, just go to the next one.

---

