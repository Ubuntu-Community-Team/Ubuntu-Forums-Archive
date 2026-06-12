---
title: "dual booting Jaunty and Vista with HP G60-249-WM - how can you do it?"
date: 2009-06-19
forum: Hardware
---

### Post by kraymore on 2009-06-19
I have a HP G60-249WM with Vista on it.  I also have the installation media that will restore the hard drive to the original factory Vista state.  It seems that when you install Jaunty and look to partition the hard drive that the recovery partition is at the end of of the physical drive.  Due to this fact, It seems that any effort to install Jaunty has to be done by making room for swap, /, and /home at the beginning of the hard drive.  Thats simple enough to do, however, after installing and writing grub to the hard drive there are two Vista entries, both of which appear to be identical in function (if my perception is correct, it might not be) I get the impression that they both launch a recovery mode and attempt to recovery the hard drive, and always fail, and render the Vista partition unusable.  

I am wondering if anyone has sucessfully gotten their factory Vista partition working in a dual boot configuration working with this laptop, with Jaunty?  

I really like Jaunty because it seems that it has a function that if the battery gets too low, it wont wait for the battery to run dry, it'll simply shut the computer down, before the battery can deplete itself completely, which is great, because if it were to run dry, it would lessen the life of my laptop battery :)

thank you for any help you can offer

---

### Post by amendt on 2009-07-28
I ran into this problem today also. Even after formatting the whole drive to ext3. I will try to set the hard drive partitions to allow for the Vista recovery potion at the back end. Is their a way to change the bios in this HP G60 to not said "Vista"

---

### Post by ZaHACKieL on 2009-07-28
Well, I used to had Vista and Ubuntu in my Dell laptop but what I wiped out the entire hard drive first. I made a backup copy of the restore partition in a dvd just in case.

After that, I installed Vista using NTFS in just one part of the HD, the rest I left it unformated. After the Vista installation was done, I just ran the Ubuntu installation and used that option that says something like: "use the next continuous free space" .

All worked fine after that

ZL

---

### Post by zenrox on 2009-07-31
i left the recover partion intact and use ubuntus partion editor and resized the main windows partion and then created the 2 partions i needed for ubuntu / and swap
so i have my recovery and ubuntu and vista

---

