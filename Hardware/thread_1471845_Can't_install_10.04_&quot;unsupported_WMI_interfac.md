---
title: "Can't install 10.04 &quot;unsupported WMI interface, unable to load&quot; acer-wmi"
date: 2010-05-03
forum: Hardware
---

### Post by bruno321 on 2010-05-03
Hi. I have an Acer Travelmate 290, and I have had previous Ubuntu releases installed without any problem -- as far as 8.04 as I seem to recall.

Now I'm trying to do a fress install of (L)ubuntu 10.04 and I can't even start the installation because of:

"no or unsupported wmi interface, acer-wmi".

I don't understand what this is, I've googled a bit and all I found was solutions for people who were upgrading from earlier versions, not installing from scratch.

So what should I do? It seems really awkward for a new version to break installation on some systems.

Thank you.

EDIT: The problem has been reduced to a malfunction (I can't play any video, for example). See posts below.

---

### Post by bruno321 on 2010-05-04
Bump-

---

### Post by bruno321 on 2010-05-04
This is still happening

---

### Post by riles32807 on 2010-05-04
Same here. Just upgraded to 10.04 on my Travelmate. The install seemed to go smoothly but on reboot, it kicked out the 'no or unsupported wmi interface' error then just hangs on a blank screen.

Any help?

---

### Post by riles32807 on 2010-05-04
This worked
[http://georgia.ubuntuforums.org/showpost.php?p=9226987&postcount=9](http://georgia.ubuntuforums.org/showpost.php?p=9226987&postcount=9)

---

### Post by bruno321 on 2010-05-05
That solution applies to the case when you have upgraded to 10.04 from an earlier version, which is not my case because I'm doing a clean installation!

Any ideas? Also, installing 9.10 and upgrading is not an option for two reasons 1) that's not a clean way to set up a healthy system 2) I'm installing Lubuntu, and there's no previous version.

---

### Post by bruno321 on 2010-05-05
Well, I did some progress.

I've managed to install the OS. When the CD boots, I pressed F4 and chose "safe graphics" mode. Then I was able to install flawlessly.

But the system wouldn't boot because of the same error. Then I applied the method post #5 is linking to and that worked perfectly.

---

### Post by bruno321 on 2010-05-05
Not so perfectly.

System boots fine, but I can't play any video (I've tried with mplayer and with VLC, and X when the video is going to play).

So I guess that KMS thing is not a solution but only a workaround.

---

### Post by bruno321 on 2010-05-08
I've done the VideoRam suggestion which was supposed to solve the issue but it does nothing. Xorg's log reads:

(WW) intel(0): VideoRam configuration found, which is no longer recommended. 
(II) intel(0): Continuing with default 0kB VideoRam instead of 130560 kB. 
(II) intel(0): [DRI2] Setup complete 
(**) intel(0): Kernel mode setting active, disabling FBC. 
(**) intel(0): Framebuffer compression disabled 
(**) intel(0): Tiling enabled 
(**) intel(0): SwapBuffers wait enabled 
(**) intel(0): VideoRam: 131072 KB

so it serves no purpose to do what is suggested. Also, the UXA option is useless, because

(WW) intel(0): Option "AccelMethod" is not used.

Here's the output of lspci -vv:
 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Subsystem: Acer Incorporated [ALI] Device 003d
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+ Latency: 0 Interrupt: pin A routed to IRQ 10 
Region 0: Memory at b0000000 (32-bit, prefetchable) [size=128M] 
Region 1: Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
Region 2: I/O ports at e000 [size=8]

Capabilities: <access denied>
Kernel driver in use: i915 
Kernel modules: i915


I insist: Workaround A lets me use the system but I can't play any video because X crashes.

---

### Post by skamarla on 2010-05-09
I had exactly the same problem on exactly the same hardware. I was upgrading from 9.10, though.

I followed riles32807's suggestion, and it worked. But when trying to play videos, I got the same problem as you.

I will open a separate request. It looks like a different problem to me. I will report back here when I get a solution.

---

### Post by skamarla on 2010-05-09
It's working now. It seems to be a well known bug for older Intel grahics cards. See [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379)

I have followed their advice and I have installed this mainline kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

It's not hard to install, but you can find some instructions [here]("http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/")

---

### Post by bruno321 on 2010-05-09
Well, finally! Thank you. Installing latest kernel seems to have fixed it.

---

### Post by JaJaBinks on 2010-05-26
> **skamarla said:**
> It's working now. It seems to be a well known bug for older Intel grahics cards. See [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379)

I have followed their advice and I have installed this mainline kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

It's not hard to install, but you can find some instructions [here]("http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/")

Thanks for the Info. I have been having the same problem on my Acer F1 desktop, the only difference being that it did not stop boot up.

I first upgraded from 9.10 to 10.04 before eventually doing a clean install, but the error message still persisted, although as I said it did not stop the computer from booting.

---

