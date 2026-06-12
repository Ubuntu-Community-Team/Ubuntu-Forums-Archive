---
title: "Missing cdrom drive in /dev"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by midfel11 on 2009-04-27
I just installed Kubuntu for the first time (switched over from Gentoo) and everything seems to have gone very smooth except I just noticed that I am missing my cdrom.  I went to mount it and noticed that I don't even see it in /dev (as /dev/hda as it was under Gentoo, or /dev/cdrom).  I installed from the cdrom so I'm assuming that ubuntu should recognize it (it's a Sony DVD-RW from only about 3 years ago).  Any ideas on how to get it to show up?  Thanks!

And I do have to say that the GUI really does look very polished and flows nice - great job to the developers on that!

---

### Post by 123456789123456789123456 on 2009-04-27
you said you went to mount, did you incert a cd, and try mounting the drive?

---

### Post by midfel11 on 2009-04-28
Yes I did put in a cd but don't even see a device in /dev to try and mount.

---

### Post by unutbu on 2009-04-28
Do you have /dev/scd0?
/dev/cdrom is sometimes a symlink to /dev/scd0.

---

### Post by midfel11 on 2009-04-28
No, I don't have /dev/scd* either.

---

### Post by unutbu on 2009-04-28
What is the output of 

```
sudo lshw -C disk
```

---

### Post by midfel11 on 2009-04-28
Solved this...

I swapped the boot order of my hard drives since I wanted to install on a different drive than I had before.  And somehow I managed to move the CDROM after the boot of the hard drives.  So I think my BIOS was hiding it from ubuntu.  Thanks for the suggestions!  I also never knew about that lshw command - good to know. :)

---

