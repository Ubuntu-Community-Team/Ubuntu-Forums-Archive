---
title: "Multimedia Mute key no longer works correctly"
date: 2009-03-29
forum: Hardware
---

### Post by Olnex on 2009-03-29
Hello, I have a Toshiba U400 laptop, it has several multimedia touch keys: mute, media player, play/pause, stop, backward and forward. They used to be working, but after I reinstalled many systems(procedures as follows), the Mute key always starts nautilus. What I did are:

1. I recovered using recovery CD to XP, and used Partition Magic to resize the only partition two two partitions(C and D for XP) and left a large unallocated space.

2. Then I installed Opensuse 11.1 on the unallocated space with three extended partitions: /, /home and swap.

3. Later I swiped the partition table and reinstalled Ubuntu 8.10 only

So after the thrid step, I found the Mute key no longer works(it used to be working under Ubuntu), when I press it, it launches Nautilus, so I checked the keyboard shortcut in Preferences, the Mute function is mapped to key XF86Mute, but when I manually reassign the mute key, it shows XF86Home, so this key is now detected as function key for Home.

Then I though it was because I messed up the settings in previous XP and it is written to hardware, so I recovered again and found the problem: When I enter the system, if the network manager is not started(Toshiba has its own network utilities called ConfigFree) and I press mute key, it lanches Internet Explorer(so it seems the key is also detected as Home key), but when the network is up, the Mute key does the correct job - mute/unmute volume.

So is it likely to be a hardware problem? I can of course manually assign the mute key to Mute in Ubuntu(although it is displayed "XF86Home") but I suspect there is a hardware problem, however I cannot send it to repair even it is withing warranty period as it is Ubuntu, not the original system, but with XP, it works fine after network is up(or some hotkey programs that takes care of multimedia keys settings).

Any one has any ideas?

Thanks!

---

