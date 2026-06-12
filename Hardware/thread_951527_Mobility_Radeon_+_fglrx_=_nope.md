---
title: "Mobility Radeon + fglrx = nope"
date: 2008-10-18
forum: Hardware
---

### Post by Mozai on 2008-10-18
I went from hapily using the 3D-accelerated fglrx drivers in Hardy Heron, to upgrading to Intrepid, and fglrx was replaced by xserver-xorg-video-radeon and the ati wrapper.

I tried xserver-xorg-video-fglrx (I understand it's an advance version of the ATI proprietary Catalyst driver, to work with the newer Xorg in Intrepid), but the module won't load.

[FONT="Courier New"]Oct 17 00:53:58 jomi kernel: [  157.074827] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Oct 17 00:53:58 jomi kernel: [  157.157556] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
Oct 17 00:53:58 jomi kernel: [  157.158685] [fglrx:drm_alloc] *ERROR* [driver] Allocating 0 bytes
Oct 17 00:53:58 jomi kernel: [  157.158741] [fglrx:firegl_init_device_list] *ERROR* Out of memory when allocating device heads
Oct 17 00:53:58 jomi kernel: [  157.158801] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed[/FONT]

(I rebooted after installing the Intrepid fglrx packages, and I killed all instances of X before attempting)

aticonfig --list-devices says "No devices found." and yet:
[FONT="Courier New"]moses@jomi:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10][/FONT]

I'm wondering (out loud) if there's another kernel module that comes with Intrepid + xserver-xorg-video-radeon that has locked the fglrx module out, or what other diagnostics I could do to find out why the fglrx kernel module isn't able to access the ATI Radeon 9600 card in my Thinkpad.  (I wouldn't say no to an outright solution.  I saw that there's a way to install ATI's own drivers, but that requires an older version of Catalyst/fglrx and downgrading Xorg to Hardy Heron's version.  Ick.)

---

### Post by gladiac on 2008-10-22
Hello!

I also experience this problem on a HP nw8000 which has the exactly same graphics-chip:

01:00:00 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

well, seems to be a problem of the driver-blob that comes from amd which is a prerelease that has been pushed out expecially for intrepid so that the ubuntu-devs have something to package. All we 9600 M10 can do is stay away from fglrx until there is a formal release by amd in a packaged form.
cheers

---

### Post by steffen on 2008-10-23
...just confirming this on the same graphics chip as the above posters.

---

### Post by drspin on 2008-10-25
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/286020](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/286020)

AND

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

### Post by Yashiro on 2008-10-25
There's no working fglrx driver for the new version of Xorg that ships in 8.10, yet.

So stay on hardy for 3d, or upgrade and get stuck with a crappy driver.

---

### Post by jocko on 2008-10-25
> **Yashiro said:**
> There's no working fglrx driver for the new version of Xorg that ships in 8.10, yet.

So stay on hardy for 3d, or upgrade and get stuck with a crappy driver.

That's wrong. The intrepid repos contain a beta version of the next fglrx release (Catalyst 8.11), which does support xorg 7.4/xserver 1.5. The latest *official* fglrx driver on ATI's website (Catalyst 8.10, released after the beta version of 8.11 appeared in the intrepid repos) does not support the latest xorg release.

---

### Post by pedrogl on 2008-10-25
> **Yashiro said:**
> There's no working fglrx driver for the new version of Xorg that ships in 8.10, yet.

So stay on hardy for 3d, or upgrade and get stuck with a crappy driver.
I have the same error on hardy.
I think that new driver (fgrlx 8.10 downloaded from ati website) just don't work for Radeon 9600.

---

### Post by Bablefish on 2008-10-25
I call it the pure HELL of Linux and ATI. They just don't like each other period.

---

### Post by jocko on 2008-10-26
> **pedrogl said:**
> I have the same error on hardy.
I think that new driver (fgrlx 8.10 downloaded from ati website) just don't work for Radeon 9600.

There's nothing wrong with support for radeon 9600. fglrx worked for me in hardy, and now it also works in intrepid.

---

