---
title: "Should not an Intel Skylake APU be totally supported in Ubuntu 16.04?"
date: 2016-03-27
forum: Hardware
---

### Post by rolltide101x on 2016-03-27
From what I understand Intel Skylake is supported after kernel version 4.3 but it still gives me issues on 16.04 (massive screen tearing).

On 15.10 I installed the Linux Intel Drivers from the link below and upgraded the kernel to 4.5. Can someone please guide me through the reasons as to why this screen tearing may be occurring? 

For reference it will not boot without the two boot parameters "idle=nomwait" and "nomodeset" after I install the Nvidia drivers I no longer need "nomodeset" to boot but the screen tearing still occurs. Let me know what commands you need so I can please solve this issue.



The cpu is Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz. I do not even care about the Nvidia card I just want the Intel graphics to work so I wont have the screen tearing.

---

### Post by rolltide101x on 2016-03-27
I am willing to use Ubuntu 14.04, 15.10, or the 16.04 Beta. I just want one to work properly :(

---

### Post by tony116 on 2016-03-28
When you describe massive screen tearing is this while viewing videos in parole, scrolling through webpages, or something else? Also what model laptop do you have and what is your dedicated video card model? 

I have the Alienware 15 R2 laptop with the Intel(R) Core(TM) i7-6700HQ and Nvidia 970m dedicated graphics card. I have slight tearing while scrolling webpages and viewing video in parole not to bad though. I am on xubuntu version 14.04-4 if I try version 15.10 I cannot suspend my laptop because it will turn screen black on resume and causes graphics drivers to crash. Do you have problems suspending your laptop on Ubuntu 15.10+ ? I have had the same issue when using manjaro i3 15.12 so maybe it has something to do with the newer kernels and or intel video graphic drivers.

---

### Post by slickymaster on 2016-03-28
*Moved to the ***Hardware*** sub-forum*

---

### Post by buzzingrobot on 2016-03-28
Skylake support in the 4.3 kernels is minimal, and not much more in the 4.4 series.

16.04 works reasonably well for me on an Intel NUC i5-6260u with a 4.6 release candidate kernel from the kernel PPA, a pre-release Mesa/Xorg/Intel stack from a Canonical staging PPA, and a kernel parameter (i915.enable_rc6=0) which keeps the CPU in high-power mode, so will impact battery lifetime.

The Arch wiki has some Skylake workarounds: [https://wiki.archlinux.org/index.php/intel_graphics#Skylake_Support](https://wiki.archlinux.org/index.php/intel_graphics#Skylake_Support)

---

### Post by rolltide101x on 2016-03-28
Sorry I forgot to attach the laptop

[http://www.bestbuy.com/site/msi-ge62-apache-pro-004-15-6-laptop-intel-core-i7-16gb-memory-1tb-hard-drive-aluminum-black/4556202.p?id=1219766811085&skuId=4556202](http://www.bestbuy.com/site/msi-ge62-apache-pro-004-15-6-laptop-intel-core-i7-16gb-memory-1tb-hard-drive-aluminum-black/4556202.p?id=1219766811085&skuId=4556202)


But I get screen tearing in virtually everything I do from scrolling down web pages to watching a video.

---

### Post by rolltide101x on 2016-03-28
> **buzzingrobot said:**
> Skylake support in the 4.3 kernels is minimal, and not much more in the 4.4 series.
16.04 works reasonably well for me on an Intel NUC i5-6260u with a 4.6 release candidate kernel from the kernel PPA, a pre-release Mesa/Xorg/Intel stack from a Canonical staging PPA, and a kernel parameter (i915.enable_rc6=0) which keeps the CPU in high-power mode, so will impact battery lifetime.

The Arch wiki has some Skylake workarounds: [https://wiki.archlinux.org/index.php/intel_graphics#Skylake_Support](https://wiki.archlinux.org/index.php/intel_graphics#Skylake_Support)

I am on 15.10 right this second because I wanted to attempt to install the Intel Graphics Drivers again. I have read that Arch page before what do you think I should try?

---

### Post by oldfred on 2016-03-28
I have Skylake i5-6500 with 16.04. 
Only Intel graphics out via HDMI.
No issues on video at all with Internet browsing and normal use. No gaming. 

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

---

### Post by rolltide101x on 2016-03-28
> **oldfred said:**
> I have Skylake i5-6500 with 16.04. 
Only Intel graphics out via HDMI.
No issues on video at all with Internet browsing and normal use. No gaming. 

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

Did you do anything special or did it for the most part just work? Because I have used 16.04 and the same issues as 15.10 (and ever other Linux distro Ive used which is quite a few).

---

### Post by buzzingrobot on 2016-03-28
> **rolltide101x said:**
> I am on 15.10 right this second because I wanted to attempt to install the Intel Graphics Drivers again. I have read that Arch page before what do you think I should try?

Can't say for sure since I'm on a different and, I think, newer chip, different motherboard, etc.

But, if you're prepared to handle things that go wrong, try using the Canonical X staging PPA ([https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging](https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging)), as I mentioned. It will install a newer Mesa, a newer xorg-xserver, and a newer xserver-xorg-video-intel driver. Do the usual PPA thing: install it, sudo apt update, then sudo apt full-upgrade (or sudo apt-get dist-upgrade). I believe all of these packages are intended for the final 16.04 release.  I do not know if they will install cleanly in 15.10. No Wily packages are at that PPA, so you may need to resort to a manual install of each package. If you do, look very carefully at what apt wants to install/remove.  On Xenial here, 11 packages are installed, nice and cleanly. It's entirely possible on Wily that you'd run into unresolvable dependency issues.

The 4.6rc1 kernel are at the kernel PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc1-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc1-wily/)

Instructions for installing these kernels are on the wiki: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

The 4.6 kernel, and the latest 4.5 "daily" kernels"  contain Skylake patches and fixes that are not in the 4.4 kernels. Unless they are backported, they won't be in future 4.4 releases.

The 4.6 kernel is at Release Candidate One stage, released just over the weekend. So, early days, yet.  It will see several candidate releases over the next several weeks.

I mentioned the kernel parameter I use.  I don't experience screen tearing.  I do experience display (GPU) freezes if I do not use that parameter.

**CAVEAT:  I have no idea if this will work on your system or on 15.10.  It might work. It might trash your system. All I know is that it works for me -- so far -- on 16.04.**

---

### Post by rolltide101x on 2016-03-28
> **buzzingrobot said:**
> Can't say for sure since I'm on a different and, I think, newer chip, different motherboard, etc.

But, if you're prepared to handle things that go wrong, try using the Canonical X staging PPA ([https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging](https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging)), as I mentioned. It will install a newer Mesa, a newer xorg-xserver, and a newer xserver-xorg-video-intel driver. Do the usual PPA thing: install it, sudo apt update, then sudo apt full-upgrade (or sudo apt-get dist-upgrade). I believe all of these packages are intended for the final 16.04 release.  I do not know if they will install cleanly in 15.10. No Wily packages are at that PPA, so you may need to resort to a manual install of each package. If you do, look very carefully at what apt wants to install/remove.  On Xenial here, 11 packages are installed, nice and cleanly. It's entirely possible on Wily that you'd run into unresolvable dependency issues.

The 4.6rc1 kernel are at the kernel PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc1-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc1-wily/)

Instructions for installing these kernels are on the wiki: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

The 4.6 kernel, and the latest 4.5 "daily" kernels"  contain Skylake patches and fixes that are not in the 4.4 kernels. Unless they are backported, they won't be in future 4.4 releases.

The 4.6 kernel is at Release Candidate One stage, released just over the weekend. So, early days, yet.  It will see several candidate releases over the next several weeks.

I mentioned the kernel parameter I use.  I don't experience screen tearing.  I do experience display (GPU) freezes if I do not use that parameter.

**CAVEAT:  I have no idea if this will work on your system or on 15.10.  It might work. It might trash your system. All I know is that it works for me -- so far -- on 16.04.**


I will probably attempt to do all of this and see how it does with a separate install of 16.04. I actually have a decent usable system on 15.10 right now using 15.10 with XFCE and Compton. Compton took 99% of the screen tearing away with the Intel Driver I am using (Compton will not load with the Nvidia one but i am not that concerned about it). But I am not a huge fan of XFCE would prefer KDE or Unity (Love Unity)

---

### Post by buzzingrobot on 2016-03-28
> **rolltide101x said:**
> I will probably attempt to do all of this and see how it does with a separate install of 16.04. I actually have a decent usable system on 15.10 right now using 15.10 with XFCE and Compton. Compton took 99% of the screen tearing away with the Intel Driver I am using (Compton will not load with the Nvidia one but i am not that concerned about it). But I am not a huge fan of XFCE would prefer KDE or Unity (Love Unity)

XFCE's window manager seems to cause serious tearing for many people.

---

### Post by fjgaude on 2016-03-28
> **oldfred said:**
> I have Skylake i5-6500 with 16.04. 
Only Intel graphics out via HDMI.
No issues on video at all with Internet browsing and normal use. No gaming. 

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

My Skylake i3-6100 only works with the Display Port for video. With HDMI no monitor output. I can live this way, but curious.

I'm Intel all the way:

```
frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.4.0-040400rc5-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P1.50 date: 11/04/2015
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed/max: 799/3700 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel Skylake DT GT2
           GLX Version: 3.0 Mesa 11.0.7
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: bcma-pci-bridge
Drives:    HDD Total Size: 756.2GB (32.1% used)
Info:      Processes: 250 Uptime: 1 min Memory: 615.2/15736.5MB
           Client: Shell (bash) inxi: 2.2.28

```

---

### Post by oldfred on 2016-03-29
@figaude
The only real difference beside motherboards, is the resolution. I am using a low cost HP monitor with only 1920x1080.
I also see where further updates to Intel/kernel/support drivers are in each further newer kernel, 4.5 & now 4.6.

---

### Post by rolltide101x on 2016-03-30
> **buzzingrobot said:**
> XFCE's window manager seems to cause serious tearing for many people.

It was happening in ALL desktop environments, I tried Unity, Gnome 3, LXDE, KDE Plasma, etc. XFCE with Compton is the only way I have found to eliminate it on my hardware.


XFCE with Compton has me with a usable system on 15.10 so I am going to stick with this until 16.04 officially releases. After 16.04 releases I will put more effort into figuring out the issue instead of putting a bandaid on it (using a DE I do not care for much)

---

