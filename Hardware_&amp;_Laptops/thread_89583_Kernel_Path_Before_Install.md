---
title: "Kernel Path Before Install"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by Mizutsuki on 2005-11-12
My BIOS put me in a bit of precarious place, making this whole install process somewhat difficult.  I'm trying to dual boot XP Ubuntu and I'm already running XP.  Ubuntu is not installed yet.
It seems that my ITE 8211F has no native linux support (strange...) and everything I've read online corroberates this idea.  So somebody named Alan Cox made a kernel patch ([http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.9-rc2/2.6.9-rc2-mm1/broken-out/add-support-for-it8212-ide-controllers.patch](http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.9-rc2/2.6.9-rc2-mm1/broken-out/add-support-for-it8212-ide-controllers.patch)) that is supposed to make my life easier.  Unfortunately I'm playing a game of chicken and egg here.  I can't install the operating system until I have driver support for my controller.  I won't have driver support for my controller until I use the patch.  And I don't think I can use the patch until linux is installed.
So really the question is, is there any way to slip this patch onto the install kernel before I get to the fdisk stage of the install?
Thank you,
Stephen

---

### Post by Mizutsuki on 2005-11-13
Dumbass...
When I made the title Kernel "Path"...
What I really meant was Kernel "Patch"
Ok...
*skulks away from shameless bump*

---

### Post by tseliot on 2005-11-13
[QUOTE=Mizutsuki]My BIOS put me in a bit of precarious place, making this whole install process somewhat difficult.  I'm trying to dual boot XP Ubuntu and I'm already running XP.  Ubuntu is not installed yet.
It seems that my ITE 8211F has no native linux support (strange...) and everything I've read online corroberates this idea.  So somebody named Alan Cox made a kernel patch ([http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.9-rc2/2.6.9-rc2-mm1/broken-out/add-support-for-it8212-ide-controllers.patch](http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.9-rc2/2.6.9-rc2-mm1/broken-out/add-support-for-it8212-ide-controllers.patch)) that is supposed to make my life easier.  Unfortunately I'm playing a game of chicken and egg here.  I can't install the operating system until I have driver support for my controller.  I won't have driver support for my controller until I use the patch.  And I don't think I can use the patch until linux is installed.
So really the question is, is there any way to slip this patch onto the install kernel before I get to the fdisk stage of the install?
Thank you,
Stephen[/QUOTE]

[COLOR="Red"]I suggest you to download and burn Breezy's livecd[/COLOR]. Then if it works you might want to install Breezy on your harddisk. 

Otherwise patching a kernel would involve a recompilation of the kernel which is something which is easier to do if you have already installed a Linux system on your harddisk.

---

### Post by Mizutsuki on 2005-11-13
[QUOTE=tseliot][COLOR="Red"]I suggest you to download and burn Breezy's livecd[/COLOR]. Then if it works you might want to install Breezy on your harddisk. 

Otherwise patching a kernel would involve a recompilation of the kernel which is something which is easier to do if you have already installed a Linux system on your harddisk.[/QUOTE]

Umm... I'm using the breezy DVD, so I'm been going back and forth between live and install.
So, either way, what do I do to put the patch on?
Thank you,
Stephen

---

### Post by tseliot on 2005-11-13
[QUOTE=Mizutsuki]Umm... I'm using the breezy DVD, so I'm been going back and forth between live and install.
So, either way, what do I do to put the patch on?
Thank you,
Stephen[/QUOTE]
1) Ok, but I don't understand if Ubuntu livecd works for you.

2) BTW I don't know how to compile a kernel before installing Ubuntu. (In Gentoo it would be easier).

I recompile kernels after the installation process is completed (see my guide in my signature below).

3) What happens if you try to install Ubuntu?

---

### Post by Mizutsuki on 2005-11-13
[QUOTE=tseliot]1) Ok, but I don't understand if Ubuntu livecd works for you.

2) BTW I don't know how to compile a kernel before installing Ubuntu. (In Gentoo it would be easier).

I recompile kernels after the installation process is completed (see my guide in my signature below).

3) What happens if you try to install Ubuntu?[/QUOTE]

I moved my DVD drive to a seperate controller, so the livecd (DVD) works fine, except that I have no access to any of the drives on the normal controller.
When I try to install Ubuntu I get to the fdisk part of the install and then there are no physical drives, so I can't proceed.
Thank you,
Stephen

