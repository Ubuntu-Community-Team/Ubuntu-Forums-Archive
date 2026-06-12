---
title: "change from 32bit to 64bit?"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by TylerTheWonderfull on 2009-10-12
okay so I installed ubuntu not too long ago but like an IDIOT I got 32bit when I needed 64bit cause I'm running 8gigs of RAM.... so I was wondering if it's posable to replace 32bit with 64bit and not lose my files and such...

---

### Post by BigCajun on 2009-10-12
You can't "upgrade" a 32-bit install to a 64-bit install (of any O/S that I'm aware of). If you want 64-bit, you'll have to reinstall. If you have an optical drive or some sort of memory sticks or other harddrives, you can copy/burn/move your files to any of those and then reinstall 64-bit and move the files back afterwards.

---

### Post by TylerTheWonderfull on 2009-10-12
yea that's what I thought..... so there's no way to replace a OS?

---

### Post by BigCajun on 2009-10-12
The only way to replace it is to reinstall. I'm not an O/S expert, but all of the compiled binaries that comprise an O/S need to be compiled with a specific memory addressing scheme (in this case either 32-bits wide or 64-bits wide). If you wanted to "replace" one with the other, you'd have to copy ALL of the files over. And in some cases, there seem to be different libraries as well (I may be wrong, I'm not an expert).

Long story short, to switch the memory addressing scheme between 32-bit and 64-bit requires a complete re-install.

You could (if you wanted and had the disk space) install a 64-but version along side the 32-bit version you have and dual boot just like people do when they want Windows or another O/S in addition to Linux. But then you'd still have a 32-bit O/S and a 64-bit O/S and you can only boot into one or the other.

---

### Post by Slim Odds on 2009-10-12
This is why lots of us recommend using a separate /home partition. It makes things like this a minor issue.

---

### Post by dj-toonz on 2009-10-12
There's another way, you can go about this if you don't want to re-install & want Ubuntu to show up the whole 8 gigs of ram, that's by installing a pae or server kernel. that's the only way I know, without doing a clean install of x64

---

