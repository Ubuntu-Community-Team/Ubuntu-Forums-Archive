---
title: "New Install on a windows vista system"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by Zard0z on 2009-01-06
I am new to Ubuntu and want to install 8.10 on my system.

I get to the graphics partition option and chicken out! I am not sure what disk and how not to screw up my vista install.

I have three disks on my system Sata1 Sata2 and Sata6

Sata6 is the new prepartitioned drive.  Any suggestions on how I can read up or a way I can be sure that the installer will not screw up the other two drives?  Can anyone talk me thru it or is there a step by step explanation for 8.10 for my situation?

Thanks in advance,

Zar

Skype  Zardoz1

---

### Post by Mark Phelps on 2009-01-06
The link below is to an Ubuntu community page on installation:

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

Yeah, I know is says 8.04, but the installation for 8.10 is the same process.

Just make sure that the partition you want to use for Ubuntu is NOT formatted as NTFS. If you find that to be the case, boot using the LiveCD and reformat that partition to Ext3 before the  installation.

---

### Post by Zard0z on 2009-01-08
Yes I read that before I posted so it did not help to reassure me that what I was about to do was correct. The step by step is not the same as 8.10. very different screens etc.  

My new disk has a fat32 for Linux and the rest is NTFS. Will this work for the installer?  The other big question is that it shows all of my disks and want to put file system on them! Why would it want to do that? and the optin to tell it not to use that partion... would that save my other disk from disaster? If so then it should work then???

thanks for your time!!

Z

---

### Post by Sef on 2009-01-08
> My new disk has a fat32 for Linux and the rest is NTFS. Will this work for the installer?No, it won't.  Use the default file system for Ubuntu, which is ext3.  

> Sata6 is the new prepartitioned drive. Any suggestions on how I can read up or a way I can be sure that the installer will not screw up the other two drives? Can anyone talk me thru it or is there a step by step explanation for 8.10 for my situation?Read both[Psychocats]("http://psychocats.net/ubuntu") and  the [Illustrated Dual Boot]("http://http://users.bigpond.net.au/hermanzone/p14.htm") for installing help.  Note: the latter has a link to booting with 2 hard drives, but it uses the alternate cd.

---

### Post by Zard0z on 2009-01-10
thanks but like I stated in my first post I have three disks!

The fisrt link has 8.10 screens thanks!! However when I launch the installer it does not report VISTA on any of my drives! And 
this is where I have my issue! 

Guess I'll have to get another computer to run Linux on :(


Thanks for your suggestions.

Z

---

