---
title: "Advice needed"
date: 2008-07-14
forum: General Help
---

### Post by Tuliku on 2008-07-14
Hi all,

I'm very new to this, but i would like some advice on installing Ubuntu 8.04.1 as dual boot on my laptop.
My laptop has a little unique setup, so that's why the advise is needed... :-)

My laptop:
- Compaq NX6125 - 250 GB harddrive - 2 GB mem - dual boot: win xp & kubuntu 7

And the harddrive looks like this
- 02 gb - EXT3, primery, Kubuntu 7(root, basic libraries)
- 48 gb - NTFS, primery, Windows XP sp3
- 20 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 75 gb - NTFS, logical, storage for windows
- 17 gb - EXT3, logical, kubuntu 7 (other libraries)
- 01 gb - Reiser FS, logical, swap

The reason for the 2 gb at the beginning of the disk was due to that Grub had an issue with the size of the disk.
*( Grub Stage 1.5 - Grub Loading, Please Wait - Error 18 )*
Now with the root at the beginning, all is fine.

My friend installed kubuntu for me back then, but he is not in the country anymore, and now i would like to install myself Ubuntu 8.04.1 instead of Kubuntu 7.

In the "graphic install" guide from ubuntu, i dont see any relevant info about having / doing something with the 2 gb root at the beginning of my disk...

I hope i am clear enough..

Any suggestions regarding how to install it correctly ?

Thanks in advance

---

### Post by coffeecat on 2008-07-14
A few thoughts rather than advice, but first a couple of comments.

> **Tuliku said:**
> The reason for the 2 gb at the beginning of the disk was due to that Grub had an issue with the size of the disk.
( Grub Stage 1.5 - Grub Loading, Please Wait - Error 18 )
Now with the root at the beginning, all is fine.

Grub error 18 is:

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).That's a pity because I've set up several multi-boots over several computers and I've never had a problem with booting from a logical root partition, even something as remote as sda13 on a 250Gb drive. It's clearly a BIOS rather than a Grub issue but can you give any more details?

> **Tuliku said:**
> - 01 gb - Reiser FS, logical, swap

Point of information - Linux swap partitions have a special filesystem. Reiser is a FS used for Linux data partititions - can be used as a root filesystem. Unless your friend did something very clever using Reiser as a swap partition. Is that possible? I don't know.

Until we know more about the BIOS limitation, it's difficult to know what to recommend. One possibility is to designate the 2Gb partition 1 as your /boot partition and the 17GB for everything else, the root (/) partition. That should get round the BIOS problem. That may be what your friend did, but 2Gb is one helluva size for a /boot. 100Mb is usually enough.

One option - if Grub/BIOS between them can reach someway beyond 50Gb (yes I know about the 8Gb in the Grub message, but we need to know the limitations of your BIOS) - is to relocate whatever it is you are doing with the three NTFS partitions, and have a Linux partition in place of the first NTFS logical one. Can you give some more details?

By the way, how old is the machine? I thought this BIOS issue was a thing of the past.

---

### Post by snowpine on 2008-07-14
Easy. You don't have to mess around with the partitions at all. Just upgrade your Kubuntu from 7 to 8.04, and then at the command line, type 'sudo apt-get install ubuntu-desktop' and you'll be good to go. :)

edit: and you can get rid of Kubuntu with 'sudo apt-get remove kubuntu-desktop'.

---

### Post by Tuliku on 2008-07-14
**@ coffeecat:**
That friend used to be the Linux expert in this company before me moved to another country / company. So i assume he was indeed clever, but i can not gove more details i am afraid.
In a few hours i will be home and give you some more info on the partitioning, as my laptop is at home.

About the bios, i have the F11 one:  [**click**]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=471756&prodTypeId=321957&prodSeriesId=471753&swLang=8&taskId=135&swEnvOID=1098")
There is also the F12, but you need to create a diskette for that, and that is not possible with a laptop.......
The laptop itself is about 3 years old, and discontinued.

**@ snowpine:**
Sounds easy, but isn't a fresh install better ?
Partially i am doing this to get to know linux better, so it would be a good experience, but i can not afford to loose anything stuff on the windows partitions.
That's why i posted for advice here.

The fast response here is really cool, thanks a lot !

---

### Post by coffeecat on 2008-07-14
I must state upfront that I've never had to deal with this BIOS limitation myself - I've been lucky - so I'm not the best person to advise.

