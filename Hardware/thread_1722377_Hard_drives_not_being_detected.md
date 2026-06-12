---
title: "Hard drives not being detected"
date: 2011-04-05
forum: Hardware
---

### Post by SinfulAnimosity on 2011-04-05
I recently installed Ubuntu on my desktop, coming from Windows 7. In my BIOS on the motherboard, I had enabled the settings for a SoftRAID 0 with my two 1TB drives. However, I couldn't find them during the Ubuntu installation, so I installed it to my 500GB drive.

I took off the SoftRAID, and in the BIOS it's detecting that they're two separate hard drives again. However, I still can't see them in Ubuntu.

Also, if I ever do get to see them, will I be able to combine my three hard drives (1x 500GB 2x1TB) into a 2.5TB RAID? Or is that not how it works?

---

### Post by dabl on 2011-04-05
Ubuntu's guidance:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Another how-to:

[http://kubuntuforums.net/forums/index.php?topic=3114477.0](http://kubuntuforums.net/forums/index.php?topic=3114477.0)

If you actually _need_ a RAID setup, you would be far better off with hardware RAID, using something like this:

[http://www.3ware.com/products/serial_ata.asp](http://www.3ware.com/products/serial_ata.asp)

Hope this helps.

---

### Post by PCNetSpec on 2011-04-05
Raid0 striping is beneficial in Windows for 2 reasons:

a) Speed.

b) to assign all available space to the C: drive.

Though (a) will still apply to Linux, (b) is much less important because Linux doesn't use drive lettering.

In windows the root of the file system and the root of the drive are the same thing... not so in Linux.

Drives/partitions can be hung off the file system (mounted) wherever you want... in other words, you can mount a drive/partition as a directory anywhere you like in relation to the root of the file system.
(at first a strange concept, but once understood, a much more flexible system than the "Windows way")

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

but if for some reason you still want to stripe your volumes... take a look at LVM.

[https://help.ubuntu.com/community/StripedVolumeHowTo](https://help.ubuntu.com/community/StripedVolumeHowTo)
and
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by PCNetSpec on 2011-04-05
Sorry, multiple posting... removed.

---

### Post by SinfulAnimosity on 2011-04-05
Thanks Dabl! Definitely did some reading there, learned quite a bit.

PC, correct me if I'm wrong, are you saying I can mount my two 1TB's and they'll automatically be 'added' to my 500GB? Sorry, kind of a newb with RAIDs.

Also, any clues on how to even see my hard drives. My board is an Asus P6X58D-E if that helps come up with a solution.

---

### Post by PCNetSpec on 2011-04-05
Yes, and no... sorry not too helpful :)

What I mean is that in Windows they would be given different drive letters C: D: E: etc.

In Linux partitions are mounted as directories "inside" the file system.

so you could have the 500GB drive as / (the root of the file system) and a 1TB drive as your /opt directory, and another 1TB drive as say /home or /home/<username>/Videos directory.

Linux's unified file system doesn't see drives/partitions as separate entities... it sees them as directories which can be mounted (attached) to the file system wherever YOU want.

So they all become "part of" the file system, rather than them all having their "own" file system... if you see what I mean ?

Think of it like this... in Windows terms, it could be like having one of your 1TB drives as say "Program Files" and another as "My Documents", or "My Videos"... the system sees them as just directories in one big file system... not separate drives/partitions.

The choice of partitioning scheme, and where to mount them is yours.

For Ubuntu to recognise the drives, you will either need to turn OFF RAID, use the **nodmraid** kernel boot parameter, or use the Alternate install CD.

[http://linuxforums.org.uk/ubuntu/linux-novice/msg41922/#msg41922](http://linuxforums.org.uk/ubuntu/linux-novice/msg41922/#msg41922)
or
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
and
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
or
[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

---

### Post by SinfulAnimosity on 2011-04-05
Thanks so much! Guess I'll have to reinstall using the Alternate one. One more question: Should I choose the Intelx86 or the 64-bit?

I have an i7-930, and 12GB of RAM. So I naturally assumed I should be using 64-bit. But am I wrong? The description for the 64bit says:

*Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.*

Will that x86 still allow me to take full advantage of my system resources?

---

### Post by PCNetSpec on 2011-04-06
You'll want the 64bit version...

32bit will only allow you to access 4GB of your RAM unless you use PAE.

64bit, despite its name (AMD64) is NOT just for AMD CPU's... I guess at some point someone will update that description to include the Intel "i" series processors.

---

### Post by Grenage on 2011-04-06
> **PCNetSpec said:**
> You'll want the 64bit version...

32bit will only allow you to access 4GB of your RAM unless you use PAE.

64bit, despite its name (AMD64) is NOT just for AMD CPU's... I guess at some point someone will update that description to include the Intel "i" series processors.

Not likely, it's AMD's x64 spec. ;)

---

### Post by PCNetSpec on 2011-04-06
Erm... explain the inclusion of "EM64T Xeon, Core 2" in the description then... :)

