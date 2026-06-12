---
title: "initramfs busybox comes up when booting after motherboard upgrade"
date: 2008-11-12
forum: Hardware
---

### Post by gully on 2008-11-12
I have a hardy/xp dualboot system and I like it how I can use ubuntu as a backup when upgrading parts that require windows to be reinstalled.

I've gone from an old via k8m800 amd board to an asus intel p5b-deluxe to an asus p5bkpl-c and finally an asus p5kpl-cm.
The first upgrade went fine for ubuntu, the second time I had to change some UUID's in /boot/grub/menu.lst and everything worked afterwards.
The relatively small change from the p5kpl-c to the p5kpl-cm (same chipset) is giving me nothing but trouble however.

I got a p5kpl-cm because the p5kpl-c broke down, because of the warranty I still had I had it replaced in a store (usually I'd do it myself.)
The store then put in the p5kpl-cm for some reason, but xp works fine with it, no reinstall needed.

When I tried to boot into hardy I get the initramfs busybox after a couple of minutes of splash screen and then a lot of errors, sometimes it hangs after that, but when I type exit ubuntu boots, sometimes it continues by itself, in both cases there are some errors in the checklist.
Ubuntu also doesn't recognize my ide dvd-rw anymore and lan is disabled.

I checked the UUID's in menu.lst, they are consistent with the ones in fstab.
When I looked inside my case I did notice that the store put the hdd's sata cable in sata socket 3 (on the other boards I always put it in socket 1.)
They also plugged in the sata connector from my case (for an external hdd, which I don't have.)

I put the hdd's cable back in socket 1, but it didn't solve the problem, unplugging the other sata cable didn't help either.

Aside from the motherboard no hardware was replaced and ubuntu has not been upgraded until well before I got my new motherboard.
I find it hard to believe that a linux system which is supposed to more stable than windows cannot survive an upgrade to a motherboard with the same chipset.

Can anyone please help me with this?

---

### Post by gully on 2008-11-17
Turns out all I had to do was unplug the (IDE) DVD-drive, boot, shut down, plug the DVD-drive back in and all the errors and slow booting went away.

I hope this will help someone else, so they won't have to work days on an end to figure out what the problem was, meanwhile not getting any replies on ubuntuforums...

---

