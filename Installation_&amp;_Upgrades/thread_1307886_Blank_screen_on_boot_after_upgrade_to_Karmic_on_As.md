---
title: "Blank screen on boot after upgrade to Karmic on Aspire 5738z"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by CalderCoalson on 2009-10-31
I tried installing Karmic onto a fresh partition of my hard drive the day it came out, and have had nothing but a huge head-ache ever since.  I've tried everything I and Google can think of, and none of it has worked, so I'm hoping someone here can help me out.

Here's the problem.  First, the Live CD would not start.  After selecting "Try Ubuntu without changes to your computer" it proceeded to a black screen instead of the boot screen, and eventually made the startup noise but the screen never worked.  After some Googling, I tried starting it with 'i915.modeset=0' and it worked!  I installed Ubuntu to the fresh partition with ext4, and restarted with hope that my new system might work.

It didn't, but then I remembered the i915 workaround, and added 'i915.modeset=0' to the list of boot options.  Here's the weird part: it seemed to start up, got to the login screen and... was unresponsive.  It was like the keyboard and mouse were completely disconnected from the computer.  This really confused me because the Live CD didn't have that glitch at all, and this was a fresh installation so it should behave much like it.

Anyway, I tried booting to recovery mode, which the keyboard did work in, and using 'X -probeonly' got some rather cryptic errors, which I would greatly appreciate some help in interpreting.

---

### Post by CalderCoalson on 2009-10-31
I don't mean to be impatient, but I know it's really easy for things to get lost once they fall of the front page, so... bump?

---

### Post by jessiebrownjr on 2009-10-31
You booted into live saw that it didnt work and installed anyway? RISKY BIDNESS

---

### Post by CalderCoalson on 2009-10-31
Well, it seemed to work perfectly once I added 'i915.modeset=0' to the boot options.  And as I said, this was thankfully just a blank partition of my HD, so I've still got Jaunty running on my main partition.

---

### Post by XTREME DEMENTOR on 2009-10-31
"Well, it seemed to work perfectly once I added 'i915.modeset=0' to the boot options."

Could someone please give an explanation / instruction for the above comment to a noob.

I also have the 5738z and 9.04 works great but i also get the blank screen on 9.10.

Thanks in advance for any help.

---

### Post by CalderCoalson on 2009-10-31
Ah, well, I meant the Live CD worked perfectly, so don't rush into updating and brake your system before this gets fixed...

You can add boot options in two ways.  The first is to do it permanently by editing you /boot/grub/menu.lst file, (which I highly recommend backing up before editing), and the second is to do it through grub at boot-time.  When you're at the grub boot menu, you can press 'e' to edit the boot-options of whatever you have selected, and you would scroll down to the 'kernel    ' line and add 'i915.modeset=0' to the end of it.  On the Live CD, I think this is accomplished by pressing F6 ad appending it to the end of those options.

---

### Post by CalderCoalson on 2009-10-31
Bump?

---

### Post by CalderCoalson on 2009-11-01
Bump again?

---

### Post by ajaypulipra on 2009-11-01
Hi,
iam having the same issue. Can you help me on this? Can you plz explain the steps one by one ? I am not aware, how to set i915modeset=0 as iam a new bie. Plz help. It's urgent


> **CalderCoalson said:**
> Ah, well, I meant the Live CD worked perfectly, so don't rush into updating and brake your system before this gets fixed...

You can add boot options in two ways.  The first is to do it permanently by editing you /boot/grub/menu.lst file, (which I highly recommend backing up before editing), and the second is to do it through grub at boot-time.  When you're at the grub boot menu, you can press 'e' to edit the boot-options of whatever you have selected, and you would scroll down to the 'kernel    ' line and add 'i915.modeset=0' to the end of it.  On the Live CD, I think this is accomplished by pressing F6 ad appending it to the end of those options.

---

### Post by CalderCoalson on 2009-11-01
I repeat: **THIS ONLY ALLOWS YOU TO BOOT THE LIVE CD, THE INSTALLED OS IS STILL JUNK.**

That said, here's how you get the Live CD working:
[LIST=1]
[*]Boot from the Live CD
[*]Select a language
[*]Press F6
[*]Press ESC
[*]type 'i915.modeset=0'
[*]Press Return
[/LIST]

---

