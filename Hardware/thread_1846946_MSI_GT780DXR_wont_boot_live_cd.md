---
title: "MSI GT780DXR wont boot live cd"
date: 2011-09-19
forum: Hardware
---

### Post by cllgnc89 on 2011-09-19
Specifications:
MSI GT780DXR-099
Intel® Core™ i7-2630QM Processor
Chipset 	Intel® HM67
GPU 	NVIDIA® GeForce® GTX 570M
RAM 16 GB
Live CD: Tried ubuntu x64 11.04 and 11.10 beta 1 

After initial purple screen the boot process is haled on a screen listing detected hardware. Is this a driver issue?

[ATTACH]202515[/ATTACH]

---

### Post by phantom_ on 2011-09-26
can you please try older versions like lucid or maverick?

---

### Post by csnavely on 2011-09-27
Hi im new to linux and im haveing the same problem with my acer aspire 5733z-4851 only it wont even attempt to boot from the live cd it just goes straight to windows start up. The live ck works on my husbands gateway nv79 only with no sound. Any ideas? I really like ubuntu and want to use it.

---

### Post by phantom_ on 2011-09-27
hello csnavely,

you've mentioned that computer boots straight from windows. i think you even do not see Ubuntu boot screen, right?

if that is the case, computer prefers to boot from hard drive, bypassing the CD. you have to change the boot sequence from the BIOS in order to force the computer to boot from CD.

---

### Post by cllgnc89 on 2011-09-29
> **phantom_ said:**
> can you please try older versions like lucid or maverick?
Yes, thanks! 10.10 works but dosent recognize the video card. I'm beginning to think that the stock nvidia driver dosen't support my GPU. I may try to modify the X config so I can get above 800x600 resolution.

---

### Post by phantom_ on 2011-09-29
hello again,

so maverick runs on GT780DXR, however GPU driver fails.

in fact, the GPU driver that you call *stock Nvidia driver* is named Nouveau, and it is kinda generic driver.

in order to fully enable an Nvidia GPU; you have to install Nvidia proprietary driver. you can download it [here]("http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html"). please try it and give us a feedback...

---

### Post by cllgnc89 on 2011-09-29
> **phantom_ said:**
> hello again,

so maverick runs on GT780DXR, however GPU driver fails.

in fact, the GPU driver that you call *stock Nvidia driver* is named Nouveau, and it is kinda generic driver.

in order to fully enable an Nvidia GPU; you have to install Nvidia proprietary driver. you can download it [here]("http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html"). please try it and give us a feedback...
Thanks, Just to clarify when I said stock Nvidia driver I was referring to the propriety driver. In windows at least I have to use a manufacturer driver instead of the standard one from nvidia. I will give it a try though....

---

### Post by phantom_ on 2011-09-29
some notes about Nvidia driver installation;

[LIST]
[*]it is best to stop X, login to a TTY terminal (by pressing ctrl+alt+f2 etc.) and run the setup file as root.
[*]you should check for any fatal errors during the installation sequence.
[*]you should run nvidia-settings at X as root (so that it can save the configuration to */etc/X11/xorg.cfg*). this program will bring a UI to change any parameter about the video controller (GPU).
[/LIST]
in what ways have you previously tried to configure GPU so that it rejected any resolution above 800x600?

---

### Post by cllgnc89 on 2011-09-29
> **phantom_ said:**
> some notes about Nvidia driver installation;

[LIST]
[*]it is best to stop X, login to a TTY terminal (by pressing ctrl+alt+f2 etc.) and run the setup file as root.
[*]you should check for any fatal errors during the installation sequence.
[*]you should run nvidia-settings at X as root (so that it can save the configuration to */etc/X11/xorg.cfg*). this program will bring a UI to change any parameter about the video controller (GPU).
[/LIST]
in what ways have you previously tried to configure GPU so that it rejected any resolution above 800x600?
That worked. I am at full resolution now. I had been trying Administration>additional drivers.

Thanks again

---

### Post by phantom_ on 2011-09-30
a question: how does Ubuntu work on GT780DXR? any flaws, failures? any unidentified hardware?

with respect to Windows 7, what do you think about the performance of Ubuntu on GT780DXR?

---

### Post by cllgnc89 on 2011-09-30
> **phantom_ said:**
> a question: how does Ubuntu work on GT780DXR? any flaws, failures? any unidentified hardware?