I've had a look at that link. They recommend you use a USB floppy drive to do the BIOS update. If you haven't got one, that's a bit of an expense just for a BIOS upgrade. Besides, as far as I can tell from the Revision History, the F12 version isn't going to help anyway. And I'm a bit leery about BIOS upgrades anyway. I've come across horror stories of things going wrong and people reducing their expensive computers to door-stops. If it ain't broke...

Have you had a look in the BIOS settings? There may be a setting you could change there. This inability to boot up from beyond a certain sector of the HD is going to be a real hurdle for you.

---

### Post by snowpine on 2008-07-14
> **Tuliku said:**
> 
**@ snowpine:**
Sounds easy, but isn't a fresh install better ?
Partially i am doing this to get to know linux better, so it would be a good experience, but i can not afford to loose anything stuff on the windows partitions.
That's why i posted for advice here.


Hi Tuliku, the advantage of the method I described is that there's no risk of damaging the Windows partition. However, re-reading your original post, you might get into trouble because the 2gb partition may get full. So I would proceed with caution.

I am not personally qualified to talk you through a fresh install given your partition situation. I would listen to advice from Coffeecat. :)

ps You should back up the critical data on your Windows partitions. That is just common sense.

---

### Post by Tuliku on 2008-07-14
**@ coffeecat:**
In the bios settings not much to change that, we checked everything when he installed kubuntu back then, but i will put some screenshots here tonight just to be sure.

**@ snowpine:**
Of course :-) already made even a full backup using norton ghost (hirens 9.5 bootcd) but i prefer to prevent any issue then to use the backup :-)

More info to come in about 1.5 hour when i am home.

---

### Post by coffeecat on 2008-07-14
> **snowpine said:**
> I would listen to advice from Coffeecat. :)

Thanks a bunch! :(

:lol:

---

### Post by Tuliku on 2008-07-14
Here some more info:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa554a554

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         253        6374    49170208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            6374       30401   192999681+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3               1         253     2026080   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5            6374        8924    20480008+   7  HPFS/NTFS
/dev/hda6            8924       18485    76802008+   7  HPFS/NTFS
/dev/hda7           18485       28047    76802008+   7  HPFS/NTFS
/dev/hda8           30280       30401      979933+  82  Linux swap / Solaris
/dev/hda9           28047       28655     4883728+  83  Linux
/dev/hda10          28655       28739      680368+  83  Linux
/dev/hda11          28739       30279    12368128+  83  Linux

---

### Post by Tuliku on 2008-07-14
And attached screenshots from the bios settings.

---

### Post by coffeecat on 2008-07-14
Firstly, if I'm not already out of my depth, then the water is up to my neck and someone nearby is making very big waves. :(

Anyway - the plot thickens. That latest partition information you posted is interesting. Your friend has setup the 2Gb Linux partition as hda3 - meaning partition no 3 - but it occupies the first part of the HD. Then comes hda1, your Windows C: partition (I presume), partition 1, but occupying the second set of sectors on the disc.

hda2 is the extended partition which is the 'container' for all the logical partitions, which are numbered (by convention) from hda5. Then come the three NTFS partitions and the swap partition and after that **three** Linux partitions, which if my sums are correct add up to the 17Gb for Linux.

To be honest, this is going to be difficult. The placing of partitions 1 & 2 in reverse order looks like your friend's way of getting round the BIOS limitation and also the need for your Windows system partition to be partition 1.

But he also seems to have spread kubuntu over 4 partitions altogether. I'm sure for very good reasons, but....

We need to know what all those partitions are doing. Can you post the contents of /etc/fstab please?

You weren't thinking of getting yourself a new laptop, were you? :p

**Edit:** should have added - I looked at that set of BIOS screenshots. My, what a classy BIOS you've got there. But you're right - I can't see anything there that will help.

---

### Post by Tuliku on 2008-07-14
**The contents of /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=926956aa-462a-4c37-bb02-31164df46860 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda11
UUID=fa0563a9-9742-46c2-8c6a-0a3a4e079a9f /home           ext3    relatime        0       2
# /dev/hda9
UUID=c0f711f1-da38-4ea7-aac7-3b2f519fbbef /usr            ext3    relatime        0       2
# /dev/hda10
UUID=5a712f86-bbde-404c-ad5f-65a0c4bef336 /var            ext3    relatime        0       2
# /dev/hda8
UUID=a11cdeee-39a3-40da-93ee-891a9c6dab90 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Tuliku on 2008-07-15
I've got my laptop with me, so i can provide any info needed quickly :-)

As a very very very last option, i'm willing to format my whole disk, and do different partitioning if needed, but i prefer to keep it as it is... for now  (until the times comes that i'm very familiar with linux)

