---
title: "Screen not detected with Thinkpad T410"
date: 2010-02-19
forum: Hardware
---

### Post by noarc on 2010-02-19
I'm running Ubuntu 9.10 on a Thinkpad T410.  It has an Intel Graphics Media Accelerator HD, which I believe is quite new. The problem is that the display isn't correctly detected (says "unknown") and the resolution is wrong, and I can't extend or clone the monitor to an external display either.

My distribution has version 2.9.0 of the intel xserver-xorg driver.  It looks like there is a newer version of the Intel graphics drivers available from [http://intellinuxgraphics.org/:](http://intellinuxgraphics.org/:)

2010-1-5: xf86-video-intel 2.10.0 released, with user-modesetting removed, together with Intel 2009Q4 graphics package released.

I think the 2009Q4 package has better support for my hardware, but I don't know how to install those drivers from source.  Is there any Ubuntu package with the new version of the drivers?  If not, any idea when I can expect such a package?  And as a last resort, are there any guides about how to install these drivers from source?

Cheers,
Nick

---

### Post by lidex on 2010-02-19
You can try using a PPA - info is here:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")

and/or enabling backports in "Software Sources". Have you ruled out your graphics driver as an issue?
What is your terminal output of this command:
 ```
lspci -nn | grep VGA
```

---

### Post by nomnex on 2010-02-21
If the answer of lidex does not solve the problem, would you mind opening a bug about the issue on Launchpad?

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

> are there any guides about how to install these drivers from source?
On the same page: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

Side note: before being adventurous, I would first open a bug on launchpad, provide the debugging information requested - since your model is new and popular, there might be a lot of feedback.  Only then, complile a newer driver from source.

---

### Post by noarc on 2010-02-21
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Arrandale Integrated Graphics Controller [8086:0046] (rev 02)

I tried lidex's suggestion and am using the latest drivers from PPA, but my display is still not detected properly.  I will open a bug on launchpad.

---

### Post by lidex on 2010-02-21
Now that we know your graphic controller, a search provided these results:
[http://ubuntuforums.org/showthread.php?t=1400524]("http://ubuntuforums.org/showthread.php?t=1400524")
[http://ubuntuforums.org/showthread.php?t=1397534]("http://ubuntuforums.org/showthread.php?t=1397534")

---

### Post by nomnex on 2010-02-23
**noarc**, are you going to install 10.04 alpha3 as suggested on Launchpad, or will you use **stacktracer **workaround (comment #3,  first of the two links provided by **lidex**)?

Can give some feedback when you have full graphic resolution, and external monitor working?

---

### Post by noarc on 2010-02-24
I used the stacktracer workaround, which works provided you disable compiz (explained how in that thread).

---

### Post by nomnex on 2010-02-24
> **noarc said:**
> I used the stacktracer workaround

What kernel version have you chosen?
Have you tested with an external monitor?

---

### Post by noarc on 2010-02-24
9.10 -- latest kernel
External monitor works as well as full range of resolutions.  Although the fact that compiz doesn't work probably means hardware acceleration isn't working either.

---

### Post by nomnex on 2010-02-24
I meant what mainline kernel version [http://kernel.ubuntu.com/~kernel-ppa/mainline/?]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/?")

hopefully, it will be fixed on 10.04 final (compiz+arrandale)

---

### Post by noarc on 2010-02-24
Yes, I meant I use whichever kernel is the latest with 9.10.  I took no special steps to upgrade the kernel besides the recommended updates.

---

### Post by nomnex on 2010-02-24
Oh I see, so let me confirm

with the default 9.10 vanilla kernel

```
2.6.31-19-generic
```1. Install PPA xorg-edgers

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

2. Replace in xorg.conf

```
"vesa" with "intel"
```3. gconf-editor, change compiz to metacity

```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```To get your graphic working?

---

### Post by noarc on 2010-02-24
Right.

---

