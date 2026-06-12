---
title: "Get rid of GUI for a fileserver?"
date: 2008-09-07
forum: General Help
---

### Post by ShiningMasamune on 2008-09-07
Hey all.  A while back I put together a fileserver for my family and I'm running ubuntu on it.  I decided against getting the server edition because I wasn't too confident in my command-line-fu, but now that I've got everything set up and some experience using ssh, the GUI is just sitting there taking up resources.  Is there a way to disable it?  Preferably without having to reboot?

Thanks

---

### Post by hyper_ch on 2008-09-07
simplest way would be to deactivate gdm, kdm or xdm - depending on the gui.....

then you could also remove it all

```

sudo apt-aptitude remove ubuntu-desktop

```
or kubuntu or xubuntu

If that doesn't remove all the packages, then you could use Aysiu's collection of the individual packages:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) (look for pure gnome/kde/xfce, then they are list for removal of those)

and then you might want to change the kernel to a server kernel.

---

### Post by ShiningMasamune on 2008-09-07
Erm... how do I deactivate it?  Also, tell me about how would I go about changing the kernel.  That kind of sounds like something that might mess up my settings...

---

### Post by hyper_ch on 2008-09-07
```

sudo apt-get install linux-image-2.6.24-19-server

```

That would be the newest kernel for hardy. You then have, after installation, to set default boot to it in the /boot/grub/menu.lst file.

As for gdm/kdm/xdm removal
```

sudo update-rc.d gdm remove

```
after a restart the gui shouldn't be started anymore.
If you want to add teh gui again:
```

sudo update-rc.d gdm defaults

```

---

### Post by ShiningMasamune on 2008-09-07
Could you explain that menu.lst editing part?

---

### Post by DouglasAWh on 2008-09-07
> **ShiningMasamune said:**
> Could you explain that menu.lst editing part?

There's a part in menu.lst called default.  You can set it to whatever.  I usually leave it at zero and move the stuff around it since when a new kernel gets installed, it will mess up the numbering.  The list you are changing is the list you see when you boot.  The one that has the recovery mode or whatever it's called.

---

### Post by ShiningMasamune on 2008-09-07
Yeah, I see the "default" part, and it is already set to 0, but what looks scary is the following part at the bottom:

```

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=332a7ae9-df3a-419b-9790-19722076f7f2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=332a7ae9-df3a-419b-9790-19722076f7f2 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=332a7ae9-df3a-419b-9790-19722076f7f2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=332a7ae9-df3a-419b-9790-19722076f7f2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

What in there do I have to change?

---

### Post by HermanAB on 2008-09-07
No, no and a few more nos. Just change the runlevel:

sudo init 3

Cheers,

Herman

---

### Post by rossjman1 on 2008-09-07
If you want to completely remove the gui and all apps that depend on it:
```
sudo apt-get remove xserver-xorg
```

---

### Post by DouglasAWh on 2008-09-07
> **ShiningMasamune said:**
> Yeah, I see the "default" part, and it is already set to 0, but what looks scary is the following part at the bottom:


What in there do I have to change?

Install the server kernel first and see if it changes itself to the default.  All those kernels are in order, 0 being the first.  So if the default is 0 and the -server kernel is zeroth, then that's what you want.  For instance, if you wanted -14 to be your default, you would just move it in front of -15 (or change your default to 2).  Just remember the "first" one is zero and you number after that, so the "third" is 2.

---

### Post by Vivaldi Gloria on 2008-09-07
> **HermanAB said:**
> No, no and a few more nos. Just change the runlevel:

sudo init 3

Cheers,

Herman

Nope, in ubuntu runlevels 2-5 are all same:

> 0: Halt / Shut down.  All processes are stopped, all filesystems are unmounted, and all users taken offline.  Power can now be safely removed.
1: Single user mode.  Only root allowed login (requires password).  All filesystems listed in /etc/fstab are mounted.  Limited set of services started.
2-5: Multi-user mode.  All filesystems listed in /etc/fstab mounted, graphical environment (if installed) brought up.  Full standard operational mode.
6: Reboot.  As with runlevel 0, all processes stopped, all filesystems unmounted, all users taken offline, the box rebooted, and taken to the default runlevel.

See [[COLOR="Purple"]this[/COLOR]]("http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/").

---

