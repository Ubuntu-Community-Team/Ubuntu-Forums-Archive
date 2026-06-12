---
title: "Help me prepare for my fresh install."
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by Cam42 on 2009-10-25
I'll be doing a fresh install of Xubuntu Karmic in a few days. Some questions

[LIST=1]
[*]If I create a large ext4 partition now, before the upgrade, move my files to it, can I use that partition as /home with the fresh install?
[*]What is the recommended partitioning scheme?
[/LIST]

[LIST]
[*] How big should each partition be?
[/LIST]

---

### Post by earthpigg on 2009-10-25
> **Cam42 said:**
> I'll be doing a fresh install of Xubuntu Karmic in a few days. Some questions

[LIST=1]
[*]If I create a large ext4 partition now, before the upgrade, move my files to it, can I use that partition as /home with the fresh install?
[*]What is the recommended partitioning scheme?
[/LIST]

[LIST]
[*] How big should each partition be?
[/LIST]

1. yes, but you should still have your important data backed up in case you mis-click during the install or the power dies or the moon and stars align resulting in a failed install. if you are unable to back everything up at this time, then i suggest sticking with your existing install until that changes. if your vital data is under 2gb and you are ok with the 'cloud', you can back it all up using [dropbox]("https://www.getdropbox.com/") or [UbuntuOne]("https://one.ubuntu.com/").

2. what i consider to kinda-sorta be the standard scheme is:

-15gb, mountpoint of /, ext4, bootable flag

-2gb, use as swap. if you give us exact hardware specs and exactly what you use your computer for, we can discuss the need for a swap at all, and how big it should be if you have one till the cows come home. if HD space is at a premium for you, let us know and we can do cost/benefit analysis with you.

-rest, mountpoint of /home, ext4... make sure you click 'do NOT format' at this point. not that you risk losing any data, really, since you will have everything backed up right?

-if you want to, you could make a /media/media partition that all users have read/write access to and put music and stuff there for all to use.

---

### Post by Cam42 on 2009-10-25
> **earthpigg said:**
> 1. yes, but you should still have your important data backed up in case you mis-click during the install or the power dies or the moon and stars align resulting in a failed install. if you are unable to back everything up at this time, then i suggest sticking with your existing install until that changes. if your vital data is under 2gb and you are ok with the 'cloud', you can back it all up using [dropbox]("https://www.getdropbox.com/") or [UbuntuOne]("https://one.ubuntu.com/").

Yes, I already have a combination of dropbox (I've actually got 2.75GB due to people I've referred) and UbuntuOne. I also have a DVD burner, so I'll do that as well.
> 
2. what i consider to kinda-sorta be the standard scheme is:

-15gb, mountpoint of /, ext4, bootable flag

-2gb, use as swap. if you give us exact hardware specs and exactly what you use your computer for, we can discuss the need for a swap at all, and how big it should be if you have one till the cows come home. if HD space is at a premium for you, let us know and we can do cost/benefit analysis with you.

-rest, mountpoint of /home, ext4... make sure you click 'do NOT format' at this point. not that you risk losing any data, really, since you will have everything backed up right?

-if you want to, you could make a /media/media partition that all users have read/write access to and put music and stuff there for all to use.
Thank you.

---

