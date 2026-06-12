---
title: "Ready to give up- nvidia install"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by velozoom on 2006-10-30
I've followed all the hints and suggestions given here and the links from other thread/sites.  Nothing has worked.  I've spent all weekend on this one problem and I still don't have a functional laptop.  I'm ready just to say the heck with it and install XP but I would really like to not do that.  I want to use/learn Linux but it's godawful frustrating for a newbie.  

I've done everything I am *supposed* to do.  I've installed the kernel source and headers, installed nvidia-glx, nvidia-kernel-common, nvidia-settings, tried this from the .run file and the corresponding xorg.conf configuration script.....I still get a broken xserver or a blank screen.  

I'm lost and if I can't sort it I'm going to have to go back to M$ hell just because I know I can get a working system.  

WHat is left to try?  

Have an HP dv9000z laptop with an nVidia GeForce Go 6150 card.  

Any help is very much appreciated.  

Thanks.

---

### Post by jazzgossen on 2006-10-30
Do you get any errors when running the .run file, or does it seem to install OK? Did you choose to make the necessary changes to xorg.conf at the end of that installation process?

---

### Post by velozoom on 2006-10-30
I did get some errors but went through and resolved them before the last attempt on a clean install of the OS.  The only one I couldn't change was that the .run app said I was at runlevel1 and suggested I enter 'telinit 3' to change to runlevel 3.  I did this but then was unable to continue using the system without rebooting which re-started at runlevel 1.  

I did choose the option to have teh app reconfig xorg.conf

---

### Post by jazzgossen on 2006-10-30
If you are at runlevel 1 that means you are in single user (=root) mode. Do you normally log in as root? Try to 

* boot up normally (not in fail safe mode or anything, which will give you runlevel 1)

* hit ctrl+alt+f1 to get a terminal screen when you see the GDM login menu

* login there

* do "killall gdm" to kill X

* then run the driver install script.

---

### Post by netztier on 2006-10-30
> **velozoom said:**
> Have an HP dv9000z laptop with an nVidia GeForce Go 6150 card.

