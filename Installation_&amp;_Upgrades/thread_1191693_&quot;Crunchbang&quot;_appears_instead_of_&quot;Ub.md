---
title: "&quot;Crunchbang&quot; appears instead of &quot;Ubuntu&quot; in menu.lst"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by ericwb on 2009-06-19
Very peculiar indeed:

I noticed that the entries in my /boot/grub/menu.lst have suddenly been changed from "Ubuntu" to "Crunchbang".

I had never previously heard of Crunchbang (I now know that it is a lightweight GNU/linux based on Ubuntu) and have certainly never installed it myself. I run a standard Ubuntu Jaunty 9.04.

This seems to have appeared after having installed and run Startup-Manager. Having noticed this, I manually changed my menu.lst and replaced "Crunchbang" with "Ubuntu".

The problem has resurfaced since the kernel update from 2.6.28-11 to 2.6.28-13. The update manager asked me to check the versions of menu.lst, and "Crunchbang" was proposed instead of "Ubuntu".

Googling around was of no use on this issue.

Any ideas, anyone?

---

### Post by dstew on 2009-06-19
Probably, the Startup-Manager installation changed the default settings in /boot/grub/menu.lst. If you get a new kernel in an update, the program update-grub is run automatically to create a new menu.lst file with the entries for the new kernel. If the default title in menu.lst is "Crunchbang", then update-grub will use this to create the new menu entries.

You will need to edit the default title entries in menu.lst. These are up at the top of the file, preceded by single # signs. If you want help, please post to the forum your **entire** menu.lst file, so we can look over the default entries at the top.

---

### Post by cariboo on 2009-06-19
DO you by chance have any crunchbang repositories in your /etc/apt/sources.list?

---

### Post by ericwb on 2009-06-20
[COLOR="DarkRed"]**@dstew:**[/COLOR] 
Nope, there are no defaults that I can see defined in my menu.lst (see below). Note that I've changed the "CrunchBang"'s back to "Ubuntu" manually.

[COLOR="DarkRed"]**@cariboo907:**[/COLOR]
I can't see anything related to CrunchBang in my sources.list (see below).

I still have no idea how the "CrunchBang" got there in the first place, and I can't find where the OS name to display in the Grub menu is defined.

Strange, but definitely not life-threatening mind you. I was mostly wondering if this was some sort of casual bug that may be worth reporting.


[COLOR="DarkRed"]**menu.lst:**[/COLOR]
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color black/light-gray white/brown

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0639457d-f6bb-4374-8eeb-06e30967e799 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(mode sans echec) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0639457d-f6bb-4374-8eeb-06e30967e799 ro splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu, kernel 2.6.28-13-generic (mode sans echec)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0639457d-f6bb-4374-8eeb-06e30967e799 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0639457d-f6bb-4374-8eeb-06e30967e799 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu, kernel 2.6.28-11-generic (mode sans echec)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0639457d-f6bb-4374-8eeb-06e30967e799 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

[COLOR="DarkRed"]**sources.list:**[/COLOR]
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
# deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
# deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://fr.archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb http://fr.packages.medibuntu.org/ jaunty free non-free
# deb-src http://fr.packages.medibuntu.org/ jaunty free non-free
deb http://ppa.launchpad.net/spring/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/spring/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main
# deb-src http://wine.budgetdedicated.com/apt jaunty main

