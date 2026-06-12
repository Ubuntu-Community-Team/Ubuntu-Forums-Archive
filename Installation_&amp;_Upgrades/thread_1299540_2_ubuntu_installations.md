---
title: "2 ubuntu installations?"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by praytor on 2009-10-24
Hi all, I'm new here and was hoping I could get some advice on partitions and stuff.  I have zero experience in this kind of thing so hopefully you can bear with me.  My computer has Vista installed on a single hard drive.  I want to install an SSD in another drive bay, and then install Ubuntu on both drives.  In other words I would like the final layout to look something like this:

Disk 1 (Hard drive):
[Vista partition | Ubuntu partition | Swap?]
Disk 2 (SSD):
[Ubuntu partition | Nondescript, unformatted partition?]

I would like to be able to set up my computer to boot into any one of the 3 systems.  Is this possible and is it difficult?  Any caveats/dangers I should know?

To take another approach at asking this question, I might explain what I hope to achieve by doing this.  I need to do a class project on studying the effects of caching hard drive contents on an SSD (so the SSD acts as a new persistent layer between the drive and the RAM).  To do this, I would need to look at performance without SSD caching (pure Disk 1 Ubuntu partition), performance with SSD caching (Disk 1 Ubuntu partition with Disk 2's unformatted partition used for caching), performance using pure SSD (pure Disk 2 Ubuntu partition).

Am I going about this the wrong way or is the layout I suggested reasonable?  What would be a good webpage to get an idea of how to partition my computer this way?  I guess I also need to tweak the BIOS?

---

### Post by urugTON on 2009-10-24
No it's not hard and no you don't have to tweak the BIOS.  The notebook I'm running on has Ubuntu 8.10 (soon to be 9.10) and 9.04 installed on it.  Effectively all you do is install Ubuntu twice.  The first time you specify that Ubuntu is to be installed on the hard drive and the second time tell it to use the SSD.

You will need to learn a little about grub, a little about partitions and some about Ubuntu.  Before you do anything with partitions or grub, back up what you have.  It is at risk!  There are a lot of little mistakes that can hurt pretty badly if you do not have a current backup.  If you have ghost that's a good place to start.

There's a good grub manual at [www.gnu.org/software/grub/manual/grub.pdf](www.gnu.org/software/grub/manual/grub.pdf).  The 1st ten pages are all you need to start.

Probably the hardest, and certainly the riskiest, part of the effort is in partitioning the hard drives.  There's a good start at [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition).  

There's more!  You'll need to take a look at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).

There are a few things to keep in mind about adding Ubuntu to a hard drive that Windows already has.  Ubuntu is nice about sharing.  Windows, particularly Vista, is not.  If you are shrinking the Windows partition see if you can get Windows to resize the partition.  There are open source tools that can reliably resize NTFS partitions, but that doesn't mean Windows will be happy about the result. In any event, clean up and defrag the Windows partition before resizing it.
  
Download Ubuntu 9.04 32 bit.  I'd stay away from 9.10.  It's new, you're new and 9.10 uses grub2 which most of us have never seen.  As far as 32 bit vs 64, I'm running 64 bit where I can.  I'd suggest 32 bit to avoid a few quirks in various packages such as java and flash.  They work fine, but I'd concentrate on your test.

Burn the DVD (generally referred to as a LiveCD) and boot it up.  Check to see that video, networking and such work on your system under Ubuntu. 

While you're running Ubuntu open a terminal and enter df -h at the command line. Write down what you see.  It'll look like:

```

jp@Vostro1510:~$ df -h | grep /dev
/dev/sda3              15G  3.9G  9.9G  28% /
udev                  1.9G  172K  1.9G   1% /dev
tmpfs                 1.9G  468K  1.9G   1% /dev/shm
/dev/sda6              99G   69G   25G  74% /Data
jp@Vostro1510:~$ 

```

The two entries /dev/sda3 & /dev/sda6 are the partitions I'm using.  There's a pretty good write up on device names at [https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html](https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html).  Keep in mind that Windows, Linux and grub all have different ways of naming the same piece of hardware.

As I noted earlier, probably the hardest part of this effort is partitioning.  The LiveCD that you booted has a nice facility for partitioning hard drives.  While you're booted into Ubuntu select System | Administration | Partition Editor.  It'll show you what you have.

With you new found knowledge of grub, partitions and dual (soon to be triple) booting you're set to go. You'll need to decide what sizes of partitions you need.  I dabble in a variety of Linuxes (Linuxi?) and Windows.  Ubuntu is pretty happy with 15GB.  That would leave a lot of room for data and programs.  OTOH you'll be using some sort of files for your benchmark and you'll have to take that into consideration.

The Ubuntu installations will take care of installing grub so that you can reference the already installed OSes on the system.  The second Ubuntu install will leave you with access to Vista and the 1st Ubuntu install.  Both Ubuntus will have a /boot/grub/menu.lst that controls grub.  Only the second one is effective.  That can be a tad confusing when you're booting into the 1st Ubuntu.  

You should supply a SWAP for each installation.  I would not share the SWAP partitions for fear of messing up your test.  I doubt that you want to have the hard drive be accessed while running the SSD test.

Google and the forums here are your friend. Please let us know how things go.

---

### Post by praytor on 2009-10-25
Thanks for the long writeup, urugTON.  :)  Looks like I have a lot of reading and stuff to do.  

I haven't installed the SSD yet (it's coming in about 5 days).  That's what I meant by tweak the BIOS-- it is unclear to me how I will get the system to recognize that there is a new drive.  I assumed I would have to interact with the BIOS.  Will it just sort of happen automatically after I install the drive and power on the computer?  

Also, I just realized that I apparently already have a partition on my hard drive-- it's the one from HP used for recovery.  (They give us this instead of a recovery CD.)  This isn't a problem right (so long as I don't do anything silly like overwrite that somehow during Ubuntu install).

Regarding swap, is it important to have a swap partition or is a swap file about as good these days?  

Thanks again.  I'll definitely keep this forum + google handy if I run into trouble when I try to partition the drives and install Ubuntu.

---

### Post by urugTON on 2009-10-25
I have no experience with SSD.  I would assume that it simply presents itself to the BIOS as a SATA drive.  Plug it in (power & data), boot it up and see what you get.

I've used a swap partition versus a file for no particularly good reason.  For comparison purposes, I'd do swap the same way for both Ubuntu installations.

I'm glad you mentioned that you have a recovery partition but no installation media.  I would encourage you to see if HP will cough up the installation media as Gateway did for me a year ago.  There may be a way to create the install media from your hard drive.  Dell let me do that some while back.

Without the Vista install media, you'll be at risk of not getting Vista to run again once you start resizing partitions and installing grub.  By all means back up the hard drive before you start.  I don't mean the files.  I mean the whole disk.  One place to start that looks promising is at:

[http://packratstudios.com/index.php/2008/03/11/symantec-ghost-who-a-list-of-open-source-alternatives/](http://packratstudios.com/index.php/2008/03/11/symantec-ghost-who-a-list-of-open-source-alternatives/)

I can see you now going "great more reading!"  Dual booting offers some interesting opportunities and some interesting problems.  Hopefully the reading will help you avoid some of the mistakes I've made along the way.

Good luck.

---

