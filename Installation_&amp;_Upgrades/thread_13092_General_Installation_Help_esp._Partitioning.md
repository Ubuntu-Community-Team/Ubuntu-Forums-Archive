---
title: "General Installation Help esp. Partitioning"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by tranceybowler on 2005-01-28
Hello,

I've recently installed Ubuntu, and although I like the interface and want to continue using it, installation was rather difficult.

Firstly I had a lot of confusion regarding partitioning as I'm an absolute beginner at this. People tried to help but I still think I made mistakes, and consequently installation was a little messy.

I now have Ubuntu working as a dual boot with Windows XP, however for peace of mind I'd like to completely uninstall Ubuntu and start again from scratch. Ubuntu was installed on its own partition. How do I remove Ubuntu, do I simply format the partition? Do I have to do something regarding booting as the computer currently boots to Ubuntu by default and I don't want to be faced with a black screen when I next turn the PC on!

The next thing I'd like to know is **exactly** how to organise partitions for a clean install of Ubuntu. As I said I'm a complete beginner at this so I could do with simple, but useful instructions. Should I sort out Partitions before the install using Partition Magic? Or can I sort it all out during the Ubuntu Install. Also, I read somewhere that it is recommended to have a swap partition, can someone help me out with regards to this?

Sorry for the long post, I'm very keen to get into Linux, I'm just a little confused about these issues. In short, I need to know:

1. How to completely uninstall Ubuntu, including anything I need to do regarding Windows XP.

2. Exactly how to sort out partitions, both before the install using Partition Magic, and during the install.

I'll be eternally grateful to anyone who can help me with these issues!

Many thanks in advance,
Matt

PS - Finally how do I check my downloaded ISO against the checksum file? I want to ensure that my file isn't corrupted!

---

