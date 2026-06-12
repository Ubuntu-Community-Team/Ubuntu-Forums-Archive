---
title: "How can I move\resize my Ubuntu partition?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by bf109 on 2009-03-13
Total newb here so I thought I'd start with fair warning. :D

I have a laptop with a 80gb harddrive running Vista and Ubuntu 8.10. I want to kill the Vista partition (boot partition) and then have my Ubuntu partition be the only OS on the laptop using the entire 80gb HD so that I can setup multiple VM's in VBox. I installed GParted and the drives look like this:

1. Unallocated - 1mb

2. dev/sda1 - 5.59gb NTFS (Vista recovery partition. I would like to image this partition and save on my server for later use if needed).

3. dev/sda2 - 44.53gb NTFS (Vista Home Premium partition) - Boot Partition

4. Unallocated - 6.77mb

5. dev/sda3 - Extended partition - 24.41gb

6. Linux Swap - 1.85gb

7. dev/sda6 - ext3 - 22.55gb (Ubuntu partition)

Please refer to attached GParted screenshot for visual.

The Ubuntu partition is in the extended partition and the recovery partition and the Vista partition look like primary drives.

I need to image and store the recovery partition and then kill all the partitions so that I can resize the ext3 Ubuntu partition to the entire 80gb capacity. Please list open-source imaging utilities to use and if possible a detailed process as I am quite new to Linux but totally loving it!

Thanks in advance.

---

### Post by taurus on 2009-03-13
You know that you cannot resize Ubuntu partition while you are using it, right?  If you want to resize your harddrive, you need to use gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

And if you want to do a backup, try CloneZilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

---

### Post by Therion on 2009-03-13
Looks simple enough to me.

Your Windows install is occupying /sda1 and /sda2.
You would want to remove those two partitions.
That should leave you with a large amount of contiguous unallocated space which you would then assign to your existing Ubuntu install, specifically /sda6.

Now then, doing this will mean your primary Ubuntu partition is going to be /sda6 (versus /sda1 like it would be had you done this at install).  I only point that out because I'm totally anal about stuff like that and it would bother me if my primary partition was NOT /sda1...  It would keep awake at night.

---

### Post by bf109 on 2009-03-13
> **taurus said:**
> You know that you cannot resize Ubuntu partition while you are using it, right?  If you want to resize your harddrive, you need to use gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

And if you want to do a backup, try CloneZilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

Yeah, I did know that much? ;)

I guess my main concerns are:

- How can I make sure that the recovery partition is bootable should I want to install Vista again later on?

- How can I resize the Ubuntu install to the whole drive while insuring that I will be able to boot into it again?

I really want to avoid having to reconfigure my Ubuntu install all over again should this process destroy my Ubuntu partition. Is there a very detailed tutorial somewhere that can help a newb ensure that this wont happen? ;)

---

### Post by meierfra. on 2009-03-13
I wouldn't resize the Ubuntu partition. Just deleted the two  NTFS partition and then create a new ext3 partition. This will only take a few seconds with gparted and can be done without a LiveCD. Resizing  the Ubuntu partition will take  a few hours. And you will have to reconfigure Grub and fstab.

And keeping  your virtual maschines on a separate partition  from you operation system  seems  like a safer option anyway.

---

### Post by bf109 on 2009-03-13
> **Therion said:**
> ...because I'm totally anal about stuff like that and it would bother me if my primary partition was NOT /sda1...  It would keep awake at night.

LOL! Well, to be honest I don't like the idea either and was kind of hoping that I might be able to image the sda6 and somehow re-apply the image so that it becomes sda1. Is that possible?

---

### Post by bf109 on 2009-03-13
> **meierfra. said:**
> I wouldn't resize the Ubuntu partition. Just deleted the two  NTFS partition and then create a new ext3 partition. This will only take a few seconds with gparted and can be done without a LiveCD. Resizing  the Ubuntu partition will take  a few hours. And you will have to reconfigure Grub and fstab.

