---
title: "problems with HP"
date: 2012-05-31
forum: Hardware
---

### Post by N0oki3 on 2012-05-31
Hello there. I am owner of HP pavilion g6 1190sm. The hardware is:
cpu : i3
graphic card: intel integrated and radeon HD 6470m
memory: 4gb ddr3

The problems have occured in Ubuntu 11.04 and 12.04LTS, pangolin precise

So the problem is...every time I reboot or shutdown laptop and when the laptop is booting again I get screen (before loading OS) that HP discovered overheating and system went into hibernate. But the point is that laptop is not overheating nor going into hibernate by itself. 
Also becouse of the hybrid graphic cards I cannot install additional drivers. Desktop resolution and all works perfectly but I cannot use unity 3D also openGL doesn't work as it should (with cairo docks)
As i've read some posts, people say that switcheero doesn't work on 12.04 so I haven't tried it. 
But I have tried [this](http://ubuntuforums.org/showthread.php?t=1930450)
But > sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
from here it didn't worked.

I have also reinstalled windows back to laptop and if you guys can help me solve this thing I will be so happy to go back on Ubuntu :)

---

### Post by Redblade20XX on 2012-06-02
In the instructions you have given it should be:
```
** sudo** chmod +x amd-driver-installer-[12-4]("http://wiki.cchtml.com/index.php/12-4")-x86.x86_64.run
```
before the line you had problems with.

If you want a better guide to help the installation take a look at this: 
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

The previous link will get you past step 1 on the instructions you have given. Follow the step 2 from your instructions very closely there might be another syntactic error.

-Red

---

### Post by N0oki3 on 2012-06-06
Hi there Red.
Sorry for a bit late reply.
Yesterday I have tried something else (as i have just seen this post)
I have fixed the overheat error with updating bios. But than, when i wanted to reinstall ubuntu I had black screen. So in grub i have changed to nomodeset and successfully install ubuntu. First thing I did, was  editing grub to 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force radeon.nomodeset=1"
updated grub.
than I have
> apt-get remove fglrx-* fglrx-amdcccle jockey-common jockey-gtk
rm -rf /usr/share/ati/
apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
apt-get install --reinstall libgl1-mesa-glx:i386
apt-get install ia32-libs dkms build-essential
update-initramfs -u
update-grub


I have downloaded latest drivers,
> 
chmod a+x ati-driver-installer-12-4-x86.x86_64.run
sh ati-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i *.deb


switching to radeon 
> sudo /usr/lib/fglrx/switchlibGL amd

and generating new xorg conf
> sudo aticonfig --initial -f --adapter=all

Everything was perfect untill here. When I did

> Service lightdm restart

No more desktop for me.

---

### Post by N0oki3 on 2012-06-07
I have also tried the guide you have posted red, and conclusion is...thanks to stupid HP and locked bios, you cannot switch to dgpu. 
Whatever I have tried, when i switch to dgpu it is no graphics error...and only thing that solves problem to get back to desktop is deleting xorg.conf

I have also seen over the forums that all HP's owners with radeon hd 6470m cannot get on desktop (blabla error, low-graphics desktop aka terminal) meanwhile sony's laptop owners with radeon hd 6470m have no problem at all w/ unity 3d

ps: all the help is still welcome

---

### Post by Redblade20XX on 2012-06-07
I got your message N0oki3 :) and will try to dig up some more info.

The guide I've given you doesn't have enough information for intel/amd hybrid graphics.
This might be resolved in the future though. I would've loved to play around with this but alas I haven't got a hybrid system.:confused:

As a future note, try looking up information, like the guide you posted, at a more recent posting time the one you've give was since feburary 2012 and a lot of things have changed since then. Maybe there is an unofficial guide somewhere out on the net.

Sorry for not being able to help any further.:(

-Red

---

### Post by N0oki3 on 2012-06-07
All of the guides are more or less the same. On my laptop, HP pavilion G6 1190sm is bios locked (only thing you can actually change in there is boot order and time), default graphic is integrated and laptop doesn't need to reboot to switch between dgpu and igpu. (muxles). It doesn't matter how hard I try to force it, its always the same. Even tho when you do 
>  sudo aticonfig --px-dgpu
It does say : Changing to Discrete Graphic's or more powerful graphic card (i forgot the exact reply). But once you reboot laptop it always toss Low graphic's mode ... + I always have to run / edit grub to nomodeset, otherwise I don't see desktop either.

If anybody is reading this thread and its going to buy new laptop soon, I recommend you to do some research before buying laptop if you are going to run Ubuntu and you want to unity 3D. 

In my case unity 2D runs smooth, graphics are awesome, resolution is max, but cairo-dock doesn't work like it should (on normal PC works perfectly)

---

### Post by mastablasta on 2012-06-08
i believe this combo should be supported. well at leats it's listed here in the end.:
 
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

---

### Post by N0oki3 on 2012-06-08
> **mastablasta said:**
> i believe this combo should be supported. well at leats it's listed here in the end.:
 
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

you mean
> SONY Vaio VPC-SC1AFM/S, Intel HD 3000, AMD 6470m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

yeah but there is also at the top 
>  If an AMD 6630m (for example) works on a HP computer, this doesn't mean the same video card will work for sure (for example) on a ASUS computer.

I really don't know why...under intergrated it does show as graphic is sandy bridges but dgpu doesn't work ;<

---

