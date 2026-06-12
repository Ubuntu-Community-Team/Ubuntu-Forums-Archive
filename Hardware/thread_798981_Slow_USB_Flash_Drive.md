---
title: "Slow USB Flash Drive"
date: 2008-05-18
forum: Hardware
---

### Post by slumbergod on 2008-05-18
Hey all, I was hoping someone with a bit more knowledge than me might be able to explain a curious issue I have...

I have an old laptop. If I do a clean install of XP, the USB works at 1.1 speed until I install an m$ driver that boosts it up to more or less USB 2.0 speeds. Then any flash drives work as you'd expect.

But I ditched XP completely some time ago in favour of Xubuntu Gutsy and now Xubuntu Hardy. But there has always been a weird issue with USB flash drives in Linux for me - they are just too slow.

I have search high and low on the net and I see many others have weird issues but here is what I have observed:
- normally 1.1 speed (about 1Mb/s speed)
- transferring a large file (like a 700mb xvid) the transfer starts off super quick like I'd expect, then after 100mb or so, drops to impossibly slow 1.1 speeds
- if I do the transfer as super-user, the speed is at least twice that of 1.1 speed (usually between 2mb/s and 5mb/s)
- external hard drives operate as expected when I plug them into a USB port
- brand and size makes no difference for the USB flash drives (mine is a Transcend 4Gb and on any Windows system it works perfectly)
- formatting the flash drive in NTFS, FAT/FAT32/EXT2 or 3 makes no difference. 

I am just relying on Xubuntu's built-in functionality to mount flash drives. I read that for these drives (removable) one should do that rather than experiment with fstab. 

Does anyone have any thoughts on this bizarre behaviour? Eventually I will replace the laptop with a newer one but it doesn't change the fact that I want to understand why it is behaving in a weird way with just one type of hardware.

Thanks

---

### Post by Dino_ on 2008-05-18
That would be very odd: usb 1.1 ports are usb 1.1 ports.
You can't get any faster then usb 1.1 on a 1.1 port.
That just doesn't make sense too me! :confused:

Anyway, a slowdown is possible but that can have a large number of causes: quality of motherboard, quality of usb ports, quality of flashdrive, are the "connections" of the port worn out, driver problem, slow HD read/access,...
But you say that things speed up as root, which points at software trouble?

I haven't noticed any slowdown on my pc though...

---

### Post by slumbergod on 2008-05-18
Yeah, I was very surprised too when I was running Windows XP after a clean install but before doing a Windows Update. I thought the USB ports had died. But then there was a driver in the updates and bingo the usb ports started working faster. Isn't there three standards for USB? 1.1 at the bottom, then Hi-Speed, then Full-Speed (2.0).

The hardware is old...but the part that gets me is that it is only with flash drives and if I use Windows XP those drives operate as they should. That suggests a driver issue - something to do with the way the USB driver modules are loaded in Linux perhaps? A search online reveals that a few others have observed this too.

---

### Post by Logiphile on 2009-12-04
i have the same problem. transfer rate start with jump then get slower gradually to unbearable extend. i tried to format with different file system FAT32, NTFS & ext3, but the same. i tried it under another PC using windows xp and worked fine. my usb flash drive [kingston data traveler 120]. i also don't know how to know USB port version 1.0 or 2.0

---

### Post by slumbergod on 2009-12-04
Actually, it's really embarrassing. I'll go to give a large file to a work colleague and they'll wait beside me. Then they'll ask "why is it taking so long?" I always have to explain, "It's Linux...USB file transfer is impossibly slow!" 

They usually reply, "Why?"

"I have no idea...it has never worked for me and they've never fixed it!!"

---

### Post by webdebbyjoss on 2010-04-29
I'm experiencing the same problem. 
How can we investigate and resolve this?

I've found that if I use "Gnome Commander" - it doesn't slows down almost to 0 kb/c.
So the problem can be in Gnome file manager Nautilus

Also the problem reproduces only on flash drive and it works Ok on my USB HDD

---

### Post by davek06 on 2010-06-25
Hi,
I might have the same problem ... but in my case it started suddenly, everything wa working perfectly, but then (perhaps after updating some packages) it started to copy slowly. It is not problem of the flash drive cos it works perfectly even on the same computer under win xp! it does the same thing with any other flash drive, but external USB drive works fine all the time. This is why I think it is software problem with a bad package, but I have no idea how to determine which one it is!! I would like to help to solve this if anybody have any idea!

edit:
OK, i found kind of solution that works for me!! turn off gnome and copy for example v mc!

1) alt+ctrl+f1
2) sudo /etc/init.d/gdm stop
3) mc
4) sudo /etc/init.d/gdm start

Ok, I hope it will help somebody! Nice day!

---

### Post by ImConfused on 2010-12-29
I was using Ubuntu 9.10.  The file transfer for large files was almost 1/2 hr.  I started using Natty XFCE 32bit.  The transfer rate doesn't take forever.  It is not good but it is usable.  Previous experiences with 700Mb files were it took a very, very, long time.  Now it is just much slower than windows and other file transfers.  Previously I had to boot into Windows XP to do a transfer.  This isn't the case any more.

---

### Post by kainalu on 2011-05-12
I've had this problem since 9.04. Two years and four versions, and NONE had working USB drive support.

EDIT :

