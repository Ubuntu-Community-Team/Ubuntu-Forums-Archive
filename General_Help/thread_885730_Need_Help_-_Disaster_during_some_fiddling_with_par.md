---
title: "Need Help - Disaster during some fiddling with partitioning tool -"
date: 2008-08-10
forum: General Help
---

### Post by ramnarayan on 2008-08-10
Hi

Did some thing very stupid a while back

I was looking at my On Board Hard disk (80 GB) and there was a
partition that was lying unused and i wanted to reformat it to VFAT.
For some reason gparted did not allow me to do anything, so very
*stupidly* i checked the change disklabel option and said yes to msdos
disklabel.

Needless to say it blew all my partitions away and said that it has
reformatted my disk (within a few seconds)

So right now there is just one grey blob that show up as an
unformatted disk /dev/sda about 75 Gigs.

the existing partions were

sda1    ntfs - about 10 Gig  with win xp OS (came by default with the machine)
sda2    vfat  - about 5 Gig windows recovery (came by default with the machine)
sda3 -  vfat - about 6 gig shared data section (
sda 4 - logical volume under which the following partitions were created
sda 5 - ext 3 /home  about 40 gig - my home - where all the data is
sda6 - ext3 /boot about 100 mb
sda7 - swap about 2.5 gig
sda8 - ext3 /   where my linux os is located
sda9 - ext3 -- this was the blank partition (i had a second ubuntu
8.04installed here and was trying to free this space to use. But I was
doing this from 7.04 and it may not have been able toread sda9 which
was created by a *later* version

***
I am not fiddling with the HD disk but have booted off a live cd and
am checking the HD with testdisk - which seems to show all the
critical partitions. At the worst case i want to recover my /home
which i did not back up for the last 15 days and there is stuff there
which i don't want to lose.

At the best case i want to return my hd to the previous working
configuration which has dual boot - ubuntu 7.04 and Windows Xp (there
is also a windows recovery boot option)

*** Like i said Test Disk is showing  most of the partitions namely

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
   Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1304 254 63   20964762 [IBM_PRELOAD]
P FAT32 LBA             1305   0  1  2033 254 63   11711385
L Linux Swap            2034   1  1  2495 254 63    7421967
L Linux                 2959   1  1  3759 254 63   12868002 [/]
L Linux                 3760   1  1  9089 254 63   85626387 [/home]

it seems to be not showing /boot and the sda3 (the shared data drive)

i don't mind losing sda3 because that data is backed up.

***

So Should i do this

run testdisk as sudo


*Step 1*
Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 80 GB / 74 GiB

*Step2*
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

so in this i select [Intel]

*Step 3*
which shows
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ MBR Code ]  Write TestDisk MBR code to first sector
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection

Note: Correct disk geometry is required for a successful recovery. 'Analyse'process may give some warnings if it thinks the logical geometry is mismatched.

QUESTION: WHAT is the correct disk Geometry ??

*Step 4 Analyse*
which shows:

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
    Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1304 254 63   20964762 [IBM_PRELOAD]
P FAT32 LBA             1305   0  1  2033 254 63   11711385
L Linux Swap            2034   1  1  2495 254 63    7421967
L Linux                 2959   1  1  3759 254 63   12868002 [/]
L Linux                 3760   1  1  9089 254 63   85626387 [/home]

*Step 5* - [MBR CODE]
Should i just do this and let testdisk do the rest
or should i do something else

Currently running of a live session of Ubuntu 7.04 
***
thanks
ram

---

### Post by gobbles414 on 2008-08-10
I'm sorry for your misfortune. But if I am correct, changing the disklabel on a hard drive does not actually overwrite the data on that drive. So it is very likely that you'll be able to recover ALL of your data!:) What you need to do is run some sort of file recovery program. Because of the way in which your hard drive is partitioned, I recommend that you do the following:

1. Purchase a new hard drive for your computer. Obviously, it would be a good idea for your new hard drive to be larger than 80 GB. If your computer is a laptop, you'll also need to purchase an external enclosure for your laptop's current hard drive. Be sure that the hard drive and enclosure that you purchase match your computer's motherboard. For example, don't buy an SATA hard drive if your computer only has IDE connectors. Similarly, don't purchase an SATA enclosure if your old hard drive is IDE-based.

2. (Desktop) Disconnect the power cable and data cable from your old hard drive. This will help to prevent you from accidentally damaging the data on your old hard drive later in this procedure. Then, install the new hard drive. If you're using two IDE hard drives, set your old hard drive to "slave", and your new hard drive to "master". If you're using one IDE hard drive and one SATA hard drive, I believe that you should set the IDE to master. If you're using two SATA hard drives, no master/slave configuration will be required.

2. (Laptop) Remove the old hard drive from your laptop. If it's an IDE hard drive, make a note of its current master/slave settings and then set it to master. Next, install the old hard drive in the enclosure. Now, install the new hard drive into your laptop. If it's an IDE hard drive, be sure that its master/slave settings are correct for your laptop -- based on the notes you took just a moment ago. Again, SATA drives don't require any sort of master/slave configuration.

3. Install Ubuntu 8.0.4.1 onto your new hard drive, and install all available updates.

4. Install a data recovery (sometimes called forensics) program onto your computer. There are several choices of such software in Synaptic. As I've never needed such a program, I cannot recommend one of them over the others.

5. (Desktop) Turn your computer off. Reconnect the power cable and data cable to your old hard drive.

5. (Laptop) While Ubuntu is on, connect your enclosure to your computer.

6. *Very carefully*, run your data recovery software.

---

### Post by ramnarayan on 2008-08-11
Hi 

Thanks Gobbles, kept some of what you said in mind
Ok so the good news is that i have my data back.

This is what i did

Booted of live Ubuntu 7.04 DVD
Added local repository that i have on an external hard disk

installed testdisk

ran its analyse and search deeper option

then asked it to write the MBR to the first sector

it managed to find the two partitions where my /home and /shared (vfat
data section shared with windows) is and now these are accessible

It has not managed to redo the ntfs win os and the windows recovery
partition or the Linux Ubuntu OS "/ " section.

But once i back my data up will try and redo this

ram

---

### Post by ramnarayan on 2008-08-11
Off this thread

but i have been noticing that many users have got "thanked" X times and "has thanked" X times in so many posts. And against my name there is 0 (zilch)

so thinking that i am very rude i looked at all my old posts and have seen enough thanks(given to others) to know i am not rude.

So whats the system to thank people and make it appear against ones profile ???

"thanks" ;-)

ram

---

### Post by gobbles414 on 2008-08-11
I'm glad that you've been able to recover your data. You may wish to save some time/effort by ordering a set of recovery CDs from HP -- instead of trying to repair your recovery partition. Besides, if it were me, I'd be happy to have the extra few GBs worth of hard drive space.

Regarding *thanks*, there's a little award medal icon in the lower-right corner of each post. If a post contains information that is either very informative and/or helps to solve the original poster's problem, the original poster is encouraged to issue a thanks. To be honest, I'm rather forgetful when it comes to thanking users who've helped me. I really should go back through my recent threads and thank some people. EDIT: Original posters are not the only ones who can give thanks.

---

