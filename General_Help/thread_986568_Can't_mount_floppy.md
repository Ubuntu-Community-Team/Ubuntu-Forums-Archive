---
title: "Can't mount floppy"
date: 2008-11-18
forum: General Help
---

### Post by Russty of Oz on 2008-11-18
I am trying to get Kubuntu 8.10 to read a floppy disk but nothing at all happens.

I have installed fdutils which is suppose to automatically mount and unmount the floppy drive but nothing happens when I put a disk in and when I look in Media there is only the CD drive.  I have also added Floppy in the user group.

Can anyone help?

Russty

---

### Post by rbc on 2008-11-18
I have read quite a few posts about this after upgrading to Intrepid, and the answer was this, although this may or may not be your problem: in terminal, run sudo modprobe floppy. You would probably know better than I why this is, but supposedly this is only a temporary fix. For a permanent solution, add the word "floppy" (without the quotes) to the /etc/modules file.

---

### Post by Dr Small on 2008-11-18
> **rbc said:**
> I have read quite a few posts about this after upgrading to Intrepid, and the answer was this, although this may or may not be your problem: in terminal, run sudo modprobe floppy. You would probably know better than I why this is, but supposedly this is only a temporary fix. For a permanent solution, add the word "floppy" (without the quotes) to the /etc/modules file.
Yeah, here's the thread for reference:
[http://ubuntuforums.org/showthread.php?p=6185315&highlight=floppy#post6185315](http://ubuntuforums.org/showthread.php?p=6185315&highlight=floppy#post6185315)

---

### Post by Russty of Oz on 2008-11-18
Thanks guys, now the floppy drive shows up.

Russty:)

---

