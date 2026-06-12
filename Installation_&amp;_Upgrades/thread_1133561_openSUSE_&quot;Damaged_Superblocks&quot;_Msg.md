---
title: "openSUSE &quot;Damaged Superblocks&quot; Msg"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by koldphlame on 2009-04-23
I was installing openSUSE on this old harddrive i had laying around and when it was deleting the old windows partion it stopped and said something about damaged superblocks:confused: can someone please explain how to fix this or point me in a direction to learn to fix it:P**** 

Help will be greatly appreciated:)

---

### Post by inobe on 2009-04-23
kinda in the wrong forum but i can assist.......


when you get kicked into command line interface "CLI" should say something like 'Control D' to restart, you want to type

```
fsck -f
```

you will then get many prompts Y/N? yes always worked for me.

then hit enter, this will force a filesystem check, if you get a warning about the drive being mounted it needs to be unmounted, do

```
umount dev DEVICE NAME HERE
```

or reboot, rebooting will launch you back to cli before the drive gets mounted.

if all goes well you should end up at your desktop but the timer is ticking on the hard drive, usually having to do this means the drive has bad sectors and is heading south.

---

