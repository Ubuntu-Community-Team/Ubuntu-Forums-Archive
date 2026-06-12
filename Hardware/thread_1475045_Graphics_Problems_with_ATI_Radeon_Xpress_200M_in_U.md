---
title: "Graphics Problems with ATI Radeon Xpress 200M in Ubuntu 10.04"
date: 2010-05-06
forum: Hardware
---

### Post by purelinuxuser on 2010-05-06
Hello!  I've been using Ubuntu on my Dell Vostro 1000 laptop since version 8.10, and I've been blown away by Lynx.  The new theme looks fantastic! The filesystem is faster than ever too. I have a problem with my graphics card though... every time I start up the computer, the entire screen is corrupted with random colored stripes flashing on the screen.  This happens when the boot up splash screen appears.

I think it has something with radeon modesetting, because when I turn that off using "radeon.modesetting=0" or "nomodeset" in the kernel boot options, the problem disappears.  However, the boot splash is in low graphics mode (Xorg itself works fine in 1280x800), compositing doesn't work, and I'm stuck with a software rasterizer for 3D.

Any suggestions?  I'm comfortable with the command line and editing config files, but I'd rather not toy around with /etc/X11/xorg.conf if it can be avoided.  I have an amd64 kernel. Thanks in advance!

Edit: I am able to work around this by restarting X (Alt+SysRq+K) until the graphics card displays properly, but this is obviously very annoying and sometimes it takes a couple reboots to get that thing to work.

---

### Post by alexpwnsn00b2 on 2010-05-06
i'm having the same problem 

[http://www.uluga.ubuntuforums.org/showthread.php?t=1471701](http://www.uluga.ubuntuforums.org/showthread.php?t=1471701)

---

### Post by purelinuxuser on 2010-05-07
My problem is like yours, but a lot more serious... you can't see anything except a bunch of random stripes.  I can't even get past the login screen without resetting X a bunch of times because the screen isn't legible at all.

Sigh... I'm having all sorts of problems with this graphics card.  This, X freezing when switching to virtual terminals, and even perspective views not working properly in some games and Blender.

---

### Post by umberstark on 2010-05-07
Try "pci=nomsi" instead of "nomodeset" as a boot option. There was an open bug about this in the run up to release, but it was patched and fixed for most (including me).

Resuming from suspend, on the other hand, is still horribly broken...

---

### Post by purelinuxuser on 2010-05-07
You  mean this bug?
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/509273](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/509273)

Yeah, I saw that one too.  I already tried "nomodeset;" that leaves me with a software rasterizer for 3D and no compositing.  Plus the boot splash is in low-graphics mode.  pci=nomsi doesn't seem to work for me :(.

I just noticed some xorg updates in Update Manager.  I'll install those and try nomodeset and pci=nomsi again.
On the bright side, suspend works well for me!:lolflag:

---

### Post by purelinuxuser on 2010-05-07
Attached is a photo to better illustrate my problem.

---

### Post by purelinuxuser on 2010-05-07
Happy to report that with the latest Xorg/kernel/OpenGL updates, the problem seems to be solved!  Virtual terminals are working fine too.  The issue tends to occur after long shut down periods however, so I'll keep this thread open for now and try again later.

Edit: Yup, issue resolved!  Thanks Ubuntu developers!
Marking this thread as [solved].

---

### Post by JHCKX on 2010-05-09
> **purelinuxuser said:**
> Happy to report that with the latest Xorg/kernel/OpenGL updates, the problem seems to be solved!  Virtual terminals are working fine too.  The issue tends to occur after long shut down periods however, so I'll keep this thread open for now and try again later.

Edit: Yup, issue resolved!  Thanks Ubuntu developers!
Marking this thread as [solved].

My Packard Bell EasyNote MZ35 laptop also has an ATI Radeon Xpress 200M video card. Suspend has never worked on this machine, graphics performance was pokey using Ubuntu 8.10, better using Ubuntu 9.04. But Ubuntu 9.10 was unstable, I had it on a test partition and it seemed to have become usable after updates in February/March but I stuck to 9.04 for daily use.

Beta 1 and 2 of Ubuntu 10.04 wouldn't boot on this computer, but from late beta 2 daily builds onward it installed fine. Some bells and whistles are missing at boot but that's no problem for me. I have noticed though that graphics perfomance is not as good as 9.04. I tried some graphics benchmarks I found on this page:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

