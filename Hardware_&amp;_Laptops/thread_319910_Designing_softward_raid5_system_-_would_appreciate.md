---
title: "Designing softward raid5 system - would appreciate input"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by ktulu1115 on 2006-12-16
Ok-

As I'm sure most other users on here have experienced at one time or another, my main storage drive is reaching capacity (again).  Didn't think I could fill up 400gb so quickly...  but anyways.

I've decided to bite the bullet and design a proper storage system from scratch.  Right now I just have a single drive, basically zero redundancy...  not good.  My main requirements are cost efficiency, along with at least some redundancy and room for expansion.  I thought two 750gb's on RAID1 would be nice, but pricey.

I finally decided on a software RAID5 solution - I have an old Athlon64 3200+ on a K8V SE Deluxe laying around with some spare RAM (at least 1gb, maybe more).  It has 4 SATA ports on it (2 standard, 2 hardware raid), I'm thinking about getting 4 x 250gb drives, giving me 750gb total.  I'm fairly certain that would be plenty of CPU horsepower for this.  Idle cycles will probably be consumed with BOINC, but IIRC that CPU supports throttling which I may enable.

The only thing I'm realizing is that I don't have any room to expand to more drives - to increase capacity I'd have to either replace all the drives with larger ones, or buy another controller card...  not a big fan of either option but the only ones available.

Comments/suggestions/concerns?  I'd appreciate any input.  I setup software RAID1 on a Fedora server box 4 years ago at my last job, but that's the extent of my experience with software RAID on linux.  Thanks!!

---

### Post by pwrstick on 2007-01-20
Hello,  I've been doing the same thing as you, and with similar considerations.  Right now I have a RAID5 in 6x200GB SATA drives.  My system is a 1.8GHz Sempron with 512MB RAM and it runs just fine.

I think one of the limiting factors in our case is, well, our case.  I.e. how many drives you can hold without compromising temperature.  But if it comes down to it I think your system is plenty powerful to run another software raid should you need to expand.  I'm sure there'd be some issues if you were doing constant heavy writing to both arrays, but it sounds like you're using it as NAS just like me.

---

### Post by ktulu1115 on 2007-01-26
First of all, thank you for the response.  Glad to hear it works well for your need - I actually ended up ordering the parts for my system shortly after writing that initial post.  It works wonderfully well, quite impressed with the performance and everything.  Threw on Edgy server edition, configured the RAID and all up and running in a matter of minutes.  I put together a NewEgg public wishlist of the items I ended up going with - [http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=4426748](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=4426748)

As for cases, I must also say that the new Coolermaster SATA hot-swap file server case I went with is nothing short of amazing - zero temperature issues period.  Sure, for my use the hot-swap feature isn't essential, but it certainly keeps the drives plenty cool.  The only minor issue that may exist is that it supports 4 drives max, but that wasn't a problem for me.

Hope this information can be useful to anyone else out there designing a similar system!

---

### Post by gurgle on 2007-03-06
is software raid working in ubuntu? I thought the wiki said that raid5 isnt supported yet. Anyone got a howto?

---

### Post by rayray2030 on 2007-03-06
I've gone down the same road as you are trying to do here and I recommend you pick up one or more of these cards for your SATA drives:

