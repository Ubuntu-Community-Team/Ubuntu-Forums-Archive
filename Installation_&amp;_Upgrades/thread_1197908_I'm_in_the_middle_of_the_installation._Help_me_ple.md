---
title: "I'm in the middle of the installation. Help me please!"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by pooja on 2009-06-26
Hi, 

I'm in the middle of the installation process.
I'm stuck at step 4: Prepare disk space. I must choose between the following 4 options:
     [LIST=1]
[*]Install them side by side
[*]Use the entire disk
[*]Use the largest continuous free space
[*]Specify partitions manually (advanced)
[/LIST]

I chose the last option, **Specify partitions manually (advanced)**, since I don't want Grub to erase Windows' boot loader. This is what I am given:
 
Prepare Partitions
```
-------------------------------------------------------------------------
Device           Type   Mount point     Format?       Size       Used
-------------------------------------------------------------------------
/dev/sda
     /dev/sda1   ntfs                                130864 MB    53448MB
     free space                                      23622 MB
     /dev/sda1   ntfs                                5552 MB      4266 MB
```

I selected 'free space' and then pressed 'New partition' button.
A new window popped up asking

Type of new partition:   Primary         Logical  
Size in megabytes (10^6 Bytes): 23622 
Location of new partition: Beginning         End
Use as: Ext3 Journaling file system (drop down list with multiple choice including ext4)
Mount point: '/' (drop down list with multiple choice)

How do I organize this free space so that upgrading to future versions is easy? Help me, please!

---

### Post by lisati on 2009-06-26
I'd go for the "Use the largest continus free space" option in preference to the "manual" option if it was my first time through. This will keep the existing data intact.

Unless I am mistaken, once installed, Grub will pass control to the Windows boot loader if you choose Windows from Grub.

---

### Post by pooja on 2009-06-26
I quit the installation process. It's a very delicate step to take so I better be sure of what I'm doing.

According to this [wiki]("http://neosmart.net/wiki/display/EBCD/Ubuntu"), (step 2) it's best to choose the 'manual' option. However it doesn't say exactly what to do in the next step.

1) What type of new partition?  Primary or Logical? (Vista and the recovery partition are both Primary partion, I saw this under Vista, when I went to shrink Vista)

2) What's the location of the partion? at the Beginning or at the End?  

3) What file system to choose? ext4 instead of ext3?

4) What mount point to choose? This one is really puzzling me, there are so many options: '/', 'home', 'swap'...

Heavens! I'm new to all this and have been reading guides over guides on this subject for over 20 days! Still I don't know what is the best choice for me! I just want a simple but efficient file system so that when upgrading to future versions of Ubuntu I may not lose any data (of course I would always backup important files...)

---

### Post by izizzle on 2009-06-26
For the filesystem, you would want to choose EXT4 because it is more efficient and faster.

---

### Post by pooja on 2009-06-26
> **izizzle said:**
> For the filesystem, you would want to choose EXT4 because it is more efficient and faster.

Thank you. 
And what about the other issues? How to solve them? 

> 
1) What type of new partition? Primary or Logical? 

2) What's the location of the partion? At the Beginning or at the End?


4) What mount point to choose? This one is really puzzling me, there are so many options: '/', 'home', 'swap'...


Please have a look at the [ wiki]("http://neosmart.net/wiki/display/EBCD/Ubuntu") in question, it may help understand my point of view.

---

### Post by merlinus on 2009-06-26
If you are wanting to have an easy time installing a new version, or re-installing the current one, then having a separate partition for /home is an excellent idea.  The filesystem itself is / (root), which can be around 7G as long as you will not be installing a huge number of applications, and swap need be no more tha 1.5G unless you hibernate.

/home can use all remaining space.

As for the other options, I am uncertain what you are seeing without a screenshot.

As for ext4 vs. ext3, the former shows much promise, but there have been a number of reports of crashes and lost data.  If you are concerned, then use ext3.

---

### Post by Zero++ on 2009-06-26
You'll want a primary partition so it can be booted from. 

You will need to create 2 partitions manually a /swap, should be about the size of your ram and a / (root) partition. 

Select Beginning

as long as you don't touch the NTFS portion there is a pretty good chance  you won't screw things up too bad.

I would recommend making sure your windows boot disk works. If for some reason grub gives you errors you can use the windows install disk to repair your boot loader and boot into windows. 

BACK UP YOUR IMPORTANT FILES!!!

---

### Post by merlinus on 2009-06-26
FWIW, only windows needs to be on a primary partition.  Linux does not care.

