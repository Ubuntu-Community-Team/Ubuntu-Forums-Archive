---
title: "already installed 32, need steps on installing windows and then 64 now."
date: 2008-08-01
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-01
Alright, I've already installed 32 just to get things going, but now I have xp pro coming to me hopefully tomorrow.

I have one hard drive (80g) that I am going to partition into 2 sections for windows and ubuntu.

Now I know I've read that putting windows on first and then ubuntu is the smoothest way for operation.

This time around I am also going to install 64 and try it out.

1) So what steps do I take to put windows on and then 64?

2) Do I have to wipe out 32 first?

3) Or just install windows over it?

4) then once I have windows installed... I partition the disk then correct?

5) What are the actual steps for doing this?

---

### Post by coffeecat on 2008-08-01
I'm not 100% sure exactly what you mean. Do you mean that at the moment you have just Ubuntu 32-bit on your 80G hard drive, and that when you get the Windows XP install disc, you're going to install both Windows and Ubuntu 64-bit? If so, this is what I would do.

**1** -    Boot up with the Ubuntu live CD and go into Gparted to erase the whole disc. Then create one NTFS primary partition (sda1) with the boot flag set. Leave the rest of the hard disc unallocated for now. That will be formatted when you install Ubuntu.

The reason I suggest using the Ubuntu CD to erase the HD and set up a NTFS partition is that I've come across threads here where the Windows install disc seems to have been confused by pre-existing Linux partitions. I don't know whether that's true, but whenever I've installed Windows on a partition that takes up less than the whole of the HD, I've always prepared a partition for it first. It's always been happy with that. 

**2**   - Close down the Ubuntu live environment and now boot from the Windows CD and install Windows.

**3**   - Now boot up from the Ubuntu 64 disc and start the installer. At the partitioning stage, tell it to use the unallocated space of the HD. You could accept the defaults or set up your own partitioning layout, but only using the unallocated space.

You're quite right about installing Windows before Ubuntu. If you install Ubuntu first, it won't know about Windows and won't put a menu entry in grub's menu.lst for you. You'll have to do that yourself. More importantly, Windows will overwrite the grub stage 1 in the mbr and you won't be able to boot into Ubuntu - or at least until you re-install grub stage 1.

---

### Post by PsychedelicWonders on 2008-08-01
> **coffeecat said:**
> I'm not 100% sure exactly what you mean. Do you mean that at the moment you have just Ubuntu 32-bit on your 80G hard drive, and that when you get the Windows XP install disc, you're going to install both Windows and Ubuntu 64-bit? If so, this is what I would do.

Yes this is what I'm trying to do.

> **1** -    Boot up with the Ubuntu live CD and go into Gparted to erase the whole disc. Then create one NTFS primary partition (sda1) with the boot flag set. Leave the rest of the hard disc unallocated for now. That will be formatted when you install Ubuntu.

1) Does it prompt me to go into Gparted?

2) Where and how exactly do I great a NTFS primary partion?  In Gparted?

3)What is a boot flag and how do I set it?

Some people have said to install windows and do the partition then... does it really matter when you do it?

---

### Post by Elfy on 2008-08-01
> Does it prompt me to go into Gparted? - No.

> Where and how exactly do I great a NTFS primary partion? In Gparted? once you have used gparted to delete all existing partitions you will be left with unallocated space for the whole of the drive. Right click and then new - format to ntfs - you will be able to set the size you want there. 

> 3)What is a boot flag and how do I set it?Right clcik the new ntfs partition - manage flags.

---

### Post by TreeFinger on 2008-08-01
Insert Windows install CD. Restart Computer. Boot from CD.

You will then create the partition that you would like to install windows on. First delete all current partitions (Make sure you have backed up your important data as it will all be gone). Then create a new NTFS partition (Whatever size you want available for windows). Now, install windows to that partition.


After you feel like installing ubuntu, insert the live CD and restart the computer. Boot into Live cd desktop to make sure everything is working correctly. Then install ubuntu using the shortcut on the desktop.

