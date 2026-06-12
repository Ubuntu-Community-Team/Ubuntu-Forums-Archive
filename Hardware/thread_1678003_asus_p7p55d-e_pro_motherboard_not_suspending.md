---
title: "asus p7p55d-e pro motherboard not suspending"
date: 2011-01-29
forum: Hardware
---

### Post by xdevnull on 2011-01-29
I'm trying to get my system to suspend or hibernate and the log says it is, but then it just pops back.  So when I select suspend, it goes blank for a second and then gives me the unlock/password screen.  I tried acpitool -s and get similar thing but without the unlock screen.  

I have the latest nvidia drivers on my two gtx 460 SLI's

Any ideas?

```
Jan 29 11:57:57 cannon kernel: [13665.667721] PM: Syncing filesystems ... done.
Jan 29 11:57:59 cannon kernel: [13666.520684] Freezing user space processes ... (elapsed 0.02 seconds) done.
Jan 29 11:57:59 cannon kernel: [13666.542218] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jan 29 11:57:59 cannon kernel: [13666.562201] Suspending console(s) (use no_console_suspend to debug)
Jan 29 11:57:59 cannon kernel: [13666.562686] au8522 16-0047: destroying instance
Jan 29 11:57:59 cannon kernel: [13666.562698] xc5000 16-0061: destroying instance
Jan 29 11:57:59 cannon kernel: [13666.642158] PM: resume of devices complete after 60.480 msecs
Jan 29 11:57:59 cannon kernel: [13667.010799] au0828: i2c bus registered
Jan 29 11:57:59 cannon kernel: [13667.268399] tveeprom 16-0050: Hauppauge model 72001, rev B3F0, serial# 7660414
Jan 29 11:57:59 cannon kernel: [13667.268401] tveeprom 16-0050: MAC address is 00:0d:fe:74:e3:7e
Jan 29 11:57:59 cannon kernel: [13667.268402] tveeprom 16-0050: tuner model is Xceive XC5000 (idx 150, type 76)
Jan 29 11:57:59 cannon kernel: [13667.268404] tveeprom 16-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jan 29 11:57:59 cannon kernel: [13667.268405] tveeprom 16-0050: audio processor is AU8522 (idx 44)
Jan 29 11:57:59 cannon kernel: [13667.268406] tveeprom 16-0050: decoder processor is AU8522 (idx 42)
Jan 29 11:57:59 cannon kernel: [13667.268407] tveeprom 16-0050: has no radio, has IR receiver, has no IR transmitter
Jan 29 11:57:59 cannon kernel: [13667.268409] hauppauge_eeprom: hauppauge eeprom: model=72001
Jan 29 11:57:59 cannon kernel: [13667.268429] au8522 16-0047: creating new instance
Jan 29 11:57:59 cannon kernel: [13667.268430] au8522_decoder creating new instance...
Jan 29 11:57:59 cannon kernel: [13667.270781] tuner 16-0061: chip found @ 0xc2 (au0828)
Jan 29 11:57:59 cannon kernel: [13667.270842] xc5000 16-0061: creating new instance
Jan 29 11:57:59 cannon kernel: [13667.275625] xc5000: Successfully identified at address 0x61
Jan 29 11:57:59 cannon kernel: [13667.275625] xc5000: Firmware has not been loaded previously
Jan 29 11:57:59 cannon kernel: [13667.275850] au8522 16-0047: attaching existing instance
Jan 29 11:57:59 cannon kernel: [13667.283038] xc5000 16-0061: attaching existing instance
Jan 29 11:57:59 cannon kernel: [13667.287732] xc5000: Successfully identified at address 0x61
Jan 29 11:57:59 cannon kernel: [13667.287733] xc5000: Firmware has not been loaded previously
Jan 29 11:57:59 cannon kernel: [13667.287734] DVB: registering new adapter (au0828)
Jan 29 11:57:59 cannon kernel: [13667.287736] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
Jan 29 11:57:59 cannon kernel: [13667.287921] Registered device AU0828 [Hauppauge HVR950Q]
Jan 29 11:57:59 cannon kernel: [13667.287984] PM: resume devices took 0.700 seconds
Jan 29 11:57:59 cannon kernel: [13667.288104] Restarting tasks ... done.
```

---

### Post by xdevnull on 2011-02-02
Shameless bump - not hints from anyone.  I thought this was a fairly popular board.

---

### Post by lidex on 2011-02-02
Have you checked for bios update?

---

### Post by kristianz on 2011-02-07
I have a similar problem with the same motherboard. When I try to either suspend or hibernate, I only get a black screen with a white blinking cursor and no suspend or hibernate action is completed. I have to hit the reset button on my computer.

I'll let you know if I solve my problem, perhaps your problem is related.

---

### Post by DukeBoxer on 2011-02-12
You guys are lucky! I can install ubuntu 10.10 on this board with a GTX460 card but only with the alternate installer and when I have it up and running it only lasts about 5 minutes and then locks up on me. Are you guys having that problem as well? Here are my full specs:

Asus P7P55D-E Pro
Core i5-760
8 gb (4x2) Gskill RipJaw
MSI TwinFrozr GTX460

---

### Post by Zookalicious on 2011-09-28
I have the exact same problem with this motherboard. Don't really want to do a BIOS update unless it is proven to fix the problem (suspend on windows works fine).

On top of that the other strange thing is if I leave the computer alone for long enough the computer will try to go to sleep and wake up "groggy" is best I can describe. It gets really really slow and the UI freezes constantly until I restart.

---

### Post by Thonixx on 2012-07-29
Hi

I just found a solution for this annoying suspend/hibernate bug. I experienced the same thing on my asus notebook PL80JT with Ubuntu 2 years ago. After hours of search I found a soultion which definetely works.

Now I tried this solution on my Asus P7P55D-LE mainboard and it works.
Feel free to try it:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

**Do not take Step 2 OLD. Just the new Step 2.**
Oh and have fun with suspend/hibernate.

---

