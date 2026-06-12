---
title: "Cannot boot from LiveCD"
date: 2013-07-09
forum: Hardware
---

### Post by Acharn on 2013-07-09
I have an old Acer Aspire M-1610, 1GB RAM, motherboard is Acer F672CR, Award BIOS dated 2007, CPU Intel Core 2 Duo 2180. Starting about a month ago I began having problems. First my internet connection stopped and could only be restarted with a reboot. Then from time to time the whole thing just stopped on me, but I could reboot. Then when I rebooted, I got the Grub menu instead of booting straight up, but all I had to do was select Ubuntu and hit the carriage return. Then that didn't work any more, but I was able to boot from my Ubuntu 12.04 LiveCD. Finally that stopped working. Then when I turned the power on all I got was a long beep. OK, finally was able to replace the RAM (DDR2 SDRAM is hard to find).

So now I have the same symptom with the hard drive. It comes up with the Grub menu, but when I hit enter it just goes black. Similarly, when I try to boot from the CD, I can get to the graphical boot menu but when I try to proceed from there it fails. I can see that some of the smaller condensers on the motherboard are slightly "domed," but my previous experience several years ago with the condenser problem on motherboards leads me to think that's not it.

The failure is not consistent. Sometimes it just goes to a black screen with an underline cursor blinking at the upper left corner, sometimes it leaves some messages on the screen. A sampling:
```

2.045378]   [<c15a8fe6>] oops_end+0x96/0xd0
2.045431]   [<c15915c9>] no_context+0xc3/0xcb
2.045486]   [<c1591711>] __bad_area_nosemaphore+0x120/0x128
2.045541]   [<c15ab1ba>] ? spurious_fault+0x5a/0xc0
2.045595]   [<c15av3d0>] ? vmalloc_fault+0x190/0x190

```
I have some more if they would be helpful, but I had to copy them by hand and now have to type them, so if I can avoid that chore I'd rather. The page ended with:
```

2.046581]   [>c1879792>] ? start_kernel+0x35d/0x35d
2.046636]   [>c15af6be>]  kernel_thread_helper+0x6/0x10

```
and then it just sits there like a lox.

I was able to run the memory test from the LiveCD and after four passes it showed no problems. When I tried to run the test on the hard drive it went to black screen, but it seems the hard drive is working, because it's able to bring up the Grub screen.

I feel sure the problem is hardware-related, but am hoping someone here can help me isolate the problem.

---

### Post by oldfred on 2013-07-09
In Disks or Disk Utility you can click on drive and look at Smart Status. I only know that passed or green is good. But it can run lots of tests on hard drive.

---

### Post by sanderj on 2013-07-09
An "oops" is not good. As the memtest reports no problems, I would rule out the harddisk: if you do a live boot from a CD, is it stable all the time? To be sure, you should disable swap, as swap also uses the harddisk.

Oh, wait: you cannot from a live CD? Why not? Errors? If so, the CD might be corrupt, or the IDE / SATA controller. If so, can you live-boot from a USB stick written with unetbootin?

---

### Post by Acharn on 2013-07-10
Thank you both for your attempt to help. I'm afraid the problem is that I cannot boot. I can start the boot process, but it halts with a black screen. The memory test I did was from the Ubuntu start page where it asks if you want to test Ubuntu, install Ubuntu, test memory, check the hard disk for errors, and I forget what else. The memory test ran, the disk test didn't. Oddly, while floundering around I inserted an unlabeled CD and found that it would boot up DR-DOS and actually run a program -- unfortunately the program was in German and seemed to be something about re-partitioning. Can't imagine why I had it or why I burned it to CD.

Actually, the situation has deteriorated from even that. The symptoms now are that the machine reboots itself after about thirty seconds. I'm sure it's a motherboard problem, and probably condenser blowout or whatever it's called. From the middle of April through the first few days of June almost every day the ambient temperature got up over 40 degrees Centigrade. I wasn't monitoring the internal temperatures, but they were probably higher than was good for the components.

I was hoping the symptoms I described in the initial post would lead somebody to tell me, "Oh, I recognize that. Your problem is ..., and the simple solution is ..."

Anyway, my wife and I discussed it and decided the best solution was to let this machine die and start saving up for a new one. I was hoping to get through until next year, but it looks like I'll have to use the neighborhood gaming shop for my internet for a few months.

---

