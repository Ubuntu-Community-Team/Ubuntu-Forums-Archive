---
title: "Looking into making the full switch.."
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by GaMz on 2007-05-25
Currently I'm running on a HP dv6000t with the following specs (I don't know, you might need them :P):
 Genuine Windows Vista Home Premium (32-bit)
Intel(R) Core(TM) 2 Duo T5600(1.83GHz/2MB L2Cache)
15.4" WXGA BrightView Widescreen (1280x800)
256MB NVIDIA(R) GeForce(R) Go 7400
2GB DDR2 System Memory (2 Dimm) 80GB 5400 RPM
8X DVD+/-R/RW w/Double Layer Support
Intel(R) PRO/Wireless 3945ABG Network Connection
12 Cell Lithium Ion Battery
Microsoft(R) Works 8.0

I've been using the Knoppix LiveCD for a while now and I'm looking to make the full switch over to Kubuntu. I am hesitant thought because it will be my first time not to have Windows to fall back on. I'm curious how easy it is to completely remove Vista and replace it with Kubuntu? Then if it didn't work out (which I don't think will happen but...) how hard would it be to remove Kubuntu and reinstall Windows?

My understanding is that I have to boot Kubuntu from a LiveCD and I will be able to install from there? I've read somewhere that Ubuntu only needs 3 GB's to install is it the same for Kubuntu?

Sorry for all the questions but I'm really exited about making the switch and I'm looking for insight.

---

### Post by WayOutWest on 2007-05-25
I am also looking to do this. except I am using XP.

---

### Post by merlinus on 2007-05-25
You basically have two choices.  If you want to lose windows completely, boot from the ubuntu (or kubuntu) live cd.  When it is up-and-running, click the Install icon.

When you get to the part about partitioning, tell it to use the entire disk.  Bye-bye redmond!

OTOH, if you are unsure, or have cold feet, you can setup a dual-boot system.  

Do the same as above, but when you get to partitioning, tell it to use the free space.

But beforehand, be sure to defrag your windows partition.

Good luck!

-merlin

---

### Post by discmaster on 2007-05-25
I kept windows around on a small partition just for things that I need to do right away, & haven't learned to do yet in linux;
Such as;

*Major printing projects, creations with a lot of text & graphics.
*Audio editing
*Video editing

Plus the fact that if I had problems, at least I had something to fall back on so I could at least get on the 'net & get some help!
:)

---

### Post by IntuitiveNipple on 2007-05-25
When using Vista you can resize the existing Vista partition from within Vista (using Administrative Tools -> Disk Management) to create space on the disk. 

Then you can start off by installing GNU/Linux in a dual-boot configuration without loosing precious disk space. When you are eventually convinced you will not need Vista you can remove the Vista partition and  use it as additional storage for GNU/Linux, move and grow one of your Linux partitions to use the additional capacity, or keep it and run it as a vmware guest OS inside Linux.

I've recently done this on a new Sony Vaio laptop. I posted [an article about it](http://ubuntuforums.org/showpost.php?p=2702973&postcount=30) in the Hardware Compatibility thread which gives some information on the disk layout I chose.

On XP you can resize using Partition Magic (if you have it), or use ntfsresize (part of ntfsprogs package) and fdisk in combination from a LiveCD. This method is, although 'free', quite complicated even for hackers (some very careful maths involving sector numbers is required).

---

### Post by GaMz on 2007-05-25
Wow, thank you that is easy...

Meh, I'm just going to jump right into Kubuntu.

It will make me get used to it so I don't just switch and do it on Windows :P. Plus I can always put Windows back on it later for any games I might want to play...

Thanks for the advice, didn't realize it would be that easy :D


Edit: Whoa, two more posts while I was typing that up. Thanks for the help, I'll let you guys know how it turns out. More likely I'll be back to ask more questions though :P

---

### Post by WayOutWest on 2007-05-27
Isn't there a partition program during the ubuntu install?

---

### Post by ramjet_1953 on 2007-05-28
Yes, after you boot the LiveCD and click on the install icon on the desktop.

You will go into a graphical installer, which gives you the option to use the entire HDD for the install, keep your existing Windows partition, or even a manual partitioning mode. 

This manual mode allows you to set-up the partitions on the hard drive any way you want to. 

Many people, including myself, set-up a seperate partition for the [COLOR="Blue"]/home[/COLOR] directory. 

If you are not familiar with partitioning, however, I would recommend either of the first two options.

Please remember this as you commence your adventure into Linux. It is not Windows and if you try to use the things that you have learned over the years of use with Windows to try to understand Linux, you will become frustrated and disillusioned.

Start with an open mind and and be willing to be a newbie again and your experience will be fun and an adventure, even when you encounter seemingly insurmountable problems.

These forums are here to help you and if you ask for help in a respectful manner, detailing each problem individually, you will not only overcome those problems, but will also learn heaps along the way.

Regards,
Roger :cool:

---

