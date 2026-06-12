---
title: "Windows 7 Destroyed my HDD.....Twice!"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by FinAkechi on 2009-06-27
Now that I have noticed a pattern never agin shall I install Windows 7 on anything.

Basically I have a "NTLDR is Missing Error" that I just CAN NOT fix.

This has happend on two seperate SATA HDD's of mine.

With both I had tried dual boot with W7 and Linux (one was Ubuntu and the current is Linux Mint)

Right now I only have Linux Mint 7 (Gloria) installed on my PC. On a single 320gb SATA drive.

I have to hit F12 to enter my boot menu and tell it to boot from the HDD in order for GRUB to load. If I don't I get the NTLDR error.

I have tried reinstalling GRUB with a live-cd and I tried reformatting and installing LM7 again. Before I got rid of Windows altogether I tried using the Windows Recovery Console (FixMBR, FixBOOT and the such). 
I have even tried Zero'ing out the hard drive.

Even tried this  FixNTLDR boot disk I found after a little research.

Nothing has worked so far and I am at my wits end.

Thanks in advance  : )

---

### Post by Mark Phelps on 2009-06-27
I've installed several versions of Seven on three different machine, all multi-booting different MS Windows and ubuntu versions ... and have yet to have any problems at all.

Windows 7 does NOT use NTLDR; that was last used by windows XP.  Even Vista doesn't use NTLDR. Also, there is no Windows Recovery Console in Windows 7 or in Vista.  That, too, was last used in XP.

Sounds like what you really did was download some XP "hack" masquerading as Seven -- which is why it tried to use NTLDR instead of Bootmanager.  Seven itself would generate no message for NTLDR because it doesn't have any need for it at all.

---

### Post by kixome on 2009-06-27
I am not a fan of windows, but you can get the ntldr file off the windows disk and place it in your windows root directory and it should boot. Otherwise windows may be installing itself to one drive while its boot loader is looking at another(just a possibility i have come across before)

There is the possibility that ntldr is missing from your disc, especially if it is a pirated/unofficial bit torrent version.

what I do is unplug the power to my sata drive hosting ubuntu, point the bios to boot from the windows drive first then install windows,re-plug the ubu drives power then point the bios to boot from the ubuntu drive and then i add windows to grub and  it should boot with no probs.

---

### Post by kixome on 2009-06-27
Of course I only do that when I turn one of my customers on to linux as I do have a network engineering degree mostly in M$oft But i do not use their software myself other than to run my magic jack.

---

### Post by presence1960 on 2009-06-27
windows 7 creates a 100 MB "System Reserved" boot partition and a Windows partition. AFAIK win 7 does not use NTLDR. Check your partitions and see if you have both the windows & system reserved partitions. 

You aren't using pirated software are you?

P.S. here is a link to NTLDR wiki- Vista & 7 definitely don't use NTLDR: [http://en.wikipedia.org/wiki/NTLD](http://en.wikipedia.org/wiki/NTLD)

Boot into Ubuntu and open a terminal and run > sudo fdisk -l BTW that is a lowercase L. let's get a look at your disk(s) and partitions. Post the output back here.

---

### Post by FinAkechi on 2009-06-27
Ahh well that could be my issue. The  officail W7 download link wasnt working for me so I used bittorrent. Well I guess I more or less effed myself huh? Oh and there is no extr partition on my drive aside from the Linux swap. only have LM7 on atm.

---

