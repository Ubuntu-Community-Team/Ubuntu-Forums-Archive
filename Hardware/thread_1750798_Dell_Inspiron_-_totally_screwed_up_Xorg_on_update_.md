---
title: "Dell Inspiron - totally screwed up Xorg on update to 11.04"
date: 2011-05-05
forum: Hardware
---

### Post by emmiesix on 2011-05-05
I had a very troublesome update to 11.04 (I had to kill it in the middle, which was a disaster, but through recovery disks and running in recovery mode I eventually got all the packages updated).

The remaining problem (I hope) is that I cannot get the desktop started.  I can start to the command line in recovery mode, but 'startx' gives driver errors.  I looked at /etc/X11/xorg.conf and there is almost nothing in it.

I tried to run 

sudo Xorg -configure

But I still get errors (I am typing these out on another computer):

(EE) module ABI major version (10) doesn't match server's version (8)
(EE) Failed to load module "intel" (module requirement mismatch, 0)

etc with other drivers.

So, any ideas on what to do ? I removed and re-installed xserver-xorg-video-intel... that didn't help.

What is wrong here?

---

### Post by emmiesix on 2011-05-05
I think I found a clue!

My xorg version is 1.09 .. odd, since I think Natty should default to 1.10??

---

### Post by emmiesix on 2011-05-05
well, I am trying to install xorg 1.10 (which maybe is stupid) and it's getting all kinds of errors for unmet dependencies.

I'm starting to think something is very broken somewhere in what my computer thinks is installed or is available.  It says that it is up to date and running 11.04, but that is clearly not the case. 

I checked my sources.list and everything looks good.

??

---

### Post by emmiesix on 2011-05-06
Well, I am going to keep updating...

I added the xorg-edgers ppa and did a dist-upgrade so now I should have the newest xorg.

The new hilarious problem? mouse doesn't work...

Maybe I should just go buy a mac.

---

### Post by emmiesix on 2011-05-06
In case anyone reads this in the wee hours of the morning with a burning desire to help...

I can now get the desktop started... sort of.  It is EXTREMELY slow to load (starts with ominous black screen).  I can launch things (thank god for gnome-do) and the keyboard works, but NOT the mouse.  

Where do I look for errors?  This looks awful and I really need this to start working so I can get back to work before my boss kills me...

---

### Post by mail4cm on 2011-05-06
I'd installed the fglrx again (I have Lenovo T500 + Mobility Radeon HD 3650)

```
sudo apt-get install fglrx
```that did the trick, but I don't think that everything works OK. Have problem with some 3D programs.

---

### Post by Novacaptain on 2011-05-06
I had problems with my upgrade too, but i think it's because of all the system settings and "fixes" that I had made while in 10.10 that didn't really work (or werent even needed) in 11.04. Have you tried 11.04 on a live CD? Does everything work there?

You can install fresh, but keeping your user files and programs. If in doubt, change your username during install to create a new /home/<username> directory and copy your old files into your new directory afterwards.

---

### Post by emmiesix on 2011-05-06
Thanks guys.

I ended up just doing a fresh install.  I had too much crap that wasn't working and it wasn't worth figuring out.  But at least the /home and data partitions were easy to remount afterwards - not stupid copying back and forth!

---

