---
title: "Upgrade problem, 8.04 to 8.10"
date: 2008-10-31
forum: General Help
---

### Post by soylentjosh on 2008-10-31
I just tried to upgrade to Intrepid from Hardy as per the instructions at:

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

The upgrade process seemed to go smoothly, but after it rebooted, all I get is a shell prompt.  It's not booting into the gnome desktop, and I don't know how to get to it.  Forgive me if the answer to this is obvious; I am relatively new to Ubuntu.  Thanks for your help!

soylentjosh

---

### Post by tbugge on 2008-10-31
hey

I got the same problem. The only option is to type in my username and following password. I get the message "unable to start up gnome-desktop" or something like that.

I could need som help too!

---

### Post by mikprice on 2008-10-31
Hi

I had the same problem. I edited /etc/X11/xorg.conf and removed any references to a second screen I had. I was then able to startx.

Now I have the problem of getting the second screen to work properly.

---

### Post by soylentjosh on 2008-10-31
I do have a dual monitor setup (NVDIA 8500 video card); I experimented with xorg.conf, commenting out things that (I thought) had to do with the dual monitor setup, but what I did didn't seem to work; I ended up returning it to how I had it.  Any ideas?

---

