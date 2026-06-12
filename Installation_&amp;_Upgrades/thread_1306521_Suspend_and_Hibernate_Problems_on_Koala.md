---
title: "Suspend and Hibernate Problems on Koala"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by eigenadam on 2009-10-30
Hello.

I upgraded to 9.10 Koala on my Dell Inspiron 13 (Intel graphics) Laptop last week. For the most part it's working great and it's awesome!

I'm having a couple of issues with suspending and hibernation. My computer no longer suspends automatically when closed. I have checked the settings under Power Management and everything seems in order.

Also, when I manually suspend or hibernate the system there is an issue. On resume, it comes back, everything works fine for about 5 seconds and then there is a hard freeze which requires poweroff and reboot.

Any ideas?

Thanks!

---

### Post by PorkyPie on 2009-10-30
Welcome to the forums :)

It's a known issue:
[http://www.ubuntu.com/getubuntu/releasenotes/910#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning]("http://www.ubuntu.com/getubuntu/releasenotes/910#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning")

---

### Post by eigenadam on 2009-10-30
Thanks for the reply, PorkyPie.

It suspended and hibernated fine in Jaunty, and my swap partition is 1GB larger than my RAM (2GB).

> **PorkyPie said:**
> Welcome to the forums :)

It's a known issue:
[http://www.ubuntu.com/getubuntu/releasenotes/910#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning]("http://www.ubuntu.com/getubuntu/releasenotes/910#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning")

---

### Post by dounestone on 2009-10-31
Hi - I've been having the same problems with a 9.10 on a Dell Mini 9, even with the Swap partition set to the correct size. What I've discovered is ...

1. you need to disable Wireless networking.

and,

2. unmount any removable media (e.g. sdhc card)


if I do both of these system will suspend/resume normally, without then system freezes and requires reboot. Not sure why this should be so or what fix might be but works as a temp solution. Hope this helps.

---

### Post by eigenadam on 2009-10-31
Thanks for the workaround, dounestone.

Works like a charm. I had to unmount both my sdhc card, and my FAT partition on my hard drive that I use to share data with Windows.



> **dounestone said:**
> Hi - I've been having the same problems with a 9.10 on a Dell Mini 9, even with the Swap partition set to the correct size. What I've discovered is ...

1. you need to disable Wireless networking.

and,

2. unmount any removable media (e.g. sdhc card)


if I do both of these system will suspend/resume normally, without then system freezes and requires reboot. Not sure why this should be so or what fix might be but works as a temp solution. Hope this helps.

---

### Post by eigenadam on 2009-11-03
It seems like it freezes right when the network reconnects on resume from suspend.

Could this be related to the Broadcom issues in 9.10?

---

### Post by cygnis1 on 2009-11-07
I am having the same problem. Before my  install of Karmic, suspend worked fine.  Just close the lid and it would resume when I reopened it.  Now it either doesn't respond, causing me to do a hard reboot, or I have to enter my password.  I have a swap partition of 5.3 gigs and Ram of 4 gigs.

---

### Post by mumutum on 2009-11-07
i have the same problem. 
And i should also add that i had never be able to successfully suspend my Toshiba L300 laptop, in all of ubuntu versions.

---

### Post by eigenadam on 2009-11-07
> **mumutum said:**
> i have the same problem. 
And i should also add that i had never be able to successfully suspend my Toshiba L300 laptop, in all of ubuntu versions.

You try disabling your wireless card before closing the lid? Does that allow suspending?

---

### Post by mumutum on 2009-11-07
OMG! I was using ubuntu 9.04 when i send the my last reply. 
Now i have upgraded ubuntu 9.10. And it is absolutely great! Actually it is more than great, it is awesome! 
For the first time, my laptop worked successfully in the stand by mode. 
And again for the first time, gave a full sound, and did not freeze in the youtube videos. 

I think there might be some other ways to solve these problems in ubuntu 9.04, but i coulnd found them, because it was my first experience with ubuntu.
Now with the version 9.10, i am seriously thinking to switch ubuntu from windows completely, :)

Bye.

---

