---
title: "Ubuntu server 9.10 gets stuck on grub install on a raid volume"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by hfeiges on 2009-11-12
Hello all,
 
My goal is to get a VMWare server up and running and inexpensively as possible, while still maintaining some degree of hardware redundancy to protect against a hard drive failure..
 
I chose ubuntu server (64 bit) because I beleive I can install a working linux host with the minimal amount of overhead, with just enough of an OS to get VMWare server up and running, and then I will be able to run a mixture of Linux and Windows guest OSs on-top of VMWare..
 
The good news is, I have already successfully done this on a single (non raid) hard drive with Ubuntu server 9.10 and VMware 2.0.2... This took some doing (I had to use another installation script for VMware), but in the end I got it to work, so at least I know I am barking up the right tree...
 
So now, I would to take the VMWare installation one step further, and use the SATA RAID functionality built in on my motherboard to provide some measure of protection against a hard drive failure.. So I obtained a second hard drive identical to the one I had already.. For obvious reasons, I would rather use the built in RAID functionality to host the virtual machines over the software based RAID functionality built in to the OS..
 
I know that the Ubuntu installation process does recognize the RAID volumes defined in my RAID bios utility (earlier, when I tried to install VMWare ESXi on this configuration, it wouldn't even recognize the defined RAID volumes and just saw the two physical hard drives, so I decided to dump ESXi and just go with VMWare server on Ubuntu..).. I have a lot of flexibility when defining the RAID volumes, and I can even mix different RAID types (raid-0, raid-1, JBOD, etc..) on the same physical hard drive pair with this motherboard...
 
Anyhow, the installation seems to go well, but then it falters when it comes to installing the boot loader...
 
What happens is it brings up the Ubuntu installer main menu (I don't remember that menu showing up at all when I was installing on a single disk), and the selection is set to the 'Install the GRUB boot loader on a hard disk' menu item... So now, if I hit enter, to supposedly install the boot loader, it tries to install it (I can see the 'installing the 'grub2' package' message flash), but then it comes right back to the same install GRUB menu item in the Ubuntu installer main menu (I don't see any error message)... I can hit 'enter' on this menu many times, and it just does the same thing and comes right back to that menu option...
 
The next option in the menu is to install the LILO boot loader, but that doesn't work either (I get error messages when trying to install LILO, no matter which option I pick)...
 
So, finally, the next option is to install without a boot loader, and I get this message:
 
'No boot loader has been installed, eihter becase you chose not to or because your specific architecture doesn't support a boot loader yet.
You will need to boot manually with the /vmlinuz kernel on partition /dev/mapper/pdc_xyz and root=/dev/mapper/pdc_xyz passed as a kernel argument.'
 
... where xyz changes depending on how I configure my RAID volumes and hard disk partitions... If I choose this option it finishes up the install okay, but then the installation will not boot...
 
Anyhow, this is where I get stuck (I have no idea how to boot manually passing arguments to a kernel), and I am not sure what to do... Ive tried several configurations of RAID volumes and linux partitions, but no matter what I do, the same thing happens when it tries to install the boot loader... I don't see why it should matter if the hard disk is a single disk, or if its a RAID array, since this is defined at the hardware level and the mirrored pair should just look like a single drive to an operating system...
 
I have installed some other linux distros (like Fedora) on this configuration and it boots up just fine, so I know that its possible to use this RAID configuration with a linux host... I would like to stick with Ubuntu server if possible, because its so light-weight and because I went through the trouble to figure out how to get VMWare working on it and all.... All I would like to do extra is get some hardware based RAID redundancy so if a hard drive fails I won't loose all the virtual machines on this box...
 
Is this possible?? Is there a particular configuration that would work better than others?? Is it possible to apply a boot loader afterwards if the initial installation cannot install the boot loader?? Am I completely off-base here trying to use RAID at all??
 
If you need more information to help me with this, please just ask and I will provide it...
 
Thank you (anyone) in advance..

---

### Post by hfeiges on 2009-11-12
Yes, I have seen this post:
 
[http://www.ericforyan.com/index.php?node=21](http://www.ericforyan.com/index.php?node=21)
 
 
And yes, I have set up the BIOS configuration SATA type to RAID (in fact, I cannot even bring up the option ROM to define the RAID volumes in the first place, unless this SATA type is set)...

---

### Post by hfeiges on 2009-11-12
One other thing,
 
I see a lot of posts in here regarding ubuntu upgrades and dual-boots rendering an existing raid array non-bootable after the upgrade...  This is not the case here...
 
For this install, I am using ubuntu 9.10 on a clean/fresh system with a raid (mirrored) pair of hard drives...   And for the most part the install works, it just falls down when it tries to install the bootloader...   So hopefully this sould be a simpler case (and I don't mind re-partitioning the drives, etc, since I have no data to loose)...

---

### Post by mellis95 on 2009-11-24
Is there a solution to this? I have the same issue. Fails on GRUB install with SATA RAID I have tired the workaround suggested here:
>               **Re: Ubuntu server 9.10 gets stuck on grub install on a raid volume**
         Yes, I have seen this post:
 
[http://www.ericforyan.com/index.php?node=21](http://www.ericforyan.com/index.php?node=21)
 
 
And yes, I have set up the BIOS configuration SATA type to RAID (in fact, I cannot even bring up the option ROM to define the RAID volumes in the first place, unless this SATA type is set)... No luck.

Any help is appreciated.

Thanks,
Matt

---

### Post by darkod on 2009-11-24
Dumb question (to both of you).

Are you sure the ubuntu installer is seeing the raid pair as raid? I have never used the server version and I am asking because I know in the desktop version it can't see raid unless you use alternate install cd.

On the other hand, I would expect the server version to support raid "out of the box". :) Just an idea to check.

And out of curiocity, if you try with the alternate install cd does it do the same?

---

### Post by mellis95 on 2009-11-25
> Dumb question (to both of you).

Are you sure the ubuntu installer is seeing the raid pair as raid? I have never used the server version and I am asking because I know in the desktop version it can't see raid unless you use alternate install cd.

On the other hand, I would expect the server version to support raid "out of the box". :smile: Just an idea to check.

And out of curiocity, if you try with the alternate install cd does it do the same?     It does seem to see the raid pair correctly.  I am going to try the alternate CD when I get a chance. I actually didn't realize that there was such a thing until this problem. In the past, I have never had an issue installing Ubuntu Desktop or Server, but I have normally been installing on older hardware.

Thanks,

Matt

---

### Post by darkod on 2009-11-25
Just a reminder, the alternate install is text based installer, not GUI. But only during install. And I think you have to select gnome desktop to be installed unless you want to end up with text based system.

Anyway, since you sound like you've done quite a lot installations, server also, you can handle it. :)

---

### Post by chrisinspace on 2010-01-06
Any luck with this issue?  I'm having the exact same problem as described by the original poster.  I'd appreciate any help.  I'm stuck.

---

### Post by lapichiflati on 2010-01-26
I had this issue too.  Instead of getting buff on new stuff I just installed server 9.04, and then did a 

```
sudo do-release-upgrade
```

since 9.04 uses GRUB legacy and the distribution upgrade doesn't upgrade the bootloader.  Now I have 9.10 with GRUB legacy and a working RAID 1.
Not pretty, but effective and mostly unattended.

---

### Post by chrisinspace on 2010-01-27
> **lapichiflati said:**
> I had this issue too.  Instead of getting buff on new stuff I just installed server 9.04...

Haha..."buff on new stuff"...:D

I took the same approach except I went with Debian (Lenny).  It's working great now and I'm getting some experience with Ubuntu's big brother.

---

### Post by TomyVk on 2010-01-27
I had the same problems with my desktop version of ubuntu, grub2 just wont install.
The best way atm is to install 9.04 and just to upgrade....

---

### Post by chrisinspace on 2010-01-27
This was for a server.  As I said before, I went with Debian instead, but I'm still using Ubuntu on a couple of other machines.  

I'm not sure what the root issue was, but I hope they get it straightened out before Lucid is released since that's going to be LTS.

---

### Post by Shane GWIT on 2010-01-28
I decided to try out Ubuntu Server from Debian 5 and it won't get past GRUB.  Nothing afterward.  I am going to try to install the previous version and upgrade as per another users suggestion.

Running with AMD 780g motherboard and an adaptec 5805 for storage.

---

### Post by Elgaard on 2010-04-03
> **lapichiflati said:**
> I had this issue too.  Instead of getting buff on new stuff I just installed server 9.04, and then did a 

```
sudo do-release-upgrade
```since 9.04 uses GRUB legacy and the distribution upgrade doesn't upgrade the bootloader.  Now I have 9.10 with GRUB legacy and a working RAID 1.
Not pretty, but effective and mostly unattended.

This worked perfect for me, i was having exactly the same problem as OP when trying to install 9.10 on my server (Intel Server Board with onboard RAID, RAID1 array). Thanks lapichiflati!

---