glxgears:
9.04: 309 FPS
10.04: 484 FPS

GLBlur
9.04: FPS 36.5, load 63.5%, polys 28
10.04: fps 17.2, load 82.8%, polys: 28

GtkPerf
9.04: 11.4 seconds
10.04: 16.6 seconds

So for glxgears, 10.04 performs slightly better, but for GLBlur or GtkPerf, 9.04 shows much better performance. You can see that GLBlur is much smoother under 9.04. I suspect that 2D/3D acceleration is turned off for the Radeon driver

---

### Post by purelinuxuser on 2010-05-10
Man... the graphical glitches have returned! :(  Same symptoms as last time, but this time, I noticed a suspicious-looking message in dmesg (which, by the way, is being spammed with "atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0)."; I need a new laptop).

```
[   17.692023] [drm] radeon kernel modesetting enabled.
[   17.697903] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.697918] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.708211] [drm] radeon: Initializing kernel modesetting.
[   17.718146] [drm] register mmio base: 0xC0100000
[   17.718151] [drm] register mmio size: 65536
[   17.718459] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
**[   17.718486] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)**
[   17.718532] [drm] Generation 2 PCI interface, using max accessible memory
[   17.718535] [drm] radeon: VRAM 128M
[   17.718537] [drm] radeon: VRAM from 0x38000000 to 0x3FFFFFFF
[   17.718540] [drm] radeon: GTT 32M
[   17.718542] [drm] radeon: GTT from 0x40000000 to 0x41FFFFFF
[   17.718580] [drm] radeon: irq initialized.
```

---

### Post by maiapilo on 2010-05-11
My symptoms are focused primarily on googleearth, which does not zoom. Trying to zoom in results in a shrinking central rectangle surrounded by radial rays. I also see the rs400_gart_adjust_size error mentioned in the previous post, viz:

[   23.585633] [drm] register mmio size: 65536
[   23.585972] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   23.585995] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   23.586044] [drm] Generation 2 PCI interface, using max accessible memory
[   23.586047] [drm] radeon: VRAM 128M


Ubuntu 9.10 had no evident graphics problems. I've tried all of the suggestions listed in this forum, but none have worked. Looking forward to a fix soon. Perhaps i should just revert to 9.10 until this gets solved.

---

### Post by maiapilo on 2010-05-11
My profile showed 9.04. I'm now using 10.4

---

### Post by maiapilo on 2010-05-11
Here's a snapshot of google earth after zooming in a little.

---

### Post by jvdurme on 2010-05-11
> **maiapilo said:**
> Here's a snapshot of google earth after zooming in a little.

Wow man, that's seriously screwed up. I also had ATI issues in Lucid with the new 10.X drivers. Since the ATI crew is really good at adding new bugs while removing others, I'll wait a few more months before the new driver is stable in Lucid.
Went back to Karmic with 9.11 ATI drivers in order not to waste more time on ATI issues.

---