And keeping  your virtual maschines on a separate partition  from you operation system  seems  like a safer option anyway.

Well, as a said I was hoping for a solution that would create a bootable image backup of the Vista recovery partition should I need to fuss around with Vista again at a later date.

---

### Post by lynnevan on 2009-03-13
> **bf109 said:**
> Total newb here so I thought I'd start with fair warning. :D

I have a laptop with a 80gb harddrive running Vista and Ubuntu 8.10. I want to kill the Vista partition (boot partition) and then have my Ubuntu partition be the only OS on the laptop using the entire 80gb HD so that I can setup multiple VM's in VBox. I installed GParted and the drives look like this:

1. Unallocated - 1mb

2. dev/sda1 - 5.59gb NTFS (Vista recovery partition. I would like to image this partition and save on my server for later use if needed).

3. dev/sda2 - 44.53gb NTFS (Vista Home Premium partition) - Boot Partition

4. Unallocated - 6.77mb

5. dev/sda3 - Extended partition - 24.41gb

6. Linux Swap - 1.85gb

7. dev/sda6 - ext3 - 22.55gb (Ubuntu partition)

Please refer to attached GParted screenshot for visual.

The Ubuntu partition is in the extended partition and the recovery partition and the Vista partition look like primary drives.

I need to image and store the recovery partition and then kill all the partitions so that I can resize the ext3 Ubuntu partition to the entire 80gb capacity. Please list open-source imaging utilities to use and if possible a detailed process as I am quite new to Linux but totally loving it!

Thanks in advance.

Duplicating some of what has been said already about using gparted live and cloning or imaging (try dd), I'd delete sda3 like you say you want to, mirror or image sda2 to whereever, then dump it, then just move sda6 to sda1.  If you go into the grub directory, you can rename sda6 to sda1 or change the UUID or whatever and it should work OK.  One thing you might have trouble w/ is booting Ubuntu after you move it, but there's solutions for that if necessary.
If you image w/ dd or copy & paste w/ qparted live, then yr vista restore should be bootable if it was meant to be bootable.

---

### Post by Therion on 2009-03-13
> **bf109 said:**
> Well, as a said I was hoping for a solution that would create a bootable image backup of the Vista recovery partition should I need to fuss around with Vista again at a later date.
I'm going to go ahead and suggest that what you want to do is possible.  HOW to do it I'm unclear, though I think I have it worked out in my head.  Even so, I'm not going to try and walk you through it because it sounds like there's a lot at stake here.

You know what I do suggest a lot though... I suggest that people simply invest in a spare hard drive.  Wait for a sale and snag a cheap internal drive.  I have a few that I use purely for experimentation purposes (read: disto-hopping).  Pop in your X-Drive (as I call them), do a full install of whatever you want for as long as you want, decide if you like it or not.  Lather, rinse, repeat!

Meanwhile your "permanent" drive with it's bootable Vista partition and stuff sits safe and sound on the closet shelf until needed (or installed and simply out of the boot-sequence until needed).  Seriously... The freedom that comes with having a spare drive or two is incredible.  Five minutes with a screwdriver and a quick BIOS change is your worst case scenario for a drive swap.  

In point of fact I've currently installed three drives in my system:  'Drive A' is my day to drive (Ubuntu 9.04 right now) but if that were to suddenly bork on me, I switch to 'Drive B' with it's known solid, stable and fully configured install of 8.04 and I'm back in business in two minutes flat.  'Drive C' is for data and backups.  My whole system could bork totally but my data stays safely tucked away on it's own physical drive.

Just something to think about.

---

### Post by bf109 on 2009-03-13
> **Therion said:**
> I'm going to go ahead and suggest that what you want to do is possible.  HOW to do it I'm unclear, though I think I have it worked out in my head.  Even so, I'm not going to try and walk you through it because it sounds like there's a lot at stake here.

