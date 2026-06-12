---
title: "[Firewire-IEEE1394] using the new kernel stack on Karmic"
date: 2010-01-24
forum: Hardware
---

### Post by huygens on 2010-01-24
Hi there,

As the new firewire kernel stack is not experimental since kernel 2.6.31 (the version on Karmic), I thought about giving it a try.
I've checked the [official stack migration wiki]("http://ieee1394.wiki.kernel.org/index.php/Juju_Migration") and did what was recommended there. As Ubuntu shipped with both the old and new stack but with the new one disabled in /etc/modprobe.d/blacklist-firewire.conf
Therefore, I've modified this last file so that it looks like this now:
```
blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2
```
So the old ieee1394 stack is blacklisted and the new firewire stack should be automatically loaded.

I have rebooted my computer so change takes effect and performed an lsmod which failed :-(
```
Module                  Size  Used by
firewire_sbp2          15112  0 
firewire_core          47296  1 firewire_sbp2
crc_itu_t               1852  2 rt61pci,firewire_core
sbp2                   22888  1 
ohci1394               29900  1 
ieee1394               86596  2 sbp2,ohci1394
```
As you can see the firewire_sbp2 is unused, whereas the sbp2 is used (I have an external firewire hard drive plugged in). If I plug out my HD, then the sbp2 gets also unused. Thus, it is the one used for the HD. And as you can see from the dependency sbp2 is based on the old stack which I had blacklisted.
*Side note*: I have unplugged my HD, then using 'modprobe -r' I removed the sbp2 and ohci1394 modules. Then, I plugged back my HD hoping that the new stack would be used... No success. Linux did not even see that I had plugged back my HD, as you can see in the dmesg output below, which only shows the device and modules removal:
```
[  268.610021] sd 6:0:1:0: [sdc] Stopping disk
[  268.650880] ieee1394: sbp2: Logged out of SBP-2 device
[  304.998148] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[0090a991e0107124]
[  304.998375] ieee1394: Node removed: ID:BUS[0-01:1023]  GUID[0010dc00006c3bb8]
```

My questions are: how do I activate and use the new firewire stack of kernel 2.6.31? Is it a bug in Ubuntu that actually the blacklisted modules are still loaded or is it "normal" behaviour?

Thanks in advance for any guidance.

PS: I do understand the risk of using the new stack which is perhaps not as well validated as the old one. I'm willing to take that risk, I'm a computer geek ;-)

---

### Post by huygens on 2010-01-30
Anyone using firewire hard disks?
Help is still welcome!

---

### Post by geoff07 on 2010-02-23
I'm not using 1394 storage but I am trying to get a dv camcorder to be read by dvgrab (or indeed any program).  I have tried everything mentioned in the forums to get it to work and can control the camcorder but not see captured video. So I decided to switch stack to see if that worked. And, lo and behold, I couldn't even switch the stack (exactly the same results as reported in this thread earlier).

I should be most grateful if someone that knows how this stuff is supposed to work can explain definitively how to switch to the new stack.

Or, how to use the old stack when all the settings, groups and permissions are correct (I believe) but still no video is captured.

Or, find a 1394 test program that runs under karmic that shows what is going on.

thanks in anticipation!

---

### Post by huygens on 2010-02-23
Just for information: I did not make any progress on switching to the new stack since my last message. I really do not understand why... I'm perhaps thinking of opening a bug report....
I will keep on notifying this thread if I learn anything new.

---

### Post by huygens on 2010-02-28
Well ... I have opened a bug report as it obviously seems that something is wrong. Here is the link : Bug #529524 [https://bugs.launchpad.net/bugs/529524](https://bugs.launchpad.net/bugs/529524)

---

### Post by huygens on 2010-03-21
And even worse! [Lucid Beta 1 (kernel 2.6.32) is still using the old driver stack, but it does not seems to work ]("https://answers.launchpad.net/ubuntu/+question/104996")anylonger!!
This would be a major regression, I hope we can switch easily to the new stack in Lucid.

