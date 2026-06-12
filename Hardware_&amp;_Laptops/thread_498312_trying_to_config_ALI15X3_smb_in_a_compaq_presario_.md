---
title: "trying to config ALI15X3_smb in a compaq presario 1692"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by lucho115 on 2007-07-11
Iam using etch and i get low tranfer rate on my hd ( 10 - 11 mb/s, when i knows 

that the same hd in other manchine run near to 26 mb/s) so i think that the 

controller is to old, but i found that its ( ALI M5229 and use the kernel module 

alim15x3) works at 33 mb/s as limit ( udma3 i think) so it could handle a hd at 

26 mb/s. So inspect my kernel log with dmesg and i found the following:

> ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade 

BIOS or
use force_addr=0xaddr
ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.

OK, so i try to find an address to pass to the kernel module, so i type this 

command: **cat /proc/ioports**
Its list all the ports in use so i try to pass others to the kernel module like 

this:  **force_addr=0x03e0** ( i add it to the grub setup) but when boot i 

have the same error , so my quiestion is : am i passing in a wrong way a address 

to the kernel module? or i passing a wrong address , in this case how i can 

knows what address use? 
Or if iam doind all wrong, somebody can help me? 
thanks, and sorry about my english, iam from argentina. bye.-

---

### Post by RavanH on 2007-09-18
Same problem here!

I noticed this only after upgrading to the latest Gutsy development but it might have been around under Feisty also...

Got the latest BIOS upgrade (so that cannot be the problem?) on a Packard Bell Easynote R3450.

Anyone any ideas?

--ravan

---

### Post by Perkins on 2008-04-10
I am having a similar problem on my old Toshiba Portege.  It worked under 6.06, but at the time I didn't have enough free disk space to install it.  Now I do, but trying to boot from either a 7.10 or 8.04 beta live CD yields the above region uninitialized, followed by the module not inserted error, and then a full halt.  


Ali was the manufacturer of this thing's sound card, and it has been the bane of my existence since I purchased the machine.  I will try using the alternate cd to install next, but from the posts above, I doubt that will work any better.


I suppose I can always remove the card.  But I would really rather have sound.  Any ideas about how to force it back to the earlier module that worked?

---

