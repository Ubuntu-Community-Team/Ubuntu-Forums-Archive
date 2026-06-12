---
title: "Faster startup and faster performance"
date: 2008-11-02
forum: General Help
---

### Post by rmcellig on 2008-11-02
I am using a PC that I put together several years ago. Ubuntu can be rather slugish on it. What can I do to Ubuntu that would make my experience with Ubuntu faster without upgrading the hardware?

Here is what I have in my PC:


description: 	CPU
product: 	AMD Athlon(tm) processor
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
4
bus info: 	
cpu@0
version: 	6.4.4
slot: 	Socket A
size: 	1400MHz
width: 	32 bits
clock: 	133MHz
capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up

description: 	L1 cache
physical id: 	
9
slot: 	Internal Cache
size: 	128KiB
capabilities: 	synchronous internal write-back
id:	
cache:1
description: 	L2 cache
physical id: 	
a
slot: 	External Cache
size: 	256KiB
capacity: 	256KiB
capabilities: 	synchronous external write-back

description: 	System Memory
physical id: 	
1c
slot: 	System board or motherboard
size: 	512MiB
capacity: 	512MiB

---

### Post by Pro-reason on 2008-11-02
You could use Xfce instead of GNOME.  Use AbiWord instead of OpenOffice.org Writer.

---

### Post by rmcellig on 2008-11-02
How exactly can I use Xfce instead of Gnome? What do I have to do. I am new to all this. Is it difficult?

Thanks for Abiword. Good advice!!

---

### Post by scouser73 on 2008-11-02
I'd follow the advice here for a quicker startup: [http://www.kshoster.net/node/22]("http://www.kshoster.net/node/22")

---

### Post by Pro-reason on 2008-11-02
Install “xubuntu-desktop” by any of the normal means for installing software (Synaptic, apt-get install...).  That will cause all the software necessary to run Xfce to be installed.  “Xubuntu” means Ubuntu running Xfce.

Then, when you are at the log-in screen, go to the session menu and choose Xfce instead of GNOME.  People generally find Xfce and all of its apps to be more streamlined than GNOME and its apps.

Xfce uses mousepad instead of gedit, Thunar instead of Nautilus, etc., etc.

If you decide to stick with Xfce, use Synaptic to get rid of gedit, Nautilus, and all the other GNOME stuff that you are no longer using.

---

### Post by rmcellig on 2008-11-02
That's it? So, if I decide to go back to Gnome, it's just a matter of selecting it in the session menu while logging in? That's cool! 

If I run Xubuntu, will all of my other programs still work?

The more I use Linux, the more I appreciate it's flexibility.

---

### Post by Pro-reason on 2008-11-02
Other ideas:

Make sure that you have plenty of free space on your hard drive.  Linux filesystems automatically keep themselves unfragmented, but only if there is enough space.

Add [this repository]("https://launchpad.net/~chameleondave/+archive") and then install fidefrag to defragment your hard drive.

Have a plain desktop background instead of an image.

Get the right drivers for your video card.

Occasionally run the “top” command to see if any processes are using up too much CPU power or RAM.

---

### Post by Pro-reason on 2008-11-02
> **rmcellig said:**
> That's it? So, if I decide to go back to Gnome, it's just a matter of selecting it in the session menu while logging in? That's cool! 

If I run Xubuntu, will all of my other programs still work?

The more I use Linux, the more I appreciate it's flexibility.

Yes, you'll still have access to any and all Desktop Environments that are installed on your computer.  You could simultaneously have GNOME, Xfce, KDE, Fluxbox and others installed, and choose the one you wanted at log-in.  You could prefer one, and your partner could prefer another.

Also, logging into a given DE doesn't mean you can't actually use the apps from another.  There's nothing stopping you starting a KDE session, and then running Mousepad (from Xfce) and Firefox (cross-platform).  However, it is good to try to use apps of the same type.  That way, the “libraries” which are loaded in the background can be re-used.  This saves time and RAM.

Of course, the more you install, the more clutter there will be in the application menus, and the more disk space you'll be using.  So, it's good to uninstall stuff you don't use.

---

### Post by rmcellig on 2008-11-02
I have over 300GB of free space on my drive so I should be good to go? This is awesome!!!! Wow!!

Can hardly wait to try all of this. Christmas just arrived! :)

And I am a hard core Mac user.

---

### Post by OrangeCrate on 2008-11-02
> **rmcellig said:**
> How exactly can I use Xfce instead of Gnome? What do I have to do. I am new to all this. Is it difficult?

Thanks for Abiword. Good advice!!

Here are the instructions to add the Xubuntu desktop (Xfce) to Ubuntu:

[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

This will give you Abiword, the Thunar file manager which is lighter that Nautilus, plus other features...

---

### Post by rmcellig on 2008-11-02
I am in Xubuntu now. How do I install the KDE desktop from the Synaptic package manager?

Where is the option in Xubuntu to share files/ folders?

---

### Post by Pro-reason on 2008-11-02
It's “ubuntu-desktop” for GNOME, “xubuntu-desktop” for Xfce, and “kubuntu-desktop” for KDE.

I don't know all the ins and outs of Xfce.  I personally share files with ssh, which is independent of the desktop environment.

---

