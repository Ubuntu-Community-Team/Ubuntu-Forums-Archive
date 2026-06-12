---
title: "Graphics not working Fresh Install"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Versial on 2009-10-06
Ok, I am relatively new to Ubuntu, I have and home-made machine and I am trying to dual boot xp and 9.04.  I cannot use the live cd or do and install from the original cd, it goes through the ubuntu loading screen, and after that my screen just looks all messed up with lines all over the place.  I tried 8.10 with the same result.  I did some research online and was told to try the alt. cd.  which i did with no problems.  However the same problem occurs when trying to load. So I did further research and was told to try dpkg-reconfigure xserver-xorg and dpkg-reconfigure -phigh xserver-xorg from the recovery mode.  However the only thing that brings up is one yes or no question about my video and the rest is all keyboard questions.  I have been fighting this for two days and I am really getting frustrated.  Sorry long winded.

---

### Post by rreese6 on 2009-10-07
We need more information.
Boot up your system to recovery mode and go to the root prompt and type:
```
lspci | grep VGA
```
Type the output of that command here.

This will tell us which video card that you have. then we can go from there.

---

### Post by Versial on 2009-10-07
```
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
```

---

### Post by mikewhatever on 2009-10-07
You may need to install the proprietary nvidia driver while in recovery mode. Try **sudo apt-get install nvidia-glx-180**. What it should download and install the driver from the repositories, but you'll need to be online for that.

---

### Post by Versial on 2009-10-08
> **mikewhatever said:**
> You may need to install the proprietary nvidia driver while in recovery mode. Try **sudo apt-get install nvidia-glx-180**. What it should download and install the driver from the repositories, but you'll need to be online for that.

I did this and it didn't help how do I know if that is even the right driver?

---

### Post by Meow27 on 2009-10-08
you should download the latest driver from nvidia
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

after you have that. follow this guide

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)



though you may want to unisntall your current driver

(make sure you download for the '7' series)

---

### Post by SkyNet2029 on 2009-10-08
that bit abit dpkg-reconfigure...
you issued a command of 
#dpkg-reconfigure -phigh xserver-xorg
ideally, since you are dealing with drivers, you should use
#dpkg-reconfigure -plow xserver-xorg
 
this will (after the keyboard and mouse info) give you a lower level of control
(more fine-grained) than the -phigh command.
 
note especially the hsync and vsync settings.
 
even if you do end up needing the nvidia driver, a selection of vesa with framebuffer should get you to a working screen. Once that is taken care of, worry about the nvidia drivers. First things first, get a working and usable screen.

---

### Post by Versial on 2009-10-08
> **SkyNet2029 said:**
> that bit abit dpkg-reconfigure...
you issued a command of 
#dpkg-reconfigure -phigh xserver-xorg
ideally, since you are dealing with drivers, you should use
#dpkg-reconfigure -plow xserver-xorg
 
this will (after the keyboard and mouse info) give you a lower level of control
(more fine-grained) than the -phigh command.
 
note especially the hsync and vsync settings.
 
even if you do end up needing the nvidia driver, a selection of vesa with framebuffer should get you to a working screen. Once that is taken care of, worry about the nvidia drivers. First things first, get a working and usable screen.

I tried this command and it just gave me the same options as before, the yes or no video question and the keyboard questions.  It stops after that.  

As far as downloading and un-installing the nvidia driver...First, how I download the driver from the terminal since I can only work from recovery mode, and what is the command(s) for un-installing the one I just put in?

---

### Post by Versial on 2009-10-09
Bump...Anybody?

---

### Post by mikewhatever on 2009-10-09
> **Versial said:**
> I did this and it didn't help how do I know if that is even the right driver?

That's the newest driver available for Jaunty, and your card, GeForce 7950 GT, is listed among the supported ones.
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

I am really not sure what's wrong. Could it be the issue with the monitor?

---

### Post by Versial on 2009-10-09
> **mikewhatever said:**
> That's the newest driver available for Jaunty, and your card, GeForce 7950 GT, is listed among the supported ones.
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

I am really not sure what's wrong. Could it be the issue with the monitor?

I had thought of that and changed out monitors to no affect.

---

### Post by Meow27 on 2009-10-09
@ mike, the jaunty drivers work differently than the ones directly for nvidia.

thats the case for me

(7300 le user)

---

### Post by Versial on 2009-10-09
Ok, well I still haven't gotten anywhere but I decided to try the live disk again.  Under the start options I push f6 for other options then type in vga=771 and it's starts up fine.  Is there anyway I can have that permanent?

---

### Post by mikewhatever on 2009-10-09
Sure, just add it to the boot line in /boot/grub/menu.lst.

```
kernel   /boot/vmlinuz-2.6.28-15-generic root=UUID=889475-blabla ro  single [COLOR="DarkRed"]vga=771[/COLOR]

```

Hope it works.

---

### Post by rreese6 on 2009-10-09
you can add the vga=771 to the kernel line in the menu.lst file located at /boor/grub.

boot up recovery
```
mount
```
see if you have a line that has /dev/sda1 or /dev/hda1 in it.
of you see one fo those then read the line the line t see what the mount point is. like "/media/sda1" or maybe "media/disk"
what ever you have then change to that directory.
Let say it is called /media/sda1
then
 ```
cd /media/sda1/boot/grub
```
then open the file menu.lst ```

sudo nano menu.lst
```
use arrow keys to move around and add "vga=771" to the end of the kernel line. in the first "Title" group. (this should be very near to the end of the file.
press ctrl X to exit , Y to save and enter.
reboot and you should have a desktop.

if you don't see a mount point for your drive then type this first
```
cd /media
sudo mkdir disk
sudo mount /dev/sda1 /media/disk
```

---

### Post by Versial on 2009-10-09
> **mikewhatever said:**
> Sure, just add it to the boot line in /boot/grub/menu.lst.

```
kernel   /boot/vmlinuz-2.6.28-15-generic root=UUID=889475-blabla ro  single [COLOR="DarkRed"]vga=771[/COLOR]

```

Hope it works.

Thanks I tried that but it mixed the loading screen of Ubuntu with the xp boot loader for some reason.  I am reverting back to 8.04 anything higher doesn't seem to work for some reason.

---

### Post by Versial on 2009-10-09
> **rreese6 said:**
> you can add the vga=771 to the kernel line in the menu.lst file located at /boor/grub.

boot up recovery
```
mount
```
see if you have a line that has /dev/sda1 or /dev/hda1 in it.
of you see one fo those then read the line the line t see what the mount point is. like "/media/sda1" or maybe "media/disk"
what ever you have then change to that directory.
Let say it is called /media/sda1
then
 ```
cd /media/sda1/boot/grub
```
then open the file menu.lst ```

sudo nano menu.lst
```
use arrow keys to move around and add "vga=771" to the end of the kernel line. in the first "Title" group. (this should be very near to the end of the file.
press ctrl X to exit , Y to save and enter.
reboot and you should have a desktop.

if you don't see a mount point for your drive then type this first
```
cd /media
sudo mkdir disk
sudo mount /dev/sda1 /media/disk
```

Those where excellent directions btw I misread the first one and tried to edit the grub from the boot loader.  However, even after following your directions it still didn't work.  I am starting to suspect a deeper issue.  But I can't place what it is, I have reinstalled xp and Ubuntu several different times and in different orders because I thought windows was causing the problem somehow.  But nothing has seemed to work.  Thanks anyway, but I am getting tired of the headache for now so like stated before I switch back to 8.04 it's the only one that still seems to work.

---

