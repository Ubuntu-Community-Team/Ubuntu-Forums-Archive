---
title: "Dual Core only Working on One Core, Switch Kernel Kills Wireless"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by mlissner on 2007-01-07
Hello, I have a dual core Intel laptop, and I've been having a bit of trouble since upgrading to Edgy. When I made the upgrade, it began a new habit of freezing for about 30 seconds at a time every 5-30 minutes and then recovering flawlessly. I haven't been able to figure out the offending process, or cause, so if anybody has any ideas there, I would be so grateful.

The other fun thing I've noticed is that my dual core is only operating as a single core:
cat /proc/*cpu*
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 996.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 3996.56

```
I found a fix for this here: [http://ubuntuforums.org/showthread.php?t=85917&page=2](http://ubuntuforums.org/showthread.php?t=85917&page=2), but when I followed the directions on that link, and switched (successfully) to the smp kernel, my wireless disappeared (dual /did/ become enabled). If I reboot and switch the 386 kernel, the wireless works again without any reconfiguration or anything (but /sans/ dual core).

My logs do have some suspicious code in them that I would love to understand:
```
[17189890.432000] ata2 is slow to respond, please be patient
[17189915.408000] ata2 failed to respond (30 secs)
[17189915.416000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17189915.416000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00

```
This code is definitely related to the system freezes. I just hung around in the terminal waiting for a freeze until I got one. When it happened, I ran dmesg, and I got the first line above. I ran it again and again, and sure enough, after 30 seconds, everything unfroze, and I got the other three error messages.

Any ideas about the freezes? What do those errors mean? How do I get wireless and dual core going at the same time? Do I need ndwrapper (or whatever it's called)? 

THANKS!!! I've run out of bright ideas on these.

---

### Post by mlissner on 2007-01-07
OK. After being threatened on the IRC with having to compile a custom kernel, I found a link that told me to install the restricted kernel modules via synaptic. 

Once that was done, all was well with wireless under the smp kernel. Fantastic.

---

