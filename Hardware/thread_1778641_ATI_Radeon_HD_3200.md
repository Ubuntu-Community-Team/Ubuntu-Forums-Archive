---
title: "ATI Radeon HD 3200"
date: 2011-06-09
forum: Hardware
---

### Post by arathorn2nd on 2011-06-09
Hello everyone,

I've been trying to change my work environment from Windows 7 to Ubuntu 11.04 but the issues with my graphic card is proving to be a show stopper and a quite difficult task.

My laptop is a HP Pavilion TX2510us, a 12" tablet running on AMD Turion X2 and the mentioned integrated graphic chipset based on ATI'S RS780. I had my doubts, but after seeing the wacom tablet recognized and working, I thought the ride would be smooth. How mistaken I was...

After weeks trying to get ATI's binary drivers fglrx to work with it, I completely gave up. It would completely destabilize the whole system while breaking dual-monitor support, something I need to work. Countless installations, customizations and purges didn't change that.

After that decision and purging every last remnant of fglrx (I hope), I came back to the radeon drivers. The issue now was performance. I don't need 3D performance, I don't game so that's not my concern. What was hurting me was 2D performance.

Hurting like hell, even scrolling a webpage in Chromium was choppy. Not to mention video rendering, especially in secondary display, and tearing even during normal use. Flash video, even Youtube's 360p was missing frames.

Last night it seemed I had finally become the winner in this long battle: I found on some other forums (phoronix or archlinux, not sure) instructions to modify Grub so radeon's modeset is loaded during boot using KMS. It broke Ubuntu's splash screen, but got me the 2D performance I needed. As a bonus I created a Xorg.conf just to set VSYNC on and eliminated the tearing problem.

It seemed everything was working fine, smooth scrolling and video rendering. At least until I got the laptop to suspend. After waking, GNOME lost Ubuntu theme and compiz and got the default look. After a GDM restart GNOME was fixed but performance was back to very bad. This, I decided I could live with, no sleep for this machine.

And at last, today I found the show stopper. Segmentation fault at radeon, completely random in nature.
```
[  1049.527] 
Backtrace:
[  1049.527] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[  1049.527] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[  1049.527] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x11040c]
[  1049.527] 3: /usr/bin/X (_CallCallbacks+0x3e) [0x8074e1e]
[  1049.527] 4: /usr/bin/X (WriteToClient+0x267) [0x80a7617]
[  1049.527] 5: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x62) [0x6cbbf2]
[  1049.527] 6: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x75) [0x6c9fc5]
[  1049.527] 7: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x4ff000+0xce17c) [0x5cd17c]
[  1049.527] 8: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x4ff000+0xd1f12) [0x5d0f12]
[  1049.527] 9: /lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xf5) [0x170665]
[  1049.527] 10: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x4ff000+0xd1e2f) [0x5d0e2f]
[  1049.527] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[  1049.527] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1f4a]
[  1049.527] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[  1049.527] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[  1049.527] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x200e37]
[  1049.527] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  1049.528] Segmentation fault at address 0xb6fd2008
[  1049.528] 
Caught signal 11 (Segmentation fault). Server aborting
```

Now, before I give up on Ubuntu (Linux, actually) as my work environment for another year, I ask if anyone has any idea at all on how to fix this one. I thought disabling DRI, and that's how I'm running, waiting for another crash and hoping it doesn't come.

Thanks a lot for your patience if you got here,
Paulo

#EDIT: I mentioned Google Chrome when I actually meant Chromium.

---

### Post by irvingswiftj86 on 2011-06-29
I have exactly the same problem and am having to select Ubuntu Class (no effects) when I log it. It now runs lightning quick, but I want my effects back!

---