You will now need to create 2 more partitions. One will be where your Swap partition. The size of this depends on how much memory (RAM) you have. Make it equal or a few 100MBs above how much you have. After you create the 'swap' partition you now create a Primary partition for your Ubuntu install + files you will be saving. Using ext3 file system is probably the best choice. (And use the rest of available storage on your harddrive unless you plan on installing another distro)

Just make sure you do not delete the NTFS partition when installing ubuntu, that is where windows is located. GRUB will be automatically configured and when you reboot Ubuntu will be your default OS but if you want to boot Windows then just select it from the menu.

---

### Post by PsychedelicWonders on 2008-08-01
> **forestpixie said:**
> - No.

So where or how exactly do I get to Gparted?

 > once you have used gparted to delete all existing partitions you will be left with unallocated space for the whole of the drive. Right click and then new - format to ntfs - you will be able to set the size you want there. 

Since its an 80 gig drive that is only ever goign to be used to run the OS', should I just split it in half?  or does windows need a bigger partition?

Right clcik the new ntfs partition - manage flags.[/QUOTE]

So when I right click and go to manage flags, there is a "boot flag" that I click on?

What does this boot flag do?

Do I boot flag both partitions, or just one?

---

### Post by Elfy on 2008-08-01
gparted is in the system - admin menu - Partition Editor

Can't answer xp pro size as I've never installed xp - but at a guess 50/50 won't hurt.

Boot flag tells which partition to boot - only put it on one, only make the ntfs partition, the ubuntu install will sort it's partition out later.

---

### Post by PsychedelicWonders on 2008-08-01
> **TreeFinger said:**
> Insert Windows install CD. Restart Computer. Boot from CD.

You will then create the partition that you would like to install windows on. First delete all current partitions (Make sure you have backed up your important data as it will all be gone). Then create a new NTFS partition (Whatever size you want available for windows). Now, install windows to that partition.


After you feel like installing ubuntu, insert the live CD and restart the computer. Boot into Live cd desktop to make sure everything is working correctly. Then install ubuntu using the shortcut on the desktop.

You will now need to create 2 more partitions. One will be where your Swap partition. The size of this depends on how much memory (RAM) you have. Make it equal or a few 100MBs above how much you have. After you create the 'swap' partition you now create a Primary partition for your Ubuntu install + files you will be saving. Using ext3 file system is probably the best choice. (And use the rest of available storage on your harddrive unless you plan on installing another distro)

Right now, I just have 2g of ram... but plan on upgrading to 8 eventaully.  I dont know when... but I might as well make the partition large enough to accomodate 8gigs now no?

so if I have 80k mb, take 36k for windows, 36k for Ubuntu and have 8500 for the swap partition?

Is that correct?

---

### Post by PsychedelicWonders on 2008-08-01
> **forestpixie said:**
> gparted is in the system - admin menu - Partition Editor

Can't answer xp pro size as I've never installed xp - but at a guess 50/50 won't hurt.

Boot flag tells which partition to boot - only put it on one, only make the ntfs partition, the ubuntu install will sort it's partition out later.


So if I want to mainly run Ubuntu... I should put the boot flag on that partition, not the windows one correct?

What does ntfs stand for?

---

### Post by TreeFinger on 2008-08-01
> **PsychedelicWonders said:**
> Right now, I just have 2g of ram... but plan on upgrading to 8 eventaully.  I dont know when... but I might as well make the partition large enough to accomodate 8gigs now no?

so if I have 80k mb, take 36k for windows, 36k for Ubuntu and have 8500 for the swap partition?

Is that correct?

I highly doubt you will need 8GB for swap. 1GB is probably enough for swap.. 2GB is definitely enough.

So 2GB for swap, then split in half for ubuntu and windows.

---

### Post by PsychedelicWonders on 2008-08-01
even if I run 8g - 2 is enough huh?

Is the windows partition #1, the swap partition #2 and the Ubuntu partion #3?

Are they given numberical value like that?

---

### Post by TreeFinger on 2008-08-01
> **PsychedelicWonders said:**
> even if I run 8g - 2 is enough huh?

Is the windows partition #1, the swap partition #2 and the Ubuntu partion #3?

Are they given numberical value like that?

Yes, the more ram you have the more unlikely your swap space will even be used.

