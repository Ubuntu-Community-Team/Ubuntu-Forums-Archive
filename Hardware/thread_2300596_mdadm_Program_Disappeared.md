---
title: "mdadm Program Disappeared"
date: 2015-10-26
forum: Hardware
---

### Post by cobalt2 on 2015-10-26
I'm in Ubuntu 14.04 live CD mode, and when I use mdadm to create an RAID array, Terminal says:
```
The program 'mdadm' is currently not installed. You can install it by typing:
sudo apt-get install mdadm
```
When I attempt to install it, apt-get shows me the wrong mdadm.
How to get the mdadm --assemble that I'm looking for?

---

### Post by weatherman2 on 2015-10-27
A live CD will lose all state after you shut down - there is no way to save any of the work/installations that you did.  If you use a live USB boot, there is a way to configure it to save some of the things you did.

Why are you using a live CD if you are also making a RAID?  Are you going to install Ubuntu for real?

---

### Post by cobalt2 on 2015-10-28
I did not need to install mdadm because it was already installed. Then I  restarted my computer, and it disappeared ever since. When I type  apt-get install mdadm, instead of showing me the RAID package, it shows  me something else. I am using the Ubuntu 14.04  LIve CD in order to  install the GRUB on a fakeRAID SSD. I tried to install the GRUB to my  SSD using the Lubuntu 15.10 Alternate Installation installer. The GRUB  installation appeared to be successful, however when I restarted my  computer, I got an error message:
```
Disk read error. Press Ctrl+Alt+Delete to restart.
```
Now I need mdadm in order to assemble the RAID arrays in Ubuntu 14.04  Live CD. It is not installed by default. When I try to install  mdadm with apt-get install mdadm, instead of offering me the mdadm for  Linux Software RAID, it offers something else. How to install mdadm in  Ubuntu 14.04 Live?

---

### Post by weatherman2 on 2015-10-28
From your other post, it seems you were using both Lubuntu 15.10 and Ubuntu 14.02.2 ?

I don't understand why mdadm would install the first time you boot a live CD then not the next time on exactly the same CD, but of course the two different versions of Ubuntu might have different things installed by default.

You might need to enable the "universe" repository on a live CD o be able to install mdadm - just a guess.

---

### Post by cobalt2 on 2015-10-28
> From your other post, it seems you were using both Lubuntu 15.10 and Ubuntu 14.02.2?
When the the Lubuntu 15.10 installer failed to install the GRUB, I switched to using Ubuntu 14.04 Live in order to fix it.

Edit: I tried enabling the main, universe, restricted and multiverse repositories to no avail. 

Any help with getting mdadm installed is very appreciated.

---

