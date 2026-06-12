---
title: "SMP mptable: bad signature [0x0]!"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Bill_Baroud on 2005-04-15
Hi,

I'm newbie with debian, but I used Mandrake an Red Hat 2/3 years ago, and I have decided to install kubuntu hoary 5.04 on Packard Bell easy note G1345, celeron M 340 1.5GHz

I've downloaded the file *Intel x86 install CD* [here](http://releases.ubuntu.com/kubuntu/hoary/), burned it, the installation works well (but I had to boot linux=vga771, and network setup failed)

After install, at the boot, in first I see that:
Apr 15 14:19:14 kernel: SMP mptable: bad signature [0x0]!
Apr 15 14:19:14 kernel: BIOS bug, MP table errors detected!...
Apr 15 14:19:14 kernel: ... disabling SMP support. (tell your hw vendor)

Then no errors, everything is [ok], but system crashes at "Mounting Local FileSystem" 

Syslog [here](http://membres.lycos.fr/thepitou/syslog_Pit.TXT), if it can help you
I've look for this error on forums, but I've found few informations, and no solutions  ](*,) 


Thanks

---

### Post by Bill_Baroud on 2005-04-18
No idea ?

Nobody has seen that, before ?

I have tried a knoppix, and same error message  ](*,) 

Help me, please  :cry:

---

### Post by alastair on 2005-04-18
Check your BIOS - is "hyperthreading" enabled? Maybe your PC does not support it? A guess.

For the later "mount" problems - show the logs.

---

### Post by Bill_Baroud on 2005-04-19
First, thanx for your reply (I'm not alone !! \\:D/ )


I have look the BIOS, no HT options (processor is a celeron), but perhaps the MB can support pentium HT too, I will ask in PB forum.

For the mount problems, are they a consequence of the SMP error, or it's an independant problem ?
I have a PB recover partition, the first one on my disk, can this do trouble ?


Thx for others future advices ;)

---

### Post by alastair on 2005-04-19
I doubt the mounting problem is related. But you should show some logs relevant to the mounting issue :

/var/log/syslog

also - your /etc/fstab file.

---

### Post by Bill_Baroud on 2005-04-21
I think there is no HT on my laptop, the SMP error depends on something other  ](*,) 

The link of syslog is in my first post, if somebody can explain me what is wrong.

hdd has being formated yesterday, so fstab files no more available  :-# 

