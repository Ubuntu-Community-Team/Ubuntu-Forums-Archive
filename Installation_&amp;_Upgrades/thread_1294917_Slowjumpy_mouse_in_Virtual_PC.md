---
title: "Slow/jumpy mouse in Virtual PC"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by B-Navigator on 2009-10-18
Ok, I recently decided to test installing Ubuntu 9.10 beta in Virtual PC 2007.  After searching a bit, I found and used the video fix to install it ... And the mouse works badly. Specifically it is VERY slow when moving across the window, forcing me to lift and reposition the mouse six times to move it a distance I could normally cover with one motion of my hand.  Plus sometimes the cursor will abruptly 'jump' to one edge or corner of the screen, often in the oppose direction that I was trying to mouse. Other than the mouse problem, Ubuntu seems to be working just fine

---

### Post by earthpigg on 2009-10-18
This is intentional on the part of Microsoft, to discourage the use of Free Software.

I suggest using this instead:
[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

---

### Post by B-Navigator on 2009-10-19
> **earthpigg said:**
> This is intentional on the part of Microsoft, to discourage the use of Free Software.

I suggest using this instead:
[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

Tried it, the mouse is faster, but the jumping problem is still there.  I can't tell if it's worst or if the faster mouse just make it seem that way.

---

### Post by earthpigg on 2009-10-19
> **B-Navigator said:**
> Tried it, the mouse is faster, but the jumping problem is still there.  I can't tell if it's worst or if the faster mouse just make it seem that way.

did you install the guest additions? the low-level stuff that it adds is what makes vbox great. it's probably the same on the windows version of vbox: machine -> install guest additions.

machine -> install guest additions will conjure a virtual CD in the ubuntu guest/virtual machine. the virtual cd has an installer that needs to be run as root in the guest machine. in the ubuntu virtual machine run 'sudo nautilus', navigate to the virtual CD, and run the script for the correct architecture of the guest operating system... x86 for 32 bit ubuntu, x86-64

those make a huge difference across the board. make sure you read what it is telling you during this process :D

don't expect the guest additions installer to work right the first time. it will likely tell you that you are missing stuff. add it, and try again. it will... probably something like this (from [here]("http://sites.google.com/site/masonux/home/notes-to-myself#TOC-Setup-vbox-to-share-folders")):

```
sudo apt-get install make gcc
```

then install the 'headers' for the kernel. run this to find your kernel:
```
uname -a
```
and look for your kernel version. once you find it, run

```
sudo apt-get install linux-headers-2.6.***28-15-generic***
```

except replace .28-15-generic with whatever uname -a gives you.

whenever you update the ubuntu linux kernel, you will need to find the kernel you are using and update the headers again.

if the installer still doesn't work, let us know.


is it a bit involved? yes. 

why doesn't virtual box automate the stuff above? because every operating system has a slightly different process, so there can be no 'one size fits all' solution. i carefully read through all the guest additions stuff myself and figured it out.

once you are all set up, you should be able to share folders between ubuntu -> windows, resize the ubuntu virtual machine's window and have the virtual machine update its resolution accordingly, get the sexy desktop cube stuff, and play 3d video games in ubuntu (with not-to-great performance), and your mouse will not only be smooth but it will be integrated into your windows desktop.

---