I'm not really sure about the numbers. I'm guessing windows will be the first partition on your harddrive and the ubuntu one the second.

---

### Post by coffeecat on 2008-08-01
> **PsychedelicWonders said:**
> So if I want to mainly run Ubuntu... I should put the boot flag on that partition, not the windows one correct?

No, absolutely not. Windows must be on a primary partition and needs the boot flag otherwise it won't boot. Linux can be on a primary partition or on a logical one - but that need not concern us at the moment. Ubuntu/Linux does not need the boot flag. The utility grub (grand unified bootloader) which will be installed when you install Ubuntu takes care of booting Ubuntu and doesn't need the boot flag. You will boot Windows from the grub menu, but grub is not booting Windows - it is merely handing the booting process over to Windows if you choose Windows at the grub menu.

To repeat: the Windows partition **must** have the boot flag set. Ubuntu/Linux is indifferent to whether or not the boot flag is set.

---

### Post by PsychedelicWonders on 2008-08-03
am I going to need to install all of my hardware drivers cds on xp pro?

This is a brand new build.

---

### Post by Elfy on 2008-08-03
I would imagine so - I've never had a win install that didn't need hardware drivers to be installed, contrary to popular belief it doesn't work ootb usually :)

---

### Post by PsychedelicWonders on 2008-08-03
how will i know what cds to use to install drivers and which ones are already ok?

---

### Post by PsychedelicWonders on 2008-08-03
> **TreeFinger said:**
> Insert Windows install CD. Restart Computer. Boot from CD.

You will then create the partition that you would like to install windows on. First delete all current partitions (Make sure you have backed up your important data as it will all be gone). Then create a new NTFS partition (Whatever size you want available for windows). Now, install windows to that partition.


After you feel like installing ubuntu, insert the live CD and restart the computer. Boot into Live cd desktop to make sure everything is working correctly. Then install ubuntu using the shortcut on the desktop.

You will now need to create 2 more partitions. One will be where your Swap partition. The size of this depends on how much memory (RAM) you have. Make it equal or a few 100MBs above how much you have. After you create the 'swap' partition you now create a Primary partition for your Ubuntu install + files you will be saving. Using ext3 file system is probably the best choice. (And use the rest of available storage on your harddrive unless you plan on installing another distro)

Just make sure you do not delete the NTFS partition when installing ubuntu, that is where windows is located. GRUB will be automatically configured and when you reboot Ubuntu will be your default OS but if you want to boot Windows then just select it from the menu.

will it prompt me to do the partitions?  or am I going to have to right click anything?

---

### Post by Elfy on 2008-08-03
> **PsychedelicWonders said:**
> how will i know what cds to use to install drivers and which ones are already ok?Used to be check by right click my computer - properties - device manager - if there are any there with x or ? then they need sorting. But can't really remember how to deal with windows problems unless I have one in front of me.

> **PsychedelicWonders said:**
> will it prompt me to do the partitions?  or am I going to have to right click anything?

Will which prompt you - the win install or the buntu one.

---

### Post by PsychedelicWonders on 2008-08-03
the 2nd stage with ubuntu

---

### Post by PsychedelicWonders on 2008-08-04
Alright, uninstalled 32 with the cd and then partitioned the hdd for windows.

I installed xp pro and the service pack and a few other misc applications and games.

But when I tried to install 64, when I clicked start or run ubuntu, the screen turned black with a red box that said "RGB no Input signal" and then basically shut off, but didnt.

I tried a couple of times to do this... what is the problem?  Windows works fine, so there isnt any problem with the connections.

---

### Post by TreeFinger on 2008-08-04
> **PsychedelicWonders said:**
> ...
But when I tried to install 64, when I clicked start or run ubuntu, the screen turned black with a red box that said "RGB no Input signal" and then basically shut off, but didnt.

I tried a couple of times to do this... what is the problem?  Windows works fine, so there isnt any problem with the connections.

Are you doing this while conducting a session from the Live cd? 

Insert the CD and then reboot your computer. Make sure your bios has option to boot from CD-Rom before harddrive. You should now be in a live session. If everything is working correctly click the Icon on the desktop to install.

