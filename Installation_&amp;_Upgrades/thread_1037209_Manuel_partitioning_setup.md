---
title: "Manuel partitioning setup"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by ShadowXRougeXEver on 2009-01-11
Hello.
I'm wanting to set up my laptop to dual-boot between Vista and Ubuntu 8.10.

I want to set it up so:
Restore 10GB
Vista 110GB
My files 72GB
Ubuntu 39GB

I don't know what I need and how much space to give in the Ubuntu part, like the swap and /home etc.
Also, what is the difference between primary and logical?
What would you recommend I do in the Ubuntu part?

---

### Post by taurus on 2009-01-11
You can only have 4 primary partitions to a harddrive and if you plan to have more than 4, then you need to make one of those primaries into an extended partition and under that extended partition, you can create more logical partitions.  Windows must be on primary or it probably won't boot but Ubuntu can reside on logical partition with no problem at all.  

It all depends how much more apps you plan to install but 10GB for / should be more than enough.  You want to make /home a little larger since all your personal files & settings will go in there.  And 1GB or 2GB of swap space (partition) should be enough.

---

### Post by ANew on 2009-01-11
Ubuntu without addition packages 2.1 GB

Swap, 128kb (???) i suppose you go swapoff since
the RAM memory is huge in your computer

---

### Post by AlexDudko on 2009-01-11
> **ShadowXRougeXEver said:**
> Hello.
I'm wanting to set up my laptop to dual-boot between Vista and Ubuntu 8.10.

I want to set it up so:
Restore 10GB
Vista 110GB
My files 72GB
Ubuntu 39GB

I don't know what I need and how much space to give in the Ubuntu part, like the swap and /home etc.
Also, what is the difference between primary and logical?
What would you recommend I do in the Ubuntu part?

Since your primary OS is Vista and as far as it can be presumed from the structure of your HDD the easiest solution would be to make simply only one root "/" partition for Ubuntu and install it on the latter.

---

### Post by akshay.bhardwaj on 2009-01-11
Carry out following steps while installing ubuntu:
1. Carry out defragmentation of your hard disk. This will make a continuous free space that is required while partition.
2. The use the partition editor that you get in ubuntu live cd to make partition of :
home 20gb ext3 
swap 1gb linux-swap
I did this much my first time.
3. than start the live cd ubuntu installer, whose icon you can find on desktop
4. During the entire process when the time come to chose partition. Change radio button to manual one and then proceed.
5. The select the 20gb ext3 partition for your /home and the 1gb partition for swap partition. The swap partition acts as virtual memory(like a extra ram as in case of windows).
6. Then proceed by pressing next
7. When the installer asks you to confirm the operations. In that window there would be a advanced option. Click on it. Another window would open. Over there select the place where you want to put your bootstrap loader program. Put it in the folder where the windows one in kept. Bootstrap loader starts the procedure of loading the operating system from hard disk to memory.
8. Then continue and install ubuntu

This might be of little help to you. If have any problem please post that problem on this thread

---

### Post by ShadowXRougeXEver on 2009-01-11
Ahh ok, thanks taurus.

One last question, what file system should the Ubuntu partitions be? ex3?

---

### Post by taurus on 2009-01-11
Yes, use ext3 filesystem for Ubuntu (/ & /home) and swap for swap partition.

---

### Post by akshay.bhardwaj on 2009-01-11
the 20gb partition should be ext3
and the 1gb should be linux-swap

---

### Post by ShadowXRougeXEver on 2009-01-11
I have setup Ubuntu, but now I can't access Vista!
I can open the restore for Vista, but everytime I try opening Vista, the screen blinks and the boot slecter opens again :(
How do I get Vista working again?
UPDATE:
I got Vista and Linux back! :)

---

