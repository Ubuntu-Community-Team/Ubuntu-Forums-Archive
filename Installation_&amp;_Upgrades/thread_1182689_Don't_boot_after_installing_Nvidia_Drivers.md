---
title: "Don't boot after installing Nvidia Drivers"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by sakisds on 2009-06-09
First of all, sorry if i posted this in a wrong section. Secondly I am new at Linux and i just installed Ubuntu to test them and i can tell i like them a lot.
But i have a problem.

When i tried to enable visual effects it asked me to install the proper drivers. The installation finished normally and i was asked to restart my computer. After the Ubuntu loading screen a black screen appeared and halted after "Checking Battery State...[OK]". I waited a bit but nothing happened. Alt+F4 and Ctrl+Alt+Del was working and i shutdown my system. Because i didn't find a solution i re-installed Ubuntu. Same problem. After reinstalling I don't install any drivers this time to avoid tis again.

Here is some info, because i am new i don't known what you would need, please ask me for more info.

64 bit running alongside with Windows Vista Ultimate
Ive installed all updates
I used version 180(of drivers)
I have two 8600 SLI
Running Ubuntu 9.04

Thanks a lot
sakisds

---

### Post by sakisds on 2009-06-09
Sorry for the double-post.
I just tried installing every version of the drivers. Same results. Please can anyone help me?
sakisds

---

### Post by chubbleton on 2009-06-09
Hey, 

I'm not going to be a whole lot of help myself, but I am having the exact same problem.

I used ubuntu about a year ago, and had this problem then - it has to do with ubuntu not knowing which is the 'primary' graphics card, or something along those lines. So you have to manually edit your xorg.conf file to include a couple lines specifying the physical location of master card, and that you want them to run in SLI.

Anyhow, I was searching for exactly what needs to be done, and I found your post, so I thought id say hi.

I'll repost here when I find the correct info.

---

### Post by sakisds on 2009-06-10
Thanks for answering. If you find the exact solution please tell me where is that conf file. I have no idea.

---

### Post by bugritall on 2009-06-10
Similar problems here, including at least four complete Ubuntu re-installs. These became necessary after exploring various ways of getting the nVidia drivers to work and then finding that Ubuntu would no longer boot to the GUI. I've been dumped to tty1 repeatedly and, being a novice, I have been clueless about what to do from there, other than re-install the OS.

Anyway, I have now created a multi-boot system with two Ubuntu 9.04 root partitions, both sharing the same boot, home and swap partitions. I call them 'ubuntu' and 'ubun2' and they were working splendidly together until I embarked on stage two of my plan and tried to install nVidia's 173 drivers on ubun2. 

After installing Desktop Effects and the nVidia 173 drivers, I re-booted ubun2 and this is what I got:

Boot from...
Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/c050...blah..54e7)=dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/c050...blah..54e7
kinit: no resume image, doing normal boot...
Ubuntu 9.04 ubun2 tty1
ubun2 login:

I can log in but what to do next is a total mystery.

Something I have noticed is that UUID 'c050...blah..54e7' is my swap partition.

Furthermore,  /boot/grub/menu.lst correctly references ubun2's root by a different UUID in its kernel statement(s).

We need help, please, all you Ubuntu gurus out there.

---

### Post by sakisds on 2009-06-10
For me, its halts at "Checking Battery State [OK]' but i can access the terminal by Alt+F4 and logon. After that, i have no idea. I only known a few commands. I tried every driver version but its always the same. I won't install them again, until i have a sure sulotion. Ive re-installed ubutu aboun 10 times these last 2 days.

---

### Post by sakisds on 2009-06-11
While I was searching, i found the 'envy' script. I downloaded it and it says that version 180 is compatible and recommended. But when i installed this version using 'Hardware Drivers' it makes ubuntu un-bootable. If i install it through envy is there going to be the same problem? Have anyone tried it?

---

### Post by mwhite212 on 2009-06-11
I'm getting something similar on initial install. Ubuntu works fine from the live CD, but hangs up with "Checking Battery State" as well during a WUBI installation. The screen blinks on and off and then comes up withe an error screen stating that "The video server has shut down 6 times in the last 90 seconds." 
 
This is getting really frustrating. I do have an onboard graphics card (disabled through cmos) AND an Nvidia. I don't understand why it would work for the live distro CD and not the install.

---

