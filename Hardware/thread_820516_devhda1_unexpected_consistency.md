---
title: "/dev/hda1/: unexpected consistency"
date: 2008-06-06
forum: Hardware
---

### Post by DM was on fire! on 2008-06-06
The scariest thing of my life almost happened a few minutes ago. srsly.
D-cha (that's me) was booting up her computer as usual, when her computer decided to run fsck. I usualy don't run it because I'm too lazy to, but this time I got the following:

*/dev/hda1: unexpected consistency. Run fsck manually.*

I restarted, booted in Recovery Mode so I could see what was going on.
If I remember right, I think something ALSA was failing. I think. I don't remember. D:

Anyway.
It asks for my root password for maitenance, I give it. 
I then receive the following output:

[i]bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found[/i]

I'm freaking, run fsck, and get this output:

[i]fsck 1.38 (30-Jun-2005)
e2fsck1.38 (30-Jun-2005)

/dev/hda1 contains a file block with errors. Check forced. **(which I don't get, seeing as I forced the check. XD)**
Pass 1: checking inodes, blocks and sizes

Inodes that were a part of a corrupted orphan linked list found. Fix? <y> (**y, naturally**)

Inode 1394369 was part of the orphaned inode list. Fixed. **(some .png in my .thumbnails folder. With the file name it gave [which I didn't get a chance to write down]), it looked like a GaiaOnline avatar filename)**[/i]

Because I thought fsck was done after it asked me to fix it, I typed shutdown -r now and it restarted. It displayed some more stuff I didn't get to write down, booted up my last kernel, I forced fsck again, checked without a hitch, rebooted on it's it, and now it's working fine (seeing as I'm currently talking to you on it).

So...what the hell just happened here, and should I count on getting a new hard drive? o_o
My heart's still pounding, due to as soon as I saw the terminal output in red, my first thought was a kernel panic.

Also, there's a folder in .thumbnails which is named "fail". Is this tied in, and should I delete it?

Thanks for your help! <3

- DM

---

### Post by wdaniels on 2008-06-06
> **DM was on fire! said:**
> So...what the hell just happened here, and should I count on getting a new hard drive? o_o

This kind of filesystem error usually happens if the system crashed or if it wasn't shutdown cleanly, but sometimes the cause is less obvious. Whilst it *could* indicate a hardware fault, it's more likely (at least by my experience) not and I wouldn't worry too much about it unless it happens again for no obvious reason.

---

### Post by DM was on fire! on 2008-06-06
Oh, phew.
Thank you, wdaniels. <3

We had a power surge yesterday, so that was most likely the cause of it. 

Thank you again!
*can now breathe a sigh of relief*

---

