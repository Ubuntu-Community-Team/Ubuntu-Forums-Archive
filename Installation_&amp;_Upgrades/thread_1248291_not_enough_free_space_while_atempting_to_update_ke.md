---
title: "not enough free space while atempting to update kernel"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by tr4sh on 2009-08-24
[FONT=Arial Narrow][SIZE=2]i'm about to install updates for my Ubuntu 9.04, but it shows me this:

[IMG]http://i4.photobucket.com/albums/y131/tampan/error_mesages/notenoughdiskspace.png[/IMG]

I follow the steps 'sudo apt-get clean' and run the updates installation again, but it cames to the same result again.
how can I clean this up? 

btw, I have few options when I'm going to start-up my Linux, there's:
Ubuntu 9.04, Kernel 2.6.28-14-Generic
Ubuntu 9.04, Kernel 2.6.28-13-Generic
Ubuntu 9.04, Kernel 2.6.28-11-Generic

how can I get rid of -13 & -11 since I'm using the -14?
can I just delete it from /boot?
[/SIZE][/FONT]

---

### Post by kpkeerthi on 2009-08-24
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by raymondh on 2009-08-24
To see disk space and allocations/used space ... access a terminal and post back (if you wish) output of :

```
df -h
```

---

### Post by philcamlin on 2009-08-24
you can use synaptic to remove the cached deb files. I think it is recommended to do this periodically
so you have disk space :popcorn:

---

### Post by raymondh on 2009-08-24
For your boot options,

you can access/edit your /boot/grub/menu.lst (small L, not 1 nor I) and comment (put a # mark) on those kernels you don't wish to see.  I recommend that you maintain at least 2 working kernels ... that way if one of them misfires', you have immediate access to the other.  To access the menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Another option is to install startupmanager (search from synaptic).  SUM is GUI-based which also writes to the menu.lst.  In SUM, you can set which kernel to boot, how many kernels to show, time to boot, etc.  Once installed, access SUM thru system > admin.

---

### Post by tr4sh on 2009-08-25
@all
thanks guys really appreciate ur suggestions...
I'm using Synaptic PM as kpkeerthi & philcamlin suggest.
since I need to free up to 20 megs (I only allocate 54megs for /boot), synaptic is the best way to "get-rid-off" my old kernels

@raymondhenson
I'll keep in mind what you said... 
I'm keeping my -14 kernel while using newly update -15

---

