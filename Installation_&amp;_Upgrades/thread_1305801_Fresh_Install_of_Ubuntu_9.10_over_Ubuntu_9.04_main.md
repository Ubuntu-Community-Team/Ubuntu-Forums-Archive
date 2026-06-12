---
title: "Fresh Install of Ubuntu 9.10 over Ubuntu 9.04 maintaining dual boot with Windows XP"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ceruleanchalice on 2009-10-30
All right, here's the problem and I hope someone out there can help me:

I originally ran Windows XP natively on my laptop. I then decided to install Ubuntu 9.04 in a dual boot environment. I have been using Ubuntu 9.04 for a while now and when 9.10 was released yesterday, selected the upgrade version option in Ubuntu 9.04 and it went about downloading around 900 mb worth of files. When it was about to install, I made sure there were no running applications and let it sit. It installed maybe 10% and then gave me an error and said it would now try and go back on it's changes, however the OS might be in an unusable state. Everything closed automatically then. I tried to load Firefox and had no luck.

Taking a deep breath, I restarted my system and found that Windows XP was still loading from Grub so my computer was not entirely useless at this point.

I then thought it might be an idea to download the .iso disc image of Ubuntu 9.10 and try installing from there, by booting up through it and doing a fresh install OVER the existing Ubuntu 9.04 partition (Ext3). I was going to format that existing partition to Ext4 and simply install Ubuntu 9.10 over Ubuntu 9.04. Unfortunately when the partitioner loaded, I had 2 choices. To install Ubuntu 9.10 by taking space from my Windows XP partition and this leaving me now with 3 operating systems, Windows XP, Ubuntu 9.04 and Ubuntu 9.10 OR manually editing the partitions.

I tried to do that then, loaded up the advanced editor and figured I pre-set the options to format and change the format of the Ubuntu partition from Ext3 to Ext4 and made sure no other changes were to be made, thus keeping the same SWAP partition from Ubuntu 9.04 as well. On clicking forward, it said something about no root partition being selected. I thought then I best come to the forum to see if I can get any help here.

What I want to basically end up with is my MS Windows XP installation in dual boot with Ubuntu 9.10. I do not want to have Ubuntu 9.04 as well. I want to install Ubuntu 9.10 on the partition where Ubuntu 9.04 is and also format it to the relatively new Ext4 format.

It should be easy enough to do, I've tried to solve this myself and am looking for some advice on how I should go about it.

Thanks for the long read lol, I just thought it might help to be thorough. :p

---

### Post by space-litter on 2009-10-30
I do not share the same problems as the OP, but I am interested in this thread because I want to do a fresh install in order to obtain the new GRUB as well as the ext4 filing. I have Vista rather than XP, but I am also currently running Jaunty. I am looking to do exactly what the OP is requesting.

EDIT: I have not tried the installation yet as the .iso is still downloading. I am just looking to head off any potential snags before I commit to the CD upgrade. I am prepared to lose all of my Jaunty settings in the process; this is irrelevant to me.

---

### Post by ceruleanchalice on 2009-10-30
Well let's hope someone has an answer soon...I'm sitting here in an Ubuntu 9.10 Live CD environment lol!

---

### Post by space-litter on 2009-10-30
ceru, if someone gives you an answer (or link to one) please copy/paste it to this thread as i will then receive an email with your reply. I do not wish to spam the boards with a question I am certain they are being hammered with.

---

### Post by ceruleanchalice on 2009-10-30
sure thing space-litter...evidently there are quite a few people interested in the answer to this particular problem so I'm glad I'm not the only one! patiently waiting though for a reply :)

---

### Post by ceruleanchalice on 2009-10-30
Addendum:

I read this from the following link: [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

However I am not 100% certain whether this will retain the dual boot into Windows option or not. Anyone know about this?
**Clean Install Upgrade (not recommended)**

 If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory. 
**Back-up any important data before following this procedure as data loss is possible, and very well may be likely.** 

[LIST=1]
[*]Obtain an installation CD for the release of Ubuntu you wish to install, and boot from it. 
[*]Start the installation process. When you reach the *Prepare disk space* stage of installation, choose the *Manual* option and press **Forward**. 
[*]Identify your current '/' (root) partition. Select '/' as the mount point and ensure that *Format* is ticked. **You will lose all data on this partition and the new version of Ubuntu will be installed there instead.** 
[*]Identify your swap partition and set its mount point as 'swap'. 
[*]Identify your /home partition. Set its mount point as '/home' and make sure that *Format* is **not** ticked. 
[*]Continue installation as normal until you reach the *Who are you?* stage, enter a username and password which *exactly match* your current username and password. 
[*]Complete the installation as normal. 
[/LIST]
Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

---

### Post by Mariano Oliveto on 2009-10-30
Hi Guys,

I think I might know what went wrong with the partitioning attempt that ceruleanchalice made:

> On clicking forward, it said something about no root partition being selected.

When you selected the 9.04 root partition (the one where the OS files are installed) you must set a "mount point". This mount point will somehow define what will be the partition's function. E.g.:

"/" would be the root partition
"/home" would be the home partition
"swap" would be the swap partition
And so on. 

If you retry installing Karmic (9.10) see if this was your problem.

But please bare in mind that I'm no expert. Your best chances are to first read something about manual partitioning first and then try it.

Hope it helped ;)

