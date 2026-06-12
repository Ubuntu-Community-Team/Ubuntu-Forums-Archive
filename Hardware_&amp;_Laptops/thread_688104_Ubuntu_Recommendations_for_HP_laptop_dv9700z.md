---
title: "Ubuntu Recommendations for HP laptop dv9700z"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by outlive on 2008-02-05
Currently I am running just Ubuntu on my desktop computer but looking forward to getting a laptop and running Ubuntu and Vista, but have some questions;

_Here are the components for the laptop_:
**Operating Systm** -	Genuine Windows Vista Home Premium (32-bit)
**Processor** -	AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-60 (2.0 GHz, 512KB+512KB L2 Cache )
**Display** 	-	17.0" WXGA+ High-Definition HP BrightView Widescreen Display (1440 x 900)
**Memory** 	-	2GB DDR2 System Memory (2 Dimm)
**Graphics Card** -	NVIDIA GeForce Go 7150M
**Personalization** -	HP Imprint Finish (Radiance) + Webcam + Microphone
**Networking** -	802.11b/g WLAN
**Hard Drive** -	240GB 7200RPM SATA Dual Hard Drive (120GB x 2)

How would I install both Ubuntu and Vista? I never ran dual or installed Linux on Windows
Would these components work?
Can I install Gutsy or do I have to install Feisty?
Are there any faults with this laptop or the components?

What would you recommend?

---

### Post by cdtech on 2008-02-05
Hello outlive,

I have the dv9608nr.  I installed a second hard drive and use my boot options (using the f9 key) to boot into either my Vist or my Ubuntu. I decided to install the 64 bit version 7.10 using the Alternate cd, which worked out great for me.  Most everything worked without too much reconfiguring and if I had to reconfigure it wasn't all the difficult to do.

Good luck on your project and let us know if we can help.

**EDIT::**
I just seen you have two drives in there already.  No biggie, just use gparted on the live cd to repartition some space for your Ubuntu.  My second drive is a 250gig so I have 100gig partitioned for Ubuntu and the rest as storage and downloads for both Vista and Linux.  Some have problems sectioning for their swap partition (no headroom for upgrade) If they have only 1gig of memory, they set the swap for 2.  So if you plan on upgrading your ram, go ahead and set your swap partition for the amount of ram you'll end up with, it could be a real headache in the end if you don't.

My partitions are 4gig for boot (for testing other kernels),  5gig for swap (I only have 2gig memory, need no more), 40gig setup for my /home partition and the rest for the / root partition.

Hope this helps you.......

---

### Post by outlive on 2008-02-05
> **cdtech said:**
> I decided to install the 64 bit version 7.10 using the Alternate cd

What if I use the 32 bit? what would be the difference?

---

### Post by cdtech on 2008-02-05
> **outlive said:**
> What if I use the 32 bit? what would be the difference?

Performance being number one.  Gzip compression, ram speed, and kernel compilation, improvement when multitasking. There is a giant improvement if you use applications that do number crunching like compiling, encoding - ripping, rendering, so on.. so on..

---

### Post by iwallet on 2008-04-11
i bought a dv9700z and have been attempting to put ubuntu and vista on it...
i have 320 gb (160 x2) sata2 ( i believe)
 my display is the same as the guy in that started this thread
amd turion 64 x2 (2.4 ghz)
wifi (i dont remember the model..) g/b/n + bluetooth
nvidia 8400m gs
uhm... finger print scanner +webcam and mic...
thats all

well long story short.. it says i cant install anything on second HD (havent really looked into the "WHY?!" part)  however ubuntu 7.10 just wont install.. the alternate cd worked but the internet didnt..
the beta 8.04 seems to work.. so i guess ill try that.. 
who did it go with you OUTLIVE?! 
please let me know!!

---

### Post by sanus|art on 2008-04-11
I'm on [dv5105eu]("http://www.sanusart.com/hp_specs.html") here, running ubuntu from dapper until the latest beta - hardy with no problems.
However, I heard some bad gossips about dual-boot with vista (I do dual-booting XP though), so I'll suggest you to run [WUBI]("http://wubi-installer.org/") first for less harm to the system if any.

---

