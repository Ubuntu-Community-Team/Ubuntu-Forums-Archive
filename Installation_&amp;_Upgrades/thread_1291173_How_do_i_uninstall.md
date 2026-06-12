---
title: "How do i uninstall"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by tonto1950 on 2009-10-14
New user having installed 9.04 yesterday running along side Win XP. Initially Ok  and dual boot no problem. Then the desktop loaded with no tabs. Then then desktop didn't load saying not enough space.
I have now tried to run the installation disc again but now getting exception processing message " c0000013 parameters75b6bf7c4 75b6bf7c 75b6bf7c " and nothing happens
Is there an easy way to uninstall Ubuntu and either start again or repair
Thanks in advance

---

### Post by oldfred on 2009-10-14
Did you get bit by the slider that you are supposed to move to give more than 2.5 GB. but didn't notice. You need a min of 4GB and 10GB is recommended.

You need to shrink the XP partition first. You should defrag, twice is even better. Houseclean out old stuff to make room to shrink the XP partition. And defrag after housecleaning.

HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)
Also check the links in this thread for additional info if you are not sure about partitioning.

If you want to put window back in the MBR so it will boot. Use the XP install disk and go to recovery:

FIXMBR  C:
FIXBOOT  C:

---

### Post by tonto1950 on 2009-10-14
Thanks for info. It is a problem with size of partition but article says I have to unmount Ubantu before I can shrink Windows partition. I have used Paragon Disk Manager to look at partitions but cannot see how to unmount. I can resize the partition with Windows on it but not sure about the Linux

---

### Post by jeremyswalker on 2009-10-14
You should use the LiveCD to adjust your partitions. Once booted, go to System > Administration > Partition Manager. Once here, I would suggest deleting the Ubuntu partition and starting over. Once the Ubuntu partition is deleted, resize your Windows partition so that there is at least about 10 GB of free space left. Then, you can go through the install process and tell it to use the largest free space (or you can set them up yourself if you feel comfortable enough).

---

### Post by urugTON on 2009-10-14
Just for folks reading this a little later on . . . 

jeremyswalker's instructions work fine for resizing partitions that XP is using.  I've done it.  That said, I've heard that Vista does not appreciate Ubuntu resizing partitions - to the point of requiring the Vista recovery disk.  Once the Vista recovery disk is run, grub has to be reinstalled.  Fairly easy to do, but no fun and in my case, lots of frustration.

Just a head's up.  Vista can resize its primary partition and will no doubt grudgingly give up 10 GB.  My experience is that Vista will not give up more than 1/2 the hard drive.  I eventually cured that issue by removing Vista, but that's another story.  :)

---

### Post by raymondh on 2009-10-14
> **urugTON said:**
> Just for folks reading this a little later on . . . 

jeremyswalker's instructions work fine for resizing partitions that XP is using.  I've done it.  That said, I've heard that Vista does not appreciate Ubuntu resizing partitions - to the point of requiring the Vista recovery disk.  Once the Vista recovery disk is run, grub has to be reinstalled.  Fairly easy to do, but no fun and in my case, lots of frustration.

Just a head's up.  Vista can resize its primary partition and will no doubt grudgingly give up 10 GB.  My experience is that Vista will not give up more than 1/2 the hard drive.  I eventually cured that issue by removing Vista, but that's another story.  :)

I have found that later-version gparted will resize a Vista partition leaving no problems with boot.  From Herman, I learned to pay attention to uncheck the "round-to-cylinder" box using a live gparted CD.  In the ubuntu liveCD, there is no need to "round-to-cylinder". 

