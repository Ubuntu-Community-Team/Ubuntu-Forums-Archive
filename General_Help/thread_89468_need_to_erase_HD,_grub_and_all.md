---
title: "need to erase HD, grub and all"
date: 2005-11-12
forum: General Help
---

### Post by Specialsauce on 2005-11-12
im having a problem. Whenever i try to install breezy (i tried to install over my old copy, because i was having significant problems), it stops and says it had an error copying the remaining packages to disk. There are a few possible causes. I hope to god that it isn't a bad disk drive, but i dont think it is. It could be a problem, with writing over the existing data, or it could be a bad disk. The latter two would be easy to fix. I want to try to format my disk before i try to burn a new disk. I currently dont have an operating system installed, so im gonna have to do it via livedisk. how would i do this? (i currently have access to knoppix and the ubuntu livedisk)?

---

### Post by poptones on 2005-11-12
It's probly just a bad CD. Wipe the one you have vigorously on your shirt (usually works for me). 

Wiping a drive is easy. Assuming you have only one hard drive it'll appear in knoppix as something like mnt/hda. So, just do a dd to hda and wait...

dd if=/dev/zero of=/dev/hda

Needless to say, make sure you know exactly which drive you are doing this to if you have more than one. Unplugging all but the target drive is cheap insurance.

---

### Post by Specialsauce on 2005-11-12
[QUOTE=poptones]It's probly just a bad CD. Wipe the one you have vigorously on your shirt (usually works for me). 

Wiping a drive is easy. Assuming you have only one hard drive it'll appear in knoppix as something like mnt/hda. So, just do a dd to hda and wait...

dd if=/dev/zero of=/dev/hda

Needless to say, make sure you know exactly which drive you are doing this to if you have more than one. Unplugging all but the target drive is cheap insurance.[/QUOTE]
thanks!

---

