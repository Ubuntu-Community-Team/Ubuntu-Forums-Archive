---
title: "External hard drive causing system to hang at boot"
date: 2013-01-06
forum: Hardware
---

### Post by BinaryFission on 2013-01-06
](*,)I've tried searching for this issue but haven't seen it yet so i'm starting a new thread sorry if i'm double posting.

I have a Dell Inspiron 620 with the following

1TB Internal Seagate Barracuda Internal with Windows 7
500GB Internal Seagate Barracuda Internal Drive with Ubuntu 12.04

1 External Seagate USB Drive formatted to windows file system i use for backup, the external drive is shared through the router for the home network and is not plugged into the tower

Before i get into a long explanation i will simply state what is happening and then explain in detail

With the external drive plugged in to the router i can boot from a cold boot into windows no problem, when i try to boot into Ubuntu though i have a system hang and see only the following after selecting the Ubuntu OS from the boot loader screen

                                                                                                                                                                   [OK]

And the system will not go any further until i unplug the external drive and then i must go into advanced settings at the boot loader when i reboot to fix it.

The only way to fix the issue is to go into advanced settings and run the tool to repair broken packages. When i do run the tool i see a message that tells me that it has fixed the problem. The problem is stated as being an error caused by a message of some kind saying the last time the system loaded was in the future. Not sure what that means really.

Once it is complete i restart the computer again, external hard drive still unplugged, the system will boot normally. However the system time was way off when i got to the user screen. It was in fact 5 hours behind though the system time was correct when i last logged off.

I did plug in the external drive while i was logged into Ubuntu and it didn't kill the OS or anything but i wasn't able to see it as an available storage device either.

Any ideas at all would be greatly appreciated. ):P

Very new to Linux and  Ubuntu but i used to be a pretty good net admin so i can hopefully follow more advanced instructions/questions :D

---

