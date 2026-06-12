---
title: "Slave Drive Not Recognised IN UBUNTU?"
date: 2008-05-29
forum: Hardware
---

### Post by davidkyn on 2008-05-29
Slave Drive Not Recognised IN UBUNTU?

Any Ideas as to why Ubuntu might of droped the slave drive.  I actually reinstalled in the hope if may of picked it up again but no luck.  Basically I am talking about an IDE drive on the same cable as the OS (Ubtunu) The jumper on the back of the slave is in the slave postion and the primary is set to mater with slave present.  BIOS has detected it which would prove the jumpers are right and ide cable working as well.

I will test the HDD on the secondary controller to see if that works...
Do you think I have to mess with the conection options like LBA or sectors ect...instead of auto????
Weird

I will go as deep as I can and check back with you all shortly...
Any Ideas would be welcomed...
Thanks:confused:

---

### Post by cdtech on 2008-05-29
List the output of:
sudo fdisk -l

This will help us help you.

---

### Post by davidkyn on 2008-05-29
Well it's very URGENT NOW...it seems windows cant see it anymore only asking if I want to format it!!!!!!

It has over 140GB of Music on it and it's also doing it to a 500GB drive now that was on the pci-ata-controller that did not seem to work.  Now I suspect that Linux has written somthing somehow in the partition tables and now I have probably lost 500GB of Divxs :confused:

here is the output anyway...I am so much in trouble...PLEASE HELP i dont want to format these drives?????????????????
Hang on..I will explain one last thing...although you can see the partition types of HPFS/NTFS in the out put...bear in mind in Acronis Disk Director the two that are now not reading in Ubuntu read as NTFS/HPFS with the readable ones only as NTFS????????

PLease anyone, I beg you...I need a solution without formating these drives...I have to beg to keep ubuntu on now as well as save all this data:confused::confused::confused::confused:the 200gb is my music and cant be accessed and one of the 500 is my movies not sure which one though in this output...? but both cant be mounted in ubuntu or windows anymore?

home@UBUNTUFileServer:~$ sudo fdisk -l
[sudo] password for home: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c064440

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4acc4acb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4feb4fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d53a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS
home@UBUNTUFileServer:~$

---

### Post by davidkyn on 2008-05-29
Could it be to do with the Disk Identifier??????????
can they some how be re-identified?

---

### Post by swerdna on 2008-05-29
> **davidkyn said:**
> Well it's very URGENT NOW...it seems windows cant see it anymore only asking if I want to format it!!!!!!

It has over 140GB of Music on it and it's also doing it to a 500GB drive now that was on the pci-ata-controller that did not seem to work.  Now I suspect that Linux has written somthing somehow in the partition tables and now I have probably lost 500GB of Divxs :confused:

here is the output anyway...I am so much in trouble...PLEASE HELP i dont want to format these drives?????????????????
Hang on..I will explain one last thing...although you can see the partition types of HPFS/NTFS in the out put...bear in mind in Acronis Disk Director the two that are now not reading in Ubuntu read as NTFS/HPFS with the readable ones only as NTFS????????

PLease anyone, I beg you...I need a solution without formating these drives...I have to beg to keep ubuntu on now as well as save all this data:confused::confused::confused::confused:the 200gb is my music and cant be accessed and one of the 500 is my movies not sure which one though in this output...? but both cant be mounted in ubuntu or windows anymore?

home@UBUNTUFileServer:~$ sudo fdisk -l
[sudo] password for home: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c064440

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4acc4acb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4feb4fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d53a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS
home@UBUNTUFileServer:~$

You've got three ntfs drives recognised here. The ntfs drives are being recognised. Perhaps all you have to do is mount them. Have you tried mounting them using ntfs-3g?

Swerdna

---

### Post by davidkyn on 2008-05-29
I'm not quite sure what you mean by ntfs-3g...The whole reason I made this post was because Ubuntu cannot mount the drives in desktop mode.  The partition table is most likely unreadable for some reason.  Windows can see them, but no longer recognizes them as a usable drive for data storage and simply wants to format them as if they are unallocated.

Although Ubuntu can see three NTFS drive only one of the is mountable.  In fact when you go to PLACES on the top panel it cant see the other two at all.

Acronis Disk Director does not seem to help as it is more of a partition manager not a diagnostic & or repair tool...I will try Partition Table Doctor tomorrow in the hope that it can repair the drives without wiping the drives or I may even try to load "DSL" Damn Small Linux on the drives themselves and if successful; copy the data (if still available) onto another FAT32 drive...

I may not be making sense because I am struggling to make sense of it all myself...what I can tell you, is that this sort of thing is quite comon, that is to say, many people come away from linux with partition table problems where there drives no longer work.Just because they are not mounted properly in Linux should not mean that windows can longer recognize them as a usable drive!  How it takes place, I am open to suggestions...but this has happened to me before...its just that this time, I am looking at loosing around 700GBs of data I have collected over years.  So forgive me If I get emotional about that. Linux should read them as it does the other working one anyway...There is obviously a problem of some sort...the output in fdisk above is being read via a dos type bios thing, yadda yadda...LOL take it what way you want...I'm just clutching at straws here...Just cause it gave the reading like that in the terminal, does not mean the Linux desktop is going to see them and in fact I tell you now that the nautilus directory does not show them at all but only one ntfs which I click on to mount to the desktop to then use.

aaarrrggghhhhhhhhhhhhhhhhhhhhhhhhhh Grrrrr............I know your trying to help...it's me not understanding is all & this time I don't believe words like emotional should be thrown at me & Dean will hopefully still be holding his big stick at bay...LOL

Thanks anyway dude................perhaps your onto something there...please could you explain a little more on that...I have to go to bed...before I start reading people the wrong way, and I be misunderstood.

