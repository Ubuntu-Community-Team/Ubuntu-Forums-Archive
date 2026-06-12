---
title: "Initial Installation"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by anup81 on 2009-09-10
I'm a first time user of Linux with very little knowledge of Linux. I've got a CD with Ubuntu 9.04 installer on it. I'm using the LiveCD option to boot the laptop into Linux. However, when I'm trying to install Linux, I'm unable to do so (probably because I'm a bit scared with all the options that are coming up and I'm not so sure of the answers).

I have 1 HDD with 2 partitions on it. C: drive already has Windows Vista on it (which I don't want to remove as of now). I plan to install Ubuntu onto D: drive (10GB space available on it). Could anyone please guide me with the installation and give the step by step procedures to be followed.

Thanks in advance

---

### Post by murph10 on 2009-09-10
Hello Initial Install Support,

As with most of us newbies, I need some assistance. Mine is similar to the above persons issues, so I am just adding to it with a reply:

BACKGROUND:
I have a Sony VIAO SZ650N/C notebook with Windows Vista Business on it currently and when the problems happened. 

Sony seems to have some crap software (bloatware) on it when it loads as I have CDs with "Vista Recovery Media Kit" the notebook came with Vista preloaded and they do bring me into a repair program but it is unable to repair anything;
As a side note -- I down-graded to Windows XP a year ago but went back to Vista Business (and XP  killed many of the features available to Vista on this notebook, I doubt it has anything to do with this but thought I should mention it). 

Vista was running fine when this started and I started the install of Ubuntu. 

Before I went to the Ubuntu 9.04 LiveCD, I cleaned out alot of crap software (remove programs) on the hard-drive, nothing system wise and Vista ran fine, I then defragged and made sure I had a great deal of space on the C (and only hard drive) around 43GB.

I should also note that flash memory cards are on this notebook and were in when this was installing they are lettered D;, E;, F: and in retrospect I should have removed them but that is not the case, they were and are in the computer.


UBUNTU INSTALL FROM LIVECD:

I then used the Ubuntu LiveCD9.04 to install Ubuntu onto the hard drive. It hung at the partition loading. This is where the problem is I suspect.

I surmise the problem is with the partitions and GRUB and currently as I write this all I get when powering up is: GRUB 1.5 will not/cannot load. ERROR 21 (which I have found means disk not where it is looking, or no disk essentially). The disk is there as I have both a NFTS and the Linux load, swap and other file partitions --- I am a little lost when discussing these but I am coming up to speed quickly and would APPRECIATE SOME HELP FROM THE Windows/Ubuntu GURU !!!

BIOS does not seem to be loading as the above noted "GRUB 1.5 will not load error" is immediate after the power up (all I get when I turn the system on). does not look like the BIOS is loading. 

I CAN load the LiveCD and run it off the CD/DVD Drive,  but I am so inexperienced in Linux that I am now NOT wanting to move forward without some help as I cannot afford to loose the Vista OS or the data there (I know it is there, I can see it in Linux) -- Nothing has been deleted and nothing has been reformatted, in looking around in Ubuntu I can see my Vista files in the "file manager" in Ubuntu and it is seeing it as unallocated space. Other files are on this partition as I know the file names, so, I just need to fix the boot sequence -- should have read up a little more but that is for later, now I need to fix the notebook to run both as I am excited about Ubuntu (despite the problems in loading it properly, my fault, not the Computers obviously).

I suspect because Sony has crap on the boot of this system something is off or when doing the partitions the bootloader got deleted, changed, or not installed properly --  I cannot afford to reformat, I need the Vista system and files/data on it and at worst....well, the OS are there, I just need to tell the system where to look for the bootloader, NO?

I have read all the other install pages and they all seem to have different issues with them. If I load the LiveCD and go from inside Ubuntu that would be great.

Thanks in advance,
Murph10

---

### Post by Zimmer on 2009-09-10
If you are attempting a dual boot with VISTA I would recommend the following reading before you start.
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

This guide will help you with setting up space on Vista ready for an Installation..
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

But when it comes to loading GRUB do as the EasyBCD site advises and load it to the UBUNTU partition and NOT the MBR, then go back in Vista, download EasyBCD and set it up to see the Ubuntu install as per the instructions

---

