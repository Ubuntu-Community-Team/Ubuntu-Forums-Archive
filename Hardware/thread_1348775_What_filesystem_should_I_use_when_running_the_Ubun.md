---
title: "What filesystem should I use when running the Ubuntu OS from a thumb drive?"
date: 2009-12-07
forum: Hardware
---

### Post by BT1 on 2009-12-07
Not sure if this is the right area to post this buuuut...

I have a few Ubuntu distros installed onto thumb drives and by that I don't mean startup disks, I mean the Operating System is installed onto the thumb drive with root, /home, etc. and I boot up the OS from it. I usually run them on 8 gig sticks but I have a few on 4 gig sticks.

My question is... well flash drives like thumb drives have limited read/write but I'm having a hard time deciding between EXT4 (with journaling), and EXT2 (no journaling). Journaling I suppose would decrease the life of the drive since read/write cycles can wear it out, but I am unsure if EXT2 has lesser performance than EXT4. I cringe at the idea that EXT4 could wear down my drive quick, but I'm loathe to sacrifice performance if EXT2 is stinky.

Which would you suggest I use as the file system? Remember, it's an OS that's running from a thumb drive and mounting the internal hard drives only when files need to be saved or accessed (like music/video/games).

Thanks for the help!

---

### Post by tom.swartz07 on 2009-12-07
Personally, I would use the ext4 file system, particularly if you decide later to turn on USB persistence and take advantage of the 8gb and 4gb of space on your drive.

If you dont plan on ever using persistence with your drives, go for ext2, but there shouldnt be much of a difference on your drive. As long as you have a mid-range to high-end drive, you dont have to worry about drive failure for a long time. I would suggest to use a higher end drive for the boot type that you talk about.

I have the same situation, and I have had no problems with SanDisk drives even after using theme for almost a year.

---

### Post by snowpine on 2009-12-07
> **BT1 said:**
> Not sure if this is the right area to post this buuuut...

I have a few Ubuntu distros installed onto thumb drives and by that I don't mean startup disks, I mean the Operating System is installed onto the thumb drive with root, /home, etc. and I boot up the OS from it. I usually run them on 8 gig sticks but I have a few on 4 gig sticks.

My question is... well flash drives like thumb drives have limited read/write but I'm having a hard time deciding between EXT4 (with journaling), and EXT2 (no journaling). Journaling I suppose would decrease the life of the drive since read/write cycles can wear it out, but I am unsure if EXT2 has lesser performance than EXT4. I cringe at the idea that EXT4 could wear down my drive quick, but I'm loathe to sacrifice performance if EXT2 is stinky.

Which would you suggest I use as the file system? Remember, it's an OS that's running from a thumb drive and mounting the internal hard drives only when files need to be saved or accessed (like music/video/games).

Thanks for the help!

In the past, I chose ext2 over ext3. Now that ext4 is the standard, I use ext4 with the 'noatime' option (in /etc/fstab) for my flash drive installs.

I understand why this is an important question if you're dealing with an expensive solid state hard drive. I do not think it makes a big difference when dealing with inexpensive thumb drives. I don't lose much sleep over whether my $10 thumb drive will wear out in 5 years or 10. :)

---

### Post by BT1 on 2009-12-07
> **snowpine said:**
> In the past, I chose ext2 over ext3. Now that ext4 is the standard, I use ext4 with the 'noatime' option (in /etc/fstab) for my flash drive installs.

I understand why this is an important question if you're dealing with an expensive solid state hard drive. I do not think it makes a big difference when dealing with inexpensive thumb drives. I don't lose much sleep over whether my $10 thumb drive will wear out in 5 years or 10. :)

Lol... me = broke college student. Kinda important for me :P

---

### Post by snowpine on 2009-12-07
By the time your flash drive wears out, you'll be graduated from school, and I'll be working for you. ;)

Good luck with the flash drive install; they are a lot of fun! My Windows-using friends always do a double-take when I boot their computers from my thumb drive and start twirling the desktop cube. :)

---

### Post by BT1 on 2009-12-08
> **snowpine said:**
> In the past, I chose ext2 over ext3. Now that ext4 is the standard, I use ext4 with the 'noatime' option (in /etc/fstab) for my flash drive installs.



Just a couple of questions...

1.) What is this "noatime" thing-a-ma-jigger?
2.) What is "USB persistence"?

I'd usually google it or do a search in the forums before I asked, but I've spent a few hours now trying to research stuff on my own about linux and reading my intro to ubuntu and linux books. My brain is kinda burned out!

Any response is appreciated. :)

Also, is there a way to disable journaling on ext4?

> Good luck with the flash drive install; they are a lot of fun! My Windows-using friends always do a double-take when I boot their computers from my thumb drive and start twirling the desktop cube. :smile:Lol yeah, I have a couple of friends that would be shocked when I booted into linux and mounted their hard drive and played movies and music off it. At my college, the school computers can be buggy with WinXP and one day no available computers were available except one that only went as far as the post check and bios, then tried to boot the hard drive and fail. I popped in the thumb drive, booted ubuntu, and after I did what I wanted to do, I turned off the puter and walked off with my thumb drive. Someone ran up to the computer after I got up (there's a line of 15 people on average all day to access the computers) and turned on the computer to find it was still an XP paperweight. I love it!

---

### Post by sgosnell on 2009-12-08
noatime tells the filesystem not to write the time of every access to every file.  That wastes probably more writes than anything else.  The default is relatime, but you can edit /etc/fstab to change it.  Ext4 can be used as a non-journaling filesystem, but I don't think it's a good idea.  In case of a crash, you can lose your data, and the cost of journaling isn't that big, either in time delays or in extra writes to your drive.  Wear-leveling is standard, and with that, you don't need to worry about getting excessive writes to a cell.  I quit worrying about it some time back, and got on with my life.

---

### Post by tom.swartz07 on 2009-12-09
usb persistence is the ability to save your session on the usb live session.

essentially it makes it so that the 'LiveCD' version that is installed on your drive saves preferences and little changes, passwords, browsing history, etc. This is useful if you just use the LiveUSB to browse the web or keep files between sessions

---

### Post by BT1 on 2009-12-10
> **tom.swartz07 said:**
> usb persistence is the ability to save your session on the usb live session.

essentially it makes it so that the 'LiveCD' version that is installed on your drive saves preferences and little changes, passwords, browsing history, etc. This is useful if you just use the LiveUSB to browse the web or keep files between sessions

Oh, that must be why a few posts up this is posted:

> 
                                                  Personally, I would use the ext4 file system, particularly if you decide later to turn on USB persistence and take advantage of the 8gb and 4gb of space on your drive.

If you dont plan on ever using persistence with your drives, go for ext2, but there shouldnt be much of a difference on your drive. As long as you have a mid-range to high-end drive, you dont have to worry about drive failure for a long time. I would suggest to use a higher end drive for the boot type that you talk about.

I have the same situation, and I have had no problems with SanDisk drives even after using theme for almost a year.He thinks I am saying I have a LiveCD install maybe? It isn't a LiveCD, it's a full Ubuntu installation on a thumb drive. If using the desktop installer, you can pick your thumb drive and create the root partition there with the GUI, and in the alternate install iso (text installer) you can do this too by scrolling down to the bottom of the list and creating a root partition on the thumb drive.

I use at least a 4 gig thumb drive running 32bit Xubuntu or Ubuntu without a pagefile. 8 Gig is preferred because you can install updates and have a little more wiggle room in case you have to download an .iso to your "downloads" folder. 32bit is because you never know what kind of processor type you'll be plugging into!

---

