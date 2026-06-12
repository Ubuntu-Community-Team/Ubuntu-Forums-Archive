---
title: "Ubuntu 9.10 LiveCD hangs during Gnome startup"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Spc on 2009-10-29
Today I tried installing 9.10rc on a rather old PC (but still having 512MB RAM), but the LiveCD won't boot normally.

It seems that everything goes fine, X starts up, xsplash works normally, a blank screen with mouse pointer on it appears, it works for some time (i.e. it loads something from the CD and I am able to move the pointer), but then everything stops responding and nothing happens. If I boot the CD in install mode, I can see the wallpaper, but then everything still hangs.

I tried adding noapic nolapic but to no avail.

I didn't have much time today, but when I was about to go I've noticed that the computer didn't have a FDD, but it was enabled in BIOS. I disabled it and tried booting Ubuntu one more time and this time I even got Gnome panels, but the clock etc. didn't appear and everything stopped responding again.

Any ideas?

For now, I'm going to burn an alternate CD and try installing Ubuntu using it tomorrow.

---

### Post by Spc on 2009-10-29
bump

---

### Post by jheaton5 on 2009-10-29
Did you verify the checksums?  You may have a bad download or a bad burn.

---

### Post by Robertjm on 2009-10-29
Just out of curiosity why did you install the RC less than 24 hours before the actual Release version was released? 

I realize it takes a long time to download on Release Day, but you might want to try that.

For myself I was going to install the RC last week, but decided to wait till today and try the formal Release, hoping all the ATI issues might be ironed out (hope springs eternal :D  )

As for your problem, I encountered a similar issue a couple of releases ago. Finally, I downloaded the .iso again and burned it at a slower burn speed, which seemed to resolve the issue. Might want to try that if you still want to use the RC.

Good luck!!

Robert

---

### Post by seatex on 2009-10-29
Well I also get a screen freeze shortly after the Gnome desktop comes up on the LiveCD.  I got it with the RC and the final, and after burning 3 disks at slowest speed with both versions.

I was trying to install the 64 bit version on a Foxconn 45CSX Atom 330 with Intel 945GC chipset and Intel GMA 950 video.  Both Ubuntu 9.04 64 bit and Linux Mint 7 64 bit run on this system without problems.

I'm really disappointed with this.

---

### Post by Spc on 2009-10-29
> **Robertjm said:**
> Just out of curiosity why did you install the RC less than 24 hours before the actual Release version was released?
That's simple: this computer is not mine, I was just asked to install Ubuntu on it, and it was much more convenient for me to do it today than to wait for tomorrow.

> **Robertjm said:**
> I realize it takes a long time to download on Release Day, but you might want to try that.
Well, using torrents it's, in fact, very fast.

> **Robertjm said:**
> As for your problem, I encountered a similar issue a couple of releases ago. Finally, I downloaded the .iso again and burned it at a slower burn speed, which seemed to resolve the issue. Might want to try that if you still want to use the RC.
Thanks, I will try it, it really might be the case, because the computer has a VERY old CD-ROM.

---

### Post by bj0 on 2009-10-29
I'm getting this hang on an Asus s5200N, with the Release CD.  I also tried booting off a thumbdrive with the .iso and grub2,  both get to the point where the desktop loads, and then the whole thing just freezes (except the mouse).  I can move the mouse, but nothing else responds, no keyboard shortcuts (ctrl-alt-backspace, ctrl-alt-f#, etc).

noapic and nolapic didn't help.

---

### Post by snowpine on 2009-10-30
> **seatex said:**
> Well I also get a screen freeze shortly after the Gnome desktop comes up on the LiveCD.  I got it with the RC and the final, and after burning 3 disks at slowest speed with both versions.

I was trying to install the 64 bit version on a Foxconn 45CSX Atom 330 with Intel 945GC chipset and Intel GMA 950 video.  Both Ubuntu 9.04 64 bit and Linux Mint 7 64 bit run on this system without problems.

I'm really disappointed with this.

Same problem on my Foxconn Atom 330 barebones. Does disabling Compiz effects solve the problem for you too?

