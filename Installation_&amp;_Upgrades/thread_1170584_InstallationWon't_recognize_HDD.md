---
title: "Installation/Won't recognize HDD"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Jim F on 2009-05-26
New to Ubuntu. Attempting to install Ubuntu 8.10 single boot on Dell Win 98 machine.

I have a C (30Gb) & D (4 Gb) drive. First attempt installed on D disk but machine booted up to old C Win 98. Disconnected D drive and tried again.

Now no drive is recognized. Drive is FAT32 if that is pertinent. Ran scandisk before installation successfully.

I really don't want to stay with Win 98. I would appreciate any help anyone can offer.
Thanks.

---

### Post by Mark Phelps on 2009-05-26
> **Jim F said:**
> Now no drive is recognized. Drive is FAT32 if that is pertinent. Ran scandisk before installation successfully.

Ubuntu can't install to FAT32, so it probably doesn't see any usable partitions.

Try downloading and burning the GParted LiveCD from distrowatch and booting from that.  If it sees your hard drive, you can use that to repartition and reformat.

---

### Post by raymondh on 2009-05-26
Hello Jim,

Kindly share with us the steps you made/took during the first install.  Reason I ask is because your intention was to have a 1-boot (sole) ubuntu install and I'm curious why "first attempt installed in D disk".  It seems to me that you/or the options made during the install pointed towards a dual-boot configuration as C drive remained intact.

Your comment "now no drive is recognized" maybe because the bootloader may have been overwritten.  What errors are you getting?  Kinldy copy them and post back

The live CD ought to have given you options (automatic, manual) as well as partition and reformat to your preferences.

Mark Phelps has a good alternative (using gparted to partition and reformat).  I think, if your intention is still to single boot, it can still be done again thru the liveCD. Just boot it again and when you get to the partitioning stage, just choose the option to install as the only operating system (sorry, cannot remember the right wordings in the installer, but you'll get it) and have a go.

I ask you if you can still access win98.  If so, and before trying to re-install using the liveCD, a defrag of the disk will be beneficial.  If not (as you say) let's go from there

What is the vintage of your machine and its' BIOS?  Just curious as (with older machines and BIOS') you may be limited with a low cylinder limit ... which can hamper IF you decide to dual-boot.

Regards,

---

### Post by Jim F on 2009-05-27
Hi Mark & Raymond,

Thanks for your fast responses.

As Mark suggested I used Gparted LiveCD. The program saw my drive & I formatted first as NTFS & then as ext3 which I found out is the Ubuntu default.

In each case I get to step 4 of the Ubuntu 8.10 installation (Prepare Partitions) and the drive is not shown. If I try to forward to the next step I get an error message "No root file system is defined" "Please correct this from the partitioning menu" which I can't do because the disk is not shown.

I no longer have access to Win 98 unless I reinstall. Before I began this process I did run scandisk & defrag. I have a Dell Dimension XPS T700r with 512 Mb RAM - Pentium III. This machine dates from 2000.

Thanks for any assistance.

Jim

---

### Post by raymondh on 2009-05-27
> **Jim F said:**
> Hi Mark & Raymond,
In each case I get to step 4 of the Ubuntu 8.10 installation (Prepare Partitions) and the drive is not shown. If I try to forward to the next step I get an error message "No root file system is defined" "Please correct this from the partitioning menu" which I can't do because the disk is not shown.
Jim

Hello Jim,

Using the Ubuntu 8.10 liveCD and the option to "try it out without changing anything on your system" ...

Can you get to a terminal and type

fdisk -l         (that's a small L)

and post back the output?

If you are not comfortable with terminal use, on the same live session, go to system >administration > partition editor (gparted) and take a snapshot of the gparted screen.  You will have to save it somewhere (desktop is a good choice).  From there, just access the internet and the forum and post/attach the .png file (the snapshot).

Having an idea of what the disk looks like can/will help.

Thanks.

---

### Post by Jim F on 2009-05-27
Hi Raymond,

I opened terminal and at the prompt ubuntu@ubuntu:~$  I typed fdisk –l which brought me back to the prompt. I input sudo fdisk –l which did the same.

I accessed the partition editor and the resulting screen is grayed out except that at the bottom “no devices detected” is indicated. I’m communicating to you with another computer since currently there is no operating system on the one I’m trying to install Ubuntu on. I couldn’t transfer the screenshot image.

Could a jumper on the hard drive inhibit the system from seeing the drive? If so, I’ll investigate that tomorrow – I work nights and it’s time for me to go to bed.

Thanks again.

Jim

---

### Post by Jim F on 2009-06-02
Just an update for anyone following this thread.
When installing Ubuntu 9.04 instead of 8.10 my disk was recognized and I was able to complete the installation.
Thank you all for your assistance.

Jim

---

### Post by raymondh on 2009-06-02
> **Jim F said:**
> Just an update for anyone following this thread.
When installing Ubuntu 9.04 instead of 8.10 my disk was recognized and I was able to complete the installation.
Thank you all for your assistance.

Jim

Am glad you have your OS back and working.  Must have been a bad 8.10 disk ... maybe ... nevertheless, am glad :)

---

