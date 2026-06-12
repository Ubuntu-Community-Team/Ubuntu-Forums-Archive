---
title: "DVD Write Speed"
date: 2008-11-10
forum: General Help
---

### Post by cegpope on 2008-11-10
I need a way to convince my system that my DVD drive is capable of writing at speeds greater than 1x. My drive is a Matshita DVD-RAM LF-D311, if I remember correctly it would burn at speeds up to 8x in windows, but no matter what burning program I try in Ubuntu I get this message or one like it:

> :-[ GET PERFORMANCE failed with SK=5h/INVALID FIELD IN CDB]: Input/output error
:-( falling down to SET CD SPEED
:-( "Current Write Speed" descriptor is not present, faking 1x...
:-[ PERFORM OPC failed with SK=5h/INVALID COMMAND OPERATION CODE]: No such device
/dev/sr0: "Current Write Speed" is 1.0x1352KBps.

I have had this issue with every version of Ubuntu that I have used: Feisty, Gutsy, Hardy, and currently in Intrepid. This has never been a huge issue because I would only burn a dvd once every few months and letting it go for a couple hours was inconsequential. However, I am starting to make videos that I would like to burn to dvd and it has become frustrating waiting hours for a single disc to be finished.

---

### Post by cegpope on 2008-11-13
I have tried rescanning the drive, it recognizes the drive model properly, but still will not allow burning over 1x.

---

### Post by cegpope on 2008-11-19
It appears that I must come to the conclusion that it is impossible to correct drive speed reporting erros in linux.

---