---

### Post by ceruleanchalice on 2009-10-30
Thanks Mariano, will give that a shot. If it works, will post so here. If not, will still post so. The screw up I foresee is me losing Windows from the GRUB list when the new one loads, but I believe there are plenty ways to rectify that so keeping my fingers crossed and giving this a shot!

---

### Post by owenll on 2009-10-30
Partyboi2 gave me this advice when I wanted to do a fresh install of 9.04 over 8.04 in dual boot, that worked for me, so I assume it will work in this scenario.
>  Re: install over ubuntu
Hi, if you are wanting to install 9.04 and format your 8.04 install when you are at the manually partitioning screen choose "/dev/sda5" and select "edit partition" then set the mount point to / and select the option to use the partition as ext3 , then tick the box next to format (make sure you have backed up all your important data as this will wipe the partition clean) then proceed with the install.

[http://ubuntuforums.org/showthread.php?t=1299691](http://ubuntuforums.org/showthread.php?t=1299691)

---

### Post by Shazaam on 2009-10-30
If you chose to follow Mariano Oliveto's advice you will be making 3 partitions to take the place of 9.04...
1. /=root
2. /home (separate partition)
3. swap (probably inside an extended partition)
Good, sound advice if you want a separate /home.
Depending on how many previous PRIMARY partitions are already on your drive you may bump into the 4 PRIMARY partition limit. If you fall into this category you have a few choices...
1. Just set / as root in the dialog box. This will install everything (except swap) on that partition (root, home, etc).
2. Manually make an EXTENDED partition (using the Partition Editor on the livecd) in the space previously used by 9.04 to hold your new 9.10 install. This will add LOGICAL partitions inside of it.
3. Add another drive/drives (costs money unless you have one laying around).

---

### Post by mag1 on 2009-10-30
I too need help with this, i've always found the partion bit confusing and could do with a visual guide of the menu's as i've read the forum thread on it and not sure if i will do it right.

Im getting the ubuntu remix for my netbook which already has 9.04 and xp on it, it doesn't have a seperate home partition and im not sure i want one as it must leave loads of config files behind from each install, i have a seperate ntfs partition from windows i can store personal files on.

Is there a video or a good guide with images?

---

### Post by ceruleanchalice on 2009-10-30
Guys, I went ahead booted with the installation CD. When I got to the partitioner, I selected manual partition (advanced) and then I could see Windows on /dev/sda1 and Ubuntu 9.04 on /dev/sda5 and swap on /dev/sda6. I then selected the /dev/sda5 partition, the one with Ubuntu 9.04 in the Ext3 format and changed the type to Ext4, it automatically selected the format partition option and in the Root space I entered '/'. Went ahead with the install as I would have done a clean install and am now in Ubuntu 9.10 and it's working fine! Oh yeah and Windows is there in my Grub options as well. My only concern was I saw the version of Grub installed is a beta. Is that really safe on part of Canonical to release Ubuntu 9.10 with a beta version of something as critical as Grub?

I don't know, just seemed a bit sketchy to me.

I hope this thread helps you guys out. Any questions, feel free to ping me.

Cheers

CC

---

### Post by mag1 on 2009-10-30
Ah thats good, it does actually sound simple enough after looking at the advice given from Partyboi2 in the other thread, i take it you don't have to worry about anything else except changing that bit then?

I think i will stick to ext3 though as i've seen concerns about ext4 being unstable and possibly causing corruption to large files, is there much of a performance boost over ext3 and is it worth using considering the potential problems?

---

### Post by stinger30au on 2009-10-30
i just finished upgrading my laptop that runs vista 64 and dual boot to ubuntu 9.10 beta

now running 9.10 final

download the ubuntu 9.10 iso and burn to cd/dvd

startup pc and tell it you want to run 9.10 with no changes to pc


when it starts up click on system , administration, gparted

on my pc there was 2 linux partitions in particular i had to delete

sda5 and sda6

the sda5 was the main partiton for 9.10 and sda6 was about 900 meg and was the swap


once these 2 are deleted you will see a grey section of hdd where these 2 partitions were

now run the install icon on the desktop

when it shows you the hard drive partitons tell ubuntu to install to the largest free space on the hdd and let it go

it will install and boot up and you can pick ubuntu or windows

piece of cake

hope this helps

---

### Post by TBerk on 2009-10-30
> **ceruleanchalice said:**
> Addendum:

I read this from the following link: [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

However I am not 100% certain whether this will retain the dual boot into Windows option or not. Anyone know about this?
**Clean Install Upgrade (not recommended)**

 If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory. 
**Back-up any important data before following this procedure as data loss is possible, and very well may be likely.** 

[LIST=1]
[*]Obtain an installation CD for the release of Ubuntu you wish to install, and boot from it. 
[*]Start the installation process. When you reach the *Prepare disk space* stage of installation, choose the *Manual* option and press **Forward**. 
[*]Identify your current '/' (root) partition. Select '/' as the mount point and ensure that *Format* is ticked. **You will lose all data on this partition and the new version of Ubuntu will be installed there instead.** 
[*]Identify your swap partition and set its mount point as 'swap'. 
[*]Identify your /home partition. Set its mount point as '/home' and make sure that *Format* is **not** ticked. 
[*]Continue installation as normal until you reach the *Who are you?* stage, enter a username and password which *exactly match* your current username and password. 
[*]Complete the installation as normal. 
[/LIST]
Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

[[IMG]http://i473.photobucket.com/albums/rr96/DrFrankenBerk/th_Screenshot.png[/IMG]](http://s473.photobucket.com/albums/rr96/DrFrankenBerk/?action=view&current=Screenshot.png)

I would suggest you take this opportunity to create separate partitions for your '/' (or Linux OS partition) and your 'HOME' partition. 

As you can see from the picture I have a preexisting WinXP partition (/DEV/SDA1) and it is formatted to NTFS. 

I also have a 2Gig LINUX-SWAP, shown in red, and two others; /dev/SDA2 which is mountpoint '/' and /dev/SDA4 which mounts to '/HOME' .

During my own update from 9.04 to 9.10rc I tried the 'upgrade in place' options I found by applying APT-GET and both liveCD/AlternateCD versions but all I accomplished was a "partial upgrade" that crashed my install.

Thankfully I had /HOME on a seperate partition so I finally bit the bullet, wiped /dev/SDA2 and (re)installed 9.10 from scratch.

During this install it defaults to using the whole drive (which would have wiped XP out all together) so I selected Manual Partition.

I selected where the **Mount Points** would be and applied changes and let the install fly and here I am, some days later, all patched and running smoothly, Data and saved files all snug and warm and non-deleted.

btw, during the endgame the install will run GRUB in discovery mode and it'll catch the Windows install and make all new entries for it as well as the Ubuntu OS on the startup menu

hth,
berk

---

### Post by ceruleanchalice on 2009-10-30
Evidently the problem has been solved with great advice from seasoned veterans. I'm marking this thread as solved and hope others who are faced with the same problem can find it easily and follow through with the advice given. For the record, I checked my Windows XP installation, booted perfectly (albeit so much slower than Ubuntu 9.10 and my prime reason for switching) and am right now in Ubuntu 9.10 and loving it. I even got my dual monitors to work on a crappy ATI card. However in doing so, lost all the nifty effects that come with Ubuntu. I read somewhere that I should install the ATI Xorg Drivers and found them in the Software Centre, but have also read how they could really screw things up. My primary worry is I got the dual monitor thing working now, if I install those drivers, I might lose it and I am not sure if I can reverse that installation perfectly to get things back into working order lol!

Cheers guys!

---

### Post by space-litter on 2009-10-30
> **TBerk said:**
> [[IMG]http://i473.photobucket.com/albums/rr96/DrFrankenBerk/th_Screenshot.png[/IMG]](http://s473.photobucket.com/albums/rr96/DrFrankenBerk/?action=view&current=Screenshot.png)

I would suggest you take this opportunity to create separate partitions for your '/' (or Linux OS partition) and your 'HOME' partition. 

As you can see from the picture I have a preexisting WinXP partition (/DEV/SDA1) and it is formatted to NTFS. 

I also have a 2Gig LINUX-SWAP, shown in red, and two others; /dev/SDA2 which is mountpoint '/' and /dev/SDA4 which mounts to '/HOME' .

During my own update from 9.04 to 9.10rc I tried the 'upgrade in place' options I found by applying APT-GET and both liveCD/AlternateCD versions but all I accomplished was a "partial upgrade" that crashed my install.

Thankfully I had /HOME on a seperate partition so I finally bit the bullet, wiped /dev/SDA2 and (re)installed 9.10 from scratch.

During this install it defaults to using the whole drive (which would have wiped XP out all together) so I selected Manual Partition.

I selected where the **Mount Points** would be and applied changes and let the install fly and here I am, some days later, all patched and running smoothly, Data and saved files all snug and warm and non-deleted.

btw, during the endgame the install will run GRUB in discovery mode and it'll catch the Windows install and make all new entries for it as well as the Ubuntu OS on the startup menu

hth,
berk

I know this thread is solved, but your advice seems brilliant to me to keep / and /home separate. My question is, I noticed you have a good deal of unused space on your / partition. Is it necessary to give / 12 gigs or looking back would you have used less? If my thinking is correct the only space it needs is what is required to put down the OS, but I feel like I may be missing something.

---

