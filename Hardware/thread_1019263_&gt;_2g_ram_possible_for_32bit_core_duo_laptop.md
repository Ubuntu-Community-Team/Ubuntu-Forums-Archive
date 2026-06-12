---
title: "&gt; 2g ram possible for 32bit core duo laptop?"
date: 2008-12-22
forum: Hardware
---

### Post by stairwayoflight on 2008-12-22
Hello,

I have read some conflicting information about the maximum amount of ram which can be used in 32 bit computers (some of it coming from other forums' messages regarding Macs). One source said technically the maximum is 4 GiB, but the computer uses up some of those values to address hardware, etc., making the usable portion more like 3.5 GiB.

My vendor says my laptop can use a maximum of 2 GiB. Is this an example of a vendor playing it safe, or is it likely to be the maximum addressable amount of ram?

If so, what is the typical amount of ram available to the kernel in Ubuntu when 4 GiB is installed on a machine with my processor?

(I have a 32-bit Core Duo laptop, not a Core 2 Duo. It is an HP dv2432ca. There are 2 dimm slots, both have a module installed (looks like 1 GiB each).)

Thanks, Stairway

---

### Post by whalebus on 2008-12-23
For your hp, the maximum is limited by the motherboard's design.  I've read that 3GB is the maximum for a 32-bit system.  Maybe a hardware engineer-type person can give some details?

---

### Post by prshah on 2008-12-23
> **stairwayoflight said:**
> One source said technically the maximum is 4 GiB, but the computer uses up some of those values to address hardware, etc., making the usable portion more like 3.5 GiB.

Quite right; to be accurate, it's 3.2 GiB. The rest of the memory will be ignored, even if you put in 4+ GiB (provided the motherboard supports it)

> **stairwayoflight said:**
> My vendor says my laptop can use a maximum of 2 GiB. Is this an example of a vendor playing it safe, or is it likely to be the maximum addressable amount of ram?

This is a tricky one. Usually, the vendor's maximum addressable RAM is based on information about RAM clips available at the production time of the machine, and is usually wrong at the current time. 

For example, in my Fujitsu LifeBook P5010, the stated maximum is 1x512Mb, but I've shoved in a 1x1Gb and it works fine. (There is only one slot).

Another example, on an old Compaq laptop, the stated maximum is 256Mb RAM ( 2x128 ), but I've successfully used 1x128, 1x256=384Mb (but I needed a BIOS update).

My suggestion; try before you buy; plug in the new RAM clips, check if the memory is recognized in the BIOS. If the BIOS recognizes the memory, you are good to go; though as mentioned before, a 32bit OS will only access upto 3.2GiB of RAM.

Given that your laptop is an HP, I'd guess that you can successfully use 2x2Gb without a problem, but you should first update the BIOS, before trying to change the RAM.

---

### Post by sdennie on 2008-12-23
> **prshah said:**
> Quite right; to be accurate, it's 3.2 GiB. The rest of the memory will be ignored, even if you put in 4+ GiB (provided the motherboard supports it)


The number will actually vary from machine to machine but, yes, generally it's between 3GB and 3.5GB.  See: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

I actually had a particularly bad experience with my last laptop (Toshiba P105) and, though various sources indicated that it would support 4GB of RAM and the BIOS would see all 4GB, the machine wouldn't boot properly with more than 2GB (tried various combinations of sticks) so, I would be certain that you can return any potentially unusable RAM before you buy it.

---

### Post by hanbin973 on 2008-12-23
if you use a server kernel, also 32bit system can use 4GB ram

---

### Post by stairwayoflight on 2008-12-23
Hah!

I found a 2 GiB module, replaced one of the 1 GiB modules, and lookee here:

```
$ cat /proc/meminfo |grep MemTotal
MemTotal:      3102604 kB
```

If its true that it could only use 3.2 GiB, then a 2nd 2 GiB module will only yield 1/10th of its value more than what I have now. Perhaps its not worth it.

Now, to upgrade the processor... just kidding ;-)

Thanks everyone.

Stairway

---

### Post by Npl on 2008-12-23
you should be able to use 64GB since core duo supports Physical Address Extension (PAE).. and AFAIK Linux supports it too. Might need to be activated in the kernel somehow, and maybe the Motherboard needs to allow it aswell. Dont have first-hand experience with it.

Its use is restricted however, its not the same as using 64GB wih a 64bit Processor.

---

### Post by stairwayoflight on 2008-12-23
Hmm,

I do some physics modeling, and intend to do some more computationally intensive work in the future.

Is there an easy way to test if a PAE-enabled kernel will enable > 4 GiB of ram on my laptop?

(cat /proc/cpuinfo reports pae support)

Stairway

---

### Post by sdennie on 2008-12-23
> **stairwayoflight said:**
> Hmm,

I do some physics modeling, and intend to do some more computationally intensive work in the future.

Is there an easy way to test if a PAE-enabled kernel will enable > 4 GiB of ram on my laptop?

(cat /proc/cpuinfo reports pae support)

Stairway

The only way to be 100% sure is to test it.  Though, in your case, 64bit might be worth at least trying because CPU bound problems often get a noticeably speedup from moving to the AMD64 architecture.

---

### Post by stchman on 2008-12-23
> **stairwayoflight said:**
> Hello,

I have read some conflicting information about the maximum amount of ram which can be used in 32 bit computers (some of it coming from other forums' messages regarding Macs). One source said technically the maximum is 4 GiB, but the computer uses up some of those values to address hardware, etc., making the usable portion more like 3.5 GiB.

My vendor says my laptop can use a maximum of 2 GiB. Is this an example of a vendor playing it safe, or is it likely to be the maximum addressable amount of ram?

If so, what is the typical amount of ram available to the kernel in Ubuntu when 4 GiB is installed on a machine with my processor?

(I have a 32-bit Core Duo laptop, not a Core 2 Duo. It is an HP dv2432ca. There are 2 dimm slots, both have a module installed (looks like 1 GiB each).)

Thanks, Stairway

The maximum theoretical amount of RAM you can use with a 32 bit OS is 4GB as 2^32 is 4GB.

Now your laptop mobo limitation might be 2GB.  You can try 4GB of RAM to see if your laptop will recognize it.  There might be a BIOS flash that will let you use more than 2GB.

---

### Post by stairwayoflight on 2008-12-23
> **vor said:**
> The only way to be 100% sure is to test it.  Though, in your case, 64bit might be worth at least trying because CPU bound problems often get a noticeably speedup from moving to the AMD64 architecture.

Ahh, I don't think I can use AMD64 with a 32 bit Core Duo though. Earlier you mentioned PAE as an option to use more ram; did you think I had a 64 bit processor?

Its moot anyways. For the price of the ram I'd get a new laptop.

---

