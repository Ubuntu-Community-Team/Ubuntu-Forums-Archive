---
title: "Help with key remapping"
date: 2008-10-05
forum: General Help
---

### Post by gausie on 2008-10-05
Hi everyone.

I have a Dell Vostro Laptop with a key setup meaning that you must use the Fn key to press Home and End. What I would like to do is swap Home with Page Up, and End with Page Dn.

I know that this is possible, and I've written an xmodmap script (~/.xmodmaprc) that reads as follows:

```
!Key map modifications made on startup

!Swap prior (page up) and Home
keycode 97 = Prior
keycode 99 = Home
!Swap next (page down) and End
keycode 103 = Next
keycode 105 = End
```

This does not reassign the keys on startup, and if I try to run **xmodmap /home/gausie/.xmodmaprc**, terminal just sits and does nothing, eventually crashing X11.

Currently, when X starts, it seems to be running xmodmap and, due to it not working presumably, causes the computer to run really slowly. I checked top, and saw at least 10 instances of xmodmap, so I ran **killall xmodmap** and that fixes the problem for the session.

Does anyone have any idea as to how I can fix this?

Cheers

Gausie

---

### Post by gausie on 2008-10-05
Bump :-)

---

### Post by crom.osec on 2008-10-06
Try this
[http://www.osec.ro/en/index.php/KB_Kubuntu:_Remapping_keys_in_kubuntu]("http://www.osec.ro/en/index.php/KB_Kubuntu:_Remapping_keys_in_kubuntu")

---

