---
title: "GRUB setup for hardy &amp; intrepid on separate drives"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by getglenn on 2009-02-10
g'day

i have hardy installed on hda and installed intrepid on hdc...

however, the boot menu doesnt reflect the change when a kernel is updated...

i have read many posts re dual booting etc but most dont describe my exact configuration and i cant my head around the grub options mentioned in the posts and in the man pages...

i'm hoping someone can point me in the right direction

regards
glenn

---

### Post by Pumalite on 2009-02-10
Have you tried changing the boot order in BIOS(HH)?

---

### Post by getglenn on 2009-02-10
thankyou for the reply pumalite... but the problem isnt with booting the drives, but with the menu.lst not being updated with the new kernel for each drive

my post was a bit vague [and some details were incorrect] so here are the correct ones...

i have Ubuntu 8.10 Intrepid on 2 separate hard drives...

the first drive [master - ide1] is the one i actually use
    [with custom settings and all the software i like]

the second drive [slave - ide2] is a default install with updates

part of my confusion comes from the fact that...

1. the grub menu.lst uses UUID xxxxx-xxx-xxxx-xxxx to identify a drive in one area
2. hdx.x in another

3. device.map uses hdx AND /dev/sdx and
4. gparted uses sdx

i will persevere, but have to go now so will try again tomorrow

---

### Post by Elfy on 2009-02-10
I found that if you didn't want to add the update kenels yourself - only one will update with update-grub then chainload

I have jaunty and intrepid and also xubuntu at the moment - I let jaunty install it's grub so that will now be updated with kernel changes.

I then reinstalled grub for intrepid and xubuntu to their own partitions - in my case it's on sda2 and sdc4 then I added these to my jaunty menu list - they all now are updated if and when there is an update when I'm in them

title 		---Intrepid---
root		(hd0,1)
chainloader	+1

title		---Xubuntu
root		(hd2,3)
chainloader	+1

---

### Post by lha on 2009-02-10
Easiest solution is to add
```

title Ubuntu on hdc
configfile (hd2,0)/boot/grub/grub.conf

```
to menu.lst, assuming that the other Ubuntu is installed on hdc1. If it installed somewhere else, just change the (hd2,0) to suit your configuration.

---