### Post by presence1960 on 2009-06-27
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4569    36596736    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2           14520       16477    15727635   83  Linux
/dev/sdb3           16478       19457    23936850    b  W95 FAT32
raz@raz-desktop:~$ 
```
sda1 is the win 7 boot partition, sda2 is the win 7 partition
if you installed a legit version of windows 7 you will have both partitions.

---

### Post by FinAkechi on 2009-06-27
Ah ok well, seeing as I got myself in a bit of a pickel here. Aside from what i have already tried anyone have any suggested?

---

### Post by philcamlin on 2009-06-27
winblows 7 now eh :P 

better then winfail vista?

---

### Post by FinAkechi on 2009-06-27
> **philcamlin said:**
> winblows 7 now eh :P 

better then winfail vista?

Leaps and bounds better, still windows though

---

### Post by presence1960 on 2009-06-27
> **philcamlin said:**
> winblows 7 now eh :P 

better then winfail vista?

There is no need to put down another OS in here. I am not particularly fond of Windows. But I respect the 'free" that I cherish so dearly in respect to others. And that would be they are 'free" to choose & use whatever OS and software they want to. There is no shame in using windows. We all would be better served if we stuck to helping others by sharing what works for us and what we know rather than putting down another product. Would you choose a product where most of the info given is about how the "competing" product is lacking or no good? I know I would not. I want to know what that product can do for me rather than what the competition can't do or does wrong. 

You will be of better help to others if you refrain from that type of assasination of windows!

---

### Post by FinAkechi on 2009-06-27
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6d9b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b779ded

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS



Thats my output. HDD is currentyl empty te 500gb is an external

---

### Post by presence1960 on 2009-06-27
> **FinAkechi said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6d9b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b779ded

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS



Thats my output. HDD is currentyl empty te 500gb is an external

well why don't you start from scratch then? Download Win 7 iso from Microsoft's site & register so you can get the Product Key. Then burn the iso as an image to DVD. 

Next use the Ubuntu Live CD or gparted Live CD to make a partition for Win 7 (this will save you having to defrag or resize windows partition when you install ubuntu). You can leave the rest of the disk unallocated for now. Install Win 7. It will put the "System Reserved" boot partition at the front of the disk automatically. Try booting to win 7 when install is complete.

Next use the Ubuntu Live CD to install Ubuntu using the unallocated space. when you get to the screen attached below click advanced and choose hd0 or sda to install GRUB to MBR. proceed with the install.

---

### Post by FinAkechi on 2009-06-27
> **presence1960 said:**
> well why don't you start from scratch then? Download Win 7 iso from Microsoft's site & register so you can get the Product Key. Then burn the iso as an image to DVD. 

Next use the Ubuntu Live CD or gparted Live CD to make a partition for Win 7. You can leave the rest of the disk unallocated for now. Install Win 7. It will put the "System Reserved" boot partition at the front of the disk automatically. Try booting to win 7 when install is complete.

Next use the Ubuntu Live CD to install Ubuntu using the unallocated space. when you get to the screen attached below click advanced and choose hd0 or sda to install GRUB to MBR. proceed with the install.


Oh I have a product key, I'm not sure if they are still offering downloads. I'll check though.

---

### Post by FinAkechi on 2009-06-27
ok used gparted to make a partition for windows. When I select the partition from the Windows installer (downloaded from the Microsoft website) I get an error

" Setup was unable to create a new system partition or locate and existing partition. See the Setup log files for more information."

Tried this multiple times

Any ideas?

and how to I look at the setup log?

---

### Post by FinAkechi on 2009-06-27
On top of this; this is the code I have been using to Zero out my drives (hoping that it would get rid of all info on the disc as opposed to just a reformat)

sudo dd if=/dev/zero of=/dev/sda bs=10MB count=1

that look about right?

---

### Post by presence1960 on 2009-06-27
if you want to overwrite all info on disk so it is gone try dban @ [http://www.dban.org/](http://www.dban.org/)

is your HDD healthy?

---

### Post by FinAkechi on 2009-06-27
> **presence1960 said:**
> if you want to overwrite all info on disk so it is gone try dban @ [http://www.dban.org/](http://www.dban.org/)

is your HDD healthy?

It's brand new, Western Digital Caviar Blue 320GB Sata 3.5"

And I have tried DBAN on my last HDD and it didnt work I'll try it on this one too though.

Unless the W7 really effed up my drive...... :(

---

### Post by presence1960 on 2009-06-27
> **FinAkechi said:**
> It's brand new, Western Digital Caviar Blue 320GB Sata 3.5"

And I have tried DBAN on my last HDD and it didnt work I'll try it on this one too though.

Unless the W7 really effed up my drive...... :(

I seriously doubt it! I just deleted my win 7 partitions and left them as unallocated space & reinstalled it. Went just as smooth as the first time. Created a 100 MB System Reserved (boot) partition and a Windows 7 partition. Just because your drive is new doesn't mean it can't be bad. it could have been dropped or banged during shipping or during handling. I would look into that.

Just to see why don't you try installing Ubuntu first to see what happens?

---

### Post by FinAkechi on 2009-06-28
> **presence1960 said:**
> I seriously doubt it! I just deleted my win 7 partitions and left them as unallocated space & reinstalled it. Went just as smooth as the first time. Created a 100 MB System Reserved (boot) partition and a Windows 7 partition. Just because your drive is new doesn't mean it can't be bad. it could have been dropped or banged during shipping or during handling. I would look into that.

Just to see why don't you try installing Ubuntu first to see what happens?

Ok so tried Dban on the new HDD

Still nothing.

So I have two HDDs that INSIST upon find the NTLDR

I mean what is there still on the HDDs that is looking for it after Dban?

What are the chances of having the exact same problem on two seperate HDDs?

And if so is there anything I have missed? I mean I feel like i have tried everything.

Also I have tried install Linux first still same deal.

And any idea as to why even though I have the BIOS set up to boot from the CD or USB first that it still gives me the NTLDR error? Its odd because if I go to the boot menu and manually slect my choice everything runs fine. I just can't get it to boot automatically.

---

### Post by cliff58 on 2009-06-28
> **FinAkechi said:**
> ok used gparted to make a partition for windows. When I select the partition from the Windows installer (downloaded from the Microsoft website) I get an error

" Setup was unable to create a new system partition or locate and existing partition. See the Setup log files for more information."

Tried this multiple times

Any ideas?

and how to I look at the setup log?

I had exactly the same problem on a pre-formatted partition and even with no partition on a zeroed drive. Only difference was my drives are IDE. I finally gave up and reinstalled WindowsXP.

A couple of weeks later, after reading more about Win7 features, performance, etc., I wanted to try again. I popped in the DVD, rebooted and 7 installed and ran just fine! 

It appears that Win7's partitioning tool is currently blind to empty drives, So my advice for getting 7 installed would be to install a previous version of Windows and as soon as it reaches the desktop, pop in your Win7 DVD and reboot.

Good luck with it!

---

### Post by FinAkechi on 2009-06-28
> **cliff58 said:**
> I had exactly the same problem on a pre-formatted partition and even with no partition on a zeroed drive. Only difference was my drives are IDE. I finally gave up and reinstalled WindowsXP.

A couple of weeks later, after reading more about Win7 features, performance, etc., I wanted to try again. I popped in the DVD, rebooted and 7 installed and ran just fine! 

It appears that Win7's partitioning tool is currently blind to empty drives, So my advice for getting 7 installed would be to install a previous version of Windows and as soon as it reaches the desktop, pop in your Win7 DVD and reboot.

Good luck with it!

I'll give that a shot if I can ever get over my current issue. But thanks!

---

### Post by cmike2 on 2009-06-28
> **FinAkechi said:**
> I have to hit F12 to enter my boot menu and tell it to boot from the HDD in order for GRUB to load. If I don't I get the NTLDR error.

It's not much of a suggestion but maybe you can set the order of boot devices in your bios. Then it will start up with grub automatically.

---

### Post by FinAkechi on 2009-06-28
> **cmike2 said:**
> It's not much of a suggestion but maybe you can set the order of boot devices in your bios. Then it will start up with grub automatically.

Ok, not to sound rude.....But why the HELL did that work???

So I only get the NTLDR error when my boot priority has my CDrom/USB before the HDD??

---

### Post by cliff58 on 2009-06-28
> **FinAkechi said:**
> I'll give that a shot if I can ever get over my current issue. But thanks!

Current issue. You must mean booting from the cd automatically.  Even with the order set right in the bios, there's a 4-5 second message that shows up on the screen:

Press any key to boot from CD....

and if you miss it you'll get the NTLDR message. In case you're not missing that then here's a good link for NTLDR problems:

[http://www.computerhope.com/issues/ch000465.htm]("http://www.computerhope.com/issues/ch000465.htm")

---

### Post by FinAkechi on 2009-06-28
Ok I figured it out...sorta

It has somethign to do with  boot from a USB device

I had USB #1 in boot priority

I can boot Ubuntu from a flash drive no problem but I have to unplug my External HDD.

My guess is the NTLDR has something to do with my External HDD

---

### Post by cmike2 on 2009-06-28
> **FinAkechi said:**
> Ok, not to sound rude.....But why the HELL did that work???

So I only get the NTLDR error when my boot priority has my CDrom/USB before the HDD??

Based on the information you gave, you were able to select a specific drive (or partition?) to launch grub instead of getting an NTLDR error. So I figure it'll help if you make that device boot before the one that causes NTLDR. That way, grub can load other OS, including windows 7.

for the record I do dual boot W7 and ubuntu. I don't have any more good advice except to install W7 first then ubuntu, but you probably already did that.

---

### Post by running_rabbit07 on 2009-06-28
Did you get the correct Windows 7 product?

 Aka, did you get the clean install package or the Upgrade Package?

 I know I have seen those two different versions with Vista.

---

### Post by FinAkechi on 2009-06-29
> **running_rabbit07 said:**
> Did you get the correct Windows 7 product?

 Aka, did you get the clean install package or the Upgrade Package?

 I know I have seen those two different versions with Vista.

Clean install 32-bit

although I have been wondering, does Hyperthreading count has 64bit?

---

