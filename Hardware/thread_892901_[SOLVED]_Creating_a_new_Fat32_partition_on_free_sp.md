---
title: "[SOLVED] Creating a new Fat32 partition on free space of NTFS drive..."
date: 2008-08-17
forum: Hardware
---

### Post by Predator106 on 2008-08-17
EDIT: Aw crap, this is probably in the wrong section. Could a mod move it to where it should be please.

Hello, I have a 250 gig drive that is currently formatted as NTFS 3g, it's mountpoint is 'sdd'. This drive has 60 gigs free, and I need to format that portion of it, into another partition of Fat32, I want it to be recognized by my PS3, and am hoping that the PS3 will actually see that Fat32 section as a drive, and not just think it's some kind of sub section or something crazy. Anyways, the data I have on it is very valuable and I am unable to back it up. This data took a very long time for me to work on (music, games, ripped from CD/DVD's, etc.).

I was thinking I could use cfdisk maybe?? Gparted sucks in my opinion, either I don't know how to use it, or it completely sucks. I would like a drive manager similar to the one in windozze xp, the GUI and etc. Whereas the command-line is much more tough for me (I'm not experienced with the terminal).

All I need is 9 gigs of Fat32 space, taken from the free 60 gigs.

EDIT2: Well, apparently cfdisk won't work, it doesn't recognize non-ext3 file systems I guess, thus my external doesn't show up in it.

fdisk seems like a good program, but being inexperienced at the terminal, I have no idea what to type in. The man pages seem overly complex and don't always give good examples.

---

### Post by Predator106 on 2008-08-18
bump :)

EDIT: Apparently you have to unmount drives before you can format them in gparted, I did not know this, talk about feeling like an idiot :) .

---

