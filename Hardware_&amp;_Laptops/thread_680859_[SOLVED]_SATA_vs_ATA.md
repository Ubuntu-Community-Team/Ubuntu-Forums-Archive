---
title: "[SOLVED] SATA vs ATA"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by nunnst on 2008-01-28
I have an old PIIII desktop PC that I have installed gutsy on.  Its working very well (no gnome - openbox).  My question is this.  Why is my IDE disk drive (multi partitions) showing up as sda when it should be hda.  If I understand correctly "sd" devices are either SATA or SCSI.  This drive is just a plain old ATA (IDE) drive with the typical wide ribbon cable connect into the MOBO.

Why does this matter to me?  Because I intend to build a custom kernel for this old machine. I want this custom kernel because there is no need to load all the modules that the ubuntu scripts are loading and therefore using my limited memory.

Any help is greatly appreciated.

---

### Post by rufius on 2008-01-28
I think its an Ubuntu specific thing. They decided to go with a standard convention of naming the disks.

As for loading modules, why not modify the modprobe and blacklist scripts? Or you could build a kernel from the src deb.

Hope that helps :)

---

### Post by jeffus_il on 2008-01-28
> **Re: HDA change to SDA confusion**             
                                                              Inside the kernel, the method for accessing ide harddisks is changing, as the sata driver can now handle pata drives as well, and on some systems does alreadyfrom:
[http://ubuntuforums.org/showthread.php?t=532823](http://ubuntuforums.org/showthread.php?t=532823)

so don't worry about hda/sda
I once used to build custom kernels, I even eliminated modules, and really saved nothing, all modules are not loaded, they are loaded as needed on demand, therefore you do not waste memory, also building a kernel makes upgrading a big hassle, With the prebuilt kernels, I sometimes don't notice that my kernel has been replaced ...

---

### Post by nunnst on 2008-01-28
Thanks,

Yeah I did a little more googling and found out about the "libata" driver replacing the older generic IDE drivers and thus my EDI (aka ATA) drive is now seen as SCSI.  Kinda strange and confusing.

Anyway, I don't really understand the module stuff, but do think some modules are loading that I do not want, eg., ACPI support.   Why on earth would I need ACPI on a desktop - no battery!  OK, I guess if you're a greenie it might reduce global warming by reducing energy consumption, however, I'm just a bit more concerned about my limited 256MB of RAM !

Thanks again for the quick responses!

---

### Post by jeffus_il on 2008-01-28
Modules were implemented to save memory, if you don't need them you, they won't be loaded. ACPI is used for things other than the battery, like powering down the computer and more.

---

### Post by nunnst on 2008-01-28
I think I need to disagree with you Jeff.  ;-)

Modules were implemented mainly to enable ease of set-up, installation, upgrading.  They actually don't save memory.  If support is compiled into the kernel for say ATA or used as a module, your still using approx the same amount of memory (actually a bit more for the modules)  The savings come into play for modules that can load and unload upon demand.  I have no need for ACPI - for battery purposes or other purposes such as CPU freq adjustment, hibernate/suspend. temp monitoring, etc. 

Using a fully modularized kernel (eg., ubuntu images) results in slower boot-ups also.  As I only have my PC on when I'm actually using it, I want fast boot-ups, because I boot-up at least two times per day.  

Well, thats my two cents. I could be wrong, but I don't think I am.

Steve

---

### Post by jeffus_il on 2008-01-29
Modules are loaded when necessary, a kernel with all the possibilities built in is much larger, an unused module is not read into memory, so does not use primary memory. Do you know what the size of your kernel is in memory as a percentage of you total primary memory? How much memory would you save not loading the ACPI module, check it out and post it. In terms of a percentage of your total memory as well. Also it would be interesting to measure the load time of the modules, You could do a boot without loading modules and check the difference in seconds, you may be surprised, and decide that the effort of building, maintaining and debugging your custom kernel is not worthwhile.  In short seeing the difference in seconds or Mb may change your thinking.
A much easier solution is to use a small distro like DSL or Puppy.

---