Bug 197762
Declined for Dapper by Jeremy Foshee
Declined for Hardy by Jeremy Foshee
Declined for Intrepid by Jeremy Foshee
Declined for Jaunty by Jeremy Foshee
Declined for Karmic by Jeremy Foshee
Declined for Lucid by Jeremy Foshee

Apparently the developers think that USB flash drives are not worth fixing FOR YEARS. Maybe they think they are a passing fad...

---

### Post by TheVegen on 2011-05-29
I have the exact same issue!  It sure would be nice if someone would fix it. It's bad enough when Windows does dumb things like this to me I guess I should have not expected more from Ubuntu. :(

---

### Post by Clancy_s on 2011-05-29
Me too - since about 9.10 (64 bit), it was OK with earlier versions.  It's gotten worse in the last few days, to the extent that large file transfer hangs on the last few Mb and the files are corrupt.  I just booted into Vista and they transfered with no problems on to the same drive there.

I'm going to poke around and look for solutions, just posting here for the record.  If I find a fix I'll add it.

---

### Post by webjack on 2011-08-07
I experience the same problem! No issues with either the hardware or the pen drive. I use Dell Studio 15 and Ubuntu Natty 64-bit. This problem is bugging me big time. I'm pretty sure that this problem is not in the kernel. Can anybody please refer this to the gnome dev community?

---

### Post by kazza765 on 2011-08-13
Same problem here. This has occurred suddenly on a system that was working previously with the same drive. USB drive works fine on windows partition on the same computer. No idea what could have caused this, any help would be much appreciated.

---

### Post by walt.smith1960 on 2011-08-13
> **webjack said:**
> I experience the same problem! No issues with either the hardware or the pen drive. I use Dell Studio 15 and Ubuntu Natty 64-bit. This problem is bugging me big time. I'm pretty sure that this problem is not in the kernel. Can anybody please refer this to the gnome dev community?

If it appears to be a Gnome problem, maybe install an alternative desktop -XFCE, LXDE, KDE and see if the problem occurs there?

---

### Post by steroid on 2011-10-19
I was having the same problem running 11.04/Gnome. Installed Thunar and manged to copy 4.4GB to a USB drive in about 3 minutes. Hopefully this works for other people too, as it is incredibly aggravating to have USB drives essentially disabled...

---

### Post by Timothy Taylor on 2012-01-12
I have a USB docking station which I use with Grsync to back up to a SATA HDD.

This used to work just fine.  Since upgrading my mainboard, with a faster CPU, faster memory, etc., access to this USB-connected drive has actually slowed!

It now takes about 5 minutes before my USB-connected HDD even shows up in File Browser, let alone allow any files to be accessed. It's like it's reconfigured itself to USB 1.0 connection or something.

The USB-connected HDD works fine when connected to my ubuntu netbook or if I boot to Windows, so something's definitely screwed up in my desktop configuration.

Any ideas?

---

### Post by iknik on 2012-02-11
I'm also having problems with writing to my flash drive, on Ubuntu 11.10. The transfer rate is painfully slow and the copying process goes into "not responding"-mode every ten to twenty seconds or so (if I'm using for instance Firefox at the same time, it also stops responding regularly when I'm cpoying to flash drive).

Not too long ago I was using 11.04 (with Unity, just like 11.10), which didn't have these problems. Also, I have a dual boot system, and Windows XP writes to USB just fine. Now I find myself restarting and booting into Windows whenever I want write a large file to my flash drive, because it's faster that way...

---

### Post by ImConfused on 2012-02-11
Glad I didn't upgrade to 11.10 from 11.04.  That would have made it go from slow but usable back to useless for this task.  Thanks for the heads up.

---

### Post by icansolvetheproblem on 2012-02-20
I have similar degraded usb throughput issues; I upgraded from 10.03 to 11.10 and my USB transfer rate dropped to 1.4 MB per second.   I tried a clean install of 11.04 and now the USB transfer rate starts out around 48 MB per second but in about five seconds it drops to 2 MB per second.  

I didn't use Wubi. This seems to be hardware specific as a different box running 11.10 doesn't exhibit any USB throttle.

Machine  with USB transfer issues (same with 11.04 and 11.10 64bit):
Intel DP45S mobo w/p45 chipset, Q8400 @ 2.66Ghz proc, 8 GiB corsair DDR3, dual velociraptor 1tb sata drives mirrored 

Machine without any USB transfer issues:
Intel Core 2 duo processor, 4GiB DDR2, dual Seagate 1tb sata drives mirrored

---

### Post by jfca283 on 2012-02-21
Hi. I'm having the same problem. Copy 3gb from my laptop no my usb takes, easily, 30 minutes. Will be this issue fixed?

---

### Post by hsantanna on 2012-03-04
This slow USB drive transfer bug is so old but still lives.

I have the same problem so many years over different hardwares.

When I have to fast transfer a big file to someone I have to boot windows and it's a shame to me.

Linux: < 1Mb/s (a 2GB file can take 1h to transfer)
Windows: > 10Mb/s

---

### Post by slumbergod on 2012-04-13
Thought I'd revisit this old thread that I started. Here I am on 11.10 and it is still painfully slow compared to Windows. It's hard to argue that it is the usb flash drive or my hardware when it works very fast under Windows on the same machine.

---

### Post by mutex023 on 2012-04-24
I've a workaround for this. Let me know if it works - 
[http://ubuntuforums.org/showthread.php?t=1963360](http://ubuntuforums.org/showthread.php?t=1963360)

---