Peace out all....ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ

---

### Post by swerdna on 2008-05-29
> **davidkyn said:**
> 

Thanks anyway dude................perhaps your onto something there...please could you explain a little more on that...I have to go to bed...before I start reading people the wrong way, and I be misunderstood.

Peace out all....ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
Like for sdd1 you make a directory for the files to be accessed fro, say /sdd1. Use this console command:
**sudo mkdir /sdd1**

Then you "mount" the drive in there. Use this console command:
**sudo ntfs-3g /dev/sdd1 /sdd1**

Then navigate to the directory /sdd1 in Nautilus and presto. there are the files.

(maybe....)

---

### Post by davidkyn on 2008-05-29
I'll take what I can get for now...system just froze brb...

---

### Post by davidkyn on 2008-05-29
home@UBUNTUFileServer:~$ sudo mkdir /sdd1 
[sudo] password for home: 
home@UBUNTUFileServer:~$ sudo ntfs-3g /dev/sdd1 /sdd1 ntfs-3g: 
Failed to access volume '/dev/sdd1': 
No such file or directory Please type 'ntfs-3g --help' for more information. 
home@UBUNTUFileServer:~$ 

Beats Me..........?

---

### Post by davidkyn on 2008-05-29
SOLVED
Thanks to Partition Table Doctor!
Somehow they were set to active partitions...anyways onto my next problem!

---

### Post by davidkyn on 2008-05-30
Heres a little more in exactly what kind of happened and how drives sometimes get their partition tables all messed up:

Hey Swerdna,
Thanks for the cooling off Period...I needed it :rolleyes: Feeling much better now.  Well I have a much clearer picture to the problem, however I may still be wrong...non the less I have "MY" files back now :P 
[center]
[size=3]**PLEASE ALLOW ME TO NOW EXPLAIN**[/size][/center]

I'll try to explain as best as I can...After installing "Partition Table Doctor V3.0" on my son's XP machine and running a test on the effected HHD's, the program recommended running its Boot Fix option to repair the apparent "corrupt boot sector" which changed it from NTFS 7 to NTFS 8. I actually saw these options in Acronas Disk Director under the oprion to change partition type and I almost then was going to test it, but was to scared to try it.  In hind sight, having noticed that the effected drives where somehow listed as active, I can't help but wonder if the  numbers 7 & 8 simply switch the drives from being active to non-active? Can't help but wonder..........anyways WHAT A GREAT PROGRAM "Partition Table Doctor" got my going again.

**OK Heres the thing that got me thinking even harder:**[u]
I re-installed the HDDs back into my Linux machine and low and behold she's all apples :D . SO for whatever reason...more likely to address another problem...I decide to re-install Ubuntu, but this time round I look forward to actually learning more as I do with all the grub errors and so forth I had been getting. 

Because of the HDD issues I had experienced and the anticipated grub errors I was getting, I kind of made took note on the back of an old envelope as I began.

I checked all HDDs in BIOS to be present and accounted for!

After loading Partition information I took note, that Ubuntu had infact seen all my drives and I then selected the apropriate Drive under the Guided Option.

Upon Restart and the CD drive ejecting the Disc I replaced it with another called “SUPER GRUB” which I downloaded of the internet and burnt to disc for the purpose to mess with Grub itself.  Why am I doing this??? BECAUSE this is really my second install of Ubuntu since putting back in my repaired HDD's.  What happened on the first attempt is that I got an error 17 & an error22...I also got an error 31 but I dont quite know how I got past that one. BUT HERES THE THING...after I corrected error 17 by editing the first line of the kernal.......by changing root (1,0) to setup (0,1) and then hitting “B” to boot which resulted in error 22 which I correct by once again editing the first line of the kernal by changing.....(& this is by memory)...I think my first editing attempt reverted back from setup to root....so I changed that again, as I know from experience, that is how I fixed error 17 in the past; but I also changed the (1,0) to assist in finding the right HDD to boot off. So because my first edit attempt reverted during the reboot and now I have to correct the HDD numbers for error 22 this is how I did that.......from.....root (1,0) to setup (0,1) and hit “B” to reboot and SUCCESS.............Ubuntu laoded without hitch due to the fact that I anticipated most of these errors this time around and I dealt with them without to much messing around.

Why am I telling you all this, and what does it mean. Well I have a theory & it's only my thoery which as you know is not worth much anyways...As I stated or have done so here or in Ubuntu this thing about HDD's going corupt after people mess with Linux is TRUE...not onlu for me but also a lot of friend I know who wont touch Linux because of the HDD issues they have had previously...Ussually to do with being unable to load windows, but more so not being able get back into the data.......WELL I THINK THE GRUB ERRORS could play a big part in it, as It was only after I 1st put the effect HDDs back into my Linux machine and went through it all without really knowing wat to do, then research how to fix those errors, which meant I chnged a lot of o's & 1's editing error 22........that I can't help but think once again in hind site at how one minute my drives were not active and the next they were that it may very well of been during the Grub issues that the partition tablbles were curupted?

As I said it's all just a theory and I've tried very hard to keep a not of it all and thing it over and ponder on my own as well as my mates issues............sufice to I (sudo gedit /boot/grub/menu.lst) and corected the lines apropriate to my machine and have had no issues....well after I updated the kernal, I re-edited the boot log again and then was all fine also.

I may be completely wrong...who knows...I have a pretty good idea on the types of conflicts that can arise with my hardware and am now armed with some reasonalbe tactics to deal with problems that may arise........I think my thought patterns work well enough for me & can only hope others out there dont mind sifting through them to at least pass the time.

I've got stacks to learn, I had a fright, but have learnt from it. I hope some of you will continue help as you have done...I'll take the good with the bad as others do in such forums.

It's been insightfull to say the least...thankyou all!

---

