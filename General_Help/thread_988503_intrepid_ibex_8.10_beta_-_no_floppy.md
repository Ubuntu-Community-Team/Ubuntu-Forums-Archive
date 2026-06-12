---
title: "intrepid ibex 8.10 beta - no floppy?"
date: 2008-11-20
forum: General Help
---

### Post by Hawk__0 on 2008-11-20
I started out this installation of ubuntu with the intrepid beta.  I have no /dev/fd0.  instead I have /dev/fd/#, where # is numbers 0-6.  I have no entry in /etc/fstab for a floppy drive.  How can I get my floppy to work???

---

### Post by plucky on 2008-11-20
> **Hawk__0 said:**
> I started out this installation of ubuntu with the intrepid beta.  I have no /dev/fd0.  instead I have /dev/fd/#, where # is numbers 0-6.  I have no entry in /etc/fstab for a floppy drive.  How can I get my floppy to work???

See this [thread](http://ubuntuforums.org/showthread.php?p=6185315&highlight=floppy#post6185315)

Good Luck

---

### Post by Hawk__0 on 2008-11-20
Thanks! ```
modprobe floppy
``` did the trick!!

---

### Post by plucky on 2008-11-20
> Re: intrepid ibex 8.10 beta - no floppy?
Thanks!
Code:

modprobe floppy

did the trick!! 

It will disappear again after you reboot.To make it appear after every reboot you need to ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a new line.


Good Luck

Please mark the thread as [color=red]Solved[/color] if you consider it solved.

---

### Post by timfrost on 2008-12-01
This issue, and solution, also applies for upgrades from hardy to intrepid release.

After a reboot, I was able to attach the floppy to a VM. So thanks to plucky for the reminder to add the entry to /etc/modules, and to Hawk__0 for the run-time solution

---

