---
title: "Extending memory for Ubuntu"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by prodigyaj on 2009-08-05
Hello all,
I have been a windows user for long , now switched to ubuntu (linux environment) because of some engineering applications that I require to perform in Linux. However i still wanted to have windows and installed ubuntu in the minimum space option from boot up (not using wubi) with windows. I am not aware of how much space is allocated to linux when its installed using minimum space. Now I fallen in love with ubuntu and want to allocate more space to it. I have a partitioned D drive, in my attempt to allocate more space to linux, is now no longer a part of windows and neither of ubuntu.
How do i make ubuntu use this unallocated drive ?
heres link to the screenshot as shown in gparted.
[http://img269.imageshack.us/img269/8985/screenshot1oap.png](http://img269.imageshack.us/img269/8985/screenshot1oap.png)

Thank you

AJ

---

### Post by SoftwareExplorer on 2009-08-05
Is sda5 the empty partition whose space you want to give to ubuntu?

By the way, welcome to ubuntu forums, prodigyaj.

---

### Post by lisati on 2009-08-05
Are you wanting to share the partition with Windows and Ubuntu?


(BTW, reading your thread title, I thought you were referring to RAM, not disk space)

---

### Post by SoftwareExplorer on 2009-08-05
> **lisati said:**
> Are you wanting to share the partition with Windows and Ubuntu?


(BTW, reading your thread title, I thought you were referring to RAM, not disk space)

Looking at his screenshot, prodigyaj only has 2.33 GB of space for Ubuntu. I'm betting prodigyaj wants more space in his root partition.

---

### Post by prodigyaj on 2009-08-05
Yes!
I think finally @software explorer put it in words !! I need more space for root and sda5 is the partition i want to attach to my root !! ( when i try to copy something to my desktop , it dsnt copy saying no space available )
Just like I am impressed with ubuntu i am extremely delighted at the as good ubuntu forums !! 

AJ

---

### Post by SoftwareExplorer on 2009-08-05
First, it is a good idea to back up. It is rare to loose data when you resize partitions, but it can happen.
The instructions I am going to tell you WILL ERASE ALL DATA ON SDA5 and give the space to the root partition.
Also, you may want to set this up and let it run while you wont need the computer for awhile cause partitioning stuff can take a long time.

You'll have to boot into a live CD because you can mess with a partition that is mounted, and for the system to run off it, it has to be mounted.

Once you are in the liveCD, start gparted.
Right click on sda5 and click delete. THIS WILL ERASE ALL DATA ON SDA5.
Right click on sda7 and click copy.
Go to the empty space left by deleting sda5 and click paste. Put it at the start of the empty space.
Right click the new partition and click resize/move. In the box that comes up stretch it out to take up the rest of the space. Click resize/move.

Click apply.
It will probably ask you if you really want to.
We'll have to set some more stuff up, but after clicking apply it will take a long time, so I'll check back in the morning. (It's 11:40 PM where I am, and I should go to sleep!)

---

### Post by SoftwareExplorer on 2009-08-05
When it's done, run ```
sudo blkid
``` and post the output. Also a gparted screenshot from the liveCD would be helpful.  That will give me a head start in the morning.

---

### Post by prodigyaj on 2009-08-05
The moment i right clicked on sda5 to delete it gave me the following error 
[http://img156.imageshack.us/img156/5393/screenshotmef.png]("http://img156.imageshack.us/img156/5393/screenshotmef.png")

---

### Post by SoftwareExplorer on 2009-08-05
OK, you need to get an ubuntu LiveCD and boot into it. You [COLOR=Red][can get it here]("http://www.ubuntu.com/getubuntu/download").[/COLOR]
[COLOR=Black]
Then try to do what I said. You can't unmount sda5 because to do that you have to unmount partitions with a higher number. Your root partition is sda7 and you can't unmount it if you are running off of it. So you have to use the LiveCD.

Edit:By the way, keep up the screenshots. I makes it a lot easier for me to see what is happening.
[/COLOR]

---

### Post by prodigyaj on 2009-08-05
ubuntu LiveCd , isnt that the normal bootable CD that is used to install ubuntu or is it something different. Because I have my bootable ubuntu CD with which I had installed ubuntu and i also had inserted the cd while doing this procedure. However let me add, inspite of adding this CD i dint get any different boot up options as i wld have expected and ubuntu started normally  as it would have without the cd. Please clarify here :)
Thank you 

AJ

---

### Post by SoftwareExplorer on 2009-08-06
Yes the Live CD is the most common way to install ubuntu. It starts a desktop that has an install icon on it. But it also has alot of other tools.

---

### Post by prodigyaj on 2009-08-06
I booted with my ubuntu CD and I get the options like
Install Ubuntu
test memory
..
..
dun remmeber
and then below we have 
F1 F2 ... F6
where F4 is mode.
How do i proceed , install ubuntu ?

AJ

---

### Post by jocko on 2009-08-06
> **prodigyaj said:**
> I booted with my ubuntu CD and I get the options like
Install Ubuntu
test memory
..
..
dun remmeber
and then below we have 
F1 F2 ... F6
where F4 is mode.
How do i proceed , install ubuntu ?

AJ
If you are sure the first option is "Install Ubuntu" and not "Try Ubuntu without making any changes to your hard disk", you don't have a live cd, you have an alternate install cd. You can't use that.

---

### Post by prodigyaj on 2009-08-06
hey I am sorry ya my first option was 
Try Ubuntu without making any changes to your hard disk, but ya so what to do next ?
Thanks 

AJ

---

### Post by jocko on 2009-08-06
> **prodigyaj said:**
> hey I am sorry ya my first option was 
Try Ubuntu without making any changes to your hard disk, but ya so what to do next ?
Thanks 

AJ
You boot up from the live cd (first option) and then use gparted (System-->Administration-->Partition editor) to:
1. Delete the partition /dev/sda5.
2. Resize the partition /dev/sda7 to take up all free space where /dev/sda5 used to be. This will probably take time, as all data will probably be moved bit by bit to the new beginning of the partition, and disk checks will be run before and after moving data. Just leave it alone until it's finished (it may take anything from 5 minutes to several hours depending on the amount of data that needs to be moved).

**Note:** If you haven't spent too much time configuring your ubuntu install, it's probably a lot faster and easier to just reinstall ubuntu and make sure you make the partitions properly.

---

### Post by prodigyaj on 2009-08-06
actually because of this i really havent spent any time working on any application !! 
So any specific procedure for reinstallation ? 
or is it just the second option ? 

AJ

---

### Post by jocko on 2009-08-06
> **prodigyaj said:**
> actually because of this i really havent spent any time working on any application !! 
So any specific procedure for reinstallation ? 
or is it just the second option ? 

AJ
Just boot up the live cd and start the installer (double click the icon on the desktop).
During the partitioning part of the install, use the advanced setup to set up your partitions manually. Make sure you delete the sda5, sda7 and sda8 partitions. 
Simplest setup:
1. Make one new swap partition (at least the size of your ram if you want to be able to use hibernation, but anything more than twice the size of your ram is probably just going to be a waste of space), make sure it is set to be mounted as swap.
2. From the rest of the free space, make one large ext3 partition. Set it to be mounted as the root file system (/).

Slightly more complicated setup:
1. Make one new swap partition (at least the size of your ram if you want to be able to use hibernation, but anything more than twice the size of your ram is probably just going to be a waste of space), make sure it is set to be mounted as swap.
2. Make one ext3 partition (8-12 Gb). Set it to be mounted as the root file system (/).
This will be where the operating system and all installed applications will be. Mine is 11 Gb, but with all applications I have installed I use only about half of that.
3. From the rest of the free space, make one large ext3 partition. Set it to be mounted as /home. This is where all your personal settings for your user account(s) will be stored, and also where you can keep all your personal files (music, photos, documents...).
This setup is good in case you need to reinstall ubuntu (or any other linux distro) in the future and want to keep all your settings and files.

---

