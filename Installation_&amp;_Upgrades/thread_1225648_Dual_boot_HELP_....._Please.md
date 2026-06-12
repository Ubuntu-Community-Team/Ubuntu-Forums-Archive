---
title: "Dual boot HELP ..... Please"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by cuzimjoesmith on 2009-07-28
[LEFT]Can someone give me a step by step on how to dual boot windows xp and ubuntu, with xp installed first.[/LEFT]
 
ive been fooling around with it and reading threads about it and its all mixed up to me.
 
i jsut need a basic step by step , after xp installed then what?  looked on how to partition and cant figure it out , dont understand the swap/home and where ubuntu is supposed to be.
 
-joe-

---

### Post by lisati on 2009-07-28
Before you begin there are one or two things which are a good idea:
[LIST=1]
[*]Clean out temporary files from your Windows partition. The "disk cleanup" utility takes care of *some* of this, but there's often a temporary folder which isn't always cleaned up. You can access the temporary folder with Start->Run and typing in %temp% - a sizeable portion can be safely deleted.
[*]Defrag Windws two or three times. Some people find it useful to disable paging and deleting the Window pagefile.sys file first.
[*]Give some thought to how you want your partitions organized.
[/LIST]
If you haven't already done so, I'd suggest having a look here: [https://help.ubuntu.com/9.04/switching/dualboot.html](https://help.ubuntu.com/9.04/switching/dualboot.html)

---

### Post by cuzimjoesmith on 2009-07-28
i have done the steps you listed and the link i have been to but im a visual person and reading instruction doesnt do much for me unless i know about it already as in if it was just windows i was working on but partitioning i dont know about and i want it to be right , i need pictures lol of some sort, so i knwo im following the right steps.

---

### Post by merlinus on 2009-07-28
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by cuzimjoesmith on 2009-07-28
thanks that link helped, i had actually done that before but never saw the guided partition section,
 
so do i or do i not need to worry about the swap /or home/ things ive been reading about and the logical , i dont know what any of those are and dont know if i need to do those.

---

### Post by presence1960 on 2009-07-28
> **cuzimjoesmith said:**
> thanks that link helped, i had actually done that before but never saw the guided partition section,
 
so do i or do i not need to worry about the swap /or home/ things ive been reading about and the logical , i dont know what any of those are and dont know if i need to do those.

If you don't know about all those things you say you don't know about you need to read and study. these are basics in computing. I would suggest some links  for you to read:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

[http://www.psychocats.net/](http://www.psychocats.net/)

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Don't rush into installing another OS until you have an idea of what it is you are going to try to do. Have you ever installed an OS before? Using a recovery CD/DVD or recovery partition does not count as all the partitioning, installation of drivers and software is done for you. If you have ever installed Windows from an install CD/DVD then you know how to partition, download & install drivers and install your software as a windows installation disk does none of that for you.

I suggest you become a little more knowledgeable prior to installing Ubuntu. You have been using windows how long? A little more time will not kill you.

---

### Post by cuzimjoesmith on 2009-07-28
i am above average when it comes to computers and i did do research and i am very familiar with windows its just that different people say different things aboutt he same topic and i am not asking about windows i am asking about ubuntu and dual booting and partitioning

---

### Post by presence1960 on 2009-07-28
> **cuzimjoesmith said:**
>  i am not asking about windows i am asking about ubuntu and dual booting and partitioning

my point exactly!

> its just that different people say different things aboutt he same topic 
That's because in Linux there are usually at least two, sometimes a multitude of ways to accomplish the same task.

---

### Post by cuzimjoesmith on 2009-07-28
ok that didnt help any, 

i just need to know if what root/home/logical is , and i have read abotu them still doesnt make sense to me, and when i install ubuntu 9.04 and when i get to the partition part i dont get a sliding bar or anythign that says root/home/logical.

---

### Post by presence1960 on 2009-07-28
> **cuzimjoesmith said:**
> ok that didnt help any, 

i just need to know if what root/home/logical is , and i have read abotu them still doesnt make sense to me, and when i install ubuntu 9.04 and when i get to the partition part i dont get a sliding bar or anythign that says root/home/logical.

Again I suggest you read some of the links given for you to read. Since you are above average with computers you will see what you need to know. Hint : the link how to partition will answer your questions about all partitions including logical (which by the way entail the same type of partitions that are used in Windows) and the free ubuntu pocket guide has a section on installing Ubuntu that is relatively simple and easy to follow with step by step instructions.

I want you to try Linux, but you need to do the prep work. if I were there I could show you but unfortunately I am not.

Lisati & merlinus gave you a couple good links to help you get up to speed. They know what they are doing, they wouldn't just suggest something for no reason.

---

### Post by cuzimjoesmith on 2009-07-28
i have read and read and read i know what it all is now
 
my prob now is when i do install ubuntu and when i get to the partitioning part i dont have the same option as i see in other pics i have seen, the sliding bar and option for logical and swap and etc. so i dowloaded another program to see if i cant get it to work that way no progress.

---

### Post by presence1960 on 2009-07-28
> **cuzimjoesmith said:**
> i have read and read and read i know what it all is now
 
my prob now is when i do install ubuntu and when i get to the partitioning part i dont have the same option as i see in other pics i have seen, the sliding bar and option for logical and swap and etc. so i dowloaded another program to see if i cant get it to work that way no progress.

if you choose guided resize you will see no options. See the attached screenshot. Choose guided resize and grab the right end of the gold partition sda2 (yours may be a different partition #) and slide it left or right to set your ubuntu partition size. The installer will take care of swap automatically for you.

Until you are more proficient at this I would stay away from the manual install option- that is where you can manually create partitions. For now I would let the installer take care of things. You only have to choose guided install and set the ubuntu partition size.

---

### Post by cuzimjoesmith on 2009-07-28
hey for some reason your screen shot looks nothing like mine, 
 
what i get is :
 
a bar saying this is microsoft xp pro
 
then says what do you want to put ubuntu 9.04
 
[LIST]
[*]then a dot liek this -saying use entire disk
[/LIST]            scsi3 (0.0.0) (sda) - 500.1 GB ata wdc 
                
            --- this will delete microsoft and intall ubuntu ( which i dont want to do ) 
[LIST]
[*]then another dot- saying specify partitions manually (advanced)
[/LIST]am i supposed to have DL somthing before installing ubuntu to get the screen you are getting?

---

### Post by presence1960 on 2009-07-28
> **cuzimjoesmith said:**
> hey for some reason your screen shot looks nothing like mine, 
 
what i get is :
 
a bar saying this is microsoft xp pro
 
then says what do you want to put ubuntu 9.04
 
[LIST]
[*]then a dot liek this -saying use entire disk
[/LIST]            scsi3 (0.0.0) (sda) - 500.1 GB ata wdc 
                
            --- this will delete microsoft and intall ubuntu ( which i dont want to do ) 
[LIST]
[*]then another dot- saying specify partitions manually (advanced)
[/LIST]am i supposed to have DL somthing before installing ubuntu to get the screen you are getting?

I have heard of others having this problem. try the alternate [text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

did you try check disk for errors when you boot the Ubuntu live CD? Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded before burning it to CD as image? Did you burn it at a slow speed like 2x or 4x. If everything checks out try the alternate text based installer

---

### Post by cuzimjoesmith on 2009-07-28
i will try and DL from a differnt mirror and i did do the cd check from ubuntu and came out error free ,i will check hash tho , and let you know what happens.
 
Thanks alot 
 
-joe-

---

### Post by presence1960 on 2009-07-29
> **cuzimjoesmith said:**
> i will try and DL from a differnt mirror and i did do the cd check from ubuntu and came out error free ,i will check hash tho , and let you know what happens.
 
Thanks alot 
 
-joe-

if everything checks out then try the alternate text based installer. I am going to bed will check back in the morning. I see that merlinus is still signed on here so he can help you if you need it. You'll be in good hands.

---

### Post by cuzimjoesmith on 2009-07-29
Hashes are the same.

---

### Post by cuzimjoesmith on 2009-07-29
[[SIZE=5][COLOR=#000000]presence1960[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=657448")-
 
 

 
 
 
 
alright this is what i have so far , for when you read this later, i DL the alt for ubuntu the txt version and got to the partition part and then got 
 
:: Because of unknown reasons it is impossible to resize this partition 
     check /var/log/sys log or see virtual console 4 for the details. 
 
so i looked to see if i could find anything on it and i did, but not much help when others have tried to fix it from help from other people they didnt get anywhere, so i will prob just reinstall windows and redo my partitions there, and start over. 
 
let me know what you find and think .

---

### Post by presence1960 on 2009-07-29
> **cuzimjoesmith said:**
> [[SIZE=5][COLOR=#000000]presence1960[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=657448")-
 
 

 
 
 
 
alright this is what i have so far , for when you read this later, i DL the alt for ubuntu the txt version and got to the partition part and then got 
 
:: Because of unknown reasons it is impossible to resize this partition 
     check /var/log/sys log or see virtual console 4 for the details. 
 
so i looked to see if i could find anything on it and i did, but not much help when others have tried to fix it from help from other people they didnt get anywhere, so i will prob just reinstall windows and redo my partitions there, and start over. 
 
let me know what you find and think .

sounds like a good idea, if you can't resize your XP partition and you want Ubuntu. First back up any files you don't want to lose. 

You can save yourself some work by doing this if you have a windows install disk, not a recovery disk or recovery partition. Boot off the Ubuntu Live CD and choose "try Ubuntu without any changes...", when the desktop loads go System > Administration > Partition Editor. Delete your windows partition and any other by right clicking on it and choosing delete. When your whole disk is unallocated (will be a gray color) click Apply (green check mark) at top toolbar.

Now you want to create 3 partitions- 1 NTFS for XP, 1 ext3 for Ubuntu and 1 swap partition. Swap size should be equal to the amount of RAM you have so you can use suspend/hibernate. Decide how much space you want for windows then the rest will be for Ubuntu.

Create the XP partition first by rightclicking the unallocated space and choose New. Set up as primary partition, set the size, set up Filesystem as NTFS. Click Apply on toolbar.

create the swap partition. Set as primary, set size equal to RAM and for Filesystem choose swap. Click Apply on the toolbar.

Create the Ubuntu (root or /) partition. Set as primary partition and File System as ext 3. Click Apply on the toolbar.

You are now ready to install windows. Boot off the windows CD and choose the NTFS partition to install windows to. Do not delete or format the other partitions you created. When finished installing boot your machine to make sure windows works. When ready to install Ubuntu boot from the Ubuntu Live CD. At the prepare disk space window choose the manual option. Highlight your Ubuntu partition and click Edit. Set parameters- "Use as" set to ext 3 and mount point set to / (very important!) Click ok or apply. Highlight the swap partition & click edit. In "use as" set as swap. Click ok or apply. Now proceed with the install.

By creating the partitions before the install you won't have to resize your windows partition. This will work as long as you don't have a recovery CD/DVD or a recovery partition. If you have that then your whole hard disk will be formatted as NTFS when you install windows. Then you will have to try resizing the windows partition again. Good luck- keep us updated.

---

### Post by cuzimjoesmith on 2009-07-29
alright sweet , well before i read your reply i did start with a new windows xp and created 2 new partitions then installed xp on the first one and had unformatted on the other and then tried to install ubuntu and  it still wouldnt let me install ubuntu on its own partiton so i just installed ubuntu without changes to computer and then went to gparted and it had 2 partitions on xp and one unformatted and messed around with the unformatted one and couldnt find anythign that i was looking for. so now i will try and do what you said and see what happens.

---

### Post by cuzimjoesmith on 2009-07-29
[[SIZE=5][COLOR=#000000]presence1960[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=657448")-
 
 
It all works!!!! Thanks for everthing:D

---