[Palladium &HP/PB (in french)](http://www.presence-pc.com/actualite/pc-tatouage-palladium-9527/) : what do you think of that ? Have anybody more informations ?

---

### Post by alastair on 2005-04-21
Well .... it says :

Apr 15 14:19:14 kernel: BIOS bug, MP table errors detected!...

So see if the manufacturer has a BIOS update.

---

### Post by Bill_Baroud on 2005-04-25
It also says "Apr 15 14:19:14 kernel: ... disabling SMP support. (tell your hw vendor)"
So I think SMP is not the problem.

I dont want to flash BIOS, too risked, I need this laptop, I have installed kubuntu on my desktop, perfect, laptop will run windows, that's all.

Thx for your help, I will take care of packard bell for my next laptop  :???:

---

### Post by Bill_Baroud on 2005-04-25
I just found a guy on PB forum, who has a G1320 laptop, same as my, only processor @1.3, and same SMP error with warty live CD (but then it works)

This guy uses Suse, without problems 

[http://forum.packardbell.com/fr/viewtopic.php?p=156103#156103 (fr)](http://forum.packardbell.com/fr/viewtopic.php?p=156103#156103) 

 ](*,)

---

### Post by basdala on 2005-06-24
Hi everybody,
I'm using a Packard Bell Easynote same as you, and I'm having the very same problem: SMP Table error and then Ubuntu hangs when setting up LVM volume groups.

Anybody found a solution? :?

---

### Post by basdala on 2005-07-26
Ok people! After messing SOOOOO MONTHS with this problem, I've found a solution.

Just add this to the GRUB command line:

acpi=off

Although the SMP BIOS table error remains, it will success when setting up LVM volume groups, where it hanged before.

Now I have my Packard Bell Easynote running Hoary Hedgehog without problems. Hope this helps!

---

### Post by 1an on 2006-08-13
Have same issue with my Dell Dimension 8100.  P4 1.4.... I don't believe it has any HT capabilities either...

---

### Post by brdoco on 2006-10-18
> **1an said:**
> Have same issue with my Dell Dimension 8100.  P4 1.4.... I don't believe it has any HT capabilities either...

I'm trying to install on my 8100 as well, and getting this same error.  Have you gotten past this?

---

### Post by mslonik on 2006-10-29
Hi!

Exactly the same problem here! I did manual apt-get upgrade from Kubuntu 6.06 to 6.10. Laptop: Aristo 2600, model: D40ES.

After boot-up the following lines occurs:
17179569 SMP mptable: bad signature [0x0]!
17179569 BIOS bug, MP table errors detected!
17179569 ...disabling SMP support (tell your hw vendor).

Regards,
Maciej S&#322;ojewski (mslonik)

---

### Post by zibi on 2007-01-28
There is an old thread on this topic 
 on the LKML forum
It is not resolutive at all but... 
[http://lkml.org/lkml/2003/11/13/31](http://lkml.org/lkml/2003/11/13/31)

---

### Post by sly_hobbit on 2007-08-14
I basically have the same problem. Originally though, when I tried to boot I got some sort of "DSDT not found" After much research I found that this was an ACPI problem. SO, what I did was turned off ALL advanced power options/support in my bios, (fortunately im on a desktop so I can get away with that) and I also added "pci=acpi off" to grub. NOW I always get this at boot:

SMP MPTABLE: No processors registered
BIOS Bug, MP table errors detected
...Disabling SMP support (Tell your hardware vendor)

Most of the time though, it skips over this and boots, other times it hangs there and I have to reboot. Would like to fix the problem if any1 finds a solution. Ive been on linux for about 2 weeks now and have learned a ton and am really enjoying myself.

---

### Post by bobbybbb on 2008-02-04
> **Bill_Baroud said:**
> Hi,

I'm newbie with debian, but I used Mandrake an Red Hat 2/3 years ago, and I have decided to install kubuntu hoary 5.04 on Packard Bell easy note G1345, celeron M 340 1.5GHz

I've downloaded the file *Intel x86 install CD* [here](http://releases.ubuntu.com/kubuntu/hoary/), burned it, the installation works well (but I had to boot linux=vga771, and network setup failed)

After install, at the boot, in first I see that:
Apr 15 14:19:14 kernel: SMP mptable: bad signature [0x0]!
Apr 15 14:19:14 kernel: BIOS bug, MP table errors detected!...
Apr 15 14:19:14 kernel: ... disabling SMP support. (tell your hw vendor)

Then no errors, everything is [ok], but system crashes at "Mounting Local FileSystem" 

Syslog [here](http://membres.lycos.fr/thepitou/syslog_Pit.TXT), if it can help you
I've look for this error on forums, but I've found few informations, and no solutions  ](*,) 


Thanks

Hi, I too experienced the same problem, I had tried everything but to no avail. So this morning I did the unthinkable, I went into my BIOS and enabled Hyper Threading Technology and saved my BIOS/CMOS settings. And guess what? The error disappeared and that's all it took, just enable HT and it should work you as it did for me.

Cheers
Bob

---

### Post by nalberto on 2008-03-05
Hi,
I have the exact same problem with an Acer Laptop Travelmate 244.

System starts with that error 

SMP mptable: bad signatue [0x0]!
BIOS bug, MP table errors detected!...
...disabling SMP support. (tell your hw vendor)

Then systems works quite slowly and eventualy crashes.
I can't enable HT in the bios because it doesn't even show that option.

I am keen to get Ubuntu going but I am stuck there and feel like I will need to reinstall Windows....

Please help

---