### Post by CalderCoalson on 2009-11-01
On a wim, I tried comparing the two /etc/var/Xorg.0.log files for the Live CD boot and the Hard Drive boot, and it yielded some interesting results.  The first significant deviation is on line 106 where the CD boot read:
```

(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)

```
and the Hard Drive boot read:
```

(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel

```

I am no closer to knowing how to fix this, but I think I kind of understand what's happening.  HAL tries to start, needs ACPI, which for some reason works from the Live CD but not the installed version.  If anyone could explain/fix this bug, we would all be eternally in your debt. :D

---

### Post by CalderCoalson on 2009-11-01
Hopeful bump?

---

### Post by CalderCoalson on 2009-11-01
Ok, bad news.  After running '/etc/init.d/acpid start', the ACPI warning goes away but the exact same thing happens.  This is REALLY weird, because now the log files from the CD and the harddrive boot are the exact same up to the point where the latter just gives up.
The CD log looks good:
```

(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x00000120 to 0x20000120
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x40012400 to 0xc0020800

```
But the harddrive boot appears to die for no apparent reason whatsoever:
```

(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x40010000 to 0xc0020000
 ddxSigGiveUp: Closing log

```

Any help whatsoever will be greatly appreciated...

---

### Post by jwang on 2009-11-01
Was "single" in your grub Kernel command line when logging normally(i.e. not in recovery mode)? If yes, probably you'll need to remove it first;

---

### Post by CalderCoalson on 2009-11-01
No, that's just for recovery mode.

---

### Post by usater on 2009-11-01
guys 

i've got the same problem.

a black screen. in recovery mode also. is this is a bug with X? or driver problem?

let me check this kenel parameter.

---

### Post by Larry Linux on 2009-11-02
In my opinion, 9.10 isn't yet ready to be considered a final release.

Many people have brought up the problem of 9.10 Live CD hanging just after boot - for example, once the CD boots up, it asks whether you want "to install"..or "use Ubuntu live". Unfortunately, no matter which option is chosen, the screen goes black with a white hash mark in the upper left corner of the screen once you choose which option you want.

I've tried numerous burns, six to be exact - at all 4x speed. I've even downloaded three separate ISO's, including two Ubuntu 9.10 and one Kubuntu 9.10. All have the exact same problem on computers with ATI graphics and Intel processors. On computers without ATI using AMD processors, this problem doesn't exist, and the CD works. Obviously, there is some type of driver recognition problem, or a problem with the kernel itself when using ATI/Intel.

I've never had this problem before with previous Ubuntu releases. In fact, previous Ubuntu releases worked as reliably as any os I've ever used. Hopefully someone at Ubuntu will read this and figure out what the problem is and get it resolved.

---

### Post by CalderCoalson on 2009-11-20
This was two weeks ago, and still no progress.

On a whim, I tried install Kubuntu 9.10, and with the same 'i915.modeset=0' it works!  So the keyboard and mouse hanging are a glitch with GDM then?  I'm not sure what to conclude from this, but I hope it helps someone help us out here.

This is especially annoying because the support for the GMA4500 is nonexistent in 9.04, and so it can't run Ogre and thus the game I'm working on.  Honestly, I really love Ubuntu, but many users take the papercuts seriously and then it won't matter how many cores your kernel can support.  (xkcd reference: [http://xkcd.com/619/](http://xkcd.com/619/))

---

### Post by CalderCoalson on 2009-11-22
[IMG]http://www.roflcat.com/images/cats/halp.jpg[/IMG] plz?

Thanks! :D

---

### Post by IBadget on 2009-12-04
I've also had the same problem. The way I resolved it was to add acpi=off to my boot options. When Ubuntu 9.10 failed to boot, I did a hard shutdown and turned the computer back on. I then got the boot menu, pressed e on the relevant kernel, and added acpi=off to the end of the boot line, after "quiet splash".

---

### Post by CalderCoalson on 2009-12-04
Cool, I'll try that right now.  Thanks!

**EDIT:** It works!  With 'i915.modeset=0 acpi=off' added to my boot commands, I finally have a functional Karmic installation!  Thank you so so so much!

---

### Post by bartvdm75 on 2009-12-05
hey, i also have a 5738Z with the same problem..

does it really works now ?? is this the solution ??

i still have the 9.04 ..

---

### Post by CalderCoalson on 2009-12-05
Yep, I'm actually posting this from the Karmic partition on my HD.  Everything is working great except for the graphics.  GLXGears still gets around 500FPS, and I can't run any 3D anything, including the game I'm developing using Ogre.  In fact, instead of just having a low framerate, everything I try to run using Ogre just displays a black screen!

