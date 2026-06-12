---
title: "wrong set root="
date: 2010-05-15
forum: Hardware
---

### Post by ramseyhead on 2010-05-15
first attempt at posting

my drive setup 1- 750gb XP sata
                      1- Raid5  XP sata
                      1- 250gb Ubuntu 10.04 ide

my problem, when I boot my system I end up with "unknown file system". I am then offered "grub rescue"
using "ls" and going through the available drives I find my Ubuntu files at "(hd2,1)".
I have tried editing from here but end up with a complaint about "grub_put_".
I have booted Ubuntu with a live CD (mine does not seem to have a broken system option). I can also boot with a "Super Grub Disk" which also finds my files at (hd2,1).

Following posts from "drs305" (The Man) I have committed the sin of editing "grub.cfg", I have altered it so that it looks for (hd2,1) and saved it, at which point it remains at (hd2,1) then as per the instructions I "sudo update grub" when by magic "grub.cfg" reverts to (hd0,1).
I am interested in computers as I like logic puzzles, so I assume among the 100000+ files on my setup there is a .mod file that holds this information.
If some one can tell me if there is one and where it is I can be happy having solved a puzzle, if not I can fell a fool and start again.

thanks, ramseyhead

---

