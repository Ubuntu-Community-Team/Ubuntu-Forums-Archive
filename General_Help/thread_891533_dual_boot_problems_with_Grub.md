---
title: "dual boot problems with Grub"
date: 2008-08-16
forum: General Help
---

### Post by surfoutsider on 2008-08-16
Hello, This is my first thread. 
 
Recently, I installed Ubuntu 64 bit on to my vista computer and I used Grub 1.5 for the dual boot up.  Then I realized that I needed 32 bit ubuntu (long story short, my ahteros wifi is easier to fix in 32 bit), so I uninstalled ubuntu 64 bit to prepare for the new installation of 32 bit.  However, something went wrong in the process and now when I turn on my computer it still goes to Grub 1.5 and then error 22.  From there nothing happens and I am stuck with the black screen.  I believe that I can do a live boot but I need to get rid of Grub so that my computer boots into Vista.  Plus I want to back-up my files before I do anymore harm!  

Does anyone know how to delete/by-pass Grub so that my computer can boot straight into Vista.  Then maybe I can re-install Ubuntu 32 bit.  Thanks!

---

### Post by Elfy on 2008-08-16
You need to reinstall the windows bootloader using the windows disc. If you haven't got that download supergrub - burn as an image, boot with it - there is a windows menu so you can reinstall it.

If you have the buntu disc it is probably easier to boot with that and iunstall 32 bit and grub will be back.

---

### Post by Hilipatti on 2008-08-16
You just deleted the Ubuntu partition? GRUB will stay on your computer that way and it's probably trying to load your Ubuntu partition. Or do you get the GRUB menu at the start that lets you choose to boot Vista or Ubuntu?

I think if you choose Vista it should still boot it correctly (or maybe not, see below, the GRUB part). It sounds like it's trying to boot into Ubuntu and the error 22 means that it can't find the partition. That shouldn't be a problem if you try to boot into Vista, I think.

If you want to remove GRUB completely and only use Vista, you need to install the Vista bootloader.. I haven't used Vista but atleast in XP/etc you can install the Windows Bootloader by putting the system install/rescue CD in and entering the command prompt. Then all you need to do is issue the "fixmbr" command. I'm not sure if this still works in Vista.

You can also try to press "ESC" at start when GRUB is loading and then choose the correct boot-entry. I'm guessing you should have Ubuntu and Vista on separate rows there. Choose the Vista one with arrow keys and press enter. You should get some rows with stuff on them. Now I don't remember what rows there are on Windows-entries, but I think there should still be a "root (hd0,0)" or similar entry. the first 0 is the number of the hard drive. If you have only one hard drive, then it's always 0 - the next hard drive is 1 and so on.. The second 0 is the partition number (the first partition on the hard drive is number 0, partitions after that are 1 2 3 and so on). Now I'm guessing that if you deleted your Ubuntu partition, Vista will actually be your first partition and the old Ubuntu partition is labeled as free space. So you need to change the second number on "root (hd0,0)" into 0 if the Vista partition is now your only and first partition. Go onto the correct row with arrow keys and press E. Edit the "root (hd0,0)" entry to correct numbers and then press enter. Then all you need to do is press B and it will try to boot.

But, if you boot with the Ubuntu 32-bit install CD and install Ubuntu again, it should re-install GRUB and you should be fine.

---

### Post by caljohnsmith on 2008-08-16
See the [beginning of this thread]("http://ubuntuforums.org/showthread.php?t=740221") for how to recover your Vista master boot record (MBR). If that doesn't work for you,[ here is a more detailed web page of other options]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") if you have the Vista DVD.

---

### Post by Hilipatti on 2008-08-16
Oh there's a detailed thread about this already, should have known :P

But yeah apparently the fixmbr command has been changed with Vista so mine doesn't work. That thread also has information on how to re-install GRUB if you want to do that separately.

My instructions are fine if you want to try if you can still boot into Vista or something.

---

### Post by Elfy on 2008-08-16
I think the biggest problem with vista and it's recovery is that you get a partition to make the discs from - but how many actually do it - there have been more than a few here who don't.

The easiest thing is probably just to reinstall the 32 bit and grub.

---

### Post by surfoutsider on 2008-08-16
Wow, thanks for the fast response.  So to answer some questions:  I don´t get the option anymore to choose ubuntu or vista for bootup.  It almost immediately goes to error 22 and then freezes.  Also, I don´t have recovery cds but there is a recovery parition on my computer.  

I´m quite a computer rookie who is bent eliminating microsoft from my life so let me review what people have said.  
1)  I can download the vista boot up on iso and burn as image to reinstall the vista boot up.  Will this remove Grub? or by-pass it?
2)  I can use supergrub to reinstall the vista bootloader.  Is this a GUI program or do I need to know command prompts for it?
3)  I can reinstall 32 bit ubuntu w/ new Grub.  Ok so I tried before this happened to install 32 bit ubuntu and when I was manually paritioning the drive (erasing the old 64 bit ubuntu and installing the new 32 bit) with the ubuntu installer it kept saying (I cant remember exactly) there was "no root".  It erased  and formated the 64 bit but it wouldn´t install the 32 bit.  The space is free (over 12 gigs) but it kept asking for the (root).  Also do I need to put a mount point on the parition?  or can I leave it blank?  On the install I should still do manual partition?

        Thanks for the help!

---

### Post by caljohnsmith on 2008-08-16
> **surfoutsider said:**
> Wow, thanks for the fast response.  So to answer some questions:  I don´t get the option anymore to choose ubuntu or vista for bootup.  It almost immediately goes to error 22 and then freezes.  Also, I don´t have recovery cds but there is a recovery parition on my computer.  

I´m quite a computer rookie who is bent eliminating microsoft from my life so let me review what people have said.  
1)  I can download the vista boot up on iso and burn as image to reinstall the vista boot up.  Will this remove Grub? or by-pass it?
2)  I can use supergrub to reinstall the vista bootloader.  Is this a GUI program or do I need to know command prompts for it?
3)  I can reinstall 32 bit ubuntu w/ new Grub.  Ok so I tried before this happened to install 32 bit ubuntu and when I was manually paritioning the drive (erasing the old 64 bit ubuntu and installing the new 32 bit) with the ubuntu installer it kept saying (I cant remember exactly) there was "no root".  It erased  and formated the 64 bit but it wouldn´t install the 32 bit.  The space is free (over 12 gigs) but it kept asking for the (root).  Also do I need to put a mount point on the parition?  or can I leave it blank?  On the install I should still do manual partition?

        Thanks for the help!
I think your best bet at this point is to go with scenario #3, and just reinstall Ubuntu (32 bit) since that is eventually what you want anyway. Then you don't have to go through all the trouble of restoring the Vista MBR, which you are going to replace with Grub eventually anyway.

I don't remember the exact steps in the Ubuntu installer, but the main point is you have to have at least two partitions for Ubuntu: one for the root file system, and one for swap space. I think the problem you ran into is, yes, you have to put a mount point on the Ubuntu partition; the main Ubuntu partition should be mounted at the root directory "/". I think that will get you through the installation, but let us know if you have more questions.

---

### Post by Elfy on 2008-08-16
Hi - to do 3 - when you get to the partitioning - choose manual highlight the partition you had 64 bit on and click edit at bottom of screen - when you get to new window, there is a mountpoint box - pick / - make sure that the partition is set to be used as ext3, close the window and that shoiuld let you proceed.

2 - supergrub - is a simp[le program to use - once you have booted - entyer until you reach a menu which has windows - use the arrow key to get to it - enter an from there you should be able to pick fix boot

not sure about 1

---

