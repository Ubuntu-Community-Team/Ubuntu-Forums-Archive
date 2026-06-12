---
title: "Random freezes. Memory problem?"
date: 2013-02-17
forum: Hardware
---

### Post by kuckunniwi on 2013-02-17
Hi everyone! I'm having some problems with an **Asus EeePc 1001PXD**, running **Mint 13 XFCE 64-bit**. I'm posting here because I've received no feedback whatsoever on mintforums, and afer all, Mint *is* an Ubuntu offspring. Plus, I suspect a hardware problem. For a few weeks now, my desktop **randomy freezes** (and it's getting pretty constant, max. 20 minutes into a session): mouse freezes, window manager doesn't work, keyboard shortcuts neither, leaving me only hard-shutdown as an option.  After forcing shutdown, it often boots into a black screen, not even a BIOS splashscreen. Or a green screen. Or reboots itself before my distro has loaded.

I've read tons of posts regarding similar problems (some on XFCE, some on cinammon), and have tried the following:

- Fixing broken packages 

```
sudo apt-get install -f
```

and 

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Updating kernel to 3.4.4 ([http://www.upubuntu.com/2012/06/how-to-install-linux-kernel-344-in.html]("http://www.upubuntu.com/2012/06/how-to-install-linux-kernel-344-in.html"))

- Updating to newer version of BIOS, as Eeepc's are known to have battery-related issues linked to BIOS (see Asus black screen of death for more info)

And then, after booting up post-freeze and post-force-shutdown, I got this:

[IMG]http://img818.imageshack.us/img818/372/dsc0003v01.jpg[/IMG]

I'm running a memory test to check if it's a memory problem, and so far, it's frozen 4 times before reaching 25% of the test. Is this definitely a physical memory problem? Thanks! (and sorry for the absolute newbie questions)

---

### Post by The Cog on 2013-02-17
I think it is very probably a hardware problem, could be CPU, memory, heat, motherboard or whatever. The reason I think it is hardware is that the memory test is quite simple - if there were a memory test software issue it would have been spotted and fixed by now, and the memory test doesn't need any fancy hardware driver software that can't always be trusted.

---

### Post by sudodus on 2013-02-17
Maybe you got no answer, because it is difficult to understand what is wrong. I do not pretend to understand it either, but maybe I can help you try some new ideas and tests.

- When you are running memtest, has it found any error or is it just freezing?
- Test your hardware booting from an external drive, either the linux mint install CD/USB drive or some other boot drive!
- Test your hardware running in text mode (no graphics screen) to see it freezes. Do things (run some text based tasks).
- Have you tried setting some boot options?

- How did you force shutdown? Hard reboot (pressing the power button or unplugging the power) might cause damage to the file system, so that you need to repair it. Boot from an external drive, unmount all partitions on your internal drive and run
```
sudo e2fsck -f /dev/sdxy
``` on your system root partition (that mounts on /). x is the drive letter and y is the partition number, it might be /dev/sda1 or /dev/sda6.
--
In the future try soft reset with the special sequence for linux.

While pressing

***alt + SysRq***

all the time, press each of the following keys one second each

***r e i s u b***

This method works many times, when the linux system seems quite locked (unresponsive) and will give the system a chance to finish writing buffers to the disk before reboot, and eliminates several problems.

---

### Post by sudodus on 2013-02-17
> **The Cog said:**
> I think it is very probably a hardware problem, could be CPU, memory, heat, motherboard or whatever. The reason I think it is hardware is that the memory test is quite simple - if there were a memory test software issue it would have been spotted and fixed by now, and the memory test doesn't need any fancy hardware driver software that can't always be trusted.
+1

Yes, if the system freezes also when booted from an external drive, then it will make us more convinced it is the hardware.

---

### Post by sulekhadahiya on 2013-02-17
Looks like it is RAM problem. I seen many messages like that on my desktop and then one day I changed the RAM. I changed my hard drive but later found out it is because of bad RAM. After new DDR3 RAM never saw those errors again in my Desktop.

You should run memory check.

Do you use Google chrome or chromium browser. Have you noticed the crashed pages in those two browsers while surfing.
> You may see the "Aw, Snap!" message if a webpage crashes unexpectedly.
If you noticed this then it is definitely RAM problem. 

One of my friend also facing similar problem. His windows shows blue screen error and Ubuntu show kernel panic occurred. He checked the RAM using windows and found problem in 1 RAM DIMM.
[URL="https://help.ubuntu.com/community/MemoryTest"]In Ubuntu see this link: https://help.ubuntu.com/community/MemoryTest
[/URL]

---

### Post by kuckunniwi on 2013-02-17
Thanks for the quick replies, guys! I see your point...I didn't exactly provide much diagnostically helpful info. So thanks for the tips! Here it goes:

> **sudodus said:**
> 
When you are running memtest, has it found any error or is it just freezing? 

No, it doesn't find any errors. It simple freezes. Every time (haven't been able to successfully complete a memtest so far)

> **sudodus said:**
> 
Test your hardware booting from an external drive, either the linux mint install CD/USB drive or some other boot drive!
Test your hardware running in text mode (no graphics screen) to see it freezes. Do things (run some text based tasks). 

Have had trouble in several occasions booting into recovery mode. System hang half-way through. 

Managed to boot Xubuntu 12.10 from USB. Worked fine for about 1/2h, then froze (black screen). I didn't manage to shutdown via SysRq, as I'm not sure which key that would be on my system.


> **sudodus said:**
> 
Have you tried setting some boot options? 
 
No, I haven't. What would you recommend me to try?

> **sudodus said:**
> 
 How did you force shutdown? Hard reboot (pressing the power button or unplugging the power) might cause damage to the file system, so that you need to repair it. Boot from an external drive, unmount all partitions on your internal drive and run
```
sudo e2fsck -f /dev/sdxy
``` on your system root partition (that mounts on /). x is the drive letter and y is the partition number, it might be /dev/sda1 or /dev/sda6. 

Yes, I've been hard rebooting. Thanks for the tip!
I ran “sudo e2fsck -f /dev/sdxy” for both partitions: 

For sda2 (/root), I got no problems.
For sda3 (/home), I got:
> 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3. Could this be a zero-length partition? 

I'm guessing this is a result of my hard-reboots. How can I fix it?

And as to the underlying hardware problem...any other diagnostics I can run?

---

### Post by sudodus on 2013-02-17
> 
Managed to boot Xubuntu 12.10 from USB. Worked fine for about 1/2h, then froze (black screen). I didn't manage to shutdown via SysRq, as I'm not sure which key that would be on my system.

SysRq is often but not always on the Print Screen key.
> 
No, I haven't. What would you recommend me to try?

Use the boot option ***nomodeset***
> 
Yes, I've been hard rebooting. Thanks for the tip!
I ran &#8220;sudo e2fsck -f /dev/sdxy&#8221; for both partitions: 

For sda2 (/root), I got no problems.
For sda3 (/home), I got:

I'm guessing this is a result of my hard-reboots. How can I fix it?

I'm not sure it is possible. Do you have a backup? You can try with Testdisk (either install it into a live session with your Ubuntu install drive (temporary install) or download one of the live repair disks containing Testdisk. See

[[COLOR="Red"]http://www.cgsecurity.org/wiki/TestDisk_Livecd[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")
> 

And as to the underlying hardware problem...any other diagnostics I can run?
I have no idea right now

---

### Post by kuckunniwi on 2013-02-17
Evidence seems to be pointing towards hardware issues.

I tried running another memtest, but from a liveUSB, and it didn't manage to get past 35% before the system froze. I've tried booting from several rescue distros (ubuntu rescue remix, RIP Linux, etc), and it freezes before the system has had a chance to boot.

There appears to be a relation between crashes/freezing and runtime: when the PC has been resting for a while, it takes longer for it to crash. After that, crashes become more frequent, until the point I can't boot into anything at all, whether from local disk or live. 

If there errors were merely to do with my hard drive, this wouldn't affect a live distro, would it? CPU or memory, then?

Would removing RAM and putting it back in, to reset it, have any effect?

---

### Post by kuckunniwi on 2013-02-17
And by the way, thanks for your help and patience!!!

---

### Post by sudodus on 2013-02-17
> **kuckunniwi said:**
> Evidence seems to be pointing towards hardware issues.

I tried running another memtest, but from a liveUSB, and it didn't manage to get past 35% before the system froze. I've tried booting from several rescue distros (ubuntu rescue remix, RIP Linux, etc), and it freezes before the system has had a chance to boot.

There appears to be a relation between crashes/freezing and runtime: when the PC has been resting for a while, it takes longer for it to crash. After that, crashes become more frequent, until the point I can't boot into anything at all, whether from local disk or live. 

If there errors were merely to do with my hard drive, this wouldn't affect a live distro, would it? CPU or memory, then?

Would removing RAM and putting it back in, to reset it, have any effect?
Yes, it is hardware-related. I think also related to the temperature.

- Can you remove dust?
- Are all the fans running (also the cpu fan(s))?
- Are the computer's input and output for cooling air free to allow the air to flow?

- If you have more than one memory card, you can remove one at a time and test if it makes a difference.

- You can also remove some cards (ethernet card, wifi card, etc), to check if it makes a difference.

If good luck, you might get it running again, but if there is a crack in some connector or some electronic unit just starting to die, you are out of luck.

---

### Post by kuckunniwi on 2013-02-17
Yeah, temperature also crossed my mind...

I'll open her up (no longer under warranty anyway) and see what can be done.

Thanks a ton!!!

---

