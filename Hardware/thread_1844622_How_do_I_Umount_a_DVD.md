---
title: "How do I Umount a DVD?"
date: 2011-09-15
forum: Hardware
---

### Post by josephine.reeve on 2011-09-15
I'm trying to install my WoW game, the Blizzard support person thing said I can just use my Cata disk, however it says "No installer data can be found. If the problem persist please contact blizzard support team". They're website isn't very helpful. I am using Wine.

I read on another page from here, probably a few years back it was made that I can do this:

/etc/fstab

sudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR=Red]unhide[/COLOR],noauto,exec 0       0

My question is, how do I do this? If this through a terminal or what? A nice easy to follow guide would be very handy please.

---

### Post by haqking on 2011-09-15
> **josephine.reeve said:**
> I'm trying to install my WoW game, the Blizzard support person thing said I can just use my Cata disk, however it says "No installer data can be found. If the problem persist please contact blizzard support team". They're website isn't very helpful.

I read on another page from here, probably a few years back it was made that I can do this:

/etc/fstab

sudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR=Red]unhide[/COLOR],noauto,exec 0       0

My question is, how do I do this? If this through a terminal or what? A nice easy to follow guide would be very handy please.


First of all i take it you are using Wine correct ? as WOW is a windows .exe which needs to be run in wine and not directly in linux.

As for unmounting a file system you can do that with disk utility or from command line.

and when running tools such as gedit you should use **gksudo** and not **sudo** and be careful playing with your fstab if you go down the route

i cant offer anymore advice than that as i do not play games i am afraid.

however there is a WOW community docs here [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and plenty of thread on this forum for it if you get stuck

cheers

---

### Post by josephine.reeve on 2011-09-15
Yes I am using Wine correctly, I've done it so the .exe opens automatically with Wine, and not with Linux. Thank you I didn't know there was a WoW community, I shall take a look into that.

---

