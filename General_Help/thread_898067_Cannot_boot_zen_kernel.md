---
title: "Cannot boot zen kernel"
date: 2008-08-22
forum: General Help
---

### Post by Animeniac on 2008-08-22
I have followed this site to build the zen kernel: [http://www.mattparnell.com/zen-kernel.html](http://www.mattparnell.com/zen-kernel.html)

Where it says "Put it in a text file named buildZen, and chmod +x buildZen after that.", I copied and pasted the code into text files named both "buildZen" and "chmod +x buildZen", and saved them in my /home/owner folder (owner is my username). I also ran the script successfully.

Then I followed the Ubuntu wiki on this site: [https://wiki.ubuntu.com/ZenKernel](https://wiki.ubuntu.com/ZenKernel)

I downloaded and installed the headers and image packages from here: [http://www.mattparnell.com/zen/2.6.24-rc5-zen1/32%20bit/](http://www.mattparnell.com/zen/2.6.24-rc5-zen1/32%20bit/)

And now whenever I boot the zen kernel, it won't even load - it starts to hang at a text screen with "starting kernel log daemon" and then it fails and goes to the generic kernel.

What did I do wrong? What else was I supposed to do first?

---

### Post by Washer on 2008-08-24
search the zen kernel thread in the tutorials forum.

---

### Post by Animeniac on 2008-08-24
That's exactly where I first heard of it.

The page where you download the .deb files is rather confusing to me. I don't know which files I need to download.

---

### Post by Animeniac on 2008-08-24
I got the wrong .deb files. I didn't pay much attention to the very top line of the first post of the thread in the Ubuntu Forums (I didn't look at the version number). That was how I wasn't able to boot the zen kernel. How careless of me. Now I understand that the files I have to download have to match the script (I have to get the 2.6.24-rc4-zen1 files for the script labelled as '2.6.24-rc4-zen1').

---

### Post by Washer on 2008-08-24
dunno, it sounded like you were having trouble with klogd & numerous people also did in that thread.. including me.

---

### Post by Animeniac on 2008-08-24
I can now boot into the zen kernel, but I end up with "Low graphics mode". I tried to install the drivers for my NVIDIA graphics card for the zen kernel by following the [Ubuntu wiki article of it]("https://wiki.ubuntu.com/ZenKernel"), but I only got a HEAVY LOAD OF ERRORS:
```
Hunk #1 FAILED at 1244.
1 out of 1 hunk FAILED -- saving rejects to file usr/src/nv/conftest.sh.rej
patching file usr/src/nv/nv-linux.h
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
4 out of 4 hunks ignored -- saving rejects to file usr/src/nv/nv-linux.h.rej
patching file usr/src/nv/nv.c
Hunk #1 FAILED at 2040.
Hunk #2 FAILED at 2052.
Hunk #3 FAILED at 3919.
Hunk #4 FAILED at 4056.
4 out of 4 hunks FAILED -- saving rejects to file usr/src/nv/nv.c.rej
patching file usr/src/nv/os-interface.c
Hunk #1 FAILED at 609.
Hunk #2 FAILED at 619.
Hunk #3 FAILED at 630.
Hunk #4 FAILED at 1373.
4 out of 4 hunks FAILED -- saving rejects to file usr/src/nv/os-interface.c.rej
Failed to apply patch file "/home/owner/xen.patch.txt".
```

I even downloaded the driver file for my Nvidia graphics card driver, and typed the code into terminal to match the driver file (sudo sh NVIDIA-Linux-x86-**96.43.07-pkg1**.run --apply-patch xen.patch.txt). Maybe I'm not intelligent enough to **really** understand the directions on how to install the Nvidia drivers into the zen kernel in the Ubuntu wiki article. Can someone please help me solve the "low graphics mode" problem? If it requires me to install the Nvidia driver, then can someone give me more-detailed directions on how to install the Nvidia driver into the zen kernel? Thanks.

---

### Post by Washer on 2008-08-25
use the envy script, as matt says in that thread.

---