AMD64 and x86_64 are identical, so all 64bit x86 architecture CPU's will work with Ubuntu (AMD64) 64bit, that is to say all the AMD or Intel 64bit CPU's **EXCEPT** the **Itanium** CPU's from Intel, which fall into the IA64 architecture.... 

So all Intel EM64T Pentium's and Celeron's, Xeon's, Core's, Core 2's, i3's, i5's and i7's are AMD/x86_64.

So why AMD64 ? .. I guess it's because AMD created and added the 64bit extensions to the 32bit x86 architecture before Intel did.

---

### Post by Grenage on 2011-04-06
> **PCNetSpec said:**
> Erm... explain the inclusion of "EM64T Xeon, Core 2" in the description then... :)

Ah, they have that on there now. :)  I remember when there was much bitching over the use of the name AMD64, and that alone.

---

### Post by PCNetSpec on 2011-04-06
It can be a bit confusing, but I suppose if anyone doesn't understand the term, and can't be bothered to ask, they'd probably be better off with 32bit anyway.

The Linux community just wouldn't be the same without the bitchin .. Oops sorry, discussion ;)

---

### Post by dabl on 2011-04-06
> **SinfulAnimosity said:**
>  My board is an Asus P6X58D-E if that helps come up with a solution.

Yep, I have that system board too.  I did not attempt to use the onboard fakeraid, so I'm not sure whether Ubuntu will support that or not.  Probably if you search this forum on the controller model (is it a Marvell?), you can learn more.

What I did was connect two WD1002FAEX drives to the SATA 6GiB/s connectors, and installed a multi-drive btrfs filesystem on them.  The btrfs default configuration is for data to be striped, and metadata to be mirrored.  So I've got about 450GB of my user data on that filesystem -- it's been running fine since late November. My OS is on a SSD -- an OCZ Revodrive PCI SSD.  It's fast.

If you want more details on how I configured my rig, just ask.  :)

p.s. you want the "amd64" architecture.

---

### Post by SinfulAnimosity on 2011-04-06
> **dabl said:**
> Yep, I have that system board too.  I did not attempt to use the onboard fakeraid, so I'm not sure whether Ubuntu will support that or not.  Probably if you search this forum on the controller model (is it a Marvell?), you can learn more.

What I did was connect two WD1002FAEX drives to the SATA 6GiB/s connectors, and installed a multi-drive btrfs filesystem on them.  The btrfs default configuration is for data to be striped, and metadata to be mirrored.  So I've got about 450GB of my user data on that filesystem -- it's been running fine since late November. My OS is on a SSD -- an OCZ Revodrive PCI SSD.  It's fast.

If you want more details on how I configured my rig, just ask.  :)

p.s. you want the "amd64" architecture.

Excellent :) Yes, I have my two WD drives connected to the 6GiB/s as well. However, I booted up with the Alternate Installer, and they were still not detected. So I have no clue what to do now.

I've considered removing one of my disk drives (BlueRay/DVD burners) to make room for them on the normal connectors. But I am definitely interested in that filesystem you have. That sounds exactly how I want it.

---

### Post by PCNetSpec on 2011-04-06
Hmmm... If you are attempting to connect them to the  Marvell 9128 PCIe SATA 6Gb/s controller, it may be related to this known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658521)

It appears the  Marvell 9128 PCIe SATA 6Gb/s controller is supported in kernels >= 2.6.37-8.20, so you might want to give the 11.04 Natty (beta1) a go, as this uses kernel 2.6.38-7.39