Is there a particular reason for not using the restricted-modules (the one that matches your kernel's version) and change xorg.conf to use "nvidia" instead of "nv" as the driver module? 

Why go complicated with installing, compiling etc?

regards

Marc

---

### Post by ronacc on 2006-10-30
if you are trying to install it in edgy(6.10) there is a change in procedures that ran me around for 3 days ,see this thread nad note the comments by tseliot  and ato "http://www.ubuntuforums.org/showthread.php?t=282638" the key to if you need this is if on boot the Xserver wont start and complains about the driver versions not matching.

---

### Post by velozoom on 2006-10-30
>>Why go complicated with installing, compiling etc?


heheheh.....cuz I'm a complete Linux NOOB and I haven't a real clue as to what I am doing.  I think I've tried the way you suggest, netztier, byt running apt-get install nvidia-glx, and nvidia-settings, and nividia-configure-enable.......is that what you are referring to?   That gave me a black screen on boot up.....

---

### Post by netztier on 2006-10-30
> **velozoom said:**
> >>Why go complicated with installing, compiling etc?


heheheh.....cuz I'm a complete Linux NOOB and I haven't a real clue as to what I am doing.  I think I've tried the way you suggest, netztier, byt running apt-get install nvidia-glx, and nvidia-settings, and nividia-configure-enable.......is that what you are referring to?   That gave me a black screen on boot up.....

Then your're almost there, but your system probably still lacks the most important component to run  X.org with nvidia drivers: the driver module itself.

If you have a fallback configuration for X (e.g. with the nv driver), then get back into X and start Synaptic Package Manager from the Menu System - Administration.

Then search for "restricted" and see the list of available packages called "linux-restricted-modules-xxxxxxxx", wehere xxxx is -686, -386, -common or -generic.

To my current unterstanding, all you need is add the two packages **linux-restricted-modules-generic** and **-common**. Where applicable, they will pick the right package from the versionised ones, automatically selecting one that matches your current linux kernel.

If X won't come up at all, you can always do it from cosole:

[B][FONT="Courier New"]sudo aptitude install linux-restricted-modules-generic
sudo aptitude install linix-restricted-modules-common
[/FONT][/B]

After that, make a backup copy of your /etc/X11/xorg.conf, then edit the file to say "nvidia" instead of "nv" (or vga or svga, for that matter) this section:


```
Section "Device"
    ...
#   Driver      "nv"
    Driver      "nvidia"
    ...
EndSection

```

This is all there is to it in the first place - proper configuration of screen resolutions and refresh rate settings left aside for the moment.

A bit intensified forum research will help you find all the other answers about nvidia installations - how to get twinview running etc.

You can also keep an eye on the file **[FONT="Courier New"]/var/log/X.org.0.log[/FONT]**, which is X.orgs log file. If any errors occur, look for lines starting with (EE), they give pretty good hints at what is going wrong.

regards

Marc

---

### Post by velozoom on 2006-10-30
Marc, thanks for all the help.  I wiped out my box last night with a fresh install of Edgy.  I went through this morning step by step and did all the recommendations mentioned or linked in this thread.  

Once again, when I restarted GDM I had a blank screen.  On reboot I have a broekn xserver notification screen.  I have the following errors-

(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
FATAL: Could not open 'lib/modules/2.6.17-10-generic/volatile/nvidia.ko' : No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***ABORTING***
(EE) Screen(s) found, but none have a usable configuration

---

### Post by VividHazE on 2006-10-30
I'm a complete linux newbie too and I had the same problems last night when installing Edgy, heres how I was guided to do it through IRC:

1.Open the Package Manager (I think its) click settings > Repositories, then check all the tickboxes (univerise, multiverse etc, its always nice to be able to search all apps i don't know why this isn't the default :P) Close that window now.
2. Click reload to add in all the extra package information
3. Click Search and type linux-restricted-modules
4. Select the linux-restricted-modules kernel for your type of computer (mine was the 386 one)
5. Search for nvidia and select nvidia-glx (as far as I know you don't need to install nvidia-settings, it actually uninstalls nvidia-glx and gives a warning,or something like that :S)
6. Click apply and let Edgy do its work.

This is where it got a bit odd for me, I entered the nvidia enable command like the help page told me to, but when i restarted this didn't work and I had to reload my old settings using the cp command. So after reverting I just opened my xorg.conf file from a terminal window like this:

gksudo gedit /etc/X11/xorg.conf

then changed the "nv" to "nvidia" and saved (should have made a backup but eh). After this I restarted my computer and it DID work. I hope that helped in some way, cause i can see some people already gave that kind of instructions (better than me too.)

Also you should type in a terminal window "glxinfo | grep rendering" and it will tell you if direct rendering is working or not, or else give some errors, dunno how useful that is though :S

Good luck!

---

### Post by ronacc on 2006-10-30
sounds like x is not finding the driver. Question , on the fresh install before you try to add the nvidia driver do you get to the desktop ? or do you get a blank screen right from the start ? If the screen is blank right from the start before you add anything your  hardware isnt being detected right and it is calling for a driver your video cant use.
If the problem only occurs after you try to add the nvidia binary (NVIDIA ******.run) the problem is either 1 the driver isnt being built 2 its being built but going to the wrong place 3 X is trying to load the wrong driver. ( note edgy didnt pass the right info on my video card to x either but fortunately my card had enough sense of humor to accept the "generic" driver (really generic not even nv)it also thought my samsung lcd was a generic crt really crappy display but atleast I had a desktop)

---

### Post by velozoom on 2006-10-30
thanks vivid but still the same......

---

### Post by velozoom on 2006-10-30
>>Question , on the fresh install before you try to add the nvidia driver do you get to the desktop ?

Yes.  Fresh install works fine.  I can get to the desktop no problem.  really, all I want to do is to get a screen resolution appropriate forom y screen.  It's a widescreen cpaable of 1440x900 and that's what I want to use btu need something other than the geenric drivers that max out at 1024x768.

---

### Post by jsnielsen on 2006-10-30
I used envy to install it. After everything else had failed, envy did the job. So thanks Albert Molino ! :)

---

### Post by RoyArne on 2006-10-30
> **velozoom said:**
> the geenric drivers that max out at 1024x768.

I don't think the generic drivers max out at 1024x768, it is more like a fairly safe default. If you run the command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

it will let you choose the appropriate resolutions.

---

### Post by velozoom on 2006-10-30
>>sudo dpkg-reconfigure -phigh xserver-xorg

Roy, this command returns the following error-

dpkg: conflicting actiona -e (--control) and -r (--remove) 

Sorry for my ignorance, I'm still learning every time I touch this machine.....

I had tried to add "1440x900" to xorg.conf earlier but it didn't work.  ;)

---

### Post by ronacc on 2006-10-30
from a working desktop FIRST backup your working xorg.conf file 
download the driver you want from the nvidia site (I used NVIDIA-Linux-x86_64-1.0-9625-pkg2.run (Im 64 bit)) edit your xorg.conf (not your bu) 

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

so that driver is   "nvidia"     leave the rest alone its working if you change too much at one time you wont know what caused the problem.

then
Open /etc/default/linux-restricted-modules-common
and add nv module
Code:

DISABLED_MODULES="nv"   (this is from ato and is what got mine working ,same problem widescreen lcd and generic drivers = shit display)

Otherwise, the default nvidia  (or whatever )kernel module load on next reboot.  ( also if something other than nv was called in your xorg.conf file disable that too (add another DISABLED_MODULES=   line))

then
ctrl + alt + f1   and run your NVIDIA******.run   DONOT run the nvidia config from the package it will screw things up .  just restart gdm or reboot and it "should" work

---

### Post by kellere on 2006-10-30
-- got nvidia up and running on hp pavilion dv9000 --

see my last post at:
[http://www.ubuntuforums.org/showthread.php?t=273767](http://www.ubuntuforums.org/showthread.php?t=273767)

-John

---

### Post by velozoom on 2006-10-30
John, 

You da man, bro!  That did it!  

The answer was-

Use the beta driver and manually config the xorg.conf file by adding "nvidia" as the driver and explicitly adding the desired resolution to each display depth.  

Now for the next task....the dreaded wireless card...lol, I give this one a week.....

---

### Post by ronacc on 2006-10-30
Here are some tips for the wireless  most important
dont give up ;) 
dont assume the ndiswrapper that comes from ubuntu will work for all combos of cards and drivers. I went through 3 versions of ndiswrapper and tried 6 different drivers before I found the right combination for my HP ZV5466. the (then ) cvs ndiswrapper and a 64 bit driver from acer finaly did it for the broadcom in my HP which shipped with win XP 32bit and HP didnt have any 64bit drivers.
check out theese sites for info on setup and config.

[http://ndiswrapper.sourceforge.net/mediawiki/index](http://ndiswrapper.sourceforge.net/mediawiki/index).
php/Installation

[http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php](http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php)

they are oriented tword suse/redhat but the procedure will be similar for a debian based like Ubuntu.
also google on your specific card try, lspci or look at device manager to identify it.
good luck and dont give up.

---

