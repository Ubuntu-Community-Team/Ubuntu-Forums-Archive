---
title: "Error 18"
date: 2005-01-19
forum: Installation &amp; Upgrades
---

### Post by MidiBoer on 2005-01-19
I installed Ubnuntu and everthing went smooth except the network installation, which I cancelled when asked.

Ubuntu ejected the cd and said it will restart.

Upon restart I get the following message:

[B]Grub loading, please wait ...
Error 18[/B]

And then the system just hangs.

Plzzzzzzzzzzzz help. This is my first experience with Linux and I hoped for something better.

[email]bladmeester@midiboer.co.za[/email]

---

### Post by hardcandy on 2005-01-19
Look in your bios and see if there is an option for Master and Slave disks. If it says none turn it on. Another thing is to make sure Grub installs itself during installation into the MBR (master boot record). Another thing is to update the bios because when grub tells the bios how large the disk is, the bios says "I don't handle disks that large". 
Any one of the 3 could be the solution.

---

### Post by Buffalo Soldier on 2005-01-19
Hope you won't mind telling us more about your installation:

- Did you use the whole harddisk for Ubuntu? Or are you dual booting with Windows?
- During installation, the installer asked whether you would like to install GRUB at MBR. What did you choose?
- How big is your harddisk and how old is your computer?

Refering to the GRUB Manual at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) 

It states that "Error 18" means,

> Selected cylinder exceeds maximum supported by BIOS.

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

If you're comfortable with changing BIOS settings, you could check harddisk mode.  If it's LBA or AUTO try changing it to NORMAL.

---

### Post by MidiBoer on 2005-01-20
Tx for the help. Changing the Hdd mode to normal seemed to do the trick.

 :D

---

### Post by sharkzf6 on 2005-01-24
I too got error 18 after initial install. I believe it's because I had a previous version of Linux (Debian Woody) installed on that drive which installed lilo in the mbr. My hope is that clearing lilo from mbr will reslove this problem. Ubuntu distributors should make this clear so newbs wanting to get into Linux don't have this problem. I would imagine it's not uncommon. I'll post my results after fixing this.

---

### Post by sharkzf6 on 2005-01-24
Fixed Error 18. it was the LBA setting in the BIOS which I consider very weak.

Also, the thing couldn't do a full install on the little 2 GB HD I tried to put it on because there wasn't enough room?! Heck, I've had 2 versions of Debian on that little drive with KDE and Gnome along with full versions of Open Office.org, Mozilla, T-Bird, games, all kinds of stuff....talk about bloated. Color me unimpressed....I'm sticking to Debian.

---

### Post by KiwiChris on 2005-03-31
That was exactly the problem I was having with my install...
Changed it from LBA to Normal and presto!

Thanks a lot guys \\:D/

---

### Post by Guillaume Lafrance on 2005-04-29
I got this error after install too. But, if I change the disk type, it doesnt do anything (except for "Large", which is what I think I need, since I have a 200GB HDD, where it just hangs). Should I modify the MBR?

---

### Post by jookie on 2005-05-21
Buffalo Soldier, I'm very thankfull, setting the disk in BIOS from 'AUTO' to 'CHS' ('normal') helped the GRUB to start. I can now boot the Ubuntu...
But I have also Windows XP on that disk and that was installed in LBA mode, so that XP won't now boot in CHS mode, when trying to start it GRUP says:

Booting 'MS Windows XP'
root (hd0,0)
Filesystem type unknown, partiion type 0x7
savedefault
chainloader +1

And it hangs... I think I'lll try to install LILO...

---

### Post by Jim Hanes on 2005-06-19
"Ubuntu ejected the cd and said it will restart. Upon restart I get the following message:

[B]Grub loading, please wait ...
Error 18"


[email]bladmeester@midiboer.co.za[/email][/QUOTE]

I had the same problem when doing a clean install of 64 bit Ubuntu on my new AMD 64 based desktop PC.  I found that I had accidentally left the jumper on the Hard Disk set to "SL".  Making it the Master fixed the problem.  Now I love Ubuntu Linux.

---

### Post by RSkog on 2006-03-24
I too got the same error when installing on a clean drive from the CD. On an old machine.

After some research I found the problem to be the BIOS didn't support the size hdd drive I have.

