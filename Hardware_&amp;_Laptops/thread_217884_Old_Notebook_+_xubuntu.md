---
title: "Old Notebook + xubuntu"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by JPMaximilian on 2006-07-17
I haven't been able to find a xubuntu forum, so I decided to post here.

I installed xubuntu on a Toshiba Notebook, its a 366 MHz amd with 32 megs of ram.  I thought that xubuntu might run decently on it, but it is so sluggish.  Additionally, the install took literally hours.  Is there anyway to selectively install packages or some other tricks to improver performance?  I have tried other distros such as DeLi, Debian, and DSL, but I haven't been able to get the install to work with these distros, and I prefer the ease of use that ubuntu provides.  Any help would be appreciated.

---

### Post by Jagot on 2006-07-17
You might want to install a more lightweight Window Manager.  Have a look here:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by awahl on 2006-07-17
You may also want to try the alternate install CD (If you haven't already). It worked well on my TP 600E with 366mhz 128mb ram. 

Quote:

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 

:Unquote

You can also try installing the server only version which doesn't include a window manager/GUI.

Once you install apt-get xubuntu-desktop to get the XFCE window manager. This is convenient because it will help keep your distro light (without OpenOffice) and alot of other stuff.

Go to Ubuntu>Downloads for the link(s).

HTH

---

### Post by Jagot on 2006-07-17
He isn't talking about installing it - he already has it installed.  He's talking about it's use when installed.

---

### Post by awahl on 2006-07-17
Thanks for correcting me - Was a but overzealous in my response. But - once you install the server version you can install any window manager that's in the repository. Good way to streamline the install and "build-up"....


:cool:

---

### Post by ORBiTrus on 2006-07-17
On 32MB?  Can't be done.

Ok, it can - I have a P300 w/ 64MB laptop, but running X is straining it...

Hints:
.) Buy a cheap USB flash key.  Use it as a high-priority swap drive, and fallback to hard drive.  Of course, on a USB 1 system, you won't see the benefits of a 2GB OCZ... (now that is nice).  Hard drives are slow, particularly laptop hard drives.
.) Don't use XFce.  The GTK libraries are too high a pull.
.) Either don't use a login manager, or if you really want one, use SLiM (Simple Login Manager)
.) Can you get the job done without pulling in X?  If not, try to use WindowMaker.  I find that even Fluxbox is a little too much, exp. since most apps are GTK.  Try to use only WindowMaker apps (whatever they are called).
.) Ubuntu, IMO, is too heavy.  This calls for a Slackware system - VectorLinux, ZenWalk (ZenWalk is my fav. on 96MB-128MB), true Slackware.  Or some minimalist distro like Arch, Frugalware, etc.  I highly recommend VectorLinux IFF it provides what you need (Vector doesn't support XDG menus, which means all menus have to be editted by hand, a right pain if you frequently add/remove programs).  ZenWalk comes with WindowMaker and SLiM, which may make it a bloody great distro.
.) Remember that ease-of-use comes at a cost.  In the case of Linux, the cost is RAM.


If any of these interest you, but you want more info, don't hesitate to PM me.  I love working with old hardware... (I just got 16MB of RAM for my 386SX so it could run Debian-Stable!)

---

