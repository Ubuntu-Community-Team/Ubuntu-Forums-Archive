---
title: "Swap to new 1 TB hard rive - How?"
date: 2008-10-19
forum: Hardware
---

### Post by Baloofalo on 2008-10-19
Bear with me, still trying to get my footing here and could not find anything on this. If there is another thread, just point me there.

I have been using Ubuntu for a little over a year. Using might be a little mis-leading, as will be my join date, since a friend help me set it up as a file server in the basement and I have had limited time to play with it.

I recently had my Windows XP hd crash and that, along with other issues, has me wanting to just switch to Ubuntu as my main OS. The only way I am going to learn it is to depend on it.:)  I took the drive from the server, put it in my old Windows machine, got it working, configured and email (evolution) going.

When I checked, the 250GB HD is at 70 + percent, so I want to swap out the drive to maybe one of the new 1TB drives. How can I do it? Would it be easier just to add it as a second drive and move files to it? The files I would be moving are those I sahre with the Win coms in the house using Samba.

Essentially, I just want to mirror the old to the new. In the Windows world, there were programs to do it. Here I am kind of lost. I am using eduubuntu (not sure how that happend) and will want to switch that at some point howeve rhtats for another thread.

---

### Post by phidia on 2008-10-19
To switch to Ubuntu from edubuntu you just need to change the repos and issue > sudo apt-get update && sudo apt-get upgrade

To move an install use "dd" (Check out "man dd" in a terminal)

The general command form is "dd if=/dev/hda of=/dev/hdb"
You will need to create a partition equal to or larger than the one you are copying, and you will need to edit /etc/fstab and /boot/grub/menu.lst.

There should be more specifics on doing that in the forums.

---

### Post by Baloofalo on 2008-10-19
> **phidia said:**
> To switch to Ubuntu from edubuntu you just need to change the repos and issue 


Remember, new guy. Where do I change the repos?

---

### Post by C.S.Cameron on 2008-10-19
Check Krupski here for dd:
[http://ubuntuforums.org/showthread.php?p=5983469#post5983469](http://ubuntuforums.org/showthread.php?p=5983469#post5983469)
To remove Edubuntu go to system' synaptic and find and un-check edubuntu-desktop.
You might end up with ubuntu-desktop already installed, if not install it from synaptic.
My advice would be to make a fresh install of 8.10 when it is released in a few days, or 8.04 now, if you can't wait.

---