---

### Post by bj0 on 2009-10-30
Doesn't the LiveCD start up with metacity running anyway?  I tried a quick 'metacity --replace' when it booted up, but it still froze about 10s later.

It's hard to determine what is causing it to freeze, because the desktop is usable for 5-15 seconds, and after it freezes, it's completely non-responsive, so I can't check any logs.

---

### Post by snowpine on 2009-10-30
> **bj0 said:**
> Doesn't the LiveCD start up with metacity running anyway?  I tried a quick 'metacity --replace' when it booted up, but it still froze about 10s later.

It's hard to determine what is causing it to freeze, because the desktop is usable for 5-15 seconds, and after it freezes, it's completely non-responsive, so I can't check any logs.

I agree; it is frustrating, which is why I'm sticking with 9.04 for a while. I'm downloading the final release (was using release candidate before) to double check whether it's been fixed.

All I can say is, it's not an Ubuntu-specific problem... exact same thing happens with Arch, so I think it's an upstream problem with X or the Intel driver. :(

---

### Post by bj0 on 2009-10-30
It looks like this is an X problem.  I was able to switch to a tty when it booted up, and it didn't freeze until I switched back (ctrl-alt-f7).

While in the tty I insalled ssh and connected from my desktop, and after the computer froze I could still use the ssh session.  I didn't see anything in any of the logs I Checked (messages, syslog, Xorg.0.log).

If anyone can think of anything to try while it is frozen let me know...

---

### Post by Fizzdan on 2009-10-31
I'd like to chime in here.

I too am having freezes around X login. Mine however freezes completely, including any ssh session. It initially occurred a week ago or so when I apt-get upgrade'd my RC release system. So I downloaded the release ISO today and reinstalled a clean system, but it hung first boot.

So it seems for me at lease that some package(s) updated between RC and release is causing my hangups 

9.04 worked fine on the same system.

Even though my symptoms appear at different versions releases, I suspect they may be the same issue.

---

### Post by hellibombelli on 2009-10-31
Have you tried the parameter "nomodeset"? IMHO the new Intel driver don't work flawlessly with kernel mode setting.

hth,
hellibombelli

---

### Post by bj0 on 2009-10-31
i tried nomodeset, no change.

I was able to get a stack trace of Xorg after it froze.  I did this twice, the first time was:

```

#0  0x0058b422 in __kernel_vsyscall ()
#1  0x001dc629 in ioctl () from /lib/tls/i686/cmov/libc.so.6
#2  0x0033f722 in ?? () from /usr/lib/libdrm_intel.so.1
#3  0x0033b4d9 in drm_intel_bo_map () from /usr/lib/libdrm_intel.so.1
#4  0x00ce3a62 in intel_next_batch (pScrn=<value optimized out>)
    at ../../src/i830_batchbuffer.c:115
#5  0x00ce3b94 in intel_batch_flush (pScrn=0x84cada0, flushed=0)
    at ../../src/i830_batchbuffer.c:216
#6  0x00d1016a in i830_uxa_prepare_access (pixmap=0x862c688, access=UXA_ACCESS_RW)
    at ../../src/i830_uxa.c:482
#7  0x00d254c4 in uxa_prepare_access (pDrawable=0x862c688, access=UXA_ACCESS_RW)
    at ../../uxa/uxa.c:155
#8  0x00d275f3 in uxa_copy_n_to_n (pSrcDrawable=0x8437710, pDstDrawable=0x862c688, 
    pGC=0x85d6f98, pbox=0xbff45ff4, nbox=1, dx=1240, dy=0, reverse=0, upsidedown=0, 
    bitplane=0, closure=0x0) at ../../uxa/uxa-accel.c:482
#9  0x006fd76b in fbCopyRegion (pSrcDrawable=0x8437710, pDstDrawable=0x862c688, 
    pGC=0x85d6f98, pDstRegion=0xbff45ff4, dx=1240, dy=0, 
    copyProc=0xd272b0 <uxa_copy_n_to_n>, bitPlane=0, closure=0x0)
    at ../../fb/fbcopy.c:396

```


and the second time:

```

#0  0x00229422 in __kernel_vsyscall ()
#1  0x002ee629 in ioctl () from /lib/tls/i686/cmov/libc.so.6
#2  0x003fadba in drm_intel_gem_bo_map_gtt () from /usr/lib/libdrm_intel.so.1
#3  0x003b11ac in i830_uxa_prepare_access (pixmap=0x86f4f08, access=UXA_ACCESS_RW)
    at ../../src/i830_uxa.c:498
#4  0x003c64c4 in uxa_prepare_access (pDrawable=0x86f4f08, access=UXA_ACCESS_RW)
    at ../../uxa/uxa.c:155
#5  0x003c727e in uxa_do_shm_put_image (pDrawable=0x86f4f08, pGC=0x874ba70, depth=32, 
    x=0, y=0, w=8, h=24, leftPad=0, format=2, 
    bits=0x876e0f4 "\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377"...) at ../../uxa/uxa-accel.c:243
#6  uxa_put_image (pDrawable=0x86f4f08, pGC=0x874ba70, depth=32, x=0, y=0, w=8, h=24, 
    leftPad=0, format=2, 
    bits=0x876e0f4 "\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377"...) at ../../uxa/uxa-accel.c:291
#7  0x081817b0 in damagePutImage (pDrawable=0x86f4f08, pGC=0x874ba70, depth=32, x=0, 
    y=0, w=8, h=24, leftPad=0, format=2, 
    pImage=0x876e0f4 "\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\323\334\345\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\322\333\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377\321\332\344\377"...) at ../../../miext/damage/damage.c:905

```

So it definitely looks like the intel driver is hanging.

---

### Post by Fizzdan on 2009-11-02
It must be something more than the Intel driver as it is affecting me with the nvidia and nv xorg driver.

---

### Post by seatex on 2009-11-03
> **snowpine said:**
> Same problem on my Foxconn Atom 330 barebones. Does disabling Compiz effects solve the problem for you too?

Yes, disabling Compiz stopped the lockups.  But the system seems sluggish compared to 9.04.

---

### Post by Fizzdan on 2009-11-05
I didn't find any compiz packages installed on my fresh 9.10 release.

---

### Post by alfjohn on 2009-11-05
I'v got the same problem on a Lenova. Tried upgrading it instead of using the live cd but it would boot then freeze up within seconds after loading the desktop.
When I tried to install the live cd would also do the same. Then it wouldn't even load the desktop.

---

### Post by apirec on 2009-11-05
> **seatex said:**
> Yes, disabling Compiz stopped the lockups.  But the system seems sluggish compared to 9.04.
I experienced EXACTLY the same but I have a Radeon Mobility 9000...

---

### Post by russ5811 on 2009-11-05
Same problem with an HP 1116nr Netbook. Anyone found a fix yet?

---

### Post by Fizzdan on 2009-11-09
I reported this as a bug [https://bugs.launchpad.net/bugs/466189](https://bugs.launchpad.net/bugs/466189), but there is no response yet, it probably needs more information and more people confirming it as an issue.

---

### Post by eris23 on 2009-11-09
Booting from karmic release media for amd64 gnome desktop comes up but gnome-panel doesn't.  Cursor in "waiting" state.  I can switch to text console and back.  Last pre-release media worked fine.

---

### Post by KhaledEz on 2009-11-09
I have this problem too,

I tried to enter to the system using recovery mode, and updated the system, but when I enter using netRoot profile it hangs as before. but when I chose the first choice in the recovery mode (clean boot I think), it opens a shell and I login using my name, then startx and every thing is fine but without sounds. This is after I installed ubuntu.

When I burned the image and entered to livecd it hangs just like after installing, I installed it using install option in the live cd.

So what we have to look to is what packages that runs in the normal mode, but not in the recovery mode.

---

### Post by delcypher on 2009-11-09
Just to confirm I had this problem too. LiveCD "Try Ubuntu First" froze once the gnome-desktop loaded.

Normal install didn't freeze though.

---

### Post by itbcn8 on 2009-11-09
I am having the same exact problem! LiveCD does not work (when you want to try without install). I burned 3 different downloaded iso's to 3 different CD's (once on windows, once on mac, once on ubuntu), and neither one worked. It freezes. SO frustrating. 

I hope they fix this before the media gets wind of it :P

:-({|=

---

### Post by budiyanto on 2009-11-15
I fixed mine, intel 945G, i suppose it wouldn't hurt to try it on yours with other display chips if it has the same lockout:
1. If your LiveCD boot freezes just after the X desktop shows up, keyboard and mouse lockup,>> install your Ubuntu Karmic without booting it up to X, just click on Install Ubuntu.

2. If your Karmic still freezes on your first install boot up, boot up again, this time choose Recovery Mode. then try edit your /boot/grub/grub.cfg, put something like this at the end of the kernel: nolapic nomodeset  
example:
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d6ac1cd6-d102-4002-965a-909a7f61bc54 ro   quiet splash nolapic nomodeset

try booting up again, if like mine, you should be able to boot up.

3. If your karmic successfully boots up, and you cannot turn on your Compiz, try it first by runnig command : compiz --replace --indirect-rendering

4. If your Compiz is OK by running command above, then put it in your Start Applications. I hope it solves yours as it solved mine

---

### Post by v_r on 2009-11-16
Pretty sure I've been getting the same problem; haven't been able to get past the new ubuntu loading screen from the "Try Ubuntu without any change to your computer". I also had the issue where just selecting "Install Ubuntu" gets as far as displaying the wallpaper, and then hangs (for me, no cursor, no menus, no nothing).

What did work for me though was to just try switching to Safe Mode before actually starting the live version of ubuntu, or kicking off the install. I'm just installing now, but so far so good.

Just for the record, I'm using a Sun Ultra 24, as standard (except for a RAM upgrade to 4gb).

---

### Post by cpisbell on 2009-11-17
> **bj0 said:**
> Doesn't the LiveCD start up with metacity running anyway?  I tried a quick 'metacity --replace' when it booted up, but it still froze about 10s later.

It's hard to determine what is causing it to freeze, because the desktop is usable for 5-15 seconds, and after it freezes, it's completely non-responsive, so I can't check any logs.

I am getting exactly the same problem with the released 9.10 live CDs - both 32-bit and 64-bit - and after an upgrade from 9.04 on an HP g3000 system that has been successfully running 9.04 and earlier versions for some time.

Disabling the internal sound card in the BIOS seems to improve things.

I spoke too soon. The system still locks up - it just takes a while longer.

---

### Post by Krzycho on 2010-01-02
> **Spc said:**
> It seems that everything goes fine, X starts up, xsplash works normally, a blank screen with mouse pointer on it appears, it works for some time (i.e. it loads something from the CD and I am able to move the pointer), but then everything stops responding and nothing happens.I have the same problem. Even mouse freezes. I tried 8.10, 9.04 and 9.10...

---

### Post by Sc10 on 2010-01-07
> **eris23 said:**
> Booting from karmic release media for amd64 gnome desktop comes up but gnome-panel doesn't.  Cursor in "waiting" state.  I can switch to text console and back.  Last pre-release media worked fine.

Can you tell us if you got the Live-CD to work afterward?

If not, does the 'Install' method work without much difficulties?

---

### Post by bj0 on 2010-02-13
Is there already a bug report for this?  

I've tried Ubuntu 9.10  and Xubuntu 9.10 Live CDs, they both freeze right after the desktop appears.

I just tonight tried the Xubuntu 10.04 test LiveCD and it still freezes as soon as the desktop appears.  

This is a serious bug as it makes all of the *buntus after 9.04 unusable on my laptop.  I haven't tried another distro, so it might not be buntu specific, but it should still be looked at.  If someone has created a bug report I'll be happy to run tests and gather any info I can.

---

### Post by Kaiyusn on 2010-04-19
Dears, I got one bios for this issue. pls see my attached file.

---

