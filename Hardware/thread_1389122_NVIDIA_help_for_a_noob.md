---
title: "NVIDIA help for a noob"
date: 2010-01-24
forum: Hardware
---

### Post by mental2k on 2010-01-24
Hi guys, completely new to this Linux lark, and feeling a bit clueless.

I have recently installed Ubuntu 9.10 and installing drivers already seems a bit beyond my abilities, but never one to back down in the face of adversity I thought I'd ask for some help.

I have downloaded a set of NVIDIA drivers for my Geforce 8600m GS graphics card in my laptop and I can't get them installed.

If I run the drivers from the desktop (and select run in terminal from the dialog box that appears) it runs in the terminal and tells me I need to be root.

So into the terminal I delved, I tried running the file using "sudo chmod +x nvidia.run" and I'm not really sure if anything happened. There was no on screen indication of anything happening and I'm not really sure how to check if anything has installed or not.  I can't seem to find any equivalent of windows device manager to check what is going on either.  So I'm at a bit of a loss.  Any help most appreciated.

Oh yeah, and the .run file is on my desktop, and I've navigated to there before I ran chmod.

Once again many preemptive thanks extended.

---

### Post by hemimaniac on 2010-01-24
Anything i have ever gotten from the NVidia site was just cd into the directory then run

sh ./name_of_nvidia_file.run as root
though i have had some give errors and you may need to drop to

telinit 3 first

---

### Post by mental2k on 2010-01-24
Thank you sir, you are genius!

---

