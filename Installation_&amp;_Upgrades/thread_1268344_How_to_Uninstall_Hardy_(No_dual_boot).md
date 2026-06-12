---
title: "How to Uninstall Hardy (No dual boot)"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2009-09-16
Hi,
I have tried Ubuntu and I like it very much, but I have to uninstall it from my work notebook (I will still have at home :)). 
I am not operating in dual boot mode, I only have Ubuntu installed. I wonder if there is an easy way to get rid of it and install XP back.

I am a newbie.

Thanks for your help.

PS: I made a mistake in the title and cannot edit it. I am not using Hardy, but Ubuntu 9.04 Jaunty Jackalope; that is the one I need to uninstall. Thanks.

---

### Post by earthpigg on 2009-09-16
> I wonder if there is an easy way to get rid of it and install XP back.

i would think it'd be as simple as popping in a windows xp install cd in and reboot.

if that doesn't work...

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by earthpigg on 2009-09-16
ugh, disregard that link above.

pop in an ubuntu live cd.

start gparted.

delete all partitions.

done, ubuntu is uninstalled.

---

### Post by Pablo W on 2009-09-18
Thanks, earthpigg. I have installed gparted as you recommended. When I want to run it, I get message "you need root privilegies to run gparted".

Any suggestion?

Thanks!

---

### Post by Elfy on 2009-09-18
start the livecd and run gparted from the system admin menu - you can't run gparted on a running ubuntu and then uninstall it ;)

you will be able to delete the linux partitions using the livecd - ater you have done that boot your XP dsic and use it to fix the boot otherwise grub will still be looking for the ubuntu install

---

### Post by Pablo W on 2009-09-18
Thanks, forestpixie. I'm one step beyond now. I can run Gparted from the live CD, but when I right-click on the partitions, the option "delete" is disabled. I have never used Gparted before. Could you please guide me?

I have tried to attach a link to a print of the Gparted screen as  I see it.
[http://docs.google.com/View?id=dfdzc3xg_7997mb6kgd](http://docs.google.com/View?id=dfdzc3xg_7997mb6kgd)

Thanks for your help.

---

### Post by earthpigg on 2009-09-18
> but when I right-click on the partitions, the option "delete" is disabled.

right click and select *unmount*, and then try it after unmounting all of them :D

---

### Post by raymondh on 2009-09-18
> **Pablo W said:**
> Thanks, forestpixie. I'm one step beyond now. I can run Gparted from the live CD, but when I right-click on the partitions, the option "delete" is disabled. I have never used Gparted before. Could you please guide me?

I have tried to attach a link to a print of the Gparted screen as  I see it.
[http://docs.google.com/View?id=dfdzc3xg_7997mb6kgd](http://docs.google.com/View?id=dfdzc3xg_7997mb6kgd)

Thanks for your help.

Also (aside from unmounting) ... for swap select swapoff.

---

### Post by Pablo W on 2009-09-19
Thanks earthpigg and raymondhenson for your answers. I am one step closer now. I could delete some of the partitions, but I still have 2. 

When I try to unmount the main partition (called "partition/dev/sda1" file system "ext3"), I get a warning message reading (excuse if the translation is not exactly as in English):
 "The partition could not be unmounted from the following mounting location: / .Since it seems that there are other patitions mounted in the same location, please unmount them manually".

The only other partition (called "not allocated" file system "not allocated") has its "unmount" option disabled.

In case this is useful info, I am dealing with an old IBM ThinkPad T42. 

I have not idea as to what to do. :confused:
Again, I attach a picture of how things look like now.

Could you guys guide me please? 
Thank you for your help.

---

### Post by raymondh on 2009-09-19
> **Pablo W said:**
> Thanks earthpigg and raymondhenson for your answers. I am one step closer now. I could delete some of the partitions, but I still have 2. 

When I try to unmount the main partition (called "partition/dev/sda1" file system "ext3"), I get a warning message reading (excuse if the translation is not exactly as in English):
 "The partition could not be unmounted from the following mounting location: / .Since it seems that there are other patitions mounted in the same location, please unmount them manually".

The only other partition (called "not allocated" file system "not allocated") has its "unmount" option disabled.

In case this is useful info, I am dealing with an old IBM ThinkPad T42. 

I have not idea as to what to do. :confused:
Again, I attach a picture of how things look like now.

Could you guys guide me please? 
Thank you for your help.

Pablo,

Notice the key symbol?  What happens if you right click on that partition ... do you have the option to unmount?

There is a tool called [dban]("http://www.dban.org/") that will wipe a hard drive clean.  You may want to consider this as your end goal is to clean-up the HD and just install XP.

Good luck.

---