[http://members.iinet.net.au/~herman546/p22/012.png](http://members.iinet.net.au/~herman546/p22/012.png)

Using Vista's disk manager, I have also managed to shrink Vista from a 320GB install to about 50GB.  As we know, microsoft has a tendency to write "immovable" system files all around the disk ..... and these are one of the reasons why it is hard to get space from Vista .  Googling around, here is a guide from HOW-TO-GEEK.  It is not the easiest but it is still possible.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

I am a gparted fan and continue to use it.  However, I also see the value of using a microsoft disk manager to work on a microsoft partition.  Both will work IMO.

Regards,

---

### Post by tonto1950 on 2009-10-14
Thanks again for info but I can't run disc because of the exception error "no disc "message I reported in earlier post.
I have tried Win Restore to earlier date but still cannot run disc so cannot resize partitions
Help !!

---

### Post by jeremyswalker on 2009-10-14
Just a thought: It may not make complete sense (I'm questioning this is my head as I type), but do you have another CD you could re-burn the LiveCD to? It seems odd that this could be a problem (beings you have already used it fine), but stranger things have happened.

---

### Post by tonto1950 on 2009-10-14
Have finally got back into Ubuntu and followed Jeremy's instructions . It confirms that Ubuntu is installed in only 2.5 gb of partition with swap file of 126mb. Tried to resize it but unable to see the Ubantu partition. The C drive is already partitioned into 4 under Windows but the one partition where Windows system and Ubuntu and presumably swap file are installed just shows as a single partition with so much free space. i can resize that but it is not telling me how to identify the different operating systems. There are no separate 2.5gb partitions showing where Ubuntu might be
Help please

---

### Post by jeremyswalker on 2009-10-14
Could you post the output of the following:
```
sudo fdisk -l
```

---

### Post by oldfred on 2009-10-14
Here is sum more info on partitions. The partitions do not say windows or linux but Fat32 or NTFS for windows and ext3 or ext4 for linux. Swap is a separate partition for when your system runs out of memory and should be 2x system memory if you have less than 1GB, one times system memory if you have 1GB or more. 

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by raymondh on 2009-10-14
> **tonto1950 said:**
> Have finally got back into Ubuntu and followed Jeremy's instructions . It confirms that Ubuntu is installed in only 2.5 gb of partition with swap file of 126mb. Tried to resize it but unable to see the Ubantu partition. The C drive is already partitioned into 4 under Windows but the one partition where Windows system and Ubuntu and presumably swap file are installed just shows as a single partition with so much free space. i can resize that but it is not telling me how to identify the different operating systems. There are no separate 2.5gb partitions showing where Ubuntu might be
Help please

As previous posters have requested/mentioned:

Access a terminal (applications > accessories) and type as well as post back results of:

```
sudo fdisk -l
```

Small L, not I nor 1.  That will help the forum decipher your HD and hopefully, provide a brief how-to in resizing.

As oldfred said, windows will have either a FAT or NTFS format whilst Linux (generally) will have the EXT2, EXT3, EXT4 formats.  Swap will be SWAP.

Regards,

---

### Post by noelvh on 2009-10-14
I dual booted my IBM x61 tablet, and I had to use the Vista partition tool. I was not able to free up much space as Pista wanted to use 75% of the drive. The up side was the Ubuntu side booted up in less than a minute, and Pista took over 3. I also found most of the tablet drivers were there in ubuntu. I have since restored the Pista build on the machine and it just sits there not being used. 

I will run 9.10 when it is released later this month.

But to the question at hand- I would use ether the live cd partitioner or Gparted. I like the later of the 2. I would then create resize the xp, and create 3 more. One for the root /, one for home /home, and a swap.

Noel

---

### Post by tonto1950 on 2009-10-15
Managed to find the Linux partition. The default installation had given it 2.5gb on my 3rd external drive ?? I had assumed it would look at my C drive first/
Anyway deleted that partition and now reinstalled it on new one on C drive with plenty of gb and seems to be working OK
Many thanks to all for the info and quick response

---

### Post by davidU on 2009-10-15
Hi Tonto1950.
You were lucky, I cannot even run the live cd now !
It dumps me at the command prompt $  SHEESH !

Time to stop pissing about I suppose.
I think I will wipe the lot (AGAIN !) and go back to Windose only !

What a choice !

ALF:guitar:

---

