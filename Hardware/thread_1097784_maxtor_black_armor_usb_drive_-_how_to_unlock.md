---
title: "maxtor black armor usb drive - how to unlock?"
date: 2009-03-16
forum: Hardware
---

### Post by atk_nut on 2009-03-16
I've just recently installed ubuntu 8.1.  Love it.

I'm running a dual boot with xp.  I have a maxtor blackarmor drive for backups.  When I connect in ubuntu, the drive shows up on the desktop but it is locked.

Is there a utility to unlock it?

Please help!!

Thanks.

---

### Post by taurus on 2009-03-16
What filesystem does it use?  

Open a terminal and post the outputs of these commands, running one line at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by atk_nut on 2009-03-16
Here they are:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e709e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2559    20555136    7  HPFS/NTFS
/dev/sda2            2560        9729    57593025    5  Extended
/dev/sda5            9196        9729     4289355   82  Linux swap / Solaris
/dev/sda6            2560        9195    53303607   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

AND:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              51G  3.4G   45G   7% /
tmpfs                 374M     0  374M   0% /lib/init/rw
varrun                374M  128K  374M   1% /var/run
varlock               374M     0  374M   0% /var/lock
udev                  374M  2.8M  372M   1% /dev
tmpfs                 374M  612K  374M   1% /dev/shm
lrm                   374M  2.0M  372M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              20G   14G  6.0G  70% /windows
/dev/scd1              36M   36M     0 100% /media/BLACKARMOR
/dev/sdb               36M   36M     0 100% /media/BLACKARMOR_

---

### Post by Leaf on 2009-03-16
From Maxtor's site
> 
Prohibits access without a password, no exceptions-not even a professional data recovery service can access the data without the password.
----
 PC Requirements
	

Pentium III, 500 MHz equivalent processor or higher
Microsoft Windows Vista Home Basic, Home Premium, Ultimate, Business or Microsoft Windows XP Home, Professional, Media Center Edition**
256MB RAM or more as required by operating system
Internet connection for software updates
1 available USB port

** Drive will not work with any other operating systems as an unlocking utility is required. 


Looks like it's got a full disk encryption going on.  Most likely you must use a utility to input the password to decrypt the drive and the program is Windows only.  Perhaps you can use WINE to run the disk utilty program?

If you dont need all that disk encryption and just want to use your hard drive, you could try formatting it to a non-encrypted file system.  Of course this means you'd lose all data on the drive.

I suppose there is a possibility that the drive has on the fly encryption built into the firmware too, which would make the drive pretty much unusable.
I just checked out some reviews and it is AES hardware encryption.

---

### Post by atk_nut on 2009-03-16
I installed wine.  It seemed to work ok.  I managed to install the maxtor utility, but it reports that there is no drive connected.

(Even though I installed the app from that drive!)

Any ideas?

---

### Post by Rowanmf on 2009-03-20
i have just been lent one of these drives and did the same , installed the manage software via wine , but no luck at all as it says there is no drive present ..
what does  -  AES hardware encryption mean ???? 
could i try the partition editor and delete all the partitions including the 35MB one that comes up as a udf cd drive under windows and then give it a fat32 partition ??
Cheers

Rowan

---

### Post by cks4131 on 2009-03-27
I just purchased a netbook which has ubuntu installed.  I also made the mistake of ordering a blackarmor drive under the assumption it would work.  any updates on this topic?  thanks.

---

### Post by stalefist on 2009-05-03
Ok guys, I think I found a temporary fix on how to mount the blackarmor in ubuntu. I found that you can mount the drive if you first unlock it using a windows VM. I used virtualbox because it has USB support.As soon as I connected the drive to my VM i entered in my pw, the drive light came on and it somehow was mounted to ubuntu. im not sure exactly how it works but I was able to access my files from ubuntu. i haven't tried writing to the drive yet but it should work. hope this helps
ps- i'm on ubuntu 9.04

---

### Post by ctphinest on 2009-05-19
> Ok guys, I think I found a temporary fix on how to mount the blackarmor in ubuntu. I found that you can mount the drive if you first unlock it using a windows VM. I used virtualbox because it has USB support.As soon as I connected the drive to my VM i entered in my pw, the drive light came on and it somehow was mounted to ubuntu. im not sure exactly how it works but I was able to access my files from ubuntu. i haven't tried writing to the drive yet but it should work. hope this helps
ps- i'm on ubuntu 9.04     I got this method work for me too, but had to add a couple more intermediate steps because I was was using the virtualbox ose (the version that comes installed with ubuntu 9.04).  I'm fairly new to Ubuntu, so I appoligize if some of my steps are not neccessary, but this is what i did in order to get it to work for me.

1) download the most recent non-open source version of virtualbox at their [website]("http://www.virtualbox.org/wiki/Linux_Downloads") .  I had to first remove the ose version before I could add the non-open sourse version - however the files relating to the virtual os were not deleted, so i did not have to reinstall the os in virtualbox (xp for me).

2)  You need to add yourself to the vbox users group.  For ubuntu 9.04, this can be done as follows (there is also instructions for earlier versions virtual box help).  I will copy the instructions below that were originally posted by member [rfs1970]("http://ubuntuforums.org/member.php?u=175564") in this [forumn]("http://ubuntuforums.org/showthread.php?t=1155643")

    a)  open terminal
    b)type in terminal:   sudo gedit /etc/fstab
    c) the fstab text files will open. At the end of the file add this line:
         none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
        
      note: (46 is the standard ID group for plugdev in ubuntu 9.04)
    
    d) save the file
    e)type in terminal:  sudo mount -a