In fact, you are better off installing all of the linux partitons to logical ones, since every hdd has a limit of four primaries.  And there is nothing to be gained, or lost, either way, except offering more flexibility in future.

---

### Post by Polaris96 on 2009-06-26
merlinus, I think only a primary partition can have a Dos type boot flag set.  So, grub needs to be on a primary with a boot flag.

for partitions, you can only have a max of 4 primary partitions.  So, you're fine with primary and it's the easiest choice.  

There ARE good reasons for logical partitions.  As I see it, though, you're better off getting your platform off the ground.  You can always mess around with the fancy stuff later.

for filesystem, the truth is your not going to notice a difference as a new user between ext3-4, xfs, or reiser.  knock yourself out.  ext has the most support in ubuntu, these days.  I would even say ext3 because it's the proven technology and you want a robust system to bang on.

I, also, would go with the "largest continuous free space" option, were I in your shoes.  Let the installer make the hard decisions.  Best of luck and remember

THIS IS FUN

---

### Post by Zero++ on 2009-06-26
Because windows expects an OS to be on a Primary, and who the heck would want 4 versions of windows on their computer (ick), I make any OS partition primary just to be safe when duel booting.

---

### Post by pooja on 2009-06-26
ok so what about this config

**swap**: 4 GB (I read somewhere it has to be twice the size of RAM), Logical, beginning

**/(root)**: 5 GB, Logical, Beginnig

**Home**: the remaining space,* Primary*, beginning

What do you think of these partitions?
What's the difference between 'Beginning' and 'End', anyway?

PS: I want Window's boot loader in charge of the booting process, not Grub which will be installed in Ubuntu's partition.

---

### Post by Polaris96 on 2009-06-28
pooja you're getting fancy, again!!

I promise to wax long and hard about multi-partition systems (I have an INSANE amount of partitions)  for now, though, do it this way:

First of all NEVER put more than 2G in swap.  It's a waste of disk space.  If you have 2G RAM, I'd only put 1G in swap (you can use the 'top' command to check swap usage - you will find it's miniscule with that much available RAM) 

Second, unless you plan to put an additional OS on and share the /home directory (very slick btw), you DON'T need a bunch of partitions.

Make a partition, make sure it's bootable (toggle the boot flag on), format it, pick '/' as the mount point and 'ext3' as the fs AND LET BLOODY INSTALLER RUN.

As you get more comfy, start tweaking around with partman, install lvm2 and/or mdadm.  Mess with fstab etc etc etc.  BUT FIRST JUST GET A BASIC SYSTEM UP.

Walk before you fly - it's a lot less painful.

---

### Post by pooja on 2009-06-28
I finished installing Ubuntu to my hard disk.
Gave some 10 gb to '/' (root), 2Gb for swap (**Polaris96**, you're right- it's almost a formality, it doesn't get used) and the remaining space for '/home'. I let Grub install itself in '/' and once the install was completed, I was automatically booted into Vista. Through EasyBCD I added a 'Ubuntu' entry in Vista's MBR pointing to Grub in the '/'(root) partition (for me it was **/dev/sda5**). I then restarted the machine and this time I was before a choice, VIsta or Ubuntu. Choosing Ubuntu led me to Grub that starts Ubuntu 9.04 by default - ie if you don't make a different choice. 

So here I am, up and running! 

Now I need to install some basic packages to see videos, listen to mp3 and customize the desktop. Is there a package called 'ubuntu-restricted' for these purposes? 

I did install Adobe Flash Player 10 for Linux directly from Adobe's webpage (the tar.gz for Linux) and let Packet Manager install the plugin for Mozilla. However when I go to see videos on YouTube, I can see the videoclips and hear the sounds too but have no control over the volume! If I don't use the system's volume control I cannot increase or lower the volume of the videos. If I mute the video's volume using Youtube's volume lever I can still hear the sounds. How's this possible?

---

### Post by Polaris96 on 2009-06-29
excellent job!  BTW the WAY you got Grub to work is very novel and I appreciate your sharing it because I've never heard of anyone doing it that way.

So far as multimedia goes, the "how to" stickies are really very good and you can probably work directly from those.  One last thing I will share is that I haven't personally had very good results with icedtea / open jdk for java plugins.

If you go with the recommended "apt-get install restricted-extras" (check the sticky I might've gotten the meta-package name wrong", You can remove icedtea and install the proper sunjava6-jre over it(also, there are good "how-to"s for that on here, so I won't belabour it.

Definitely install vlc as a media player, too.

Other than that, welcome aboard and happy computing!

---

