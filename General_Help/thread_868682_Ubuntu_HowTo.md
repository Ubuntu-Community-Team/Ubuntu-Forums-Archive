---
title: "Ubuntu HowTo"
date: 2008-07-24
forum: General Help
---

### Post by Daniel Foligie on 2008-07-24
Greetings all

I installed Ubuntu 7.03 on my PC at work but have never managed to get access to the Internet etc (I don't have admin rights).  I'm now considering installing it on my PC at home instead and removing it from my work machine, as I don't use the work installation at all (the System Administrator is also starting to ask some tricky questions as well!).  It is installed with GRUB which allows me to choose between Win XP and Ubuntu at startup.  

Is there a simple HowTo available to show me how to un-install this Ubuntu installation?

Thanks

Daniel

---

### Post by hyper_ch on 2008-07-24
(1) where don't you have admin rights?
(2) 7.04 is already over a year and 2 releases old
(3) how did you install it? On its own partitions?
(4) have you asked for help on how to fix your network problem?

---

### Post by Daniel Foligie on 2008-08-10
greetings hyper_ch

Thanks for the reply. I haven't had a chance to reply sooner.  In answer to the questions...

*(1) where don't you have admin rights?*

Answer: 
On my workstation PC at work.  Within the Windows XP environment, I don't have any admin rights to install software etc.  It's impossible to be granted rights to install software that you want to try out (company policy).  So, I installed Ubuntu 7.04, just to see if I could set up a C compiler.  

Reason: I'm experimenting with microcontrollers and electronics and wanted to try setting up a C compiler that I could use for burning to external SRAM devices via RS232.  At this stage, I didn't have a PC at home.  I now have one and will be installing linux on that, hence there's no need to have Ubuntu on my work machine (the sys admin guy doesn't know I installed it and wouldn't be too happy about it).

*(2) 7.04 is already over a year and 2 releases old*

Answer:
I realise this.  It's just that I had the disks at home and wanted to see if it would install successfully (which it did).
 
*(3) how did you install it? On its own partitions?*

Answer:
The Ubuntu installation partitioned the hard drive automatically.  I choose whether I want to boot up Windows XP or Ubuntu via GRUB at startup. 

*(4) have you asked for help on how to fix your network problem?*

Answer:
I no longer need network access at work using Ubuntu.  As mentioned above, the sys admin guy wouldn't be happy at all that I installed linux in the first place.  Anything other than MS products are frowned upon where I work.

I could always delete whatever's on the Ubuntu partition (using basic MSDOS utilities), but I need to get rid of GRUB as well and I'm not sure how to do this. 

Daniel

---

### Post by ragflan on 2008-08-10
It's pretty easy to do if you have your Windows installation disc. Put it in the drive and reboot your computer. Let windows load up all the files till you come to the screen where it says Install..

Don't press install. Instead there's some options like... I think it's called Repair Computer.. Look for that. Once you click Repair, you'll be given some options. Open the Command Prompt and type:

bootrec.exe /fixmbr

Once done, restart. You'll no longer see the options menu asking which computer you want to boot into. It'll automatically boot into Windows.

Then you can delete or format your Ubuntu partition in Windows.

---

### Post by lukjad on 2008-08-10
I found this link a while ago and was just waiting to use it. Here you go:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

If course, it is my suggestion that you do keep Ubuntu installed since, in my opinion it is better, it is up to you.

---

### Post by dexter.deepak on 2008-08-10
i think what you need at present is just uninstalling ubuntu ..right ?
actually, uninstalling an operating system doesnt make a sense, you should rather say removing ubuntu.
to remove it, you can just format the drive/s containing ubuntu..simple!!
afterwards, boot from a windows cd , and when reach the command prompt stage, issue the command :
fixmbr

---

### Post by Zorael on 2008-08-10
> **Daniel Foligie said:**
> The Ubuntu installation partitioned the hard drive automatically.  I choose whether I want to boot up Windows XP or Ubuntu via GRUB at startup.

...

I could always delete whatever's on the Ubuntu partition (using basic MSDOS utilities), but I need to get rid of GRUB as well and I'm not sure how to do this.
I generally use **testdisk** for this. Package with the same name. I'd boot the system up on a live CD, install testdisk, then start it up with superuser permissions. Pick Intel partition table, and then "write MBR code". Then delete the Ubuntu partition and resize your Windows partition.

```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
**[ MBR Code ]  Write TestDisk MBR code to first sector**
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```

If you can't get a 'net connection set up (or simply aren't allowed to), you could manually download the package from [the repositories](http://packages.ubuntu.com/hardy/testdisk) and sneak it in on your removable medium of choice.

> **Daniel Foligie said:**
> Anything other than MS products are frowned upon where I work.
Yeah.

---

### Post by Mgiacchetti on 2008-08-10
got a windows disk and the admin pass to login to the pc?
you will need both for this 

insert xp disk into cd drive and reset
hit any key and boot to cd (if thats possible)
enter recovery console
login to the xp installation 
type fixmbr
type exit
[source]("http://askbobrankin.com/fix_mbr.html")

----OR----

If you have a floppy drive, (or know how to make a [boot CD]("http://www.pcsupportadvisor.com/bootable_%20CD_page1.htm") instead of a [boot FLOPPY]("http://www.bootdisk.com/bootdisk.htm"))

read [here]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")

---

### Post by Inane_Asylum on 2008-08-10
If you **do** want/need to use Ubuntu at work (or elsewhere) for one reason or another without installing it, [pendrivelinux.com]("http://www.pendrivelinux.com") has a few different options for putting different versions of Ubuntu on a thumb drive with persistant changes so you can carry it wherever you go, saving changes straight to the thumb drive.  No worries about sysadmin finding installations on the work hard drive.

---

### Post by Daniel Foligie on 2008-08-12
Greetings all

Thanks very much for all the feedback.  It's great to have found such an active forum.  

*dexter.deepak said:*
*i think what you need at present is just uninstalling ubuntu ..right ?*

That was the original idea, given that I'm not using it much at work (I'm installing Linux on my new machine at home).  The sys admin guys seem to do after-hours software updates (with automatic power-on of machines on LAN) i.e. the main concern is that if my machine happens to be off and gets powered on remotely, GRUB might cause a problem at startup.  I'll probably try implementing the options suggested by Inane_Asylum and Zorael which may solve this problem. 

*actually, uninstalling an operating system doesnt make a sense, you should rather say removing ubuntu.*

Uninstall, remove, erase, wipe out, destroy, obliterate... you get the picture

*to remove it, you can just format the drive/s containing ubuntu..simple!!*

Read my posts above for why it's not as simple as that (no admin rights or passwords, reconfiguring network settings, setting up net access etc).

[I]boot from a windows cd , and when reach the command prompt stage, issue the command :
fixmbr[/I]

As mentioned by others, this is a possible option for which formating the drive is not a requirement.

Thanks again for the feedback everyone, I think I'm on the right track.

Cheers, 

Daniel

---

