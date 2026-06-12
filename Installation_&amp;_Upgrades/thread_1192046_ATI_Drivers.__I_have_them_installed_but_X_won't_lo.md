---
title: "ATI Drivers.  I have them installed but X won't load"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by jus71n742 on 2009-06-19
My Xorg is actually trying to load these drivers.  I am using the same driver as before with these 4850 HD's 
I exited X and ran 
```

sudo sh *.run

```
said installer ran.  I got back to X no problem.  Even altered some stuff, then when I rebooted everything went crazy. No screen, no display in TTY1-7
but I can get there in recovery mode.  thats it.  I Have tried removing and reistalling a different way with
```
 
--buildpkg Ubuntu/8.04

```
on the end of the driver. still nothing. 
when I look at my xorg.conf file It is trying to load the correct ATI driver.  So I am stuck as to what may be causing this. I have read a few different threads on how this works but nothing has worked so far.

I went back and repaired the following package:
> 
fglrx-amdcccle

 since this package was broken. then reinstalled the drivers since they still weren't detected.  They are still the default loaded drivers in the xorg.conf file though.
I am using these drivers

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

---

### Post by markbuntu on 2009-06-19
You need open a terminal and run 

aticonfig --initial

What ubuntu are you using and which driver?

---

### Post by jus71n742 on 2009-06-19
8.04
and the driver is at the link in my post

```

aticonfig --initial

```
produces the following output
> 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-4


---

### Post by markbuntu on 2009-06-19
It should work OK now after you restart x. I am using that driver on my Hardy amd64 Ubuntustudio and have no problems. This driver uses randr and you need to disable randr if you have more than one display.

---

### Post by jus71n742 on 2009-06-21
How would I disable that? never heard of that setting.

Also, when I install it again and again I can get into catalyst control center HOWEVER, if I change ANYTHING. and log out to restart X.  it fails immediately and I can't do a thing again.  No display until I reboot into recovery mode.  Is there a setting in the Xorg.conf file that will let me disable randr?  Also it will not detect the second video card as a video card, just as an unknown device and will not allow the card running 2 monitors to split them into separate displays which is what I want.

also lspci returns the following:
```

02:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
02:00.1 Audio device: ATI Technologies Inc Unknown device aa30
04:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
04:00.1 Audio device: ATI Technologies Inc Unknown device aa30

```

---

### Post by jus71n742 on 2009-06-24
Ok when I start the package manager I recieve the following broken package

libamdxvba1

and so I remove it.  attempt to reinstall and again...broken package.
I can not find this package in the package manager unless its broken. is there another way to acquire this package?
I also receive the error that 
```

errors were encountered while processing:
libamdxvba1.deb

```
then above that it says no such file or directory.

this is all from running 
```

sudo sh *.run --buildpkg Ubuntu/8.04
sudo dpkg -i *.deb
aticonf --initial -f

```

also if I just rm all that deb files and start fresh....then this is what happens:
```

Errors were encountered while processing:
fglrx-amdcccle_8.852-Oubuntu1_amd64.deb
fglrx-kernel-source_8.582-Oubuntu1_amd64.deb
libamdxvba1

```

So I am really confused at this since none of this happened last time I installed them.  I would REALLY appreciate any ideas on this.

---

### Post by jus71n742 on 2009-06-24
Got different drivers and it is sorta kinda working...meaning I am in the regular kernel (not recovery) and The main screen works and is the correct resolution
However when I try and change the other 2 screens ...everything gets distorted and scrambled up.
one of them even shows the desktop in the bottom corner and the rest of the screen looks like a TV does when it is snowy just not moving.

---

### Post by markbuntu on 2009-06-25
You should check out this thread about getting dual monitors working

[http://ubuntuforums.org/showthread.php?t=1171926](http://ubuntuforums.org/showthread.php?t=1171926)

---

