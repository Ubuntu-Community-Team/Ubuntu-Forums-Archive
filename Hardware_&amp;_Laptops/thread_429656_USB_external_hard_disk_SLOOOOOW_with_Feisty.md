---
title: "USB external hard disk SLOOOOOW with Feisty"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by ntt on 2007-05-01
Hi,

since I've upgraded to Kubuntu Feisty, my USB external hard disk became slow as hell.

To give an idea, writing data to it went down from 20+ MB/sec to about 3 MB/sec.

After some investigation I've discovered that the external HD is now automounted with the 'sync' option (as shown in /etc/mtab while mounted), which might well explain the ridiculous performance.

But I don't know how/where to modify the default parameters for the automount service, so that I can specify to mount USB devices (or at least _that_ USB hard disk) with the 'async' option by default.

Thanks in advance for any hints.

---

### Post by bozackt on 2007-05-03
I have exactly the same problem. Dapper was fine, feisty is slow (I skipped edgy because it wouldn't install on my system). I hope someone comes up with a solution as the usb drive is my backup drive. What used to take an hour do to a backup now takes all day. Ugg.

---

### Post by ntt on 2007-05-04
Hi,

Good news!  I have eventually fixed that problem.

It turned out to be a problem with the automount feature of KDE (I use Kubuntu) and NOT with Feisty itself.

So you have two possible solutions:

1) If you use Kubuntu, let KDE mount the drive and then right-click on the HD icon on the desktop, choose Properties and uncheck the checkbox for "sync" ( I did also disable "atime", but that's another story).

2) If you use Ubuntu, I suppose Gnome has a similar feature but don't know for sure.

Actually there's a third possibility, not depending on the desktop environment: open a terminal, and mount that device using "pmount"; the defaults for pmount in fact include the 'async' option.

In my case, the disk is seen as '/dev/sdb1' and it pmounts by default under '/media/disk'; thus if I issue the command 'pmount /dev/sdb1 /media/disk'  I'm all set with normal drive speed.

I'm confident that one of the options above will fix the problem for you as well.

cheers.

---

### Post by bozackt on 2007-05-04
Thanks for the tip. I think we must have some kind of psychic bond - I discovered the same thing about when you did.

I'm still a bit confused about when changes in the "Properties > Mounting" configuration tab take effect. When I unsellected "Synchronous" the mtab still showed "sync". (Maybe mtab doesn't get updated.) So I unmounted and remounted the drive. Maybe that wasn't necessary. I do some experiments to pin this down.

Also, I would be nice to find out how to change the default mount behavior. And why is "synchronous" the default?

---

### Post by ntt on 2007-05-04
I'm not sure about the mtab "delayed" behavior, but probably the difference will show - as you said - next time you unmount/remount the device.

The default mount options must be buried somewhere in the general KDE config files, but I'm damned if I can guess where to dig for them.

The sync option: in theory it's a safer way to handle removable devices [you know, those things people tend to rip off the socket just before the write operation completes] but as a side effect the system makes a physical write operation every few bytes of data, resulting in down-the-drain performance.

Not to forget,  it's also a good way to quickly kill flash memories... those things do have a _limited_ number of write cycles they're meant to support, and doing a write for every damn byte will definitely wear out the flash memory in a short(er) time.

heck, in the long run I'm afraid the sync option might damage even conventional hard disks... my external USB drive kept on spinning and writing for ages with the sync option set.

OK, catch you next time.

cheers

---