Is it just me, or were the Intel graphics drivers supposed to be fixed in this release?  I'm going to look into downgrading my drivers to 2.4, on the hearsay evidence that that helps.  Honestly, this is a rather poor effort on the Ubuntu team's part if it does.

---

### Post by Basenji on 2009-12-24
This problem persists at me or maybe I haven't understood the solution.
I've got ASUS K50IJ, Intel DUO and Intel 4500M GC. I tried to instal Ubuntu 9.10 but after pressing 'Install Ubuntu' black screen appeared and I had to hard shut down.
So I added the 'i915.modeset=0 acpi=off' to the boot command and the instalation finally worked. But after the instalation reboot there was the black screen again. 
The problem is that the computer doesn't react on the Live CD in DVD mechanic as it normally did when the OS wasn't installed.
Could anyone help?

---

### Post by CalderCoalson on 2009-12-25
You'll have to edit the Grub boot options.  This can be done (I think) by pressing selecting the boot menu option and pressing 'e', then appending options to after '... splash quiet'.

---

### Post by Basenji on 2009-12-25
Even after pressing "e" the screen goes black and even if it loads new LiveCD/USB with other distribution, the screen is black althought the CD might be loaded.
There's a problem that I have only Ubuntu on the PC and now there's no way to get it uninstalled...

---

### Post by CalderCoalson on 2009-12-25
Sorry, you have it installed properly, no?  If so, you should be booting off the hard drive, not a LiveCD.

---

### Post by Basenji on 2009-12-25
Well I installed it only thanks to adding 'i915.modeset=0 acpi=off' to the boot command line before the instalation. But it obviously wasn't installed properly because after I turn the PC on (I remind that it wrote the installation was complete), there's the same black screen which appeared instead of installation guide when I didn't put the 'i915.modeset=0 acpi=off'.
So I tried to uninstall it or to install another distribution but after turning it on, the screen writes GRUB then I press "e" and then the screen goes black...
Well, is there some way I could uninstall the OS so I could install other? Because now I can do absolutelly nothing... Thanks

---

### Post by CalderCoalson on 2009-12-25
What is your Grub timeout set to?  Because 'e' should just bring it to the boot option editor within Grub, not actually boot anything.  If you can't do that then either Grub is automatically booting before you can edit the config options, or this is a Grub problem, (which I highly doubt).

If you really want to install another OS, you don't have to uninstall Ubuntu first, just reformat the disk and everything will be erased.

---

### Post by Basenji on 2009-12-26
Well the "e" may work but there's still the problem with the black screen...
I can't install any other OS because even if it loads the CD/USB, the screen goes black

---

### Post by CalderCoalson on 2009-12-26
One second, now I really don't understand.  You're saying regardless of what OS you put in the CD drive, when you boot from it you are met with a black screen?  That doesn't make any sense.

Now, before pressing 'e', just verify that you get to the Grub boot menu.  You can't press 'e' until you've selected the option you want to boot/edit.

---

### Post by nomnex on 2009-12-26
CalderCoalson: How do you set acpi=off for the session during boot time on Karmic (grub2)? Pushing "e" on the splash screen has no effect.

---

### Post by CalderCoalson on 2009-12-26
**To configure Grub 2 boot options, you must first get to the Grub menu.  This may require changing the timeout so the first OS doesn't automatically load.  Only when you are in the Grub menu may you select the option you wish to boot and press 'e' to change the boot options.**

---

### Post by nomnex on 2009-12-26
> **CalderCoalson said:**
> To configure Grub 2 boot options, you must first get to the Grub menu.  This may require changing the timeout so the first OS doesn't automatically load.

Single OS Ubuntu Karmic here. There is not boot menu available on a single OS Ubuntu. Can I configure acpi=off **during the splash screen** or do I need to edit the boot config. file right away.

Edit: "Shift+Esc" opens the Grub menu. I am fine now.

---

### Post by Trixstar91 on 2009-12-27
hey im having this problem..
i just considered maybe installing an earlier version and then upgrading? anyone tried it?

---

### Post by Basenji on 2010-01-09
This solution ( [http://ubuntuforums.org/showthread.php?p=8190708#post8190708](http://ubuntuforums.org/showthread.php?p=8190708#post8190708) ) fixed my problem.

---