### Post by rudi on 2005-01-28
[QUOTE=tranceybowler]
    1. How to completely uninstall Ubuntu, including anything I need to do regarding Windows XP.
    [/quote]
 You don't have to uninstall Ubuntu. Just reinstall, and do the rest from the installer. You can remove your previous partition using the install.
    [QUOTE=tranceybowler]
    2. Exactly how to sort out partitions, both before the install using Partition Magic, and during the install.
    [/QUOTE]
    You really don't need partition magic.  So, Windows on one half, Ubuntu on the other.
 First create a partition using the ubuntu installer, mount the root filesystem on that. A swap partition is generally twice the size of your RAM memory (so an old myth describes), but i'm using 1 GB which is sufficient. If you still have room you could create another vfat (fat32) partition, so you can share files with windows if you need to do so. If you don't use a shared partition i would recommend a seperate partition for your /home , because if when you reinstall Linux again, you have your settings and files safe.
    
    So to sum it all up e.g. 40 GB disk:
    fair amount of space for Windows (10GB)
    fair amount of space for Linux (10GB)
    1 GB of swap space
    extra partition (vfat, /home or even both) (19GB)
    
    Hope it'll help.
 
 [edit]
 Owjeah, how to check file integrity. I'll assume you've downloaded the ISO using windows. There are several tools to check the MD5 sum ([http://www.fastsum.com/download.php](http://www.fastsum.com/download.php) for instance). Read to accompanied documentation on how to use it). So, download the ISO with the accompanied MD5 checksum. Then use the tool
 [/edit]

---

### Post by tranceybowler on 2005-01-28
Rudi, many thanks for your informative reply, it's very useful.

A few things I'm still unsure about though, how do I create a partition during the ubuntu install? I remember it not being very clear and there were several options to do with "logical volumes" or something? Sorry I don't remember more clearly.

Secondly, when dealing with a partition during the installer, it asks for several options, a few I didn't understand, one was "bootable". Should I turn this on or off for the main partition? When I first tried it turned "on" the installer stopped after a while, don't know whether this was anything to do with it? Also, how should I format the main partition for Ubuntu, ext3? And how do I mount all these partitions, just on "/" ? And the same questions for the swap partition.

Finally, the partition I have assigned for linux is only about 3GB at the moment, how do I go about increasing that?

I will definitely follow your advice on creating a vfat partition, I have lots of free hard disk space so running out isn't really a problem.

Once again, many thanks! It's great to see people so kind in helping out new users like me  :D

---

### Post by mxreader on 2005-01-29
I'm interested in this too.  Except my situation is different. I've just wiped out XP with its featured Blue Screens at random.  I dont like this feature so I simply put in the Ubuntu CD that I got from LInux User & Develper magazine and let it partition the whole 80Gig drive and I think XP should be dead.  I did however want to keep a separate partition to use with another unix distro for experimentation but the install instruction led me to believe I could change the partitions later, this is not so.  So I got 80G WD800JB with just Ubuntu.

After reading the above thread seems the way is to reinstall and choose the second option about partitioning.  However I'm also likely to not really know what is a good partitioning scheme and what sizes to choose.  The thread has given me some clues, thanks.

---

### Post by rudi on 2005-01-29
Partitioning really isn't that hard. (i hope i recall the steps correct, as i do it all from memory now :p)
    
    When you boot your Ubuntu installation CD and come up to the partitioning bit choose **manually edit partition table**. You will see an overview of your existing lay-out
     ```
IDE1 Master (hda) - 80GB Maxtor
 	#1 Primary	 20GB (lightning bolt <-- bootable) NTFS, this is your Windows part.
       #2 ..
       #3 ..
    
``` 
 If you don't have any files you want to keep on the partitions #2, #3 and so on you can delete them to make a shiny new layout. (experimenting in the installer isn't dangerous, you only commit the changes when you choose **write partition table to disk**)
    
    So, you now have 1 primary partition with Windows XP, and a whole lot of free space. Now choose **create primary partition** (if i recall correct). For your Linux system you need to choose mount point **/** (that's foreward slash). Let's say we're using 20GB for this. Don't make it bootable! Now you need to select a filesystem. Ext2 is proven and stable, and fast, ext3 is a journalling version, and reiserFS is also a journalling filesystem (fast if you hava a lot of small files). The choice is really up to you. When you are done choose **done** (or something like that). Now you will see an icon of a skull to make clear that partition is going to be formatted.
    
    Do the same as before, but now choose the size of 1GB and **usage** is swap. You now have 39 GB available (in this example i've used a 80GB disc). Create another partition, **usage/format** vfat. (or create two, one for **usage /home** to keep your settings/ prefs when you reinstall Linux. Now you have a new overview:
     ```
IDE1 Master (hda) - 80GB Maxtor
 	#1 Primary	 20GB (lightning bolt <-- bootable) NTFS, this is your Windows part.
       #2 Primary	  20GB		   (skull)    EXT3
   #3 Primary	 1GB		 (skull)	swap
   #4 Primary	 39GB		 (skull)	vfat
     
``` 
    Choose **write changes to disc **to commit your changes and the partitions will be formatted. Ubuntu installer follows.
    
    I hope i have recalled the options and steps correctly, don't kick me if i'm wrong [img]http://www.ubuntuforums.org/images/smilies/eusa_pray.gif[/img]
    
    Rudi

---

### Post by tranceybowler on 2005-01-31
Hey Rudi,

Thanks again for your wonderful advice, I just went to try the installer again and I realized another reason why I was so confused the first time. When I select **manually edit partition table** it displays the overview of my existing layout as you say. But there is no option to **create primary partition**. The only options I have are:

**Configure Software RAID** 
**Configure Logical Volume Manager** 
**Guided Partitioning** 
**Help With Partitioning** 

When I select any of the first 2 it says that it will write any changes made to the partition table, so I have never continued past this stage.

The **Guided Partitioning** just takes me back and asks me whether I want to manually edit partition table or format the whole drive.

Any idea what to do? Should I create the partitions in Partition Magic instead?

Thanks again!
Matt

---

### Post by Zillion on 2005-01-31
Sry for being a n00b... but I have Win XP and Suse 9.2 installed, dual boot. I decided to try Ubuntu instead of Suse, I hope I get better results with Ubuntu concerning Ati Radeon dual head and my Audigy2.  

Is it possible to replace Suse 9.2 (and its boot menu) and keeping WinXP (and it's NTFS and FAT32 partitions) intact while installing Ubuntu?

---

### Post by rudi on 2005-02-01
[QUOTE=tranceybowler]Hey Rudi,
     
 Thanks again for your wonderful advice, I just went to try the installer again and I realized another reason why I was so confused the first time. When I select **manually edit partition table** it displays the overview of my existing layout as you say. But there is no option to **create primary partition**. The only options I have are:
     
     **Configure Software RAID** 
     **Configure Logical Volume Manager** 
     **Guided Partitioning** 
     **Help With Partitioning** 
     
 When I select any of the first 2 it says that it will write any changes made to the partition table, so I have never continued past this stage.
     
     The **Guided Partitioning** just takes me back and asks me whether I want to manually edit partition table or format the whole drive.
     
     Any idea what to do? Should I create the partitions in Partition Magic instead?
     
     Thanks again!
     Matt[/QUOTE]
     Hi Matt,
     
 The reason why you can't create a primary partition is probably by the fact that you're disk is allready partitioned using all the space. What partition lay-out is displayed? How many initial partitions are listed when you start the installer? If there is only one partition #1 you have to resize that partition to make room for ubuntu. Resizing can be done using partition magic or a free tool from ranish, partition manager (bit more complicated though). If more then one partition is listed you could copy all the files from the second partition to the first (use windows for that, just copy the files from D to C), so all windows files are on one partition. Then using the installer delete partition #2 and then follow the guideline as i've written in my previous post. 
     
 If you're not sure what to do, start the installer, at the point of partitioning write down your partition lay-out and post it back here (also the szie of your disc).
     
     ................. 
     
 [QUOTE=Zillion]Sry for being a n00b... but I have Win XP and Suse 9.2 installed, dual boot. I decided to try Ubuntu instead of Suse, I hope I get better results with Ubuntu concerning Ati Radeon dual head and my Audigy2. 
      
 Is it possible to replace Suse 9.2 (and its boot menu) and keeping WinXP (and it's NTFS and FAT32 partitions) intact while installing Ubuntu?[/QUOTE]
 Yes no problem. Just run the installer, and during the partition setup select the partitions from SuSE and leave each partition marked NTFS or vfat alone. After ubuntu is installed you'll also have the ubuntu boot menu.

---

### Post by tranceybowler on 2005-02-01
[QUOTE=rudi]
     
 If you're not sure what to do, start the installer, at the point of partitioning write down your partition lay-out and post it back here (also the szie of your disc).
[/QUOTE]

Hello again Rudi,

Here is the Partition layout:

IDE1 Master (hda) 200GB WDC some random numbers
   #1 primary     196.8GB    NTFS
   #5 logical            3.1GB    ext3

on #1 there is a jagged arrow between the 196.8GB and NTFS.

It's a 200GB disc as you can probably see. Hope this is useful, thanks once again!

---

### Post by Zillion on 2005-02-01
tx for the help. I succesfully installed Ubuntu and I feel it totally rocks.  :D

---

### Post by rudi on 2005-02-01
> **tranceybowler]Hello again Rudi,
       
       Here is the Partition layout:
       
       IDE1 Master (hda) 200GB WDC some random numbers
          #1 primary     196.8GB    NTFS
          #5 logical            3.1GB    ext3
       
       on #1 there is a jagged arrow between the 196.8GB and NTFS.
       
       It's a 200GB disc as you can probably see. Hope this is useful, thanks once again![/QUOTE]
       Hi,
 The arrow means that that partition is bootable, don't change it. #5 is logical, means it's in an extended partition (there should by an extended partition mentioned which is named #2..is it?!). If there is some free space left on the 1st partition (there ought to be with 196Gig! [img]http://www.ubuntuforums.org/images/smilies/icon_surprised.gif[/img]) you could to resize the partition using partition magic or partition manager. Read the documentation of those programs on how to do that (defrag, defrag defrag i've heard someone say). After the resize you should have a lay-out like, 
       #1 100GB (arrow)  NTFS
       free space 96 GB
       #5 3.1 GB etx3
       
 You can now delete $5 (i am assuming it is unused) to have a 100GB windows and 100 GB free space. Now you can add a primary partition (e.g 50 GB), mount it **/ **and format it as ext3. Add another partition, 1GB and choose usage swap and format it as swap. The remaining 49 GB could me formatted as vfat (vat32 for windows) so you can use it to share files with windows.
       
 If you have made backups, and you are not scared on installing windows again i would recommend to wipe out the entire thing and use the partition method on my Debian double boot guide ([http://www.bio-informatics.nl/debinstall1.php]("http://www.bio-informatics.nl/debinstall1.php")). Don't ask why but i'm not a fan of partition resizing. 
       To sum it all up:
       **method 1:**
 ```
1. use a partition tool to resize your 196 GB NTFS partition to about 100 GB	 (read the manual for the tool on how to do it safe!!)
      2. Check if your resized partition is functional (e.g reboot your pc, use a diagnostic tool...or not  said:**
> 
       tx for the help. I succesfully installed Ubuntu and I feel it totally rocks.
       
 [img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]didn't hurt did it ;)

---

### Post by tranceybowler on 2005-02-06
Well, thanks for your response Rudi, I did everything as you said, resized the partition, the in the ubuntu installer set up the partitions as described. Then it immediately threw up some error message "debootstrap program exited with an error" or something. Installation wouldn't continue so I rebooted and tried again. This time it got further but towards the end of the boot loader install it said "unable to install selected kernel linux-amd64-generic". Again Installation couldn't continue.

So now I've tried several different things, tried and re-tried and nothing will work. Unfortunately the GRUB boot loader doesn't work now, it just says "error 22".

So it seems linux is not for me, which is a shame as I really wanted Ubuntu to work  :-x 

Anyway, the most important thing is to get Windows XP back, can someone tell me how I should do this? As I say it's still there, but GRUB won't start. Please help! Once again, thanks again Rudi for all your help.

---

### Post by rudi on 2005-02-07
Hi tranceybowler,
    
 What a shame it didn't work out for you. All those errors... have you downloaded the ISO from internet or did you order an official Ubuntu CD? It could be that those errors are a result of a faulty install disk. If you're still in a good mood you could try to download another ISO image, check for errors using MD5sum and burn a new CD (perhaps even verify the burn afterwords). ... But if you have enough of fiddling with your PC i won't be surprised! :D
    
    About Grub and your error 22...
 ```
22 : No such partition This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.
``` You could try to boot using a linux live CD, and try to fix your grub menu file (**/boot/grub/menu.lst**). But as you said that installation didn't went flawless i really advice to download another ISO and check it for flaws and try again. 
    
 If you really really really have enough of Linux you could try to use fdisk to give the MBR (master boot record) back to Windows. If you have a setup/boot disk of windows i would suggest to use it and run the command **fdisk /mbr** from DOS. That program will overwrite your master boot record where grub is installed.
    
 Sorry it didn't work out for you. Good luck with it (and keep us posted, even if you wipe out all of linux, i'm hoping it'll work out allright!)
    
    Rudi

---

### Post by tranceybowler on 2005-02-07
Hello Rudi,

I made a DOS boot disk but when I tried to go to C: it says "invalid drive", this is not a good sign surely? When I try the Fdisk command it doesn't recognize it. I tried using the Partition Magic boot disks which took me into a dos version of partition magic. Here it displayed all the partitions, but the one which was "active" was the Linux ext3 one. So I changed the "active" partition to the NTFS but it still won't boot.

GRUB now gives error 17. I am very very confused now, I'm starting to wonder if I will be able to get Windows back! Do you have any suggestions on what to do now?

Many thanks as always!
Matt

---

### Post by rudi on 2005-02-07
error 17 means it can see the partition, but the filesystem is not recognized therefore grub can't mount it. It sounds like you made the ext3 partition bootable in the ubuntu installer...
  Could you post your partition lay-out as partition magick gives it to you, including flags etc.
 I think your data is still there, otherwise it won't display the NTFS partition, just a screwed up partition table (one of the reasons i don't like partition resizing). You could try and insert the windows XP cd, and reinstall windows **DON'T FORMAT**, just overwrite your existing install, it shoud keep your files safe. But if you have the posibility, boot using a Linux live CD, mount your NTFS partition and burn all your files on CD before re-install.
  
If you can please post your /boot/grub/menu.lst file and the partition lay-out from partition magick....

---

### Post by tranceybowler on 2005-02-07
Hi Rudi, here is my partition layout in Partition Magic:

Type              Size            Status          Primary/Logical

NTFS              99,998        Active           Primary
Linux ext3      90,295        None            Primary
Extended       486.3          None            Primary
Linux Swap    486.3          None            Logical

Originally the Linux ext3 partition was set to active but I changed it to NTFS to see if that would work, however it made no difference. Any ideas on what to do?

I can't post the contents of my /boot/grub/menu.lst as I can't get into Linux, however if you think using a Live CD is the best way of getting windows back then I could do this.

Thanks!
Matt

---

### Post by rudi on 2005-02-08
LOL :D well, oke, it seems that giving the bootloader back to windows isn't that hard! 
 I inserted my windows XP installation CD to give exact instructions on how to get your windows back using the recovery console. Well, it seems that Windows is so agressive that it will overwrite the MBR without prompting, and after step1! [img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]
  
  So now i've lost my grub LOL
  
  Oke, here'sthe way you could do it:
  
 Boot your PC with the Windows XP installation CD. After all the drivers are loaded you get a partition layout. Select the NTFS partition to install windows on. After you hit enter you will get a warning that there is allready a windows installation there. Hit esc. or F3, to cancel installation and F3 again to reboot. Remove your CD and voilla, a Windows greeting screen.

---

### Post by tranceybowler on 2005-02-08
Hello Rudi,

I'm really despairing now. I tried what you said and restarted and then not even the GRUB loader error message was displayed, it just froze. I ran the Partition Magic emergency disk and it only displays one partition, and says the partition has an error #108. I ran the ubuntu installer and it shows a completely empty drive.

So I guess now I have lost everything  :sad: I have absolutely no idea what to do now except re-format the whole drive which will be very annoying as I have to re-install drivers etc. Unless anyone has any final ideas? 

Thanks for trying to help anyway Rudi, I guess my computer just doesn't like me!

Matt

---

### Post by rudi on 2005-02-08
oh that's not good. Are you sure you did exactly as i did? It sounds like you hit one enter to much. I did it exaclty as i describes, and i've lost nothing (well, except for grub).
 I'm affraid that you're data is gone. You could try to recover your data using data recovery tools, but that's only worth the trouble if it's really valuable information.
   
 Perhaps you where to anxious and didn't read carefully, i hope you will try linux again, because if you're going to re-partition you might as well leave some 10GB (or more) for linux. 
   
 Sorry this particular thing didn't worked out for you. I did my best to describe it as clear as possible. Good luck..... even i feel depressed right now[img]http://www.ubuntuforums.org/images/smilies/icon_sad.gif[/img]
   
   *pat on your shoulder*

---

### Post by tranceybowler on 2005-02-09
Yes, I did do what you said, I stopped just before formatting and that is what happened. Oh well.

I thought considering I now have an empty hard disk I may as well try installing ubuntu again, but every time I tried to install on the supposedly clean partition, it stopped at the same point as when I first tried to install it ("failed to install kernel amd64-kernel-linux" or something). I tried this several times with different partition arrangements and the same thing kept happening.

So I ran the Partition Magic boot disk and formatted the ext3 partition from there, then deleted all 3 partitions that the installer had made, and lo-and behold, it worked! I can only assume that when the ubuntu installer says it will format the partition, it isn't doing a very good job, as it seems to know that something has been installed there.

After this, install went reasonably well, until it comes to the point where you make a user account. No matter what I typed in here, it wouldn't accept it, it just kept going round in circles and asking for a user name / password again and again. So i hit ESC, and skipped this part. The rest of the install seemed to finish ok (apart from the internet connection not working yet, but I'm sure that's eaily fixed). So the problem is now when I boot up, Ubuntu loads fine, but I can't log on! How can I create a user account or log in as an admin?

I'm not really sure why I've kept trying all this, as it seems that everything that could go wrong has. Perhaps it's because I've spent so much time trying that it would be weak to give up now! So anyway if anyone can tell me how to log on or create a new user name that would be very useful. Then I'll see about getting the internet connection working via a wireless ADSL modem!

Thanks,
Matt

---

### Post by rudi on 2005-02-10
You must have installed Ubuntu with a faulty disc, or you have found a lot of bugs :D. Really, the things you've described, must be the worst introduction to Linux ever! 
  
 I really would recommand to download and burn (and verify) another disc. Then run the installer again. Really there should be no errors at all, not with the kernel installation, adding a user... man.... I respect your will of going on. Really! If those things happened to me i think i threw away the CD and think really nasty words about Ubuntu ;)

---