[http://www.newegg.com/product/product.asp?item=N82E16815124020](http://www.newegg.com/product/product.asp?item=N82E16815124020)

I picked up 2 to support 5x250gb drives in software RAID 5.  This way I can keep adding hard drives as the need arises.  Also make sure you get a decent power supply to power your stable of drives.  From what I understand I believe processing power plays a small role in your performance because the proc needs to do the RAID5 xor'ing but I believe most i/o bottlenecks will be still be in the network so you may not even notice any performance increases due to processor/memory unless you are supporting a lot of simultaneous read/writes.  Anyone care to give the skinny on how much processor affects software raid 5 performance?

---

### Post by gurgle on 2007-03-06
Thanks a lot for the help. According to this article:

[http://arstechnica.com/guides/buyer/guide-200701.ars/1](http://arstechnica.com/guides/buyer/guide-200701.ars/1)

The processing isnt too bad with RAID5. From what i have gathered doing some research, it is in fact pretty minimal with modern processors.

If I have this MB:

[http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=310](http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=310)

Do I need another SATA card? I have 6 slots already.

---

### Post by ktulu1115 on 2007-03-06
> **gurgle said:**
> is software raid working in ubuntu? I thought the wiki said that raid5 isnt supported yet. Anyone got a howto?
I'm not sure why the wiki would say that...   software raid5 is supported quite well.  I was able to create the RAID itself during the install process...  I'm not 100% sure which partition editor is used in the Ubuntu server install process, but it allowed me to create the raid array itself, and that was basically the whole part of the process.  Everything else was a basic server install plus some NFS stuff.
> **rayray2030 said:**
> From what I understand I believe processing power plays a small role in your performance because the proc needs to do the RAID5 xor'ing but I believe most i/o bottlenecks will be still be in the network so you may not even notice any performance increases due to processor/memory unless you are supporting a lot of simultaneous read/writes.  Anyone care to give the skinny on how much processor affects software raid 5 performance?
I will agree with that.  Processor plays a relatively small role while the array is up and running, however during an initial array build/rebuild CPU will be taxed.  Under normal circumstances, CPU usage seldom reaches above 30% or so IIRC, and this is on an Athlon64 3200+ idled down to 1Ghz.  The bottleneck is certainly the network in this case.

---

### Post by gurgle on 2007-03-06
Did you setup the RAID in bios first or did you just let the ubuntu install handle it for you?

---

### Post by ktulu1115 on 2007-03-06
> **gurgle said:**
> Did you setup the RAID in bios first or did you just let the ubuntu install handle it for you?
My setup was software-based, so there was no BIOS.  I manually created the array during the install process in the disk partitioning/setup portion of the server-based Edgy release.

---

### Post by gurgle on 2007-03-06
did you just follow the wiki? i think i might play around with it this weekend to see if i can get it setup.

---

### Post by ktulu1115 on 2007-03-07
> **gurgle said:**
> did you just follow the wiki? i think i might play around with it this weekend to see if i can get it setup.
Didn't follow any wiki - just configured the RAID during the Edgy server install process - the partitioner allowed me to create the array right there.  Which wiki are you referring to?, I'd like to take a look at it.

---

### Post by gurgle on 2007-03-07
[https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

I think I am going to just try it out with some hard drives I dont care about. We will see how it goes! Which RAID version did you choose?

---

### Post by ktulu1115 on 2007-03-07
> **gurgle said:**
> [https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

I think I am going to just try it out with some hard drives I dont care about. We will see how it goes! Which RAID version did you choose?

FTA: > This is *NOT* for people with new, blank hdds. For you it is much easier IMHO to set them up using linux software raid

I set mine up during a new fresh install on a new box, so the article did not apply in my situation.  Used RAID5 for my setup - 4 x 250gb drives.  I would try using the software raid, it's fairly easy to set up (during the install process at least).  Let me know if you have any troubles.

---

### Post by ktulu1115 on 2007-03-07
I also noticed that the wiki mentions Warty and Dapper - I have a feeling this information is outdated somewhat, not sure if it's needed for newer releases.

---

### Post by gurgle on 2007-03-07
oh i just posted that article for you - I was reading wiki stuff. 

It sounds pretty straight forward now. I am going to get 2 of those SATA pci cards and hook them up. Cant wait to get this set up with my new c2d system! I love gig ethernet.

---

### Post by ktulu1115 on 2007-03-07
> **gurgle said:**
> oh i just posted that article for you - I was reading wiki stuff. 

It sounds pretty straight forward now. I am going to get 2 of those SATA pci cards and hook them up. Cant wait to get this set up with my new c2d system! I love gig ethernet.

Best of luck.  I'm not so certain you would need any additional SATA cards for software RAID...  if you wanted to save some $$ - as long as you have enough ports on the motherboard and Linux recognizes the drives, it should work just fine.  I'd be interested to hear your results setting up the array - if you don't mind posting your results after all is said and done.

---

### Post by gurgle on 2007-03-07
absolutely. I only have 2 sata ports on the dell i am installing the array in to, so the pci cards are required. oh well, i will have extra room to expand if need be.

---

### Post by gurgle on 2007-03-08
Also, do I need to follow this howto:

[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

Or will the server install disk create teh raid for me? 

How would I then go about expanding the array?

---

### Post by ben.s on 2007-03-18
I have an old tower case (AOpen HX08 ) that I converted into a NAS.  It's running CentOS 4 (but my desktop is Ubuntu :)) and I've got a crazy hodgepodge of disks in there.  What I did is I took the two 160GB ATA disks I had in my desktop (upgraded them to two 320GB SATA disks), the 200GB ATA disk I had in my MythTV PVR box, and a 200GB SATA disk I had for storage on my mail/web server (yes, these are all in my home setup, I like to tinker :)).  The motherboard I'm using for the NAS doesn't have any SATA ports so I picked up a couple of cheap SATA PCI expansion cards (about $30 each) so now I have the four on-board ATA ports and six SATA ports on the expansion cards.

I initially set up the array using only the ATA disks (I needed to move the contents of the SATA disk to the NAS after setting it up).  I formatted it JFS and used the information [here]("http://www.redhat.com/magazine/022aug06/departments/tips_tricks/") and [here]("http://scotgate.org/?p=107") to grow the array without losing the data.  It was a little harrowing, but it worked without a hitch.  It worked *so* well, in fact, that I bought a couple more 160GB disks (they're stupid cheap now) just yesterday.  I'm going to grow the array by another disk and use the other as a hot spare.

Another project to check out is [http://www.freenas.org/]("http://www.freenas.org/") -- I tried it out and it's very cool (the ability to install it on a 32MB thumb drive is *very* handy).  I decided to go with CentOS instead so I can replace the aforementioned mail/web server with it.  

It's been up for a month now and it's working quite well.

---

### Post by ktulu1115 on 2007-03-18
> **gurgle said:**
> Also, do I need to follow this howto:

[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

Or will the server install disk create teh raid for me? 

How would I then go about expanding the array?
That is entirely up to you; if it's a new machine/install, you can load Ubuntu then follow the instructions, or you can configure the RAID during the install process itself - I know the server version has support in the partition editor while in the install...  IIRC, the one that came on Edgy server was similar to gparted but console-based instead of GUI.

...actually I just realized I still have a screenshot (sorta) of the partitioning process during my install:

[[IMG]http://img458.imageshack.us/img458/9264/img0187smallqu7.th.jpg[/IMG]](http://img458.imageshack.us/my.php?image=img0187smallqu7.jpg)

---

### Post by gurgle on 2007-03-21
cool. i am goingto try making a raid tonight - thanks for the growing links ben. anyone else have experience with growing the raid, or swapping out disks?

I found this article too, hope it helps someone:

[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)

---

### Post by gurgle on 2007-04-05
OK, i created my RAID with the server install of Edgy. Everything seemed to go fine, I installed wedmin, so here is my "Linux RAID" page:

**RAID device options**     **Device file** /dev/md0   **RAID level** Redundant (RAID5)   **Filesystem status**  Active but not mounted   **Usable size** 1465151808 blocks (1398 GB)   **Persistent superblock?** Yes   **Parity algorithm** Default   **Chunk size** 64 kB   **RAID status** clean   **Partitions in RAID**  SCSI device A partition 1 
SCSI device B partition 1 
SCSI device C partition 1 
SCSI device D partition 1 
Any clue as to why it is not mounting? When I set it up in the install, I had it mount to:
/storage

---

### Post by CarlosinFL on 2007-04-06
Guys - I am also looking to setup "software RAID" on my Ubuntu 6.10 install. I have two identical drivers that I want to setup as a RAID0. 

I have looked through this thread and I am really unclear how I create a software RAID when it comes up to the partitioner in regards to make my 2 x 250GB S-ATA drives as a RAID0 array.

Obviously one will be /dev/sda and the other will /dev/sdb.

What is the 1st step or where do I start? Should I create a software RAID 1st and or should I manually partition /dev/sda like setup sizes for /, /boot, /var, /usr, swap and so on...

Thanks for any info or points in the right directions!

---

### Post by CarlosinFL on 2007-04-06
This is the installer showing the two drives: 

As you can see I have no partitions on them but I am really confused as to where I begin. I would assume that the partition table I am looking to setup will just show /dev/md0 which will equal 500GB of disk space if I do RAID0 on sda and sdb.

[IMG]http://img407.imageshack.us/img407/6554/img1921bw8.jpg[/IMG]

---

### Post by ben.s on 2007-04-08
> **Carlwill said:**
> Guys - I am also looking to setup "software RAID" on my Ubuntu 6.10 install. I have two identical drivers that I want to setup as a RAID0. 

I have looked through this thread and I am really unclear how I create a software RAID when it comes up to the partitioner in regards to make my 2 x 250GB S-ATA drives as a RAID0 array.

Are you absolutely sure RAID-0 is what you want?  RAID-0 offers *no* redundancy and *no* fault-tolerance: if *EITHER* disk fails, you lose *EVERYTHING*.  Not worth it for the minor performance increase IMHO.  If you want performance and redundancy, your best bet is RAID-10 (i.e., a mirrored pair (RAID-1) of striped (RAID-0) disks).

---

### Post by CarlosinFL on 2007-04-12
Guys - where in the Ubunut / Kubuntu installer is there an option for "Software RAID"? I have ran the installer and it appears to only be a GUI installer which is more annoying IMO however I don't see where it allows you to select a partition for RAID anywhere. I walked though steps 5/6 and become frustrated. In Debian it is very simple. You create a partion and then select type and select SOFTWARE RAID.

I can't find this in Ubuntu.

---

### Post by ktulu1115 on 2007-04-13
> **Carlwill said:**
> Guys - where in the Ubunut / Kubuntu installer is there an option for "Software RAID"? I have ran the installer and it appears to only be a GUI installer which is more annoying IMO however I don't see where it allows you to select a partition for RAID anywhere. I walked though steps 5/6 and become frustrated. In Debian it is very simple. You create a partion and then select type and select SOFTWARE RAID.

I can't find this in Ubuntu.
I know it was on the server install disk for Edgy...  it was part of the partition editor, allowed you to create the array right there.  If you scroll up I have a picture I took of the process itself.  I havn't tried it on a non-server install CD yet.

IIRC....  First you have to create the partitions on the drives, set them to 'software RAID' fs-type, then create the array(s) after that.  It was pretty straightforward to figure out from what I recall.

---

### Post by CarlosinFL on 2007-04-13
Ah - I found it. Ubuntu and Kubuntu only offer their LVM and RAID options built into the kernel that is supplied with the "Alternative CD" download .ISO.

I tried doing a simple RAID1 config last night and it failed to load GRUB and I got a error 17, can't load the partition. It was having a hard time finding where /boot was to load the kernel.

I then tried a quick reinstall of the OS on my machine still using the two identical S-ATA 160GB drives. This time I the same things as above except I created an extra partition on each drive making it a total of 3 primary partions per disk so /boot where "Grub" is stored would not be a part of the RAID. The partition looks something like this now:

/dev/sda

- dev/sda1 = 512 MB swap space
- dev/sda2 = 1024 MB Ext3 mounted to /boot (bootable enabled)
- dev/sda3 = 158.6 GB RAID Partition

/dev/sdb

- dev/sdb1 = 512 MB swap space
- dev/sdb2 = 1024 MB Ext3 not mounted or used in FSTAB
- dev/sdb3 = 158.6 GB RAID Partition

/dev/md0 = 158.6 GB Ext mounted to /

Now as above the system booted fine and here is what I found in /proc/mdstat

```
root@server:/home/cwilliams# cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda3[0] sdb3[1]
      154794240 blocks [2/2] [UU]
      [======>..............]  resync = 33.5% (51960256/154794240) finish=2.0min speed=828699K/sec

unused devices: <none>

```

It appears to be syncing the two devices but none the less both disk show up status and I think I have a functioning RAID1 setup, no?

Do you know why it could not load Grub if I added /boot into the RAID1 /dev/md0 partition?

---

### Post by ktulu1115 on 2007-04-13
> **Carlwill said:**
> Ah - I found it. Ubuntu and Kubuntu only offer their LVM and RAID options built into the kernel that is supplied with the "Alternative CD" download .ISO.

I tried doing a simple RAID1 config last night and it failed to load GRUB and I got a error 17, can't load the partition. It was having a hard time finding where /boot was to load the kernel.

I then tried a quick reinstall of the OS on my machine still using the two identical S-ATA 160GB drives. This time I the same things as above except I created an extra partition on each drive making it a total of 3 primary partions per disk so /boot where "Grub" is stored would not be a part of the RAID. The partition looks something like this now:

/dev/sda

- dev/sda1 = 512 MB swap space
- dev/sda2 = 1024 MB Ext3 mounted to /boot (bootable enabled)
- dev/sda3 = 158.6 GB RAID Partition

/dev/sdb

- dev/sdb1 = 512 MB swap space
- dev/sdb2 = 1024 MB Ext3 not mounted or used in FSTAB
- dev/sdb3 = 158.6 GB RAID Partition

/dev/md0 = 158.6 GB Ext mounted to /

Now as above the system booted fine and here is what I found in /proc/mdstat

```
root@server:/home/cwilliams# cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda3[0] sdb3[1]
      154794240 blocks [2/2] [UU]
      [======>..............]  resync = 33.5% (51960256/154794240) finish=2.0min speed=828699K/sec

unused devices: <none>

```

It appears to be syncing the two devices but none the less both disk show up status and I think I have a functioning RAID1 setup, no?
From the looks of it to me, yes, the RAID1 is configured correctly.

> 
Do you know why it could not load Grub if I added /boot into the RAID1 /dev/md0 partition?

Not entirely sure, but if I had to guess I'd assume that Grub doesn't have capabilities to read mirrored devices (RAID arrays), it only knows how to read (and therefore boot) from standard block devices (hard disks) with certain filesystems (EXT2, EXT3, XFS/Reiser maybe, etc).

On my system, I have the root partition as /dev/md1 (RAID1 composed of hdb1 & hdc1), but Grub is set to boot from /dev/hdb1 instead of md1.  I havn't tried to boot from /dev/md1, but I suspect I would get the same error as you.

The only thing that I wondered was if booting from /dev/hdb1 would have any effect on the RAID array, ie: root is mounted on /dev/hdb1...   I'm assuming the kernel is smart enough to propagate all changes over to /dev/hdc1 even though it didnt boot from md1, follow what I mean?

---

### Post by gurgle on 2007-07-03
I think my software raid5 died :( 

I set up this software raid with edgy server edition, and everything seemed to work fine. Now, one of my disks isnt showing up, and now it mount even mount. This morning it was working fine. My info:

mdadm: md device /dev/md0 does not appear to be active.

evan@server:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4863     1622565    5  Extended
/dev/hdb5            4662        4863     1622533+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect
evan@server:~$

---