with respect to Windows 7, what do you think about the performance of Ubuntu on GT780DXR?
The wifi dosen't work (centrino wireless-n 130) but I may be able to use compat-wireless and intel provided firmware. Webcam doesn't work (but thats not very important). I expected some hardware issues since the gt780dxr is an off brand. Ubuntu is more stable and much faster than windows 7. If I could get adobe cs5 and endnote on linux I would ditch windows entirely.

---

### Post by jwistead on 2011-10-16
> **cllgnc89 said:**
> Specifications:
MSI GT780DXR-099
Intel® Core™ i7-2630QM Processor
Chipset 	Intel® HM67
GPU 	NVIDIA® GeForce® GTX 570M
RAM 16 GB
Live CD: Tried ubuntu x64 11.04 and 11.10 beta 1 

After initial purple screen the boot process is haled on a screen listing detected hardware. Is this a driver issue?

[ATTACH]202515[/ATTACH]

I can confirm that I also saw this behavior with Kubuntu x64 11.10.  I also tried installing/booting the live cd from VMWare (on Windows 7), but I kept getting kernel panics right off the bat... I tried googling for these, but *nothing*.

So just out of curiosity, I tried the Kubuntu x64 11.10 *alternative* cd.  This installed without any problems at all to VMWare.  The installation on bare metal was slightly more difficult: after installing and rebooting, the system hangs with no apparent error messages, just a blank screen.  Reboot: at the same point where it hangs, I got an error message (don't remember it, because of the next step).  

I rightly figured it's the X server that's not working: reboot into safe mode, then oddly, this asks if you'd like to continue booting into regular mode.  This *worked* for me.  Upgrade the nvidia drivers using Applications --> System --> Additional Drivers (kubuntu... not sure what the equivalent is for ubuntu).  Then everything works great after that.

Point of the story: use the alternative cd's.  Not sure why it makes a difference, but it does.

---

### Post by phantom_ on 2011-10-16
jwistead,

thanks for the info. i'm sure many planning to install Oneiric to GT780DXR will benefit from that.

the thread owner may simply install Oneiric, since i remember that he had previously failed to install Natty, thus creating this thread...

by the way, any other problems with the GT780DXR+Oneiric configuration? any failing device drivers and/or applications?

---

### Post by jwistead on 2011-10-17
> **phantom_ said:**
> by the way, any other problems with the GT780DXR+Oneiric configuration? any failing device drivers and/or applications?

*Yes*.  

I realized when I got into work this morning that there are issues with sound over headphones--namely, there isn't any.  While I haven't tested this issue out in Windows, I'm betting this isn't GT780DXR-specific... I've had this happen on other laptops over several versions of Kubuntu.  It's frustrating, but something I'm sure they'll fix (and then break again) soon.

The CD/DVD/whatever drive doesn't open either (no support for the S panel that I know of).  But that's almost a "who cares" scenario I think.  The S panel "sort of" works during BIOS, so you can open the drive then, or you can boot windows and do it, or you could make an iso of the cd and stick it on USB... I'm at the point where I'd be happy without a CD drive at all.

Edit: the touchpad spazzes out from time to time as well.

---

### Post by crxyem on 2011-10-17
A work around for the cd/dvd drive. open k3b , choose devices and click eject. Pops open the cd-rom drive. I'm also going to give wine a go with the s-bar software

---

### Post by jwistead on 2011-10-18
> **jwistead said:**
> 
I realized when I got into work this morning that there are issues with sound over headphones--namely, there isn't any.  While I haven't tested this issue out in Windows, I'm betting this isn't GT780DXR-specific... I've had this happen on other laptops over several versions of Kubuntu.  It's frustrating, but something I'm sure they'll fix (and then break again) soon.


Good news, a bunch of updates were released today, alsa-utils (or alsa something) was in the list.  I just checked, headphone sound works fine now.

---

### Post by jwistead on 2011-10-18
> **crxyem said:**
> A work around for the cd/dvd drive. open k3b , choose devices and click eject. Pops open the cd-rom drive. I'm also going to give wine a go with the s-bar software

Brilliant, I can confirm that this works for me, hah hah hah :)

---

### Post by Doug-le-Guedin on 2012-01-10
Hi all!

Is there any way to succeed in installing Ubuntu 11.10 x64 on GT780DXR.
I had the same problem that the original poster had. It doesn't make any sense to me...

Thank you very much for according your time to my case!

---