---

### Post by PsychedelicWonders on 2008-08-04
I just installed the cd, restarted the computer and booted up from the cd yes.

then it brought me to a menu screen, start and install menu screen where it gives you a few other options as well.

I clicked on start and install and then got this blackscreen error message?

---

### Post by TreeFinger on 2008-08-04
Instead of booting, select the option to 'check cd for defects'.

if no defects are found.. come back. if they are, redownload the iso if your iso is bad or just re burn the cd

---

### Post by PsychedelicWonders on 2008-08-04
alright I will check that out on lunch.

This is a brand new 64 cd though, i've never used it before and is scratchless.

It is version 7.04

I planned on installing this version and then just downloaded the 2 upgrades.

---

### Post by PsychedelicWonders on 2008-08-04
How exactly do I switch from ubuntu to windows and vice versa?

---

### Post by Elfy on 2008-08-04
Whne ubuntu is installed to will have windows in the menu.

If you are going to install 7.04 then upgrade sequentially 7.10 to 8.04 - why don't you just download 8.04 - it'll be less to download in the end.

Also there is a possibility of problems in each upgrade.

---

### Post by TreeFinger on 2008-08-04
> **PsychedelicWonders said:**
> How exactly do I switch from ubuntu to windows and vice versa?

You should just download the version you plan on using, upgrading can lead to troubles.

You will choose which OS you would like to boot when your computer starts up through GRUB

---

### Post by PsychedelicWonders on 2008-08-04
So at each bootup, it will prompt me to choose either windows or ubuntu?

And If I am in ubuntu, there is a windows tab under menu that just starts loading windows?

does it then shut down ubuntu... or keep it running in the background?

What about when i am trying to leave windows to go to ubuntu... how do I do that?

does it then also keep windows running in the background?

Or will it always completely shut down the other OS when I'm switching around?

---

### Post by Elfy on 2008-08-04
You will need to reboot to access either os.

Edit- perhaps you are talking about wubi, a dual boot installation is different - when you boot you will get a menu - choose buntu or win.

When you want the other you will have to reboot to do so.

---

### Post by PsychedelicWonders on 2008-08-04
ok, so the "menu" you guys are referencing is basically the DOS startup?

At startup it will give me the option of OS?

There isnt actually a tab in windows for ubuntu and a tab in ubuntu for windows?

What is this wubi?

Does this allow you to have a quick "shortcut" button in either windows or ubuntu to quickly launch the other and shut down the current?

---

### Post by TreeFinger on 2008-08-04
> **PsychedelicWonders said:**
> ok, so the "menu" you guys are referencing is basically the DOS startup?

At startup it will give me the option of OS?

There isnt actually a tab in windows for ubuntu and a tab in ubuntu for windows?

What is this wubi?

Does this allow you to have a quick "shortcut" button in either windows or ubuntu to quickly launch the other and shut down the current?

Restarting is the quickest way possible.

---

### Post by Elfy on 2008-08-04
The menu is the grub loader - yea 

There is no tab in ubuntu or windows afaik

Wubi is a way of installing inside windows - but, again afaik, you can only be running one or the other.

A virtual machine would install ubuntu inside windows, or windows inside ubuntu - but, it doesn't make use of hardware in the same way - graphics is 2D regardless of graphics card for example.

I would just do the dual boot installation as you have been planning, but I would suggest that you download 8.04 and install with that.

---

### Post by PsychedelicWonders on 2008-08-04
alright thanks guys.

I will have to wait another day or so until my dsl gets activated to download anything new.

Does the grub menu time out and default to loading ubuntu if I do not choose otherwise at startup?

Or will it always prompt me and wait for me to choose?

---

### Post by TreeFinger on 2008-08-04
> **PsychedelicWonders said:**
> alright thanks guys.

I will have to wait another day or so until my dsl gets activated to download anything new.

Does the grub menu time out and default to loading ubuntu if I do not choose otherwise at startup?

Or will it always prompt me and wait for me to choose?

You can modify a configuration file that will allow you to choose a 'default' os, and also the amount of time until this default os is booted.

---

