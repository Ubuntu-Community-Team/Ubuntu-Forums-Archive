---
title: "gam_server partial fix"
date: 2005-11-30
forum: General Help
---

### Post by jjmckay on 2005-11-30
I installed kUbuntu 5.10 today and it works fine except that after mounting four large NTFS partitions my cpu was at %10 utilizaiton (mostly from gam_server) and KDE was subsequently sluggish and jerky. 

**UPDATE: my steps below didn't fix the issue!!  Now it's consuming %40 cpu.

I found the resolution is to make a file in my home directory called .gaminrc and put the following entry in it:

fsset ntfs none

That is the only uncommented line I have in the file.  It tells gam_server to not monitor any ntfs volumes (which I mount as read only anyway) for changes, etc. Alternatively, I could put the above line in a file at /etc/gamin/gaminrc  to make it universal across all users.

I found the documentation on the gamin home page at [http://www.gnome.org/~veillard/gamin/](http://www.gnome.org/~veillard/gamin/)  to be quite unsatisfactory yet I guessed that 'ntfs' was what I needed to enter on the fsset line.  It seemed to work.  *shrug*

Before I found this solution and with some work (compile erorrs and *no* gcc installed by default in kUbuntu!!), I got a successfull compile of the latest gam_server (0.1.7 seems to be two revisions newer than the one that comes with kUbuntu 5.10) but 'make install' didn't install it at all.  The old gam_server file was still in /usr/lib/gamin/gam_server and I don't know how or where the gam_server is called (by kde?).  I can find nothing in the kUbuntu GUI or command line as from where gam_server is loaded..

If anyone has some advice on how to activate or link gam_server to the one I compiled I would greatly appreciate it.  Thank you.

I hope this helps anyone else with that blasted gamin thing.

JJ
ps.
This was my primary unpleasant experience with kUbuntu.  Otherwise it's a nice distro and I was able to upgrade it to KDE 3.5 without much difficulty.

---

