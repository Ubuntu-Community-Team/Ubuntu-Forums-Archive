---
title: "Sound not working"
date: 2013-12-30
forum: Hardware
---

### Post by aman207 on 2013-12-30
Ubuntu recognizes my sound card but for some reason it doesn't want to use it. When I type lshw -C sound into terminal, I get this

```
*-multimedia UNCLAIMED  
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fabf8000-fabfbfff


```
In settings under sound, it says "Dummy Output"

I am running Ubuntu 13.10

Anybody have any ideas on what's wrong and what I can do to fix it?
Thanks!

---

### Post by dsc1596 on 2013-12-30
I had this problem when I installed the development branch (Trusty Tahr). My sound didn't work, and the fglrx and fglrx-updates additional drivers did not work. I ended up installing a newer kernel which worked like a charm. I believe the kernel was upgraded from 3.11-14 to 3.12-xx. I believe I downloaded the .deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.6-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.6-trusty/)

---

### Post by aman207 on 2013-12-30
> **kolb-john79 said:**
> I had this problem when I installed the development branch (Trusty Tahr). My sound didn't work, and the fglrx and fglrx-updates additional drivers did not work. I ended up installing a newer kernel which worked like a charm. I believe the kernel was upgraded from 3.11-14 to 3.12-xx. I believe I downloaded the .deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.6-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.6-trusty/)
So do I install that one or this one for saucy (my version)?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.10.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.10.1-saucy/)

---

### Post by dsc1596 on 2013-12-30
Try the saucy version, and if that doesn't work, then you can try the 3.12... version. See [this link]("http://news.softpedia.com/news/How-to-Install-Linux-Kerrnel-3-12-in-Ubuntu-13-10-397013.shtml") for a walkthrough of how to install 3.12 on saucy. Of course the usual warnings apply (don't use this on a mission-critical system, and backup your files of course if you have anything precious.) Usually you can just uninstall it though, per the walkthrough. [Here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/") is a link to the Saucy version of 3.12 if you would like you can try that one instead. I've read somewhere that 3.12 is sometimes better for video, not sure about audio though.

---