### Post by oldos2er on 2008-08-04
> **PsychedelicWonders said:**
> alright thanks guys.

I will have to wait another day or so until my dsl gets activated to download anything new.

Does the grub menu time out and default to loading ubuntu if I do not choose otherwise at startup?

Or will it always prompt me and wait for me to choose?

 You can edit the grub menu to have it do anything you prefer. But yes, after you install Ubuntu it will be set to boot Ubuntu after a 10 sec. delay.

---

### Post by PsychedelicWonders on 2008-08-04
what exactly is this grub menu?

what does grub stand for? 

Is there a "gumped" version of what this actually does?

I dont think I need to edit the grub.

The 10 sec delay is ok.

I may cut it in half later, well see.

---

### Post by Elfy on 2008-08-04
what does grub stand for? Grand Unified Bootloader

Hours of reading - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by PsychedelicWonders on 2008-08-04
literally has hours of reading.

let me ask you this, I wanted to modify my computer that when it starts up, it plays music, a video or pictures... whatever I choose to "greet" me as it boots up. instead of the basic stock stuff that is there.

Is all of this handled in the grub?

anyone know of an easy walk through for what I'm talking about?

Oh by the way, i went to the "check cd for defaults" tab... and it did the exact same thing as when I try to run it.

So I guess I'll just have to download the newest version.

---

### Post by Elfy on 2008-08-04
> Is all of this handled in the grub?You can change what starts after grub, you can change the music and stuff within buntu afaik - I have nothing at all.

---

### Post by PsychedelicWonders on 2008-08-04
So when I download the newest 64 version, it will give me an icon on my desktop in windows?

And then I just install it accordingly?

Do I then just restart and it boots in ubuntu?

Should i download from ubuntu.com?

---

### Post by Elfy on 2008-08-04
you will download an iso which then needs to be burnt on a cd as an iso. Make sure that the laptop/pc is set to boot from cd first.

Boot with the livecd it will have an install icon on it's desktop - use that.

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Not sure how you installed last time

---

### Post by PsychedelicWonders on 2008-08-04
i had a 32 cd taht worked fine.

I will be using nero for the first time, will nero be able to burn it in its native .iso format?

---

### Post by Elfy on 2008-08-04
Burn as an image.

---

### Post by PsychedelicWonders on 2008-08-04
is .iso an image file system?

or are you meaning a .jpg or bmp?

---

### Post by Elfy on 2008-08-04
No it's not that sort of image the information is in one of the pages I gave you - this is one of the links

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by PsychedelicWonders on 2008-08-04
> **forestpixie said:**
> Used to be check by right click my computer - properties - device manager - if there are any there with x or ? then they need sorting. But can't really remember how to deal with windows problems unless I have one in front of me.

Alright I figured out where this place is, installed some additional drivers, I may have to download some more...

but ideally i want to keep downloading drivers until I have NO yellow ?'s correct?

---

### Post by Elfy on 2008-08-04
I would try to - but that's windows, there used to be some I didn't bother with a times, but I don't know which you're talking about so can't really help.

---

### Post by PsychedelicWonders on 2008-08-04
i think my dsl just got activated today, so when I get home I will try to download ubuntu 64 and all the drivers needed for windows and if i have any left over I'll let you guys know.

Thanks.

---

### Post by Elfy on 2008-08-04
You're welcome, good luck with it. IF you have issue with the buntu install it might be better to start new threads rather than tacking on to the end of this one.

---

### Post by oldos2er on 2008-08-04
> **PsychedelicWonders said:**
> what exactly is this grub menu?

   Is there a "gumped" version of what this actually does?

 

I see you've already had an answer about what grub stands for. The menu allows you to choose which OS, and/or which kernels you wish to boot.

 I don't know what "gumped" means.

---

### Post by Elfy on 2008-08-04
> I don't know what "gumped" means.I ignored that lol

---

### Post by PsychedelicWonders on 2008-08-04
> **oldos2er said:**
> I see you've already had an answer about what grub stands for. The menu allows you to choose which OS, and/or which kernels you wish to boot.

 I don't know what "gumped" means.


gumped, like forrest gump.

Break it down easy for me.  :D

---

