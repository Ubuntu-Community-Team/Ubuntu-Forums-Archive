---
title: "Am I crazy? VAIO 505G and Ubuntu..."
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by pohaku on 2006-12-23
Hi all,
Here is what I hope to do: I have inherited a really nice Sony VAIO PCG-505G that is at the end of it's miserable Windows lifecycle. I want to resurrect it for a son leaving for college by installing Ubuntu on it. It has 96mb RAM (maxed out!), a 2gb HDD (which I am planning to upgrade to 40gb), the Sony external floppy drive, the Sony port replicator, and the Sony PCGA-CD5 external cd-rom drive. I have tried unsuccessfully to install the alternate Ubuntu 6.10 distro - I can boot from the cd-rom just fine and start the install from the menu, but at a certain point it tries to detect the cd-rom and fails. My complete lack of any linux experience whatsoever doesn't help! My questions are: 1) Should I even try this? 2) If so, does anyone know what I need to do to get Ubuntu to see the cd-rom? 3) If Ubuntu isn't a good idea, does anyone have other distros to suggest?

Many thanks!

](*,)

---

### Post by tdwester on 2006-12-23
You may want to try xubuntu instead. Ubuntu needs at least 128 mb of and xubuntu is a very light weight desktop.

---

### Post by pohaku on 2006-12-23
> **tdwester said:**
> You may want to try xubuntu instead. Ubuntu needs at least 128 mb of and xubuntu is a very light weight desktop.


Thank you for the advice - I've downloaded the xubuntu 6.10 alternate image and I'm still having the same cdrom recognition issues. I'll keep trying!

---

### Post by pohaku on 2007-01-02
](*,) 

I haven't had any luck with this install as yet - has anyone else out there had experience with the Sony PCGA-CD5 external cd-rom and Xubuntu (or any other flavor)? I have found a couple of references on the web to disabling the PCMCIA support during an install of RedHat 5.2 and reassigning the input/ouput addresses that the cd-rom uses, but nothing about doing it with Xubuntu. Does anyone have any ideas on how I could accomplish this via a command line or some alternate method? Any help would be greatly appreciated!

---

### Post by pohaku on 2007-01-05
:p 

I was lurking in a Yahoo Tech Group ([http://tech.groups.yahoo.com/group/sony505/message/19733](http://tech.groups.yahoo.com/group/sony505/message/19733)) and found out how to get my 505g's cd-rom to work! Boot using the alternate cd for xubuntu 6.10. At the main installation menu press F6 for "More Options" and at the front of the boot command line add "ide2=0x180,0x386 pci=off". This string 1) reassigns the port the kernel looks to for the cd-rom AND 2) (very importantly) turns off the pcmcia services so that the kernel can just talk to the cd-rom directly. So far the install is going great! Hope this helps anyone who has had a similar issue.

---

