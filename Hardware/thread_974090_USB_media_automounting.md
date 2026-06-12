---
title: "USB media automounting"
date: 2008-11-07
forum: Hardware
---

### Post by JanusDuo on 2008-11-07
Okay guys, this is a long one I've been working on a while, but until recently I had kind of lost the trail.

I am trying to get the USB card support working in a game called OpenITG.  OpenITG is based on an eary CVS version of StepMania 4 which is called 3.95.  Anyhow, it's USB card support is pretty bad in modern Ubuntu, although according to others it works fine in Sarge.

Basically the problem seems to be that it was designed to automount drives itself because at the time it was made Linux didn't support automounting USB drives.  Also OpenITG only attempts to mount the drive if it's defined in fstab.

I'm using usb-storage, my fstab is like so:
```
/dev/sdb1   /media/sdb1   vfat   rw,user,noauto,sync,exec   0   0
/dev/sdc1   /media/sdc1   vfat   rw,user,noauto,sync,exec   0   0 
```

I created the mount points for it, then used gconf-editor to turn off media_automount and media_automount in apps>nautilus>preferences.  At first I was just using gnome, and couldn't to get it to mount at all, it would go like this:

> mount: special device /dev/sdb1 does not exist
WARNING: failed to execute 'mount /dev/sdb1' with error 8192. 

If I executed the command from the commandline however the drive would mount in the operating system though the game ignores it.

So here I was stuck for awhile, until I realized the one guy that does have it working but forgot how he did it is running the K desktop!  So off I went to install KDE.

KDE gave me a much better experience, the drives still fail with the same error about 50% of the time.  Seems that OpenITG and KDE are racing to grab the drive first and whoever gets there first wins.

So that's where I got stuck the second time.  A few days ago I was explaining our progress to someone on a forum.  When I told him that Gnome and KDE produce different results that user replied that "a desktop can't be the problem for USBs not working"

Someone else chimed in to back my finding up however, saying **"he's right, get rid of the HAL daemon (hald)"**

So I did.  This try around I decided to not only lose HAL I'd lose the window managers all together.  I turned off the gdm service and took the executable bits off of hald like so:

sudo chmod ugo-rwx /usr/sbin/hald /usr/lib/libhal-storage.so.1

This will cause it to fail loading at bootup.  I edited the xinitrc file to exec the openitg binary.  The result: a wonderful recreation of the arcade experience!  You turn the hardware on, it loads the operating system, and the operating system loads your game!

Not only that but everything in the game WORKS!  The usbs work great.  They still fail mounting occasionally if you unplug and replug them too fast but that's about it.

You'd think that that proves that hald was causing the problem now wouldn't you?  Well that's that I thought at first too, but nope.  Apparently hald is just one stop in the multi-program path your USB gets passed through when you plug it in til when it gets mounted.  When I forced it not to load it broke the chain.  It could be any component of hald, or possibly something further up the chain that I prevented the thread from reaching that caused the card to work correctly.

So now I'm trying to isolate the problem.  I did alot of misc script tweaking last night.  I added my user and my root to the plugdev and cdrom groups on recommendation of one posting on hald.  I inspected the scripts the connect dbus and hald and make minor adjustments wherever I see the scripts trying to limit what users can and can't call on them.  Nothing's seemed to work.

My question aside from "Do you have any ideas" is also: what is the order the USB gets passed down in Gnome, on KDE, and without a window manager.

Although I have a solution that works I'd like to narrow down the actual problem and also get this working in a desktop environment that also works.  Disabling HAL might fix USBs just for OpenITG, but it breaks most other pieces of hardware in the system, so it's not a solution I'm prepared to implement.

---

### Post by gaarie on 2008-11-11
UDEV.

you've prolly heard on BR forums, but the delay caused by UDEV creating the device turns out to be quite a problem. DEVFS (static devices, /dev files always exist) was last supported in kernel version 2.6.12, which was also the kernel version run on ITG machines. makes sense, huh?

right now i'm looking through the source to see if a small pause before looking for the device might help the issue. you might also be interested in my release of ITG2AC pico installer (i just thought up that name...) this friday. it'll be around 1-2gb download but will be fully working copy of an arcade drive. info will be on BR.

---

