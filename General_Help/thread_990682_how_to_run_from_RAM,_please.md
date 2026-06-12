---
title: "how to run from RAM, please?"
date: 2008-11-23
forum: General Help
---

### Post by tenmoi on 2008-11-23
I have been searching for a howto run from RAM but there is none. Can anyone please write one. 
RAM is so cheap today that we can run ubuntu from RAM to boot up its performance.

THanks.

---

### Post by swoody on 2008-11-24
Are you talking about running the entire system from RAM instead of a harddrive? As far as I know that's impossible due to the fact that RAM is volatile - it will lose any information stored in it when they coputer is restarted. You can have a solid-state hard drive that acts more like ram than a traditional hard drive, but that's a different question, and that is very easy by just replacing a hard-drive.

If you're talking about making your computer faster by making programs use RAM instead of the swap files on a computer, you can do that by decreasing the swappiness - the amount your computer uses your hard disk swap files instead of RAM. Try this:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Maybe if you can clarify what you meant I can help you out more :)

---

### Post by Portmanteaufu on 2008-11-24
> **woody86 said:**
> Are you talking about running the entire system from RAM instead of a harddrive? As far as I know that's impossible due to the fact that RAM is volatile - it will lose any information stored in it when they coputer is restarted. You can have a solid-state hard drive that acts more like ram than a traditional hard drive, but that's a different question, and that is very easy by just replacing a hard-drive.

If you're talking about making your computer faster by making programs use RAM instead of the swap files on a computer, you can do that by decreasing the swappiness - the amount your computer uses your hard disk swap files instead of RAM. Try this:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Maybe if you can clarify what you meant I can help you out more :)

I think the OP is referring to running the way that Puppy Linux does. Because Puppy Linux is so tiny, it's loaded entirely into RAM at boot time. All your documents, etc can still be saved to mounted drives but the OS itself is running from RAM. It's really snappy, I agree. I don't know how much RAM it would take to get an OS as big as Ubuntu to do the same, however.

---

### Post by Skripka on 2008-11-24
> **Portmanteaufu said:**
> I think the OP is referring to running the way that Puppy Linux does. Because Puppy Linux is so tiny, it's loaded entirely into RAM at boot time. All your documents, etc can still be saved to mounted drives but the OS itself is running from RAM. It's really snappy, I agree. I don't know how much RAM it would take to get an OS as big as Ubuntu to do the same, however.

Unless the OP has 4+GB of RAM I doubt it would work...and even then boot time would really suffer as you have a few GB of system data to put into RAM

---

### Post by Oliver.BS on 2008-11-24
Well even if he had 4+gb wouldn't it be pointless because he would loose all his settings once he restarted ?

---

### Post by Skripka on 2008-11-24
> **Oliver.BS said:**
> Well even if he had 4+gb wouldn't it be pointless because he would loose all his settings once he restarted ?

If Puppy Linux loads as Portmanteaufu says, I'd wager there's a way around that issue.....but Puppy Linux or Damn Small Linux are far smaller than *buntu-so there is performance to be gained.

---

### Post by Oliver.BS on 2008-11-24
Is puppy Linux what you would put on these new Web Books then such as the dell mini ? with a tiny HDD

---

### Post by Portmanteaufu on 2008-11-24
> **Oliver.BS said:**
> Is puppy Linux what you would put on these new Web Books then such as the dell mini ? with a tiny HDD

You could, sure. I don't know how strong Puppy's wireless card detection is, though -- you'd have to ask someone more knowledgeable. As a rule, I think a lot of people look to Puppy Linux when they're trying to use an old computer with hardware that would struggle with modern, full-sized operating systems.