Or is moving partitions also an option if that helps and creates no issue's ?

---

### Post by coffeecat on 2008-07-15
Light at the end of the tunnel! I'd realised that your friend must have put /usr in another partition - it's the largest system directory - but I couldn't be sure what the other two partitions were for. It all makes sense now.

To interpret:

hda3 = / - That forward slash means it is the root partition.
hda9 = /usr
hda10 = /var - another big system directory.
hda11 = /home - contains not just your home folder, but any other accounts that are created.

And hda8 = swap.

If you are intending a clean install, boot up the live Ubuntu CD and on the desktop double-click the installer. When you get to the partitioning stage, the button you **don't** want is usually pre-ticked. What you want (from memory) is 'Custom'; I think it's the last choice. If I have time I'll boot up a live CD and check this out. After this take care. You'll need to choose the partitions exactly as above, except that (for reasons that don't matter at the moment), in 8.04 you'll probably find that hda3, hda9, etc are referred to as sda3, sda9, etc. For /, /usr and /var choose for the partitions to be reformatted. For /home you have a choice. If you leave it unformatted you get to keep all your personal configurations and settings (and files in your home directory). Trouble is, with Kubuntu you were using the KDE desktop and, if I'm remembering the beginning of this thread correctly, you're about to install the Gnome version of Ubuntu. Gnome and KDE config files are entirely different. They don't interfere with each other but you won't get (most of) the advantages of a preserved home. Needs thinking about.

After that the installer should be plain sailing. If you get halfway into it and develop cold feet, you can always bail out and come back and ask questions. If you do want to cancel make sure you do so before it reformats any partitions - that's the point of no return.

Health Warning 1: I may have forgotten something. No guarantees.

Health Warning 2: On the principle of any piece of software always has yet to be discovered bugs, the installer just might do something nasty to your other partitions, or leave you with an unusable Ubuntu. If I was in your position, I would do an image/ghost backup of my Windows partition and archive all personal files. This is not to criticise the Ubuntu developers in any way. That installer will have been extensively tested, but your partition layout is unusual.

---

### Post by coffeecat on 2008-07-15
> **Tuliku said:**
> I've got my laptop with me, so i can provide any info needed quickly :-)

As a very very very last option, i'm willing to format my whole disk, and do different partitioning if needed, but i prefer to keep it as it is... for now  (until the times comes that i'm very familiar with linux)

Or is moving partitions also an option if that helps and creates no issue's ? 

I was thinking about that yesterday. There's the BIOS limitation to think about. Your friend obviously knew his onions and had looked into this carefully. If we concoct a different partition layout, we might trip over the BIOS problem again. It seems to safer to stick with the current layout. If it works, it'll work with a later version of Ubuntu.

(Famous last words - :| )

---

### Post by Tuliku on 2008-07-15
Sounds all good and logic to me.
The backup image i made already, so after lunch i will try this.
When done, will update it here :-)

Thanks a lot !

---

### Post by Tuliku on 2008-07-15
Live update: 

13.15 - Configuring the installation
13.22 - Installation started
13.36 - Installation finished, rebooting
13.37 - Dual boot visible, Booting into Windows XP
13.38 - Booting into Windows XP = successful :-)
13.39 - Booting into Ubuntu 8.04.1 = successful !!!!! :-)
13.40 - Me very happy !

Thank you very much, i appreciate the quick and great help a lot !
Topic can be closed

---

### Post by snowpine on 2008-07-15
> **Tuliku said:**
> Live update: 

13.15 - Configuring the installation
13.22 - Installation started
13.36 - Installation finished, rebooting
13.37 - Dual boot visible, Booting into Windows XP
13.38 - Booting into Windows XP = successful :-)
13.39 - Booting into Ubuntu 8.04.1 = successful !!!!! :-)
13.40 - Me very happy !

Thank you very much, i appreciate the quick and great help a lot !
Topic can be closed

Yay! Glad you got it working! :)

---

### Post by coffeecat on 2008-07-15
> **Tuliku said:**
> Live update: 

13.15 - Configuring the installation
13.22 - Installation started
13.36 - Installation finished, rebooting
13.37 - Dual boot visible, Booting into Windows XP
13.38 - Booting into Windows XP = successful :-)
13.39 - Booting into Ubuntu 8.04.1 = successful !!!!! :-)
13.40 - Me very happy !

Excellent news. And it's good to see the output of /var/log/Tuliku. :wink:

---

