---
title: "XP/Ubuntu dual boot help for a new user"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by sabredog on 2005-12-19
I hope asking this again is not causing any issues, but how do you prepare to install XP and Ubuntu on two seperate drives? 

I have an WINXP Pro (SP2) PC and know that XP needs to be installed first and located on Master/Primary, but is there anything else special that needs to be done, in particular to the new hard drive on the secondary IDE channel, before I start installing Ubuntu? 

Here is the setup I am hoping to use:
Primary IDE: (C-Drive)
Master
GRUB in the MBR
20Gb NTFS for Windows

Secondary IDE: (D-Drive)
Master
10Gb partition for Ubuntu
10Gb FAT32 for shared data
1Gb Swap

Will this work without a lot of trouble/problems, and will Ubuntu automatically see both and configure GRUB accordingly?

I intend to format the 20gb as one partition within XP's disk management as FAT32 initially.

Once I start the Ubuntu install, will the partitioning configuration pick up both physical HDD's as HDA1 and HDB1, thus allowing me to re-partition D-Drive (HDB1) to the 3 new partitions I require?

I am assuming once re-partitioning is done and install commences, I will be asked if GRUB is to be installed into the MBR of C-Drive allowing a dual boot to either OS?

I would not want GRUB installed where it cannot boot either or just one OS!

The more I read, the more confused I get!

Thanks in advance :)

---

### Post by alamba on 2005-12-19
Go ahead buddy. Don't think u'll hit into any problems per se. Install XP first on the 20 gb. Leave the secondary harddisk untouched without any partitions.

Then install ubuntu. Create the 3 partitions in the secondary drive as required and install. Just be careful on which partition you install. 

Grub should pick up both the OS.

Akshay

---

### Post by rachii on 2005-12-19
sounds like you already have it all worked out!  setting it up like that is real easy because it all just works. select manual partition and set it up how you described, and for dual booting the installer has always detected the first hd and setup windows and grub automatically in my experiences.  so all you have todo is pop the disc in and load

---

### Post by Zonkle on 2005-12-19
I will tell you the easiest way to dual boot with XP, I used this way.

In Windows XP format the Hard Disks as you like.

Then decide which Paritition you don't need for XP to make Ubuntu's paritition ... for Example "G:".

Right click on "My Computer", then go to "Manage", then look for "Disk Management" on the left under "Storage".

Now you see your Parititions, just right click on the Paritition you want Ubuntu to use it (For example "G:") and select "Delete Logical Drive", but be carefull and double check you are deleting the right one :) And that's set!

Restart and load Ubuntu in the CD Rom .... when it asks where to install, just tell Ubuntu "The Largest Continus free Space", and you are done :)

Hope it helpded ... it helped me a lot.

Cya ;)

---