```

---

### Post by jreyes33 on 2009-06-21
I'm having exactly the same "problem" since the last kernel update.

---

### Post by ericwb on 2009-06-22
> **jreyes33 said:**
> I'm having exactly the same "problem" since the last kernel update.
Did you also install and use Startup-Manager like I did? If not, then the problem is not related to Startup-Manager.

---

### Post by dstew on 2009-06-22
The problem is very weird, I don't see any problem with menu.lst that would cause update-grub to add the Crunchbang title to any menu option.

---

### Post by ericwb on 2009-06-22
Where does Grub get the default title for the OS anyway? I can't find an option in the menu.lst entries that seems to correspond.

---

### Post by dstew on 2009-06-22
Ah, you are right. The update-grub program does not get its titles from the default entries, but from the kernel images themselves that reside in /boot. See the [update-grub man page]("http://pwet.fr/man/linux/administration_systeme/update_grub"). Maybe you should remove (use Synaptic or apt-get) the crunchbang kernels, if there are any with such labels.

---

### Post by ericwb on 2009-06-23
I can't find anything in my /boot directory that explains this.

I tried a ```
$ sudo find . -name *crunchbang*
``` which yielded:
```

./var/cache/apt/archives/grub_0.97-29ubuntu50-1crunchbang1_amd64.deb
./var/cache/apt/archives/notification-daemon_0.4.0-0ubuntu3-1crunchbang4_amd64.deb

