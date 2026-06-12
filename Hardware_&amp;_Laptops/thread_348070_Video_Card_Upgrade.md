---
title: "Video Card Upgrade"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by sekcon on 2007-01-28
hey guys, im updating my geforce 4 to a geforce 6200 and wondering if im likely to run into any problems when i do so. im running ubuntu edgy and have just recently done a clean install and really not in the mood to do it again any time soon. should i uninstal the nvida drivers before i switch? what else should/shoulden't i do? :)

edit*
I also have some native linux games installed and 2 games which i installed through cedega, will switching video cards affect them at all?

---

### Post by sekcon on 2007-01-29
theres no one that has ever change video cards on an ubuntu install?

---

### Post by ushaba on 2007-01-29
you're probably going to have to do a dpkg reconfigure on xserver-xorg. i don't remember the exact command, but someone can help. the kernel has support for nvidia cards already, but you may have to manually edit the xorg.conf file for your card. it might be best to set the driver for your video card to vesa temporarily to ease the transition. 
cheers,
ushaba

---

### Post by sekcon on 2007-01-30
thanks ushaba, can anyone go into a little more depth? what do i have to edit in the xorg.conf file?

---

### Post by ushaba on 2007-01-30
```
sudo dpkg-reconfigure xserver-org 
```
is the command i was looking for. if you want to manually edit /etc/X11/xorg.conf (probably the most edited file on any linux system...) you just 
```
gksudo gedit /etc/X11/xorg.conf
```. 

go under the "device" section and look at the name of the card and the manufacturer, as well as the driver. if you are switching cards, probably switch the driver to  something really basic, either vga or mesa/vesa? whatever the standby is called. then make sure that any options you have enabled for the card are commented out. it's probably easier to just remember that ```
sudo dpkg-reconfigure xserver-xorg 
```
command though, but if your luck is as bad as ours, you'll likely have to do that from a command line after login... once that's done, 
```
startx
```
 to get x working again. 
good luck

---

### Post by tommcd on 2007-01-30
After you do <sudo dpkg-reconfigure xserver-xorg> you will have to reinstall the nvidia driver. I would just use the nvidia driver from the repos. It works fine with the nvidia 6200. If you have previously installed the driver from nvidia's website you will need to completely remove that before you install the driver from the repos. As a precaution I would first backup my xorg.conf before doing anything.
<sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak>
Hope this helps.

---

### Post by Derspankster on 2007-03-24
> **sekcon said:**
> hey guys, im updating my geforce 4 to a geforce 6200 and wondering if im likely to run into any problems when i do so. im running ubuntu edgy and have just recently done a clean install and really not in the mood to do it again any time soon. should i uninstal the nvida drivers before i switch? what else should/shoulden't i do? :)

edit*
I also have some native linux games installed and 2 games which i installed through cedega, will switching video cards affect them at all?

Where you able to upgrade? If so, how? I'm trying to do the same thing without success.

---

### Post by tommcd on 2007-03-25
> **Derspankster said:**
> Where you able to upgrade? If so, how? I'm trying to do the same thing without success.

If you are using the nvidia-glx driver from the repos you should be able to just pop in the new card and be off and running. Both the gforce 4 and the gforce 6200 are supported by nvidia-glx:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

