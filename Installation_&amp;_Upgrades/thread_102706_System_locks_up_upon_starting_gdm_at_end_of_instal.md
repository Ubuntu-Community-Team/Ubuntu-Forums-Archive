---
title: "System locks up upon starting gdm at end of install"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by teoryn on 2005-12-12
First off, big hello to everyone, I've been a gentoo user for half year and decided to give ubuntu a shot. 

I'm running a AMD64 with GeForce 6600. Everything in the install went fine until the end of the part after the reboot. As soon the loading bar finished some text started appearing at the bottom of the display. From what I could get before it disappear it mentioned the GNOME Display Manager starting. Right after that the screen got filled with a repeating, mostly junk, patter of colors and the system stopped responding. During the screen resolution part I tried once selecting my monitor's native resolution (1280x1024) and the defaults, and on another try I selected only my monitor's native resolution, both times had the same result. 

Thanks for the help,
Kevin

---

### Post by NotJustANewbie on 2005-12-12
Try
```
sudo dpkg-reconfigure xserver-xorg
```
(and choose a smaller res e.g. 800x600 - you can reconfigure your resolution when you are in Gnome later)

then
```
sudo /usr/sbin/gdm stop
```

then
```
sudo /usr/sbin/gdm start
```

then
```
sudo reboot
```

then... pray

---

### Post by teoryn on 2005-12-12
I did as stated, however upon typing 
```
sudo /usr/sbin/gdm stop
sudo /usr/sbin/gdm start
``` Both stated that an instance of gdm is already running. So I ran ```
sudo killall gdm
``` and started gdm after that, but got the same problem. The problem also occured after rebooting.

I then killed gdm and just ran startx, but I got a bunch more junk on the screen.

---

### Post by NotJustANewbie on 2005-12-13
I got that. I know how to possible fix your problem. Get a copy of Knoppix and insert. Then mount your local hard drive. From the live CD, go to /etc/X11/XF86-Config and copy it to your local /etc/X11 (overwriting the old one - but make a backup of your old one just in case ;))

Remove knoppix and reboot.

---

### Post by teoryn on 2005-12-13
I did that as well, but it didn't work, I'm pretty sure because knoppix uses XFree and ubuntu uses X.org

I also tried using the ubuntu live cd but got basically the same problem.

---

### Post by NotJustANewbie on 2005-12-13
Its a tricky one, must be something to do with gdm then... I had the same problem when I tried to install Debian Stable on my laptop and then install the xserver-xorg package separtly after the main install... Anyone else got any ideas??

---

### Post by jon-of-pob on 2005-12-15
Hi,

I've got exactly the same problem.  I've also got a GeForce 6600, my monitor is a LG L1715S.  Anyone got that set up working, or any more ideas?

Thanks

---

### Post by alejandrops on 2005-12-15
Hi, I have exactly the same problem, Nvidia 6600, 17"LCD.

---

### Post by Easycola on 2005-12-15
Not likely considering this issue, but just making sure that you all have that extra power 4-pin/whatever power cord attached to GFX-card? 
Diddo that error once after rebuilding this box and forgot to plugin the power-cord on my 6600 gt. Ubuntu installed just ffine and so on. When I did adjust orig xorg with nvidia provided setup tool next boot up was messy, thou there was clear error message stating that I didn't have power cord plugged in. Stupid user error, fixed by finally somewhat "intelligent" error msg...:)

---

### Post by jon-of-pob on 2005-12-15
Hi,

I've been looking around, seems like this should sort the problem. [http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/]("http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/").  Seems that the nvidia drivers have to be installed before ubuntu lieks a geforce 6600.

I managed to follow most of this, but while installing the driver package got an error about needing libc development libaries.  I installed libc6-devel, but that gave a new error message about having a newser version of gcc installed (4.0) rather than the one used to build the kernel (3.4).  Do I need to install a different libc package?

---

### Post by bartt on 2005-12-15
Hi Everyone-
Nube here, so please be gentle. 

This is first distro I've tried on this new rig that even got this far. 
I'm running an Opteron Dualie with an NV6800 card and have the same trouble as described above. But like I said, no other distro go as far on install, most give up finding the SataII drives. 

Anyhow, I see some instructions above for running some commands. When and how do stop the boot process to get a cmd prompt.?

OH, I forgot to mention this is the AMD64 version (duh)..
Also I don't think the system is dead it does give a drum beat if I hit <CR> once the mixed up screen shows. So I am sure that this is a video driver issue.

TIA..

---