You know what I do suggest a lot though... I suggest that people simply invest in a spare hard drive.  Wait for a sale and snag a cheap internal drive.  I have a few that I use purely for experimentation purposes (read: disto-hopping).  Pop in your X-Drive (as I call them), do a full install of whatever you want for as long as you want, decide if you like it or not.  Lather, rinse, repeat!

Meanwhile your "permanent" drive with it's bootable Vista partition and stuff sits safe and sound on the closet shelf until needed (or installed and simply out of the boot-sequence until needed).  Seriously... The freedom that comes with having a spare drive or two is incredible.  Five minutes with a screwdriver and a quick BIOS change is your worst case scenario for a drive swap.  

In point of fact I've currently installed three drives in my system:  'Drive A' is my day to drive (Ubuntu 9.04 right now) but if that were to suddenly bork on me, I switch to 'Drive B' with it's known solid, stable and fully configured install of 8.04 and I'm back in business in two minutes flat.  'Drive C' is for data and backups.  My whole system could bork totally but my data stays safely tucked away on it's own physical drive.

Just something to think about.

Good suggestion Therion. I have a 320gb USB mini HD that I can use for that (actually its my girlfriends and she isn't using it for anything right now. I'm pretty sure she'll let me appropriate it and if she doesn't let me all I'll have to do is take away sex for a week and its mine ;). It has a mini-laptop drive in its enclosure that I'm pretty sure will install in my laptop but if not the way the economy is I'm sure I can pick one up dirt cheap.

Well, if you have any spare time today or next few days and you want to give me a breakdown of how you have it mapped out in your experienced little head there then I will take all responsibility for any mishaps that occur after implementing your strategies. I promise I won't hire a private dick to hunt you down so I can ingeniously destroy your life involving torture and/or fire should something go wrong. Really, trust me. ;)

All kidding aside if the recovery partition gets hosed its not the end of the world. I just wanted to save it if possible. I will study up on the imaging utilities mentioned in the thread and all and use this little project as a way to learn more about Linux since I really am enjoying it so much more than Windows.

Side question: I installed Wine and tried to run an ancient golf game using it called Links98 and the frame rates where so low that I couldn't play. Any suggestions from an expert?

---

### Post by bf109 on 2009-03-13
Well after some thought I've decided to try a full drive image backup using clonezilla then use gparted to format the Vista partitions to ext3. Seems like the easiest and safest approach. Thanks all for your time and input.

---

### Post by BudE on 2009-03-14
> **bf109 said:**
> Total newb here so I thought I'd start with fair warning. :D

I have a laptop with a 80gb harddrive running Vista and Ubuntu 8.10. I want to kill the Vista partition (boot partition) and then have my Ubuntu partition be the only OS on the laptop using the entire 80gb HD so that I can setup multiple VM's in VBox. I installed GParted and the drives look like this:

1. Unallocated - 1mb

2. dev/sda1 - 5.59gb NTFS (Vista recovery partition. I would like to image this partition and save on my server for later use if needed).

3. dev/sda2 - 44.53gb NTFS (Vista Home Premium partition) - Boot Partition

4. Unallocated - 6.77mb

5. dev/sda3 - Extended partition - 24.41gb

6. Linux Swap - 1.85gb

7. dev/sda6 - ext3 - 22.55gb (Ubuntu partition)

Please refer to attached GParted screenshot for visual.

The Ubuntu partition is in the extended partition and the recovery partition and the Vista partition look like primary drives.

I need to image and store the recovery partition and then kill all the partitions so that I can resize the ext3 Ubuntu partition to the entire 80gb capacity. Please list open-source imaging utilities to use and if possible a detailed process as I am quite new to Linux but totally loving it!

Thanks in advance.

For what it's worth, I just took my 320gb hdd and added another partition to hopefully put Win2K on it for some older programs that need Windows. I did it by going to the desktop and then System / Administration / Partition Editor      Made an 80GB chunk then let Linux 8.04 have the rest all to itself. Worked like a charm and didn't destroy not one bit of data. 

Bud

---