### Post by snafu006 on 2011-06-29
have you tryed this the open source drivers? [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by SenorHelmut on 2011-07-05
@Snafu 

I have the exact same tablet you have, and the video card issues have been driving me nuts for awhile now too. As you may have been discovering, Linux's support for hardware is either spot on, or not at all. If it doesn't work when you install, there is a distinct possibility it may never be fixed. I have been using linux for 2 years now, and I can tell you that hardware support for our tablet has been spotty at best, and has diminished greatly with each new version.  

The GPU worked fine in 10.10 (major Suspend issues forced me to remove that build) and it worked ok in 11.04 under Unity. However, in Unity, my GPU was running so hot with the desktop showing and nothing running, that I was leaving marks in the wood on my kitchen table. I personally found Unity to be clumsy and backwards, so I switched to Gnome3. I like Gnome3 better; its a lot like Unity, but with a lot less suck and feels almost intuitive! And Gnome3 is much faster than Unity, but with a major caveat...

In Gnome 3, the GPU doesn't work AT ALL. Proprietary Drivers (from ATI.com, xorg edgers, and the Additional Drivers app) just skewed everything, scrambled the desktop, and would eventually lock up after an hour or so. I traded suspend issues, clumsiness, and WiFi issues for a functional desktop that can't run 3D anything! There is a compatibility issue with Mutter, and I think at fault is a combination of ATI and the devs working on Gnome3/Mutter. 

Fedora 15 worked perfectly with my GPU, and had a lot of nice features. However, it has issues with the firmware used for the wireless card, and after 20 minutes of browsing the internet the WiFi card would drop out and not come back without a restart. Sure F15 worked better overall, but is much more "hands on" than Ubuntu and can take 3 times longer to configure. Support for minor issues can also be harder to find than Ubuntu.

At this point, Im not really sure where to go. I have tried every distro that runs Gnome, and I have even tried Kbuntu (same GPU issues) and OpenSuse KDE (worked 100%, but was a bit too slow). Windows 7 works 100% and has great wacom support, but its even more clumsy than Unity, slower than Gnome3 even without GPU support, and doesn't have the apps I like. At this point, I think I'm about to put this tablet on Amazon and just buy a Galaxy Tab 10. Android seems to be the only semi-linux that just works when you need it to.

---

### Post by Yellow Pasque on 2011-07-05
Do your homework when purchasing hardware. Don't listen to salespeople. Good luck.

---

### Post by SenorHelmut on 2011-07-06
> Do your homework when purchasing hardware. Don't listen to salespeople. Good luck.     This computer is 4 or 5 years old. And for the record, I just reinstalled 10.04 after my post, and it works 100%. WiFi works without cutting out, and the GPU using the FGLRX via jockey is working without screwing up my whole screen. 

Though, to be honest, I miss the feel of Gnome3. Why must I always make these sacrifices when it comes to linux? 

I know that the average user is not the target for linux. But if the devs who make these distros can't nail down the basic requirements of any OS, they mind as well keep playing with themselves. I know it's mostly ATI's fault, but the average user isn't going to care; only that Windoze worked and Linux doesn't. 

Personally, I want OSS to win, but it has to be able to connect to the internet out of the box and not screw up my screen if it wants more than a 30 minute trial out of me. First impressions can be a fickle bitch.

---

### Post by arathorn2nd on 2011-07-06
> **Temüjin said:**
> Do your homework when purchasing hardware. Don't listen to salespeople. Good luck.
We should be allowed to do whatever we want with our hardware, even running Linux on it. Sounds familiar?
Would you justify "Do your homework when choosing your Operating System and pick one that works for you hardware. Don't listen to geeks."
I've got this laptop to work on Photoshop, never intended to run ubuntu as I have a desktop for that. That changed as I changed jobs. I didn't expect to change hardware as well.

> **SenorHelmut said:**
> This computer is 4 or 5 years old. And for the record, I just reinstalled 10.04 after my post, and it works 100%. WiFi works without cutting out, and the GPU using the FGLRX via jockey is working without screwing up my whole screen. 

Though, to be honest, I miss the feel of Gnome3. Why must I always make these sacrifices when it comes to linux? 

I know that the average user is not the target for linux. But if the devs who make these distros can't nail down the basic requirements of any OS, they mind as well keep playing with themselves. I know it's mostly ATI's fault, but the average user isn't going to care; only that Windoze worked and Linux doesn't. 

Personally, I want OSS to win, but it has to be able to connect to the internet out of the box and not screw up my screen if it wants more than a 30 minute trial out of me. First impressions can be a fickle bitch.
If Linux/GNU is to be more than a quirky/geeky/arcane OS, getting hardware support onboard the train is more than necessary, it's essential. That's what made Microsoft and that's what breaks Linux/GNU.
Currently I'm running ubuntu virtualized inside windows. It's enough for my needs, but slow as hell even without a GUI.
It's a shame we have to go trough this. How can we defend an OS running like this?

---

### Post by dandnsmith on 2011-07-06
The comments in this thread are interesting, and mostly valid.
However, I think you'll find that the MSoft approach isn't too far away, as they don't support old hardware, and the new versions are designed for current hardware - so, for 5 year old hardware you could be looking at XP, not W7 (which the equivalent to trying to use Ubuntu 11).

---

### Post by arathorn2nd on 2011-07-06
> **dandnsmith said:**
> The comments in this thread are interesting, and mostly valid.
However, I think you'll find that the MSoft approach isn't too far away, as they don't support old hardware, and the new versions are designed for current hardware - so, for 5 year old hardware you could be looking at XP, not W7 (which the equivalent to trying to use Ubuntu 11).
I don't quite understand what you are saying. This 3 year old hardware (in my case) works fine running Windows, from XP Tablet Edition to 7. But it does not work completely in any version of Ubuntu I tried, from 11.04 to 10.04.
The latest is where it runs best for me, only video suffers and let's be honest, that's not even a Linux issue, but AMD/ATI's. I just expected the alternative to binary driver to really be an alternative, but issues arise from it's use.
Older ubuntu releases present issues with webcam, wacom tablet, ethernet, alsa and many other things.

> **Ok, finally got it.** Removed Natty and installed Lucid instead. The versions of Xorg and FGLRX are behaving nicely. Hopefully I'll be able to lock these versions before updating to the next LTS release.

---

