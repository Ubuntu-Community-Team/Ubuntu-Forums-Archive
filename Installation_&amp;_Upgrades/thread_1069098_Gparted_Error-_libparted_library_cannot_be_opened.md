---
title: "Gparted Error- libparted library cannot be opened"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by blue_bullet on 2009-02-13
I am having a problem with Gparted.  I have completely removed it via Synaptic then reinstalled it.  I still get the same error when I issue the command
"sudo gparted" from a terminal window.

Error is:
gparted: error while loading shared libraries: libparted-1.7.so.1: cannot open shared object file: No such file or directory
 
Can anyone help me with this?  I want to reformat an external hard drive for backups.

---

### Post by Taemojitsu on 2009-02-13
have you tried also reinstalling libparted if it's a package?

if you wanted to be lazy, you could always just create a LiveUSB, which has lots of handy utility including Gparted :&#8203;P (it is possible to 'break' a LiveUSB if it's persistent and you mess it up accidentally, but that usually won't happen!)

---

### Post by blue_bullet on 2009-02-14
Thank you for the suggestion.

The libparted package in question is not offered via Synaptic.  I created a live CD and will either use that to reformat my new external hd or one of my other machines where Gparted is not broken.  From what I could find out via Googling the error this was reported as a bug back in August of last year.  The person responsible for fixing the error closed it saying the Libparted source simply had not hit all the mirror sites yet.  Right.  I believe in general it is not a good idea to depart from official Ubuntu offerings such as those in Synaptic so I did not pursue getting 1.7 from the GNU site.  I believe 1.8 is what is current in Synaptic.  I don't even know how Gparted got broken on only one of my 3 machines.  All 3 are kept current with updates.  It is a bit disconcerting the Gparted cannot be successfully reinstalled. 

Just like the guy at GNU consider the problem closed (solved).

---

