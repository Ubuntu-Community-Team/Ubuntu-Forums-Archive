---
title: "Can't boot to Windows after installing wubi &amp; Ubuntu - but Ubuntu works!"
date: 2008-10-18
forum: General Help
---

### Post by crashtest on 2008-10-18
Strange problem here.  I had Windows XP Pro installed on a Lenovo T61 notebook.  Installed wubi and Ubuntu 8.04 - everything worked properly.  Did a dist-upgrade to Ubuntu 8.10 which also worked properly.  The first time I tried to boot into Windows it failed - simply loops back to the Lenovo splash screen and starts to boot again.  No options for Windows work - Last Known good configuration, Safe Mode, Safe Mode with command prompt - nothing works and there is no error message - BUT - booting into Ubuntu does work!

From within Ubuntu I can browse down through /host and see all the Windows files, and I can even execute programs using Wine.

I thought I might have some file corruption somewhere in the NTFS filesystem, so I tried to boot from a Windows CD, and use the recovery console, but recovery console claims it cannot find an attached hard drive!

So... the boot loader works for Ubuntu, which is running out of the NTFS partition, so none of this makes any sense to me.  How can I repair the situation and get Windows back?  Thanks in advance for any help.

---

### Post by ago on 2008-10-18
In the recovery console can you get to the shell? From there you should be able to run chkdsk /r

---

### Post by crashtest on 2008-10-18
No - recovery console fails to start with an error message saying that no hard disk has been found.

Very strange problem, but not to worry.  I've reinstalled with the whole drive given to Ubuntu, and I'm installing a virtual windows machine using VirtualBox.  I think this is a better solution (for me) because 95% of what I do is in Linux, and I can now access Windows for the other 5% of tasks without rebooting.

---

### Post by ago on 2008-10-20
Very good choice ;)

---