3)  Open virtualbox and select the setting tab for the virtual os you want to use (the virtual machine must be closed out to enter settings)
4)  in the left hand pane click on USB.
5)  click the box to enable USB controller
6)  on the right side, click on the usb icon with the green plus sign.  A list of USB connections will pop up.  From there, you should see an option for maxtor black armor.  Click on it and then click the check box to next to the newly added blackarmor in your usb device filters list.
7)  click ok at bottom and then start up your virtual envirnment
 8 ) once the virtual system starts, go to the Devices menu at the top of the screen and select maxtor black armor - you will be promted for the password and then you're in!  Once you unlock the system you can then access in in ubuntu or your virtual windows system.

Thanks stalefist and rfs1970 for your posts!

---

### Post by sdotsen on 2009-12-16
Guys, I had one of my co-workers helped me, this is what we did.

We tried everthing, DD, fdisk, etc ... make sure the drive is unmounted.

Run "parted" and create a new label (I chose msdos - I think this was the default). Create the parition, blah blah. Exit parted and go run fdisk. Delete the partition and re-create a new one but this time make it a linux partition. I'm not sure if this step is needed, but we did it just to see if we were able to manipulate the drive using fdisk (we couldn't originally - you guys found out the hard way like we did). Besides, fdisk showed that it was an NTFS filesystem so re-creating it and making it ext3 was required.

Ok, once that's all done, mkfs the damn thing and mount it. Viola! I was ready to sell the thing on ebay but luckily my co-worker was able to help

---

### Post by ordirules on 2010-03-03
There is a problem if you're not in the vboxusers group, then the "Black Armor" usb device is unclickable!
The guy here has a fix for this:
[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

Basically, the idea is u need to add yourself to the vbox users group. (you can also do this by just adding yourself manually in the /etc/groups file if you want to get more familiar with Linux)

Thought I'd post this to help, works great for me, I've been looking for a solution off and on for almost a year!
(dual boot is no fun)

ordi

---

### Post by lnthai2002 on 2010-04-11
sdotsen, can you give more detail of what you did to remove the encryption and reuse the disk as normal external usb drive? I tried to parted, it fail the first time then i retried and now this is what i got:
```

GNU Parted 1.8.8.1.159-1e0e
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Error: /dev/sdb: unrecognised disk label                                  
(parted)

```

---

### Post by LoungeLizard on 2010-06-03
Any updates from anyone???  I've tried everything - even physically removed the drive from the chassis and directly plugged to mobo.  Nothing works for me.  Parted gives me the same error as lnthai2002.  And it matters not whether I'm plugged via USB or directly as SATA.  Every time drive is unplugged from a Win workstation (will not work on Windows Servers, whether VM or Native, either - Maxtor's ridiculous manager program is just stupid!) - the "unlock" directive goes away and the drive "locks".  I did some research on FDE drives (which this is) - but Seagate did some crazy stuff to force the drive's encryption and will ONLY work if connected to it's little USB circuitboard and connected to a Win XP or Vista or Win 7 workstation via USB and must run Maxtor's Manager to unlock.  Even running Seagate's "SeaTools" FDE utility will not work.  What a PITA this drive has become! :mad:

da Lizard...

---

### Post by lnthai2002 on 2010-07-20
after a while researching in anger, i finally smashed the cover and took out the drive. I though the circuit board is responsible for forcing the encription but i was wrong, pluggin it to a sata dock only show that it's not initialized. I want to replace my ps3 disk with this one but no hope. This document [http://www.seagate.com/staticfiles/support/disc/manuals/notebook/momentus/5400_3/100443773b.pdf](http://www.seagate.com/staticfiles/support/disc/manuals/notebook/momentus/5400_3/100443773b.pdf) (section 1.2.1) shows how this **** is built. I guess other than toss it to the garbage, there is noway i can reuse this.

---

### Post by lnthai2002 on 2010-07-20
Another document [http://www.seagate.com/staticfiles/support/sedqual/MB595_1_0905US_SelfQual.pdf]("http://www.seagate.com/staticfiles/support/sedqual/MB595_1_0905US_SelfQual.pdf") indicates that the drive has 2 security modes: one receives the password from BIOS and the other from third party software - I suppose the maxtor manager is one. I tried to hook it to my thinkpad and set the password as i did with maxtor manager but i still can't touch the disk.

---

### Post by Dwnshft on 2011-01-12
So, Has anyone come up with a easy method of unlocking this POS drive?  I just recently decided to try Ubuntu from Win 7 and so far I like it. However, I can't make the switch from my dual boot to standalone Ubuntu 10.10 if I can't transfer over my files.
 
Even if someone has a work around for eliminating Win 7, keeping ubuntu installed and then being able to transfer over my files w/o havingto use the stupid Black Armor drive then I'll take that too.

---

### Post by TonMoan on 2011-09-28
I have a maxtor black armor 160gb with encryption.  I've been wanting to turn it into a regular usb drive since I got it but I am to afraid to mess with it because I might brick it.  sdotsen gives me hope but those arent very good instructions.  I can use gparted(a virtual machine unlocks it) but I'm not sure about fdisk.  I guess I'll just buy a regular one and keep the black armor encrypted if I cant dump that encryption.

---

