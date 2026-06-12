---
title: "getting a fast hard drive that my motherboard will support"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by fakie_flip on 2006-07-26
I am going to buy a bigger and hopefully faster hard drive for my mainboard. I have looked in the owner's manual, and could not find out if my mainboard supports sata2 hard drives or regular sata hard drives or any other types of hard drives besides pata. Also I would like to know my bus speed and what is the best hard drive for my computer without getting one that is a whole lot faster than my bus speed because then I am wasting lots of money. Could you please tell me what hard drive would be good for my computer when you know what my bus speed is and what types of hard drives my mainboard can support? Thank you. I dont know what type of socket I have or what the serial number is. Here is some information the Linux kernel is giving me about the motherboard and cpu. I have a K7S5A PRO REV: 5.0 mainboard. Here is the owner's manual I found for it. I hope it is the right one. [http://chris1.myftp.org/k7s5apro50eng.pdf](http://chris1.myftp.org/k7s5apro50eng.pdf)

chris@ubuntu:~$ cat /proc/cpuinfo
processor : 0
vendor_id : AuthenticAMD
cpu family : 6
model : 8
model name : AMD Athlon(tm) XP 1800+
stepping : 1
cpu MHz : 1493.759
cache size : 256 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips : 2988.29

chris@ubuntu:~$

---

### Post by bigken on 2006-07-26
sata2 is backward comptible with sata1 by jumper settings ;)

your board dose not support sata but you could buy a pci sata card

---

### Post by cracker on 2006-07-26
Both SATA standards are interchangable, the only time you need to change a jumper is with certain SATA2 drives using SATA1 ccontrollers. Most of the time, they will 'just work' automatically. 
Your motherboard does not support SATA. You will need an SATA controller. I recommend this card: 
[http://www.newegg.com/Product/Product.asp?Item=N82E16816102062](http://www.newegg.com/Product/Product.asp?Item=N82E16816102062)
Or, if you're looking for hardware RAID, this card:
[http://www.newegg.com/Product/Product.asp?Item=N82E16816102060](http://www.newegg.com/Product/Product.asp?Item=N82E16816102060)
Yes, they're a tad expensive, but they are quality products that are known to work under Linux, and don't have any fakeRAID to deal with.

---

### Post by mkw87 on 2006-07-26
As cool as sata sounds, the benefits of increased speed are mostly only on paper.  I have a fairly new Sata2 Western Digital, and I get 133 mb/s transfer speed, where as my IDE drive gets 110-115 mb/s or so.  If you run RAID 0 then sata is beneficial (or any raid, but raid 0 specifically for speed), other than that IDE seems to still be satisfactory.  However, a pci sata controller card should be that much, but as always make sure it wont be too big a hassle to install/use it with ubuntu (or any operating system you use).  As for hardware raid, most people nowadays use software raid as its not only SLIGHTLY faster in some cases, but if something goes bad you stand a lot less of a chance of losing data (if in raid 1 or other backup raid).

Just make sure the hard drive you get is a 7200 rpm hard drive or more and you'll be happy with it.  You can always check out ebay too if you are looking to save a few bucks, I was looking yesterday and they had some nice HD's on there.

---

### Post by cracker on 2006-07-26
I have to disagree on the speed factor--while the numbers aren't that much better, I find the 'feel' to be 3-4 times faster. When I upgraded from a 7200RPM 8MB cache IDE drive to a 7200RPM 16MB cache SATA2 drive, the difference was phenominal. OS loading times were quartered, without reinstalling.

---

### Post by fakie_flip on 2006-07-27
Isn't sata2 a whole lot faster than pci? I do not mean pci express. What's the point of having something a whole lot faster than what can be used? I don't want to get a sata2 hard drive if my bus speed is only as fast as IDE. I'd be wasting money. I am a full time college student, so I do not have a whole lot of extra money to use unfortunately. I would want to get a sata2 hard drive that comes with a controller if my bus speed is fast enough to use the hard drive at the hard drive's full speed because I can get better deals on those. I do not plan on running raid untill I get at least 4 hard drives. What is the jumper that people are speaking of?

---

### Post by bigken on 2006-07-28
the jumper setting is if you have a sata 1 on your motherboard and you have a sata 2 HDD ie western digital you would set a jumper over pin 3 & 4 or 5 & 6 to downgrade the HDD to sata 1 if I were you I would be looking at buying sata 2 with a compatible pci card so when you upgrade 
your mobo you will already have the drives :D

---

### Post by fakie_flip on 2006-07-28
Is anyone going to answer my questions?

---

### Post by cracker on 2006-07-29
Your PCI bus has almost nothing to do with how fast of a hard drive you get.  SATA II is twice as fast as SATA I, but it really doesn't matter because hard drives can't even utilize the full capability of SATA I. Really, any SATA drive is going to be much faster than an IDE drive. Your PCI bus is most likely not going to be the bottleneck of the system. The reason is that there is more information transferred between the controller and the drive than there is between the controller and the PCI bus. This is especially true if you have multiple drives.

---

### Post by fakie_flip on 2006-07-30
I went to newegg.com to look for hard drives to buy. I am still not sure what is best for me. I can't buy the best because then I won't have money left over to buy other things. Can I buy a sata2 hdd that comes with a controller? Is it a better deal to buy the sata2 hdd with the controller? I know I will be needing it because my mobo does not support it. I am confused about which hard drives are sata2. I went to newegg.com and I have these choices: 

Interface

    * CF+ Type II (2)
    * IDE Ultra ATA100 (43)

	

    * IDE Ultra ATA133 (12)
    * SATA 3.0Gb/s (51)

	

    * SCSI Ultra320 68pin (22)
    * SCSI Ultra320 80pin (21)

	

    * Serial ATA150 (26)
    * Serial Attached SCSI (SAS) (5)

I don't see sata2 there. Which one is sata2? How much more expensive are sata2 hdd than ide?

---

### Post by bigken on 2006-08-01
SATA 3GB/s is sata 2

---

### Post by fakie_flip on 2006-08-08
I noticed some people were trying to look at the manual for my motherboard, and were getting errors because the file was not there. I put it back on the server. Here is a link to it.

[http://chris1.myftp.org/k7s5apro50eng.pdf](http://chris1.myftp.org/k7s5apro50eng.pdf)

---

