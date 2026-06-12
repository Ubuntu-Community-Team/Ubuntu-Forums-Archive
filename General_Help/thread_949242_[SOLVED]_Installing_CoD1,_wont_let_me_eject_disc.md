---
title: "[SOLVED] Installing CoD1, wont let me eject disc"
date: 2008-10-16
forum: General Help
---

### Post by little8020 on 2008-10-16
I am trying to install Call of Duty 1(Game of the Year edition) on Ubuntu 8.04 computer.
Installation works fine in WINE until it gets to the point were it needs the 2nd CD. When I try to eject it, through pushing the button on the drive or right clicking on the drive and unmounting, It pops up an error saying that it can't eject due to an application(the installation) needing the disc, even though it is asking me to put in the 2nd disc.

It doesn't seem like a problem with WINE because the message is in the Gnome style.
The computer is able to play the game inside Windows.
It is the latest cernal of 8.04.

I will try to give any additional info if needed.
Thanks in advance for your help
Jeremy Little.

---

### Post by jerome1232 on 2008-10-16
Actually I remember this as being a Wine issue, there is some wine eject command give me a moment to find it.

edit: Lol, it's a pretty easy command actually ;) This should make wine release the disc and allow gnome to unmount it. I would check in winecfg and make sure the cdrom is configured as a cd-rom and not a hard drive (it's the default and I remember it caused this problem for me)

```
wine eject
```

---

