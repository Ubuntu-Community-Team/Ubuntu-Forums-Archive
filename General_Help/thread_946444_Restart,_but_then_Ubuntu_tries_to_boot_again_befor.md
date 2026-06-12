---
title: "Restart, but then Ubuntu tries to boot again before ever getting the Grub menu"
date: 2008-10-13
forum: General Help
---

### Post by jasper.davidson on 2008-10-13
I have a really strange problem. Ubuntu 8.04 was working fine up until a few days ago, but now when I try to do a "restart" from the shutdown menu, I get the usual Ubuntu "decreasing" progress bar showing Ubuntu is shutting down, but then right at the point where the progress bar reaches zero and my computer should restart, Ubuntu tries to boot again! :confused: I get the oscillating progress bar followed by the progress bar showing that Ubuntu is trying to boot again, and finally Ubuntu freezes. But never do I get back to Grub on start up, and of course I don't see my usual BIOS screen flash on either (which is what normally happens on start up). 

Any ideas of how to troubleshoot this? Thanks in advance.

---

### Post by geirha on 2008-10-13
Sounds like the runlevels are messed up somehow. Have you run any update-rc.d-commands lately? made symlinks in /etc/rc.* folders? Done any changes on files in /etc/event.d/ ?

---

### Post by jasper.davidson on 2008-10-13
Nope, haven't messed with any run level stuff. The only thing I can think of is a few of my packages were updated by the automatic updater around the time I noticed this. Is there somewhere I can find out what packages were recently updated? Maybe that would give a clue.

---

### Post by geirha on 2008-10-13
There's probably an apt command that will generate a list of newly installed packages, but I don't know it at any rate. You might get a fair overview by doing ```
ls -ltr /var/cache/apt/archives
``` which should show you the dates the packages were downloaded (sorted by date)

And you can look at the changelog for a specific package with ```
aptitude changelog *packagename*
```

---

