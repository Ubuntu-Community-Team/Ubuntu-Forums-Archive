---
title: "GRUB error on load (GRUB repeats on screen)"
date: 2008-08-05
forum: General Help
---

### Post by i2adoo on 2008-08-05
Hello. I am running Ubuntu 8.04 on a Dell XPS M1130. It is not a dual-booting machine, Ubuntu is all I have on it. Here is the problem I have encountered and how it happened:

Last night everything was working fine and I closed the laptop in the way I usually do (which is the normal decent way). Today when I tried to run it again I never got to boot ubuntu. On a black background I get "GRUB GRUB GRUB GRUB" written a million times. It seems to be looping the command or whatever makes it print GRUB. Pressing any key gets me a nice motherboard beep. (Sometimes the loop stops and I am just stuck with a screen full of GRUB).

I would like to know what I did wrong or what went wrong and how I can fix it. I would rather not reinstall Ubuntu.

Sorry if this is a common error or anything of the sort, I have been unable to trace through the wonder of Google other people with the same problem.

---

### Post by caljohnsmith on 2008-08-05
Sounds like it could be a hardware problem, but you could try reinstalling Grub to the MBR. Boot up a Live CD and do:
```
sudo grub
grub> find /boot/grub/stage1
[should return a partition (hd0,X), most likely (hd0,0)]
grub> root (hd0,X)
grub> setup (hd0)

```
Give that a shot and let me know if it helps. If not, you may have hardware problems.

---

### Post by lewdev on 2008-09-17
That helped me!  Thanks!  I was trying to install Puppy Linux 4.00 to the harddisk after partitioning using gParted.

---

