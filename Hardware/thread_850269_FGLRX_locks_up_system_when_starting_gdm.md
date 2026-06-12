---
title: "FGLRX locks up system when starting gdm"
date: 2008-07-05
forum: Hardware
---

### Post by outlaw45 on 2008-07-05
I'm using Ubuntu Hardy Heron 8.04 and installed the latest FGLRX drivers through envy.. When the system reaches runlevel 5 it displays a black screen and locks up, only hard reset and Ctrl+Alt+PrtScrn+B still work.

At first I thought it was the fglrx driver but Xorg.0.log doesn't displays any errors. After that I looked at the GDM log and found the following errors (attached both files): 
Exec failed for command "/tmp/firegl1.isse.0f00a7d0.486f90b3.000c86d9" (No such file or directory)
Exec failed for command "/tmp/firegl1.isse.0f00a7d0.486f90b3.000c8bb4" (No such file or directory)

So I hope I found the problem and its solvable, google doesn't give me a lot results.. 
I asked here first but if no one knows I'll create a official bug..

uname -r: 2.6.24-19-generic

---

### Post by outlaw45 on 2008-07-19
bump..

---