To fix the problem, I reinstalled off the CD. When getting to the partitioning I did not accept the automatic partitioning, but rather created a small partition at the beginning of the drive (the first partition). I made it 50 MB. Map this partition to "/boot", and proceed. Now the stuff Grub needs to load is reachable through the BIOS functions it uses and everything works fine.

---

### Post by Superschill on 2006-04-02
It did not for me.  I just tried to install Ubuntu, and it was all ok until i rebooted after the installation.  I also got error 18.  I changed the HDD to normal, but it still gave me the error.

---

### Post by Goweb on 2006-12-16
How do you change the hard drive to 'Normal'?

I get the error 18 as well on a PIII 933 CPU with a 160GB drive.

Thx!

---

### Post by bethnesbitt on 2007-01-16
I'm having this problem now.  I installed Linux XP, then a friend told me about Ubuntu, which I love.  When i first installed it it worked fine.  I had a problem with administrative problems, I did not go very far with any problems with installing anything, so I decided to start from scratch.  After the next install I got the error 18.

I read the page that was suggested, when I try CHS mode, it just hangs, my pc won't boot in CHS mode, I'm running a newer board with a 250gb hd.  I flashed my bios some time ago, that is upto date.  But what I did notice was that in my HD setting in bios, my hd read as 33gb when like I state it is 250gb.  The page says that it has to do with my bios problem not reading the same size as ubuntu which reads the size correctly.  I've flashed i've tried every setting.  The only thing I can think is to manually set my sector sizes in bios, but.... UGH i do not have this option.  ANybody else have any other suggestions?

I DON'T WANT TO USE MS NOOOOOOOOOOOOO

---

### Post by TekNullOG on 2007-01-25
I found a solution that I would like to share. It is not the best solution but it can be used when nothing else mentioned above works.

I have had tons of problems with the darn Error 18 message. I updated my bios and everything but nothing helped...

The only thing that works for me (and I really wished their was something else) is to install windows xp and then reinstall Ubuntu by erasing the whole disk.

Since it worked, I thought the problem was completely solved but it wasn't...

In the first few hours I had my Ubuntu installed, I played around with it a lot and installed tons of useless packages and preferred to reinstall it. To my surprise, the error 18 message returned and the only thing that worked (once again) was to install windows on the disk and then reinstall Ubuntu.

I am not a pro with computers so I have no logical explanation for this but I recommend trying it since it worked for me and it might save you time.

Good Luck
[Techno.FM Radio]("http://techno.fm")

---

### Post by Gizmokid2005 on 2007-01-29
New to these forums, and partially to Linux.  I have been running Ubuntu in a VM for a while now, but I decided it was time to run it Natively.  But I need to keep my Windows install as I have a lot of stuff on there that I need to keep and is winderz only.

Now, I had an issue with the IO-APIC that I got solved from another thread on here, but now after I install Ubuntu on my third partition of my drive I get error 18...I've deleted the said partition (including the swap, root, and normal partitions) and fixed the MBR for windows, and then tried to reinstall but I get the same error.  For some reason I remember doing this before and putting the root on my windows partition w/o it causing errors as it installed an actual boot selector before it would start either OS.

So, I'm not sure how to go about this...I have my Main windows drive (C:) backed up, and I believe I have my Program drive (D:) backed up, and the third partition is going to be my Ubuntu partition....so can I have Ubuntu use my main windows partition w/o deleting any information on it and having to reload?

Thanks in advance!

---

### Post by Curious65 on 2007-02-22
thanks to all of you who posted help tips. i put Kubuntu 6.1 on an older box today using a 100 GB HDD and had the same error 18 problems. with your tips i was able to fix the problem. ended up using a 5.8 GB boot partition. i've now got that, a 8.4 GB and a 91 GB. only the 91 seems to be seen as the other two show up as unmounted when the mouse rests on them. 

but that's ok. heck it's more than ok since the drive is easily large enough for what i want to do. 

anyway thanks again. i'm looking forward to learning all i can about Linux as a replacement for Windows.

---

### Post by bigfatdummy on 2007-04-25
Ok, so if I try and configure my own partitions what size is suggested. I have a 250gb drive. 

I was thinking 

100 mb for boot, 10 gb swap and the remainder for the rest

Any suggestions?

---