### Post by purelinuxuser on 2010-05-11
I have the same problem- and it's not just with Google Earth, it's with Blender and SuperTuxKart too (that I've seen anyway).  On my desktop that has an ATI X800XT, I have relatively fantastic frame rates in FlightGear (20+ in some instances), but there are disappearing polygons...

---

### Post by alliance1975 on 2010-05-12
Switched back to 9.10 as suggested by maiapilo and am now much happier. Too bad, since 10.04 is a LTS. Perhaps by the time 9.10 is obsolete I'll have a new computer that does not have an ATI video card.

---

### Post by purelinuxuser on 2010-05-12
To anyone who has the same problem I do (screen corruption on boot), I found a new fix (if your suspend works properly anyway).  Close the laptop lid so that the computer goes into suspend, then open it up to restore-.  If your cursor has disappeared, switch to a virtual terminal (Ctrl+Alt+F1) and then back to X (Ctrl+Alt+F7, Ctrl+Alt+F8, or Ctrl+Alt+F9).

---

### Post by RavanH on 2010-05-13
Having sudden and **random lock-up** issues along with **compositing suddenly switching off** from time to time on my Packard Bell EasyNote R3450 with the infamous Xpress 200M on board I noticed that line
```
[drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
``` in dmesg log.

Thinking it had to do something with shared memory size (being forced to 32Mb) I thought I should reduce it from the 128Mb I had set in BIOS (hit F2 at boot on this machine) to 32Mb. Boy, did that look scary! Completely scrambled display was the result :(

Changing shared memory to 64Mb gave me back a working screen but I have not worked long enough with that setting to be able to say if the lock-ups are still occurring... 

Also tested with editing radeon.modeset=0 at the boot command and booted with that. Seemed to work OK (compositing still but also not worked with it long enough to be able to tell if the freezes are gone.

**Anyway, to those with scrambled graphics: have you tried with different shared video memory sizes?** On my machine that problem seems to be limited to 32Mb shared memory.

---

### Post by benrb on 2010-05-13
I'm running 9.10 with no problems but get window corruption like purelinuxuser describes when trying out the 10.04 live CD. I found that this fixes my problem:

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx#Window%20corruption%20with%20older%20ATI%20graphics%20cards](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx#Window%20corruption%20with%20older%20ATI%20graphics%20cards)

---

### Post by purelinuxuser on 2010-05-13
> **RavanH said:**
> **Anyway, to those with scrambled graphics: have you tried with different shared video memory sizes?** On my machine that problem seems to be limited to 32Mb shared memory.

I wish I could!  My "BIOS" gives me almost NO control over my laptop hardware. :(

---

### Post by purelinuxuser on 2010-05-13
> **benrb said:**
> I'm running 9.10 with no problems but get window corruption like purelinuxuser describes when trying out the 10.04 live CD. I found that this fixes my problem:

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx#Window%20corruption%20with%20older%20ATI%20graphics%20cards](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx#Window%20corruption%20with%20older%20ATI%20graphics%20cards)

I don't think that applies to me... it's for older graphics cards with 32MB of VRAM or less.  My card has 128MB of VRAM.  Plus, it's not window corruption... it's the ENTIRE display!

---

### Post by purelinuxuser on 2010-05-13
I noticed a bug report on the issue we're having:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

Doesn't seem like much is happening to fix this though.

---

### Post by RavanH on 2010-05-13
> **purelinuxuser said:**
> I noticed a bug report on the issue we're having:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

Doesn't seem like much is happening to fix this though.

Well, marking it as "affects me too" won't hurt. And if many do, it's more likely to be upped to Urgent :)

And I wonder if [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/509273](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/509273) is about the same issue (looks like it to me) because that one is marked as Fix Released !

---

### Post by RavanH on 2010-05-15
Sad to say this but the nomodeset disabling KMS did not prevent my system from freezing up completely **three** times today! So either it is not enough or my problems are not related to the Radeon Xpress 200M issue :(

What is interesting is that it never showed the "Updates available" icon in the notification area while there turned out to be many updates available. And after running the Update Manager and having them installed... **no more crashes**!!

Wonder if it has something to do with the update notifications ...

---

### Post by eesofgraham on 2010-08-04
This is a "me too" for 10.04 and google earth 5.2. I get the same broken maps with radial lines and it get worse the more you zoom. I have an HP Pavilion zv6000 laptop which has the relevant graphics card configured with 128MB of dedicated and up to another 128MB of shared memory - settings for shared memory make no difference. I never saw this with earlier Ubuntu releases (but also earlier google earth versions too).

Everything else seems to work well, but I haven't tried many other graphics intensive apps yet.

---

### Post by megamanexent on 2010-08-17
I dont know if this will help you guy, but I was experiencing many compiz crashes and weird lines in Firefox ( I couldn't open more than 2 tabs without compiz crashing ) I found a bug in launchpad and one of the commenter's said that a patch was made upstream to the radeon DRM ( it was a bug with this ) in the kernel. He gave a link to a ppa for the patch, but when i went there I couldn't find the patch. So I ended up installing the 2.6.33 kernel and now I have no problems at all. Been running for 5 hours and every virtual desktop has a window open. 

If you decided to install the kernel you must get 

[linux-headers-2.6.33-020633_2.6.33-020633_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb")
[linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb") or amd64 if you run 64 bit Ubuntu
[linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb") or amd64 if you run 64 bit Ubuntu

and install in that order. You can get those debs here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/")

I'm running an ATI Radeon Xpress 200 chipset so i think this might help.

---

### Post by DV8 on 2010-08-22
I've got that card and the bug with Google Earth too.

I was thinking it was link somehow with the 3D acceleration as none of the 3D game run properly with that card.

No Nexuiz, no Tux Racer even Freedroid will not run.

So sad...

I try to install the 2.6.33 kernel, didn't fix the bug at all.

---

### Post by Gitanes on 2010-09-07
> **megamanexent said:**
> I dont know if this will help you guy, but I was experiencing many compiz crashes and weird lines in Firefox ( I couldn't open more than 2 tabs without compiz crashing ) I found a bug in launchpad and one of the commenter's said that a patch was made upstream to the radeon DRM ( it was a bug with this ) in the kernel. He gave a link to a ppa for the patch, but when i went there I couldn't find the patch. So I ended up installing the 2.6.33 kernel and now I have no problems at all. Been running for 5 hours and every virtual desktop has a window open. 

If you decided to install the kernel you must get 

[linux-headers-2.6.33-020633_2.6.33-020633_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb")
[linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb") or amd64 if you run 64 bit Ubuntu
[linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb") or amd64 if you run 64 bit Ubuntu

and install in that order. You can get those debs here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/")

I'm running an ATI Radeon Xpress 200 chipset so i think this might help.

Hey thanks for posting that.  I've got the Xpress 200 as well and updating the kernel seems to have done the trick.  I'd read an earlier posting that said ATI no longer supports this series and I started to feel pretty pessimistic about getting it fixed.  I was experiencing messed up graphics and freezes when I had alot of stuff open in Firefox.  I spent half of the day messing with getting DVDs to play (finding all that restricted stuff) and then I started to notice the problem with the graphics and spent the latter half trying to resolve that.  Actually not bad when I stop and think about it: in the past it probably would have taken me several days on each issue alone.

---

### Post by ets2006 on 2010-09-25
> **Gitanes said:**
> Hey thanks for posting that.  I've got the Xpress 200 as well and updating the kernel seems to have done the trick.  I'd read an earlier posting that said ATI no longer supports this series and I started to feel pretty pessimistic about getting it fixed.  I was experiencing messed up graphics and freezes when I had alot of stuff open in Firefox.  I spent half of the day messing with getting DVDs to play (finding all that restricted stuff) and then I started to notice the problem with the graphics and spent the latter half trying to resolve that.  Actually not bad when I stop and think about it: in the past it probably would have taken me several days on each issue alone.
Would you mind telling me which kernel version you are running? I've updated to the latest one but I'm still having issues with graphics and suspend. Thanks

---

### Post by cardanomath on 2010-09-27
I can't solve this Google Earth graphic issue both in Ubuntu and Mint and Zenwalk... I have the same problem when I try to zoom in. My video card is ATI Radeon XPRESS 200M

---

### Post by enieffak on 2010-12-26
> **cardanomath said:**
> I can't solve this Google Earth graphic issue both in Ubuntu and Mint and Zenwalk... I have the same problem when I try to zoom in. My video card is ATI Radeon XPRESS 200M


I have got the same problem with GoogleEarth with Ubuntu 10.10 (amd64) on a Dell Vostro 1000 with ATI Xpress 200M.

---

### Post by petermck on 2011-01-09
I've got the same problem. It is worse with the 'Show terrain' option unchecked in Googleearth options.
I'm using a motherboard with an on board Radeon 2100 chip, Ubuntu Maverick and the ATI open source driver.
It appears this combination may be the problem. Someone else on here told me the fglrx closed source drivers work, but these drivers do not support this chip set (and a bunch of others) on kernels past 2.6.29.
So, at least in my case, it appears to be a problem with the ATI open source drivers.

---

### Post by Belfry on 2011-01-20
One thing to try is add "nomodeset" to the kernel parameters. Edit /etc/default/grub and change the line starting GRUB_CMDLINE_LINUX_DEFAULT= from "quiet splash" to "nomodeset quiet splash"

You will get an ugly boot splash screen, but this fixes the graphics corruption problem seen in Google Earth on Radeon 200m's and x1250's using the open source driver.

---

### Post by Belfry on 2011-01-20
One thing to try is add "nomodeset" to the kernel parameters. Edit /etc/default/grub and change the line starting GRUB_CMDLINE_LINUX_DEFAULT= from "quiet splash" to "nomodeset quiet splash"

You will get an ugly boot splash screen, but this fixes the graphics corruption problem seen in Google Earth on Radeon 200m's and x1250's using the open source driver.

---

