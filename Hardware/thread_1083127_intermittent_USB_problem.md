---
title: "intermittent USB problem"
date: 2009-02-28
forum: Hardware
---

### Post by linuxape on 2009-02-28
Hi I migrated from WinXP to Ubuntu8.10 about 5 months ago and have not gone back since.
Recently I am begining to experience some problems with my USB ports.
Setup: IBM Thinkpad T43p
Processor: 1.86GHZ
Memory: 2GB
HDD: WD 250GB
OS: Ubuntu8.10 (no dual boot here and no other OS exist on this HDD)
Kernel: 2.6.27-11 generic

I am using this Logitech VX Revolution USB wireless optical mice and sometimes all of a sudden in the middle of a session it wont respond. Same would be true if I have a USB drive.  I have tried two so far Kingston DataTravellerII plus 2GB and Sandisk Cruzer Titanium 4GB.  It seems the USB ports are not working at all, pluggin in or plugging out does not evoke any response from the OS.

If I swap the old WinXP HDD and boot from that there is absolutely no problem with any of my USB devices.  Which makes me think that the hardware is OK.  Infact everything was perfect only couple of weeks ago.

Any help would be greatly appreciated.
Thanks.

---

### Post by JAYCEE1 on 2009-03-01
Very interesting.

I have an IBM T41 and I have a very similar problem. I only notice my problem when I copy a movie on to my thumbdrive. All at once, the usb drive will just disappear and the copy process fails. 

I have noticed that if I keep perfectly still and do not move the computer at all, the copy process will finish. I assume that I have a physical problem (loose usb jack, maybe). 

Does your usb problem occur after moving your computer? (Even slightly moving it?)

Since it is intermittent, I don't know of a way to test it.

---

### Post by linuxape on 2009-03-02
it is plausible that the usb connection to the motherboard might be loose ever so slightly, but I doubt it. Since I had to do something critical and the usb was failing me repeatedly so out of desperation I swaped back the old XP HDD and used it for more than five hours at a stretch and it worked without a glitch. 

later on I recalled that I updated wine thrice to1.1.14 to 1.1.15 and then again to 1.1.16 over the last few weeks and the problem cropped up.  So just out of curiosity I reverted back to Ubuntu repo 1.0.1 (stable version) and since then for the last 24hrs+ I haven't encountered the USB issues.  I am not an expert in Linux by any stretch of imagination but I think wine might be doing it.  I will wait and see if it returns .. ......hope it doesn't.

Also on a side note after upgrading to 1.1.15 and then to 1.1.16 my bootup times increased significantly, now it is close to as it was before.
Maybe it is just a freak coincidence.

Thanks.

---