---

### Post by huygens on 2010-03-21
sadly no luck with switching to the new stack :-(

So with Lucid Beta 1 you cannot use a firewire hard disk either with the old stack (which does seems buggy now) or with the new one (as with Karmic the migration does not work)

Check the other bug report for Lucid: Bug #543488 - [https://bugs.launchpad.net/bugs/543488](https://bugs.launchpad.net/bugs/543488)

---

### Post by sualo4711 on 2010-03-26
My external disk: "LaCie Quadra 1TB", connected to Asus P5Q Deluxe.
Kernel: Linux xxx 2.6.31-21-server #59-Ubuntu SMP Wed Mar 24 08:26:06 UTC 2010 x86_64 GNU/Linux

I was used to connect the disk by USB2, more du to similar observations you made. "hal" recognized some IEE1394 device activity, but no mount etc. happened.

Then I tried the module configuration you proposed and rebooted the system.
I logged on to the desktop and plugged the FW plug - no reaction by dmesg.
Then I unplugged the USB2 plug from the harddisk device itself (I disconnected it from the PC, but left the other plug in) and reconnected the FW plug.

A voilá: Desktop media management shows the device and its partitions.

regs
--
Mar 26 15:12:01 legolas kernel: [  309.211161] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Mar 26 15:12:03 legolas kernel: [  311.156943] firewire_core: created device fw1: GUID 00d04b9b0202ab93, S400, 3 config ROM retries
Mar 26 15:12:03 legolas kernel: [  311.176196] scsi9 : SBP-2 IEEE-1394
Mar 26 15:12:04 legolas kernel: [  311.635637] firewire_sbp2: fw1.0: logged in to LUN 0000 (0 retries)
Mar 26 15:12:04 legolas kernel: [  311.642513] scsi 9:0:0:0: Direct-Access     LaCie    Hard Drive            PQ: 0 ANSI: 4
Mar 26 15:12:04 legolas kernel: [  311.642660] sd 9:0:0:0: Attached scsi generic sg6 type 0
Mar 26 15:12:04 legolas kernel: [  311.647054] sd 9:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 26 15:12:04 legolas kernel: [  311.650451] sd 9:0:0:0: [sde] Write Protect is off
Mar 26 15:12:04 legolas kernel: [  311.650454] sd 9:0:0:0: [sde] Mode Sense: 10 00 00 00
Mar 26 15:12:04 legolas kernel: [  311.652709] sd 9:0:0:0: [sde] Cache data unavailable
Mar 26 15:12:04 legolas kernel: [  311.652711] sd 9:0:0:0: [sde] Assuming drive cache: write through
Mar 26 15:12:04 legolas kernel: [  311.662169] sd 9:0:0:0: [sde] Cache data unavailable
Mar 26 15:12:04 legolas kernel: [  311.662171] sd 9:0:0:0: [sde] Assuming drive cache: write through
Mar 26 15:12:04 legolas kernel: [  311.662175]  sde: sde1 sde2
Mar 26 15:12:04 legolas kernel: [  311.735971] sd 9:0:0:0: [sde] Cache data unavailable
Mar 26 15:12:04 legolas kernel: [  311.735974] sd 9:0:0:0: [sde] Assuming drive cache: write through
Mar 26 15:12:04 legolas kernel: [  311.735977] sd 9:0:0:0: [sde] Attached SCSI disk
--

---

### Post by huygens on 2010-04-10
Thanks for the information sualo4711. However, I had only the firewire cable plugged in, so I was out of luck...
Anyway, I have been trying Lucid lately and though at first the firewire support was worse (it did not work even with the old stack) now it is back to normal with the old stack, and with a patch I was able to use the new kernel stack.
I have updated the bug report (Bug #529524 [https://bugs.launchpad.net/bugs/529524](https://bugs.launchpad.net/bugs/529524)) with all information about the patch.
This patch will work for firewire HDD, I do not think it will work with audio firewire devices as it relates to hdparm...

---

