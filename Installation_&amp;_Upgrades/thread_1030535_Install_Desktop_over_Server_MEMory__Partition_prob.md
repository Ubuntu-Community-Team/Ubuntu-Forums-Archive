---
title: "Install Desktop over Server MEMory / Partition problem!"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by porfavor on 2009-01-04
Hello. I am very new at this and is currently also very confused and frustrated. :confused: How do I uninstall/remove the UBUNTU 8.04.1 LTS SERVER Edition from my computer and replace it with the DESKTOP EDITION? 

I have the Desktop LTS CD, but every time I pop it in and try to run it, it says 
```
[  334.486386] Out of Memory: Kill process 3979 (gconfd-2) score 981 or a child
[  334.486452] Killed process 3979 (gconfg-2)
```
 I think it's because I Might have accidentally formatted the SDA1 partition? 

Anyway, I really have no use for a home server, and want to run the desktop. (somehow, I can reinstall the server edition, but the desktop CD won't install.) I'm thinking of reinstalling the server edition, it's the only way I know how to get to repartitioning. Then make some space by freeing memory. But which partition should I delete? Should I delete? Why won't the CD work? Why don't I have memory? I don't wanna resort to child abuse. I just want ubuntu desktop!

This is what comes up, the overview of my partitions.
```

This is an overview of your currently configured partitions and mount points.
Select a partition to modify its settings (file system, mount point, etc.), 
a free space to create partitions, or a device to initialise its partition table.
     
       guided partitioning
       help on partitioning
    
       SCSI1 (0,0,0) (sda) - 30.7 GB ATA Maxtor 33073U4
           #1 primary   30.6 GB  B     ext3
           #5 logical   172.7 MB  F    swap        swap

```

I just cleared the data from #5 although I didn't delete it. I hope there wasn't anything viral in there? 

I admit. I don't know what I'm doing, so I'd REALLLY appreciate some help, por favor? =)


also, i've tried to install desktop on the server, by putting 
```
sudo apt-get install ubuntu-desktop
``` but it couldn't find that file/package ..and now I just want to completely remove the server...I don't have a windows CD to install, so I dont think I can boot into windows XP either. **[SIZE="4"] Please help. 8-[[/SIZE]**


muchos gracais. :-)

---

### Post by tad1073 on 2009-01-04
Do you have any other OS's on disk?

Are you dual booting, etc.

---

### Post by porfavor on 2009-01-04
Thanks fro your quick reply!
& no. this computer used to run on a bootlegged version of Windows XP that someone installed for me. I don't think there's another OS because when I installed Server Edition, I chose the **guided partition ** option to partition the whole drive...who do I know if I'm dual-booting? I don't think I am.

---

### Post by ajgreeny on 2009-01-04
Do you realise that to use the CD you probably need to boot from it and that means restarting the machine with the CD in drive and BIOS set to boot from CD first.  Or is this not the live CD?

How much memory does the machine have and what is its full spec?  You need at least 256 MB to run ubuntu with gnome desktop, and preferably more.

You can see if windows is still there by running the command in your server install ```
sudo fdisk -l
``` and reporting the output back here.  If you still have windows there will be a line something like the first of the lines here:-

**/dev/sda1   *           1        3932    31583758+   7  HPFS/NTFS**
/dev/sda2            3933       19777   127274962+  83  Linux
/dev/sda4           19778       19929     1220940    5  Extended
/dev/sda5           19778       19929     1220908+  82  Linux swap / Solaris


 You could also use the ubuntu live CD and go to System > Administration > Partition Editor to see how the partitions are laid out on disk.

I am sorry to say that it looks as if you have no windows left on the machine from the partition overview.

---

### Post by porfavor on 2009-01-04
This is what I got when I tried that command: 
(click thmbnail to enlarge)
[[IMG]http://img201.imageshack.us/img201/5200/12966280oo4.th.png[/IMG]](http://img201.imageshack.us/my.php?image=12966280oo4.png)

I think this machine has enough memory. I was able to install Ubuntu SERVER [which requires 1GB of disk space.] The computer was bought a long time ago, so i don't have any papers, but it's a HP Pavilion desktop, with Windows ME. 

Can I not remove the Server without another OS? If I can get Windows OS, what do I have to do with it to remove the server? Just pop the CD in?

 This is the Live CD (It's the "Ubuntu 8.04.1 LTS Server Edition" CD Ubuntu sent me via mail.) and I see the Ubuntu icon when I pop it in and reboot. But is there a possibility that it may NOT be booting from the CD when I try the Desktop Edition CD? If so, how do I change it? [both CDs were sent from Ubuntu via mail.]

---

### Post by rushikesh988 on 2009-01-04
I think you can remove YOUR OS with another Os 


If get failed in it  just get a cd of partiton editir tools such as 

Gnome partition editor or Ultimate boot cd u can user acronic tools too

---

### Post by porfavor on 2009-01-04
so I just get that CD and run it? Sounds simple enough.
What does the CD do? Where can I get one? Is it free like ubuntu?

---

### Post by ajgreeny on 2009-01-05
That command I told you about was ```
sudo fdisk -l
```that's a lower case L at the end not 1 (one).  Try it again and we might get more info.  Also let's see the output from ```
free -m
```which will tell us how much memory you do really have.

You have still not told us how much memory the computer has, just that you think there is enough.  I still suspect that if it is a Windows ME machine it may not be of high enough spec, or may not even have sufficient disk space, but let's see exactly what we are dealing with.

---

### Post by porfavor on 2009-01-05
oh I'm sorry, my mistake. You've got a good eye AJgreeny! :)
It makes more sense now. This is what I got for 
```
sudo fdisk -l
```
[[IMG]http://img81.imageshack.us/img81/7597/sudolai2.th.png[/IMG]](http://img81.imageshack.us/my.php?image=sudolai2.png)

This is what came up for 
```
free -m
```
[[IMG]http://img266.imageshack.us/img266/307/freemys0.th.png[/IMG]](http://img266.imageshack.us/my.php?image=freemys0.png)

So what do you think? Do I have enough memory? Where do I go from here? :confused:

---

### Post by ajgreeny on 2009-01-06
Thanks for the screenshots.  They show conclusively that you don't have enough memory to run ubuntu in any form, there being only 58 MB, and certainly you have no windows on the disk any more; that must have been overwritten when you reformatted.  Perhaps have a look at puppy linux if you want a gui desktop.

---

### Post by porfavor on 2009-01-06
It only has 58 MB in the whole harddrive?! . .man..it's older than I thought.

Puppy Linux sounds like a great idea. Which version would you recommend? 
So I just download Puppy Linux onto a CD or USB. Will it automatically open and when I put it in? Or will I have to remove the Server Edition somehow?

---

### Post by ajgreeny on 2009-01-07
No not 58 MB on your disk, you have a 30.7GB disk but only 58 MB of ram.  The disk is big enough, but the ram is definitely lacking as you really need a min of 256 to run ubuntu, and more to install it from the live CD with any certainty.  If you can't add to ram to get 256 MB at least, I would suggest you try the Puppy Linux I suggested
You can run puppy from a live CD or from a usb flash drive (if a machine that old will boot from a flash drive) and it will run pretty fast.  Go to [http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.1.2-k2.6.25.16-seamonkey.iso](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.1.2-k2.6.25.16-seamonkey.iso) for the best download and give it a try on CD first without installing.  With only 58 MB ram, I don't think it will load totally into ram, as it would if you have 128MB, but it will still run pretty well, and you can even install it to hard disk and run it that way if you want to try it, possibly removing/overwriting the ubuntu server edition if you want to, though you could dual boot the two with 30.7GB disk quite easily.

---

