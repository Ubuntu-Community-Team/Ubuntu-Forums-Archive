---
title: "USB 3.0 Harddrive is unresponsive for several seconds occasionally"
date: 2016-10-26
forum: Hardware
---

### Post by claudius-ellsel on 2016-10-26
I already asked for help for this on a German forum and on askubuntu: [http://askubuntu.com/questions/839703/usb-3-0-harddrive-is-unresponsive-for-several-seconds-occasionally](http://askubuntu.com/questions/839703/usb-3-0-harddrive-is-unresponsive-for-several-seconds-occasionally) but did not manage to fix the problem.

  I changed my PC setup recently. Now I have some problems with a 1TB  external 2.5" harddrive. It worked without problems before. In the old setup (will call it PC A) it was plugged into a front USB 3.0 port. After  changing the setup I plugged it into an USB 3.0 port on the back (might  be the reason or the issue was introduced with an update). Since then I get lags for about 10-20 seconds every now and then when  accessing the drive (watching a movie or playing music).
The issue occurs on Ubuntu 16.04 and also after upgrading to 16.10.

  I experience the same issues on a second PC (will call it PC B), also attached to a rear USB 3.0 port.
  In the German forum we found out that there is a message in dmesg after the problem occurs:

  ```
usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
```

  Immediately after this message appears everything is working normal again.

Someone on askubuntu suggested to try the front USB connector again. There it seems to be still working normal.

  Unfortunately I don't know what causes the problem. So I hope someone can help.

---

### Post by TheFu on 2016-10-26
I have the same USB3 pause issue on a 1st Gen Core i5 and MSI motherboard. Doesn't matter which port I use - both are aftermarket USB3 cards.
On a newer Pentium G3258 with a $50 MB, USB3 works perfectly.  Both run 14.04 server.  I think is really comes down to the maturity of the HW and support for USB3.  

Of course, I really don't **know** what is causing the issue.

---

### Post by claudius-ellsel on 2016-10-27
At least I am not the only one with this problem. I experience the issue with a Core i5-4670K (PC A) and a Xeon E3-1225V3 (PC B), if that helps. Might also be a Hardware specific issue with the Kernel or some other stuff on software side. I will try to test this on Windows.

---

### Post by claudius-ellsel on 2016-11-03
I did a short test on Windows with PC B (around 30 Minutes of watching video) and  did not experience this problem. Will maybe do a longer test to ensure  that this is really not happening there.

@TheFu Do you run Windows to do a test as well?

But  it seems that this is software specific. So if anyone knows more about  this, I'd be glad to get your help. Otherwise I will probably create a  bug report on Launchpad after ensuring that this does not happen on  Windows.

---

### Post by TheFu on 2016-11-03
It is a driver issue that probably cannot be corrected. The bug is with the vendor NOT creating solid, Linux F/LOSS drivers or releasing detailed specs for F/LOSS teams to build.

My systems are running multiple, production, virtual machines and cannot be converted to Windows on the physical hardware.

---

### Post by claudius-ellsel on 2016-11-03
Alright, so then I will do some more testing with Windows.

---

### Post by TheFu on 2016-11-03
> **claudius-ellsel said:**
> Alright, so then I will do some more testing with Windows.

I'm curious. Exactly how will that help? The problem is with a non-Windows OS.

---

### Post by claudius-ellsel on 2016-11-03
I want to make sure this is really OS specific before reporting it as a bug.

---

### Post by TheFu on 2016-11-03
> **claudius-ellsel said:**
> I want to make sure this is really OS specific before reporting it as a bug.

The device that stalls for me is this:
```
Bus 004 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge

```
In your bug report, they will want something like that.  Mine is an add-on USB3 card PCI connected.

Did a little searching this morning. Found this:```

create a /etc/modprobe.d/blacklist-usb3.conf file with
  blacklist uas
```
Can't reboot to test it until Saturday.  [https://bugzilla.redhat.com/show_bug.cgi?id=717633](https://bugzilla.redhat.com/show_bug.cgi?id=717633) is the source. There were other threads with similar recommendations. Might not be the same issue for you or me. I dunno.

---

### Post by TheFu on 2016-11-05
Rebooted and tested this morning - nope, *blacklisting uas* didn't help.

---

### Post by claudius-ellsel on 2016-11-06
Thanks for reporting. Since the bug report was from 2011 and looks like fixed, I am not too surprised it didn't work, thoguh.

I did further testing on Windows, but on my first PC (will call it PC A to avoid confusion from now on, also edited my past posts). This time I used VLC to play a video and it seems like the problem occurs there as well. After that I tried the default movie app of Windows. It hanged after pausing the video, but had no problems during playing for now.

---

### Post by TheFu on 2016-11-06
I really expected it to work, but it has been an issue for years now and really only impacts during backups, 2am-4am daily, local time.

USB2 should have more than enough bandwidth to support playback of 1080p or less videos. Music shouldn't be an issue with almost any USB connection, ever. On a 2.5inch external HDD, my only concern would be power. Using an external power supply, not just the USB port. Some USB ports don't provide sufficient power and need external power.

The blacklisting didn't change that my system is really I/O blocked when the USB3 disk (externally powered) is in heavy use.  Since it is a VM server, I see connections to guest machines dropped due to a lack of response in the allowed period.  Not really that much of an issue for email or web servers, but for my desktop (runs inside a VM), it is a hassle to reconnect, but nothing more (no data loss). The blocking happens almost every night during backups.  Short of replacing the system, I don't really see an answer for my HW. It is 6+ yrs old now and $250 would easily get to a system 5x faster.  Really need to replace a power-sucking i7 first. Gotta retain the system redundancy.

Probably not related to your issue, but video playback can also be a GPU driver issue.  If HW is being used to decode the vcodec, then CPU use should be less than 10%.  3% is what I see on a r-pi.  If not HW decoded, it could be 60-100% CPU. You know all this already - just info for lurkers.

---

### Post by TheFu on 2016-11-14
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1208993](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1208993) is another bug with a possible solution.  Testing it here now. So far, seems to work.  System-wide impacts are definitely less now.  Will need a few more days to see if it really is working or not.  Seems people running into the issue added RAM to their systems, post Ubuntu installation.  I did as well.  

Modify /etc/sysctl.conf - adding these lines:
```
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10

```
**$ sudo sysctl -p**
to reload the new settings.

[https://www.kernel.org/doc/Documentation/sysctl/vm.txt](https://www.kernel.org/doc/Documentation/sysctl/vm.txt) has the documentation.

---