[https://launchpad.net/ubuntu/+source/linux/2.6.37-8.20](https://launchpad.net/ubuntu/+source/linux/2.6.37-8.20)

[http://www.ubuntu.com/testing/natty/beta#Download%20Beta](http://www.ubuntu.com/testing/natty/beta#Download%20Beta)

Or wait till the 28th for the 11.04 final.

This may be why **dabl** isn't having issues, his signature *seems* to suggest he's using aptosid which if it's version 2011-01 uses 2.6.37, and Kubuntu **11.04** ?

FYI, Ubuntu 10.10 (Maverick) uses kernel 2.6.35

---

### Post by dabl on 2011-04-06
> **PCNetSpec said:**
> 

This may be why **dabl** isn't having issues, his signature *seems* to suggest he's using aptosid which if it's version 2011-01 uses 2.6.37, and Kubuntu **11.04** ?



Yes, that is true.  However, (k)ubuntu 10.10 Alternate Install CD will support installing a btrfs filesystem.

So, if you wish, use "dd" to nuke the mbr of both hard drives, connect them to the SATA 6GiB/s ports, and then boot the 10.10 or 11.04 CD and install a btrfs filesystem on both of them.

When connected to the Marvell controller, the two drives will not appear in the main AMI BIOS, they will only appear in the Marvell BIOS.

Then use whatever SSD or fast SATA hard drive that you have for the installed OS, and use the btrfs multi-drive filesystem for your data.

[https://btrfs.wiki.kernel.org/index.php/Getting_started](https://btrfs.wiki.kernel.org/index.php/Getting_started)

[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

[https://btrfs.wiki.kernel.org/index.php/Gotchas](https://btrfs.wiki.kernel.org/index.php/Gotchas)

---

### Post by SinfulAnimosity on 2011-04-07
Love you two for this! Thanks a ton! I'll definitely look into using kubuntu. Thanks a ton, learned quite a bit from you two!

Also, if I use the natty beta, will that decrease any functionality that I had in 10.10? As in, will applications like WINE still function properly? Or will I be all set? I like the GNOME GUI, and have gotten quite used to it, so I'm a bit hesitant about trying out Kubuntu xD But if it's my only option, I'll use it :p

---

### Post by PCNetSpec on 2011-04-07
You don't have to use **K**ubuntu 11.04, you can get **U**buntu 11.04, and you don't HAVE to use Unity either, you can select the standard GNOME desktop if you wish.

[http://askubuntu.com/questions/28050/how-do-i-use-use-the-classic-gnome-desktop](http://askubuntu.com/questions/28050/how-do-i-use-use-the-classic-gnome-desktop)

also see here, if it's still needed:
[https://bugs.launchpad.net/ubuntu/+bug/734373](https://bugs.launchpad.net/ubuntu/+bug/734373)
(though I *think* the menu's and global menu issues have been fixed if you get the updates)

Or stick with 10.10, and do it **dabl**'s way.

---

### Post by SinfulAnimosity on 2011-04-07
Heh, I already have everything deleted from messing with my hard drive and BIOS settings, so might as well give Natty a shot :p

---

### Post by SinfulAnimosity on 2011-04-07
zOMG it lives! It detected my Marvell RAID setup with no problem. Finally dual-booting Win7 and Ubuntu <3. Thank you all soooooo much!

---

### Post by dabl on 2011-04-07
Good job! Natty is still in development, so you'll need to run ```
sudo apt-get update && dist-upgrade
``` daily, or at least every other day, until they finish with the new packages. But I would not expect your hard drive setup to be affected.  :popcorn:

---

### Post by PCNetSpec on 2011-04-07
As **dabl** say's remember you are running a beta, so keep up with the updates, and don't expect it to be as stable and polished as 10.10 yet, but it will get there :)

---

### Post by SinfulAnimosity on 2011-04-08
Yup, got it all installed fine :)

I'll be sure to run those commands daily! Or would it be good enough to just run the updater?

Also, believe it or not, my video settings are **better** with 11.04 than with 10.10, and my intermittent internet connection seems to have gone away. 11.04 isn't even released yet and I'm loving it!

You two are seriously my heroes. Wish there was some way I could rep you guys up!

And.... another problem. GRUB seems to have disappeared. It just boots into Windows now. Is there a way I can make GRUB go back to being the bootloader? I've got Natty installed to my RAID, and Windows installed to my 500GB. So it's not on the same drive if that makes a difference.

---

### Post by PCNetSpec on 2011-04-08
Ooops, did you install Windows AFTER Ubuntu?
(It's usually easier to install Linux AFTER Windows, so GRUB overwrites the Windows bootloader, and not the other way round)

If so, GRUB has probably been overwritten by the Windows bootloader, you'll need to reinstall GRUB.

Instructions can be found here:
[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD)

But before you rush off and do that... explain how you set the system up, ie. did you install Ubuntu, THEN start adding drives ?

Was Ubuntu installed before Windows ?

did you change any drive settings in the BIOS between installations?

What I'm getting at is... did GRUB get overwritten, or have you now got 2 bootloaders on different drives, but the Windows one has priority in the BIOS boot order.

---

### Post by SinfulAnimosity on 2011-04-08
Oh boy... long story lol.

I originally had my Storage Config set as AHCI, instead of IDE, which I used to have on my old setup.

I went to install Windows first, and towards the end, I got a Windows Setup couldn't configure Windows to run on this hardware. Something like that.

So I tried again, and it showed me I had Windows installed. So I proceeded to install Ubuntu onto my RAID'd drives, and installed GRUB to my 500GB hard drive, where the Windows install was located. It wasn't until I went into my BIOS that I realized I had it set as AHCI instead of IDE. So I redid the installation of Windows.

So it basically went like: Failed Windows Install -> Ubuntu -> Successful Windows Install

---

### Post by PCNetSpec on 2011-04-08
OK, your options are to reinstall GRUB from the LiveCD (link in last post), or to start again from scratch, but this time install Windows first... up to you ;)

---