---

### Post by tseliot on 2005-11-13
[QUOTE=Mizutsuki]I moved my DVD drive to a seperate controller, so the livecd (DVD) works fine, except that I have no access to any of the drives on the normal controller.
When I try to install Ubuntu I get to the fdisk part of the install and then there are no physical drives, so I can't proceed.
Thank you,
Stephen[/QUOTE]
I have read (in the Gentoo forums) that your chipset is supported by Kernel 2.6.13 or higher.

I suggest you to try OpenSuse which has kernel 2.6.13 (it's a nice distro). Then you can try Ubuntu again when Ubuntu 6.04 Dapper Drake (which will have at at least that kernel version) is released (next April).

In this way you can try Linux and enjoy it.

---

### Post by Mizutsuki on 2005-11-13
[QUOTE=tseliot]I have read (in the Gentoo forums) that your chipset is supported by Kernel 2.6.13 or higher.

I suggest you to try OpenSuse which has kernel 2.6.13 (it's a nice distro). Then you can try Ubuntu again when Ubuntu 6.04 Dapper Drake (which will have at at least that kernel version) is released (next April).

In this way you can try Linux and enjoy it.[/QUOTE]


Are there any live distros that have that kernel?  It'd be nice to just take a look and see if it works first.
I thought ubuntu released every 6 months?  Yeah, so April looks about right.
Also, is there any version of the 2.6.13 kernel out now that I might be able to install instead of the 2.6.12 the ubuntu has now?  Like, is there any way to install that way?
I realize I'm asking the same question, I just don't feel like I have a definative answer yet.
Thank you,
Stephen

---

### Post by tseliot on 2005-11-13
[QUOTE=Mizutsuki]Are there any live distros that have that kernel?  It'd be nice to just take a look and see if it works first.
I thought ubuntu released every 6 months?  Yeah, so April looks about right.
Also, is there any version of the 2.6.13 kernel out now that I might be able to install instead of the 2.6.12 the ubuntu has now?  Like, is there any way to install that way?
I realize I'm asking the same question, I just don't feel like I have a definative answer yet.
Thank you,
Stephen[/QUOTE]
1) There is Opensuse Livecd (1 or 2gb), or RR4 Linux (an installable Livecd with a customised version of Gentoo). Try one of them (I recommend you Opensuse) so as to see if they work.
have a look at [http://distrowatch.com/]("http://distrowatch.com/")


2) Sorry but I don't know how to compile a kernel BEFORE installing Ubuntu (usually you compile it from an already installed system)

---

### Post by Mizutsuki on 2005-11-13
[QUOTE=tseliot]1) There is Opensuse Livecd (1 or 2gb), or RR4 Linux (an installable Livecd with a customised version of Gentoo). Try one of them (I recommend you Opensuse) so as to see if they work.
have a look at [http://distrowatch.com/]("http://distrowatch.com/")


2) Sorry but I don't know how to compile a kernel BEFORE installing Ubuntu (usually you compile it from an already installed system)[/QUOTE]


But couldn't I just compile it under the bootCD?  I feel like we're going in circles here.  What I really mean to ask is, assuming I can compile the kernel, is there anything I can do with it so that I can run the installer off of it?

---

### Post by tseliot on 2005-11-14
[QUOTE=Mizutsuki]But couldn't I just compile it under the bootCD?[/QUOTE]

No, I guess not. If you want to do such a thing you have to try Gentoo (another distribution) (and read all the installation manual).

The point is that Gentoo provides you a livecd that gets you to the command line. Then you can "emerge" (i.e. download and install with a command) the kernel sources of the latest kernel version available and then you have to compile it and enable the support for your chipset.

However I warn you that Gentoo can be difficult for a newbie (you have to study its documentation which you can find in its webpage)

I don't think it is possible in Ubuntu. Because its boot disk is NOT a livecd.

Another thing.

Try to do a "Server installation". You should be able to choose it as soon as the bootcd shows you the "Ubuntu" logo.

---

### Post by jbarroso on 2005-12-07
Ok, if you have linux, you can Install kernel source and compile the module.

When you have a compiled module, you can insmod it before Ubuntu install process detect your disks, pressing "ALT-F2"

I'm having problem with ataraid , When I compile it, Ubuntu kernel sais me "-1: Invalid module format"

I don't know about how compile this module ok ! 

Thanks you !

---