### Post by pedrogl on 2008-10-26
> **jocko said:**
> There's nothing wrong with support for radeon 9600. fglrx worked for me in hardy, and now it also works in intrepid.

Which driver version do you use in hardy?
For me, all versions up to 8.9 work acceptable in hardy (with some issues, no resume/hibernate, etc).

---

### Post by jocko on 2008-10-26
> **pedrogl said:**
> Which driver version do you use in hardy?
For me, all versions up to 8.9 work acceptable in hardy (with some issues, no resume/hibernate, etc).

I just realized I only used the repo version in hardy, and then I went back to gutsy because of the crappy dual screen support (I like being able to run a separate x screen on my tv for watching movies fullscreen. Dual screen haven't worked at all with any drivers newer than the 8.37 ones in the gutsy repo).
I've tested most releases until 8.7 or 8.8 in gutsy. They work, but as they don't fix dual screen support or xvideo overlay, none of them are as good as the old 8.37 driver.

---

### Post by monikersupreme on 2008-12-26
First off: HP NC8000 notebook (w/ Radeon 9600 mobility graphics) and Ubuntu Intrepid v8.10 with all the updates. 

What is the consensus on the current (as of 12/10/08) Linux_x86 drivers released on the ati.amd site:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I had hella problems when I upgraded to these under v8.04; now I've a fresh install of v8.10 and a working (but slow) vesa driver (I think, I don't see any proprietary drivers listed under "Hardware Drivers" so I assume I'm currently running under the open source graphics driver set)... 

Is it worth upgrading to the proprietary drivers?

How do I back out to my initial driver set should the proprietary ATI drivers not take?

Multiple monitor support is going to be important to me going forward, along with the ability to switch between single and multiple monitor configurations automatically (based on the monitor's detected, so that I don't need to worry about reconfiguring every time I pull my laptop off of it's docking station)...

Any advice would be much appreciated!

---

### Post by DWade on 2008-12-26
I am going to add mine in here too.

I have an older emachine M6809 with radeon 9600 anthlon mobility 64 3000+, 1.278 gig memory.  I have tried ati catalyst from add remove programs no workie
tried from amd/ati version 8.11 which is the only driver that works with xorg 7.4
and no workie 

both at running sudo aticonfig --install come up with
backing up files
segmented files unable to continue.
$

at that point you have to uninstall the ati package or else your in 800x600 graphics.

I also have a new dell quad core with radeon hd 2400 xt.  Have to boot up with a live cd copy the ati driver to /home/documents directory, boot up in recovery mode and run comandline and run the driver because it boots up with monitor out of range and no video at all. After the drive runs and installs, Then it works great.

but this radeon 9600 no workie...

---

### Post by johny_ on 2009-01-04
My machine runs 9600 also, and, I realized this lack of fglrx too.
However, 8.10 installed with the default driver, which I assume must be
"the open-source one" ATI driver, as  compiz is enabled.
What I see though is slow text scrolling, in browsers (even dillo!), and text editors, resulting i high CPU consuming.

Has anyone of you noticed anything similiar?

---

### Post by loig on 2009-01-07
yes, I have the same problem :
 * only the free radeon driver
 * everything is soo slow and cpu consuming
 * firefox crashing at  every wink

 and it's even worse  after upgrading  to jaunty

---

### Post by johny_ on 2009-01-07
> **loig said:**
> yes, I have the same problem :
 * only the free radeon driver
 * everything is soo slow and cpu consuming
 * firefox crashing at  every wink

 and it's even worse  after upgrading  to jaunty

I jumped in to the #ati channel on Ubuntu IRC network, and some guys
have adviced me to add this line to my xorg.conf device section

```
        Option          "Accelmethod"     "EXA"

```

It's a recent enhancement to the GLIB xorg extension, introduces another method to 2d displaying.
They told me, it was supposed to be enabled by default in jaunty, maybe it hasn't been yet; I suppose, you're on a version still in development.
It helped me a lot with the slow scrolling, go ahead to give it a try.

P.S: Make sure to put all the "endings" to the sections when you edit xorg.conf

---