Its system requirements (from the distribution's web site) are: 

CPU : Pentium 166MMX
RAM : 128 MB physical RAM for releases since version 1.0.2 or failing that a Linux swap file and/or swap partition is required for all included applications to run; 64 MB for releases previous to 1.0.2
Hard Drive : None
CDROM : 20x and up

Speaking from experience, it is possible to create a persistent installation of Puppy. All your settings / documents can be saved normally.

---

### Post by eeeek on 2008-11-24
Damn Small Linux has some pretty good documentation on running an OS from RAM. I've tried it and it is pretty cool. An old computer can be just as fast as you can click. But to my knowledge the "toram" boot code will only work on those smaller distros. 

You might try installing Ubuntu to a USB flash drive - that might boost performance. Never tried it, but I've read up on it some.

Theoretically, you do lose your settings on a "toram" option, but that's why you have a few files saved to the HDD under this setup.

---

### Post by jerrykenny on 2008-11-24
I read last year ( i think) about ubuntu pre-installed machines with RAM only . . . but they were thin-clients

---

### Post by snowpine on 2008-11-24
Ubuntu sort of does run from ram already. It aggressively caches applications and data to ram as needed. This is why your ram usage keeps going up over time, even if you quit out of applications. However, it would be silly to pre-cache everything to ram, as a typical Ubuntu install uses at least 4gb of hard drive space; not only would it fill up your ram, but it would increase your boot time as all that data (which you aren't necessarily even going to use) gets copied over from the hard drive to the ram. 

ps The average USB device is much slower than the average internal hard drive. No performance boost there!

---

### Post by richardh9936 on 2009-02-22
Thanks for this discussion.  I'm also interested in performance-boosting options.... and I've used DSL and other micro-distros with TORAM to put the kernel into RAM during boot, as a LILO or GRUB boot option.  

Does Linux keep its kernel in RAM?  (I suspect other OS pages some of itself out....)

I'll look for specific performance tips, too.

---

### Post by richardh9936 on 2009-02-22
...and true to form, the Ubuntu community has provided the answer already:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by mcduck on 2009-02-22
The kernel is loaded into RAM and is never moved out of there. Actually you can even calculate the size of the kernel if you look at how much RAM you have available (since the memory area used by kernel isn't even calculated as available memory.)

For example I have 2GB of RAM (2048MB). When I check the amount of available RAM in any program they will tell that I have 2024MB of RAM. The missing 24MB is the amount of RAM kernel takes.

Anyway, you probably wouldn't want to try loading your full Ubuntu install into RAM, it's too large for that and this way of doing things only really works for a lot smaller distros. What you *can* do instead is use preloading, which loads the programs you want into RAM during the boot process. You'll find plenty of threads and some rather good HowTo:s for preload in these forums.

(swappines can be tuned, but since if you have a lot of RAM your swap is hardly used at all anyway, so adjusting swappines won't have any noticeable effect)

---

### Post by DeMus on 2009-02-22
> **mcduck said:**
> 
(swappines can be tuned, but since if you have a lot of RAM your swap is hardly used at all anyway, so adjusting swappines won't have any noticeable effect)

Can you tell me why my system uses swap memory even though I set swappiness to zero?

Entry in /etc/sysctl.conf:
#No swapfile
vm.swappiness = 0

I have 4GB ram and though with setting vm.swappiness to zero I would use only my physical ram memory.

---

### Post by mcduck on 2009-02-22
It's a actually a bit more complicated than this, swappiness is just one of the parameters used when determining if and when swap should be used.

*distress* is a value telling how much troubles kernel is having freeing memory. it starts from zero and grows up to 100 based on how many attempts the kernel needs to do until it's able to allocate memory for something.

*mapped_ratio* is approximate percentage of how much of the system's total memory is mapped.

*vm_swappiness* is a parameter used to configure how much kernel should prefer swapping versus dropping cached data.

The actual swap usage, *swap_tendency* is then calculated like this:
*swap_tendency* = *mapped_ratio*/2 + *distress* + *vm_swappiness*

The result is that even with swappiness set to 0, the kernel will still use swap if it needs to (if the *distress* value gets high enough). It's just less likely to do that when compared to having swappiness set to 100.

Anyway, little swapping isn't actually that bad (at least when it comes to performance, of course if you are thinking about saving battery life on a laptop or reducing disk usage on SSD drives it's a different thing).

But since you have that much free memory I don't think the kernel should be using any swap on normal use, even with the default swappiness of 60 it shouldn't do that. But in your screenshot you seem to have quite a bit of CPU load, so using swap could be related to whatever you are doing at the time.

---

### Post by OracleNix on 2009-02-26
If you wish to have your machine run like grease lightening using only ram without touch the hard drive then just netboot your machine using pxe boot or something such.  In google search & go to "ubuntu documentation", then search on pxe or thin client...

Alternatively you may purchase a pricey solid state hard drive ;)

Hope this helps
G

---