### Post by sakisds on 2009-06-11
I think this is a common problem :(
Can anyone help us?

---

### Post by sakisds on 2009-06-12
Anyone?

---

### Post by jprophet420 on 2009-06-12
you have to replace your xorg.conf file, there should be a backup:

```
jp@pbox:~$ ls /etc/X11/
app-defaults             fonts  xkb               Xsession.options
blackbox                 fr     xorg.conf         XvMCConfig
cursors                  ja     xorg.conf.backup  Xwrapper.config
de                       ro     Xresources
default-display-manager  X      Xsession
fluxbox                  xinit  Xsession.d
#sudo rm /etc/X11/xorg.conf
$mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
There may also be a /etc/X11/xorg.conf.failsafe file, that should work also.

---

### Post by epborden on 2009-06-12
> **jprophet420 said:**
> you have to replace your xorg.conf file, there should be a backup:

```
jp@pbox:~$ ls /etc/X11/
app-defaults             fonts  xkb               Xsession.options
blackbox                 fr     xorg.conf         XvMCConfig
cursors                  ja     xorg.conf.backup  Xwrapper.config
de                       ro     Xresources
default-display-manager  X      Xsession
fluxbox                  xinit  Xsession.d
#sudo rm /etc/X11/xorg.conf
$mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
There may also be a /etc/X11/xorg.conf.failsafe file, that should work also.

If you have nvidia drivers installed do not use the failsafe.

Instead, issue these commands:

cd /etc/X11
sudo rm xorg.conf && sudo rm xorg.conf.failsafe && sudo rm xorg.conf.backup*
nvidia-xconfig

Reboot your pc, and login.

Then type: startx

If you don't have the drivers installed:

Don't download the driver from Ubuntu's repositories, or worry about the "hardware drivers" option to "enable" the driver.

If you have a GUI & browser: Just download the driver from NVIDIA.com: [[http://www.nvidia.com/Download/index.aspx?lang=en-us]](http://www.nvidia.com/Download/index.aspx?lang=en-us]) Make sure you choose the appropriate fields such as card type & series, and which Linux version i.e. 32-bit, 64-bit.

If you have a command line:
w3m [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
move the cursor to the appropriate link [should be in color] for your OS, and hit Enter
The file should commence to download a .run file.

The installer is intelligent enough to look for the old drivers and uninstall them.

After you download the driver, cd [change directory] to where you downloaded the .run file.

Then open a command line [i.e gnome-terminal, xterm, or logout to CL] and:

sudo sh name-of-file.run

Follow the instructions, choose to remove old installations if it prompts to, do not download a pre-built module let the installer build a new one, then if you haven't already create a new xorg.conf.

Reboot, login, and startx.

---

### Post by jprophet420 on 2009-06-12
> **epborden said:**
> If you have nvidia drivers installed do not use the failsafe.

Instead, issue these commands:

cd /etc/X11
sudo rm xorg.conf && sudo rm xorg.conf.failsafe && sudo rm xorg.conf.backup*
nvidia-xconfig

Reboot your pc, and login.

Then type: startx
Why not use failsafe with nvidia?

---

### Post by epborden on 2009-06-12
> **bugritall said:**
> 
I can log in but what to do next is a total mystery.

Something I have noticed is that UUID 'c050...blah..54e7' is my swap partition.

Furthermore,  /boot/grub/menu.lst correctly references ubun2's root by a different UUID in its kernel statement(s).


You don't have to worry about this, if you really to change where boot picks up its resume image then you can do this at command line:

fdisk -l 
This finds out which drive is your boot drive: usually /dev/sda1, /dev/hda1, or sda5,hda5 if you put swap at beginning - this is based on partition/format defaults.

blkid
Find out your UUID for the boot drive you notated from fdisk -l, and notate it as well.

sudo pico /etc/initramfs-tools/conf.d/resume
Erase the UUID and put your UUID if it doesn't match, you might need to erase the # [comment] in front of RESUME - try both ways.

sudo update-initramfs -u

Reboot.

---

### Post by epborden on 2009-06-12
> **jprophet420 said:**
> Why not use failsafe with nvidia?

It is based on X11 defaults, not NVIDIA, and I assumed he wanted to use NVIDIA - that's all.

---

### Post by sakisds on 2009-06-14
Edit: Nothing sorry

---

### Post by slamhound on 2009-06-14
If you have two video cards (which I think you do from the first post), you will need to configure X to recognize and use both cards.  I followed this post to get it to work:

[http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

The main thing is running sudo nvidia-xconfig -a , which configures X for multiple cards.

Also, I think the nvidia drivers that Ubuntu supplies have a bug, so I got an error when nvidia-xconfig looked for the file: libnvidia-cfg.so.1 .  You need to create a symbolic link to the version-specific libnvidia-cfg.so.1 file (as described here:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863))  It worked perfectly for me after that.

---

### Post by sakisds on 2009-06-15
Thanks a lot, its works perfectly now.
(YaY Compizzzz :P)

---

### Post by bugritall on 2009-08-05
I have returned to this thread after getting the Nvidia 180 drivers working on Jaunty by removing the second of my SLI configured 7950 cards. It wasn't really a good solution, its sole virtue being the fact that it worked.

I see that there is a proper way to do things and it works for sakisds so it should work for me too and allow me to restore my SLI setup. Thank you, **epborden** and others for all your help. It truly is appreciated.

---

### Post by konqui on 2009-08-05
Forget the xorg.conf!

It isn't used as from version 8.04 with Nvidia drivers.

Just install downloading driver from Nvidia site. Save to your home folder. Rename to nv.run

Then restart, boot in recovery mode. Choose drop to root shell. Type sudo sh nv.run. Answer everything in a way that installation proceeds.

---