```
I have no idea how these thingies appeared.

---

### Post by dstew on 2009-06-23
The first entry is a Debian package for a new update-grub program that works with crunchbang. Perhaps that is the problem. The second one is a daemon that probably serves to support the first package.

It is possible that your installed update-grub program is from this crunchbang package. You could try to fix it this way:```
sudo apt-get install grub
```That *might* remove the older crunchbang-grub, and replace it with the regular Ubuntu grub package, which has the regular update-grub program. At least, this trial would be unlikely to hurt your system. If it doesn't work, you might need to use more primitive commands, like **dpkg**, to get rid of all trances of crunchbang-grub. That would probably allow a new, clean Ubuntu-grub program to go in unmolested.

---

### Post by rwabel on 2009-06-23
I've the same Crunchbang now also in my grub menu. I still have the entry for the other ubuntu kernels, however if I want to boot with one of them, it tells me file not found.

Since using Crunchbang it seems that I've lost the Visual effects and icons are sometimes no longer displayed or not correctly displayed. Not sure if that is related with Crunchbang or not.

How can I get back to my old normal linux kernel?

---

### Post by DJ_Peng on 2009-06-24
> **dstew said:**
> The first entry is a Debian package for a new update-grub program that works with crunchbang. Perhaps that is the problem. The second one is a daemon that probably serves to support the first package.

It is possible that your installed update-grub program is from this crunchbang package. You could try to fix it this way:```
sudo apt-get install grub
```That *might* remove the older crunchbang-grub, and replace it with the regular Ubuntu grub package, which has the regular update-grub program. At least, this trial would be unlikely to hurt your system. If it doesn't work, you might need to use more primitive commands, like **dpkg**, to get rid of all trances of crunchbang-grub. That would probably allow a new, clean Ubuntu-grub program to go in unmolested.
/me clicks the Thank button for dstew, or would if it were available
I was wondering about this issue myself. What I ended up doing was searching for "crunchbang" in Synaptic, looking in Version. That turned up six or seven packages, and grub was in fact one of them. I did the downgrade and then locked the version since Synaptic offered to upgrade again to the crunchbang version.

Doing a search in launchpad PPA's I see that I probably got it from [Philip Newborough's PPA]("https://launchpad.net/%7Ecorenominal/+archive/ppa"). I'll disable his source until I find I need something specific of his again.

---

### Post by ericwb on 2009-06-25
Interestingly, when I do a ```
$ sudo aptitude remove grub
``` it answers:

[FONT="Courier New"][COLOR="Navy"]The following packages will be BROKEN:
  startupmanager
The following packages will be REMOVED:
  grub
[/COLOR][/FONT]
So I guess it *does* have to do with StartupManager after all. I guess it's time for a bug report…

---

### Post by Jimmy_r on 2009-06-25
I will just quote what I said in [the bugreport]("https://bugs.launchpad.net/startup-manager/+bug/391992").

> I am not quite sure I understand the problem.
As stated in the ubuntuforums thread the ubuntu package of startupmanager depends on grub.

What that has to do with crunchbang, i dont really understand as grub is the default bootloader in ubuntu and is one of the things startupmanager is supposed to configure.
Also, the official package[1] does not have a hard dependency on grub but that should not matter in this case.

[1] [http://sourceforge.net/projects/startup-manager](http://sourceforge.net/projects/startup-manager)


Startupmanager does not have anything to do with crunchbang at all, and as dstew said all the renaming and stuff is handled by update-grub so it is not anything startupmanager could affect.

---

### Post by ericwb on 2009-06-25
I removed the CrunchBang version of Grub, which prompted the installation of the correct version of Grub.

I double-tested the "bug" by firt removing then reinstalling and using StartupManager. Everything seems to be working fine, and the "title" entries of **menu.lst** have not been changed to "CrunchBang".

I also realize that **aptitude** said the right thing: If you remove Grub, then StartupManager will obviously be "broken". Without Grub, StartupManager is actually quite pointless!

---

### Post by rwabel on 2009-06-29
I never had StartupManager installed and got the Crunchbang entires

---

### Post by jreyes33 on 2009-06-30
> **rwabel said:**
> I never had StartupManager installed and got the Crunchbang entires
yeah, me too. I've never heard of StartupManager. Well, I changed it by hand in menu.lst, but it's funny because I have #! in another PC and it's entries in grub read "Ubuntu" (I know Crunchbang IS Ubuntu)

---

### Post by rwabel on 2009-06-30
I think the only thing that change on my ubuntu is the name of the menu entry with crunchbang. Technically there is nothing different. Just strange that something did modify the grub menu.

---

### Post by DJ_Peng on 2009-07-01
As I posted earlier, I got it from [Philip (corenominal) Newborough's PPA]("https://launchpad.net/%7Ecorenominal/+archive/ppa"). His PPA has some packages I love, like the gimp-brushes and Liberation fonts. I recommend checking your sources list for [http://ppa.launchpad.net/corenominal/ppa/ubuntu](http://ppa.launchpad.net/corenominal/ppa/ubuntu) and if you see it force the version number on Grub to before 0.97-29ubuntu50-1crunchbang1, then disable Philip's PPA in your sources until there's another update you need. After you disable Philip''s PPA you can safely unlock the version number on grub.

You should also make a point of not accepting grub updates while you have his PPA enabled. I'll post something about this on my blog to try to get the info spread out a little farther.

ETA: It turns out the fix isn't as easy if I thought. My /boot/grub/menu.list still shows "crunchbang" for some reason, but you can safely edit the file to get rid of that designation. I'll also contact Philip to see if he has some info about it that I should pass along in my blog post.

Also, as I was writing my blog post about this issue I fired up startup-manager and somewhere in the process my kernels got renamed "Ubuntu 9.04" rather than "CrunchBang", so it turns out SUM is a very handy tool for resolving this issue.

---

### Post by rwabel on 2009-07-01
you were right, I had this repo also due to the liberation fonts. I've also just read your blog entry. Many thanks for your feedback. I'm going to downgrad it now.

---

### Post by DJ_Peng on 2009-07-01
I just got a response from Philip (corenominal) that has one additional fix that may be needed by some.
> I am sorry to read that one of my modified Ubuntu packages has been
causing some issues. The package was modified for use with CrunchBang
Linux and looking back, I should not have pushed it to my PPA. I have
now removed it.

Regarding fixing up your grub boot list, if you have already rolled
back the package, you should be able to run the following command to
remove the CrunchBang references:

    sudo update-grub

Apologies again for the boob.

At the risk of self-promotion, I do have a bit more info on my [blog post]("http://nancib.wordpress.com/2009/07/01/running-gnulinux-and-seeing-crunchbang-in-your-kernel-list-weve-got-a-fix-for-it/") for anyone who may need a more step-by-step set of instructions.

---