### Post by sjunior on 2007-05-12
For me was very easy…, I had 2 pin in my HD one in Master and the other in Slave (this is for Cable select mode) I only get off the PIN for Cable select in my Western Digital Hard Disk,  I am using only Master pin, it works. Sergio from México.

---

### Post by willux on 2007-06-03
Indeed, changing the setting for the hard drive to Normal fixed the problem for me too!  Thanks for the help.  Now I can enjoy Ubuntu...

---

### Post by Marko25 on 2007-08-07
Hi. New to the forums and new to Ubuntu. I have Ubuntu 7.04 (Feisty Fawn), and I've been having constant errors. I have a 1.60 GHz Pentium 4 Dell Dimension 4400... with a 300GB drive from Maxtor. I installed from Windows XP Home Edition as a permanent replacement. Heh, so much for that. This partitioning business is turning the inside of my computer into a living hell. I think my first install (I'm on my... fourth or fifth now) was a guided partition, 54% split. I came to the part where I had to restart. Ubuntu shuts down, ejects the disk, then says, "Press Enter to Continue." Enter doesn't work, so I'm forced to kill the machine manually (via holding in the power button.) I turn on the machine and get the Error 18 message. I tried to do the manual partitioning, but my brother-in-law is the IT expert, I'm just using trial and error here. I already lost everything on my hard drive. Please, *somebody* tell me how to manually partition my drive so this will all go away. I don't even know what the "swap" partition is. Please help.

**EDIT:** Wanna know how I'm typing this from Firefox in my new, working copy of Ubuntu "Feisty Fawn"? The best solution that worked instantly for me was downloading the alternate CD ISO file. Worked perfectly. It has a different installation method, but it hooks everything up right away, and I didn't even have to worry about those tormenting partitions. The alternate CD installed straight to my 500GB hard drive without any splitting or creating swap drives, and I must say, what a beautiful system. I love the clean interfaces and the awesome screensavers. Way to go, Linux!

---

### Post by RSkog on 2007-09-29
This is one wqay of solving it that worked for me:

When presented with the automatically chosen partitions select manual partitioning. Delete all the partitions. Add a partition. 50 MiB should be enough, but if you have lots of hdd space why not make it a 100 MiB. Select ext2 file system. And set the mount point to /boot

Now add another partition. Make it three times you RAM size and select it to be a swap partition.

Now add another partition. Make it occupy the rest of the disk. Selecte ext2 as the file system. And set the mount point to /. This will be where all the files exept for the files in /boot will reside.

Now go on with the installation.

This was done with the alternate installation cd. Don't know if it will work that same way with the Desktop cd.

/Richard

---

### Post by amileaway on 2007-10-30
I am getting error 18 and 17.

I have 320gb Sata drive. vista installed and 40gb sec, ubuntu installed. Installation went fine and then when I started I got error 18. Then I read some online added /boot then I get error 17. I dont know what the deal is. 

Here is what I get when I boot up with live cd with fdisk command. 

sk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39fc380c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         662     5314560   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         662       38914   307254272    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fbb9fbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris
/dev/sdb2              63         186      996030   83  Linux
/dev/sdb3             187        4865    37584067+  83  Linux

Normally error 18 is for BIOS problem that does not support large capacity drives. But thats not the case here  or im missing something. Can somebody help me out ? If I need to modify grub how can i do it by booting from live cd?

---

### Post by markp1989 on 2007-11-08
> **KiwiChris said:**
> That was exactly the problem I was having with my install...
Changed it from LBA to Normal and presto!

Thanks a lot guys \\:D/

thanks, this helped me out alot  when putting linux on my friends old comp for internet etc

---

### Post by Wyn on 2007-11-09
I changed my primary master from "user" to "auto" and it worked. THanx guys

---

### Post by ctsiow on 2007-12-01
Thanks guys, came back out of hospital to find my gutsy server dead following power probs. Searched after getting grub error 18 prob, played with bios and all ok. Once again the forums save the day!
Mark

---

### Post by bigtexjc42 on 2008-01-11
FYI, I have just encountered a week of this Error 16 and Error 18 business with 7.10 i386 install, and I would like to share my solution for those of you also struggling.

Briefly, here was my stall:  brand new NVidia MB with Quad Core Q6600 and an internal SATA running 64-bit Vista Ultimate, then an eSATA 750GB drive to hold many things, one of which a bootable Ubuntu 7.10 i386.  Problem - constant boot issues where system would not start for any one of the following reasons:

1)  Missing operating system
2)  Error 16
3)  Error 18
4)  GRUB Bootloader from within the Microsoft Bootloader (DO NOT EVER USE!!!!)

Solution:

Follow the advice of those telling you to create a small (250MB is fine) partition at the beginning of the drive containing the UBUNTU OS and then another partition for the actual OS (I used 20GB) and a third for the swap partition (I used 3GB).  Then go through the install using the alternate CD, and make sure you write to the MBR (master boot record) of the UBUNTU drive.

Make sure you go into your BIOS and select the drive with the UBUNTU OS as the first HD in the boot priority.  Otherwise (especially with a Vista dual-boot) you will be forced into the Microsoft Bootloader, which will FOUL UP YOUR hard drive (sda, sdb, etc) assignments in the GRUB bootloader.  Best to use the /boot/grub/menu.lst as your dual/multi-boot menu.  You can then edit the menu.lst file as you add more OS's to the list.

Hope this helps any of you others that happen on this thread as a result of the evil Error 18!!!!!

---

### Post by yoda akkers on 2008-03-30
Hi Guys.

Am completely new to all this.  Last used Linux about 9 years ago as a Student.
Getting fed up with MS and Mrs Yoda wants me to get rid of.  Downloaded the Ubuntu CD onto laptop and  used it to install onto desktop.
Seems fine but when I re-booted without the cd it gets the grub error 18 message.

Now, it seems that changing the HDD mode is the solution.

So I went into bios to see where i need to do this. Cant seem to find the option.:(

Where can i change the HDD to normal.

Causes of the problem i can think of... 40GB HD? 
Dell PC?

Thx all

---

### Post by 5735guy on 2008-04-04
Excellent thankyou:):)

---

### Post by sreplow on 2008-04-09
Hello,

I am a first time Linux user, just downloaded Ubuntu 7 (most recent) and I have run into the error 18 roadblock.  

Black screen, "GRUB loading, please wait....Error 18"  this is going on an old custom built system that was running win98 and later on XP.  I put a new 320g EIDE HDD to start from fresh and used the live desktop CD downloaded straight from the ubuntu site.  

what can I do to get this up and running easily?  my lack of computer expert flavor is counting against me....

thanks for all of the help!  im excited to get this going.

---

### Post by abish on 2008-06-12
hello.
i was really happy with 7.10.. then i installed 8.04.
it was working perfectly for a month or so.. 
then suddenly... error 18!! on GRUB..

i dont have any other OS installed.. and it is a single partition...
what do i do now.. i dont want to lose my data.. please help!!

---

### Post by meierfra. on 2008-06-12
Does the grub menu appear at boot up  (Press Esc after the bios screen) ? Are you able to boot the older kernels?

> it was working perfectly for a month or so..
then suddenly... error 18!! on GRUB..

This sounds like the typical Error 18 situation: You bios are  able to see only the first 130GB of your hard drive. After one of the recent kernel updates your new kernel got placed at the far end of your hard drive  and now the bios are unable  to see the kernel.
  If this is true you will have to create a separate boot partition.

Please   boot from the Ubuntu LiveCD open a terminal and post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

This will tell us whether parts of you hard drive is withing the 130GB limits and other parts are outside. 

All about Error 18: [Hermanzone]("http://users.bigpond.net.au/hermanzone/p15.htm#18")


You also might see whether SuperGrub (see my signature) is able to boot Ubuntu for you.

---

### Post by okmaster0 on 2008-06-19
'Kay, I've tried everything.

Switching from LBA to CHS,
Making a small boot partition.
I made sure all my jumpers were right.

but it still hangs.

I'm using Hardy Heron and a 120 GB HDD btw

---

### Post by okmaster0 on 2008-06-27
oh yeah, i tried flashing my bios too

---

### Post by doctor strangelove on 2008-07-12
I've also got the Error 18 message.
I've installed Ubuntu from the downloadable CD onto a 40 gb partition of an 500 gb external drive and I've got Windows XP on my internal hard drive.

My bios offers me the options CHS, Large, LBA and Auto. On all options but CHS Error 18 appears and on CHS nothing happens. What can I do to fix this? Or if I can't fix it, how do I get rid of the GRUB? :mad:

---

