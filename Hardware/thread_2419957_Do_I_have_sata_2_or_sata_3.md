---
title: "Do I have sata 2 or sata 3"
date: 2019-05-27
forum: Hardware
---

### Post by crip720 on 2019-05-27
Have an Acer Aspire E5-511, everything I read says it has sata 3.  Bought a new Patriot Burst 2.5" sata 3 SSD, removed old hard drive and replaced with SSD and installed 19.04 clean.  Nicer but not wow nicer.  Speed around 290 mbs, instead of closer to rated speed of 580. Some commands I did.  dmesg ```
 dmesg | grep -i sata | grep 'link up'
[    3.310973] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
```,  smartclt  ```
sudo smartctl -a /dev/sda | grep "^SATA" SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 3.0 Gb/s)
``` and hdparm gives ```
sudo hdparm -I /dev/sda | egrep "Model|speed"    Model Number:       Patriot Burst                           
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
``` and  ```
sudo hdparm -I /dev/sda | egrep "Model|speed|Transport"
    Model Number:       Patriot Burst                           
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
```
I also did the nasty and installed Win 10 and updated BIOS.  Speed is similar in win 10.  Grub has added 'noatime'(?spelling).  Question is there anything I can do to get up to 6gbs instead of the 3gbs I have now?  There is no other drives on/attached to laptop.  Most googling I have for done this usually stops at this point.  Laptop does have a USB 3 port. The orginal hard drive is suppose to be sata 6gbs interface. Thank you.

---

### Post by DuckHook on 2019-05-27
Your drive is operating at half-capacity. *dmesg* is telling you that the HW system thinks it's a 3 Gbps link. Therefore, it doesn't matter what the system reports for your SSD itself: your bus is only operating at SATA 2 "SStatus 123", whereas SATA 3.0 is "SStatus 133".

Both *smartctl* and *hdparm* query the SSD and tell you nothing about the bus. There's nothing the OS can do if your MOBO is constrained to a SATA 2 bus.

If you are certain that your MOBO supports SATA 3, try going into your BIOS and seeing what the SATA bus is set at.

---

### Post by DuckHook on 2019-05-27
FWIW, even if you get SATA 3 bus working (i.e. just a misconfigured BIOS setting), don't expect 580 MBps throughput. Most SSDs will not come close to their factory-rated maximums. But you will do better than 290 MBps.

---

### Post by crip720 on 2019-05-27
Bios is basic settings just 'achi' and think something else has also setting xhci on/off for usb3, it's on.  Cruible is offering sata 3 ssd for this and the old hard drive is sata 3.  Everything I see or read says this should be sata 3.  Why else would they sell sata 3 ssd for this instead of sata 2s.  I even installed Win 10 to update bios to see if that would help.  Would be happy if I got somewhere in the 400s. Any other commands(copy/paste) I could use to check.

---

### Post by DuckHook on 2019-05-27
> **crip720 said:**
> &#8230;Everything I see or read says this should be sata 3.
I'm not trying to be argumentative with you. I'm just translating what your system is telling you.
> Why else would they sell sata 3 ssd for this instead of sata 2s.
Perhaps because there's no point selling SSDs in anything other than SATA3 these days?
> &#8230;I even installed Win 10 to update bios to see if that would help.
&#8230;which, based on your own research, returned the same results. I.e. the issue is not the OS and you won't find the solution there.
> Would be happy if I got somewhere in the 400s.
Which is about the maximum you should be expecting out of SATA3 anyways.
> Any other commands(copy/paste) I could use to check.
```
sudo lshw -c storage
```&#8230;then search the web for the specific SATA controller. Frankly, I don't know what you expect to do even if you find this info. If your MOBO is built in such a way that SATA 3 cannot be activated, then there's nothing left to do and certainly nothing that we can help with.

You might try contacting the OEM with a query/complaint.

---

### Post by crip720 on 2019-05-27
After painful searching for this  Atom Processor E3800 Series SATA AHCI Controller,I found this which seems to state it has USB3 but only SATA2 if I read it right(doubtful).   [https://www.dfi.com/product/index/172](https://www.dfi.com/product/index/172)
Thank you for your help anyway.

---

### Post by DuckHook on 2019-05-27
Yep&#8230; that is what it says. You have read it properly.

If it's any consolation, a SATA 3 disk is not entirely wasted on a SATA 2 bus because it is capable of operating at the bus limit. If you install a SATA 2 disk, you may not get even 290 MBps. As further consolation, I too have installed a SATA 3 SDD on a SATA 2 bus in my older laptops and am quite happy with results. There are few SATA 2 SSDs anymore, so the cost isn't a big issue and things are still a lot snappier because SSDs don't have a moving arm thrashing around for highly fragmented files. It's breathed new life into old machines and that's a pretty good deal IMO.

---

### Post by crip720 on 2019-05-28
If any of you reading this want to find out your specs and have Windows somewhere, this program should tell you HWinFO, but you have to read the report it makes, not the GUI.  More info here for basics.  [https://www.quora.com/How-do-I-find-if-my-laptop-supports-SATA-3-so-I-can-replace-my-HDD-with-an-SSD](https://www.quora.com/How-do-I-find-if-my-laptop-supports-SATA-3-so-I-can-replace-my-HDD-with-an-SSD)

---

