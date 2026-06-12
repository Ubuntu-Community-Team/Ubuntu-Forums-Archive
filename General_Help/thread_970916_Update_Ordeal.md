---
title: "Update Ordeal"
date: 2008-11-04
forum: General Help
---

### Post by Jesdisciple on 2008-11-04
After learning of Intrepid, I OKed the upgrade last night.  Today, as I began to use my laptop in parallel with the update, the update manager crashed.  I tried to complete the update, but the update manager was still running in the background.  I couldn't cut the power except by holding the button for 4 seconds.

When the computer restarted (which it did on its own), it was complaining about "Kernel panic" involving VFS and not being able to find the root fs.  I killed it and restarted, and tried the first (8.10, I guess) recovery mode.  It had the same complaint, so I restarted again and tried the second recovery mode.  It went through a long "update manager"-esque process in the shell, where a lot of stuff failed.

When it came out of the shell, it still couldn't update.  It told me to run "dpkg --configure a", but typing anything with the failed update manager still open made the terminal freeze.  I closed the update manager, tried again, got an error about package "a" not being found, and started the update manager again.  It's still running.

Throughout this ordeal, *About Ubuntu* hasn't known which Ubuntu I have.  Also, my clock doesn't know anything about timezones like it did before.  Finally, I got two crash report bubbles the last time I started up.  (I had previously installed KDE and quit using it due to several difficulties.)  The default summaries were:

* "package kmouth 4:3.5.10-0ubuntu1~hardy1 failed to install/upgrade: trying to overwrite `/usr/share/icons/mono/scalable/apps/kmouth.svgz', which is also in package kde-icons-mono"

* "package kttsd 4:3.5.10-0ubuntu1~hardy1 failed to install/upgrade: trying to overwrite `/usr/share/icons/hicolor/16x16/actions/nospeak.png', which is also in package kmouth".

What can I do to correct this?  Thanks!

---

### Post by wpshooter on 2008-11-04
My solution would be to make sure you install a SEPARATE /home directory the next time you install Ubuntu and then from now on when you want to upgrade your version of Ubuntu you do a fresh install from a burned Ubuntu CD and just leave your present /home directory intact.  But even at doing that I would not guarantee you that you would not have any problems after changing versions.  The only way to be fairly safe of getting a good working install is to WIPE the drive clean and do a fresh install of Ubuntu from scratch.

Thanks.

---

### Post by Jesdisciple on 2008-11-04
But can I fix the above problems in this install?

---

### Post by pschwarz on 2008-11-05
I have the same issue. I will let you know if I find a solution

---

### Post by pschwarz on 2008-11-05
Okay, I went to synaptic and remove kdeaccessibility (or whatever it is called)...it took out kde with it, but i believe that was kde3. I rebooted and everything was fine (rebooted to make sure kde was still working).

---

### Post by Jesdisciple on 2008-11-06
Precisely what problems did that fix for you, pschwarz?  I ripped out every trace of KDE I could find, then restarted, and nothing improved.

---

