---
title: "Gigabyte GA-EP45-DS3R"
date: 2008-07-27
forum: Hardware
---

### Post by SVMartin80 on 2008-07-27
I plan to buy a Gigabyte GA-EP45-DS3R main board. I would like to know if it is well supported:

- firewire
- sata
- raid-0
- lan
- audio

If you have this main board running with any ubuntu variant, I would like to hear your experiences!

Much thanks in advance!

---

### Post by hotweiss on 2008-07-27
> **SVMartin80 said:**
> I plan to buy a Gigabyte GA-EP45-DS3R main board. I would like to know if it is well supported:

- firewire
- sata
- raid-0
- lan
- audio

If you have this main board running with any ubuntu variant, I would like to hear your experiences!

Much thanks in advance!

The motherboard raid will not work for sure as it's software RAID, but you can accomplish the same thing using Linux's dmraid. Everything else I assume will work, but buy it from a store where you can return it just in case. I have a P35-DS3R...

---

### Post by SVMartin80 on 2008-07-28
Thanks for your reply. But now I wonder: if it is "just" software raid, why do some motherboards support it, while other's don't?

---

### Post by murrie on 2008-07-28
hello svmartin80,
                          I have a gigabyte ep43-ds3r motherboard with an intel q9450 cpu, and standard ddr2-800 mhz ram.  It is overclocked to 3.2 ghz and under hardy heron, it runs superbly. In the bios, you must change the sata to ahci and linux will then reconize all hard drives.  The output from cat /proc/cpuinfo is as follows 

vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 3200.111
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6400.27
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual

Hope you find this useful.  The system really flies.  If you need help with overclocking the cpu, email me and I will assist you.

By the way, I am running hardy heron 64 bit.

Regards Muz

---

### Post by SVMartin80 on 2008-07-28
Hi Muz,

thanks for the info. I will use a Q6600 (9450 just a bit too expensive) and 8 GB of OCZ memory that support 1066 MHz.

I indeed might overclock the system right away, I was told that this works great on these systems :-) If I need any help, I will certainly contact you, thanks for that!

Just one thing: are you using a RAID setup as well?

Martin

---

### Post by SVMartin80 on 2008-07-28
After some "googling" it looks like on-board raid is just software raid, but the bios recognizes raid during booting the OS.

So I could also buy the GA-EP45-DS3L, which doesn't have Crossfire support (which I don't need), does not support dolby home theatre (which I don't need) and does have only 1 network adapter (I don't need a second one).

I was told that using Ubuntu software raid just works without the on-board chip.

---

### Post by SVMartin80 on 2008-07-28
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by hotweiss on 2008-07-28
> **SVMartin80 said:**
> After some "googling" it looks like on-board raid is just software raid, but the bios recognizes raid during booting the OS.

So I could also buy the GA-EP45-DS3L, which doesn't have Crossfire support (which I don't need), does not support dolby home theatre (which I don't need) and does have only 1 network adapter (I don't need a second one).

I was told that using Ubuntu software raid just works without the on-board chip.

Yes get the non-raid version for sure...

---

### Post by calgaryconehead on 2008-08-08
> **murrie said:**
> 
...snip...
I have a gigabyte ep43-ds3r motherboard with an intel q9450 cpu
...snip...
The output from cat /proc/cpuinfo is as follows 

vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 3200.111
cache size	: 6144 KB
...snip...
Regards Muz

I notice that only 6144KB cache is reported.  The Q9450 is supposed to have 12MB cache.  Do you know why this is?

I just built a new box using a Gigabyte GA-X48-DS4 mobo and Q9450 and I see the same 6144KB cache reported.

Thanks,
John

---

### Post by PhailQuail on 2008-09-07
I have a Gigabyte EP45-DS3R and have encountered a very similar (if not the same) problem.

As said in [http://ubuntuforums.org/showthread.php?t=607953&page=2](http://ubuntuforums.org/showthread.php?t=607953&page=2) I attempted to run Ubuntu with "noisapnp pnpacpi=off pnpbios=off" boot flags, and it works now.

So give that a shot.

EDIT:
Odd, it doesn't seem to work after a reboot, but it was working.

---

### Post by arwilson529 on 2008-09-19
I just bought one of these bad boys.  Its been a pain to set up but once you figure out its quirks its not so bad.  For Mythbuntu, I had to enable AHCI, disable all the stuff for the floppy, and use the ' all-generic-ide ' boot flag in order to get the install running.  My big problem is that XP requires AHCI to be turned off before it will load.  I've also noticed that when I turn on and off AHCI, the BIOS changes the boot order of my hard drives every time.  Needless to say, that can cause some problems when you have four hard drives in a HTPC.

---

### Post by rsff on 2008-09-20
> **calgaryconehead said:**
> I notice that only 6144KB cache is reported.  The Q9450 is supposed to have 12MB cache.  Do you know why this is?

I just built a new box using a Gigabyte GA-X48-DS4 mobo and Q9450 and I see the same 6144KB cache reported.

Thanks,
John

yeah i also have one of this processors and im also curious about pnly half cache being reported, already google it but couldnt find a answer..
could anyone enlight me,thanks
edit:
already found the answer..
the cores share memory between them like 6MB for each pair..
do 
# dmidecode -t cache
and there it is the 12mb

damn vendors...

---

### Post by twisted_steel on 2008-11-11
Has anyone with the GA-EP45-DS3L updated to Intrepid (8.10)?  I am planning on buying one of these boards in the next month or two and wanted to make sure everything works.  I see that there is a BIOS change that was required in Hardy, and it's not a big deal if I still have to do that.  I was leaning towards Intrepid 64-bit as well.

Thanks.

---

### Post by twisted_steel on 2008-11-16
After reading reviews of both the GA-EP45-DS3R on Phoronix, it sounds like the boards worked fine in Intrepid Alpha 4 (64-bit).  Here is the full review: [http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1)

---

### Post by oprater on 2009-01-04
What is dmraid and how do I use it?

---

### Post by jsc3 on 2009-01-05
As another user pointed out, but did not label it as such, there is a software raid HOWTO here:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

If software raid (dmraid) is what you want, you might want to look for threads related to that specifically.  Try searching for "dmraid" or "software raid".

---

### Post by jsc3 on 2009-01-05
I have a GA-EP45-UD3R, and I was able to use Hardy Heron (8.04) after setting both SATA_RAID AHCI Mode (ICH10R) and Onboard SATA/IDE Ctrl Mode (Gigabyte SATA2 chip) to AHCI in the BIOS.  I also set SATA Port0-3 Native Mode to Enabled in the BIOS.

I booted/installed from my PATA DVD using the onboard IDE connector, and am using a WD SATA drive connected to SATA port 0 of the ICH10R.

Before I set these, I was able to boot from CD, but Hardy Heron (8.04) could not see the HD.  Intrepid Ibex (8.10) did not require these BIOS changes to see the HD, but I want to use 8.04 because it is supported for VMware Server 2.0.

---

