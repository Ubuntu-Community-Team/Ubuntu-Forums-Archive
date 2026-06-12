---
title: "Delete file from QNAP NAS bypasses Trash Can Bug, anyone else have this Bug?"
date: 2019-03-29
forum: Hardware
---

### Post by jeff-myremoteaccess on 2019-03-29
I have a QNAP TS-653A. 

Running Ubuntu Mate with Cinnamon using AMD Threadripper with 16 GB RAM.

This issue started about a year ago, I was running Manjaro and after a firmware update, every time I deleted a file, it asked if I wanted to permanently delete it, I made this thread: [https://forum.manjaro.org/t/trash-not-working-on-nas/73921](https://forum.manjaro.org/t/trash-not-working-on-nas/73921)

Long story but as you might know, I left Ubuntu because of issues with NVIDIA Driver, and other open issues I left on this forum, to use Arch Linux, trust when I say I left because I was upset over the way NVIDIA drivers were handled, and I love the way they are handled now, so glad to be back, but Arch Linux turned out was not very stable, and never will be by design, so I switched to Manjaro, after this issue I switched to LMDE, where it worked, but Felgo would not run, so I switched back to Ubuntu, did not find Cinnamon, so I used Mate and installed Cinnamon on it, I like Mate, but I Love Cinnamon, where I got NVIDIA to work, so I am happy with Ubuntu, and happy to be back, but still have this problem, but in all fairness, this turned out to be not an Arch Linux Manjaro Bug, since it also effects Ubuntu now.

I have been working on this issue since that time, and working with QNAP support, which has been good, they confirmed the bug in Manjaro, so I switched, but now I think I know what is going on, I think it has to do with the drivers in the OS and firmware on the QNAP, I believe that this is a bug on QNAP side, I have 3 other NAS's that do not have this issue, so I think it has to do with the fact that LMDE uses a stable version of Debian, and stable really means old, so when they update, this bug will then affect it, so it only works on LMDE till that time.

To reproduce this Bug, make sure Samba and NFS is installed, since you need to have a QNAP NAS, those will already be installed, so just try to delete a file and see where it goes, if it gives you that message it cannot move it to the trash can, then you have the bug, and it does not matter if you use Samba or NFS to delete it.

Do not get confused with the Recycle bin in QNAP, as far as I can tell, it is only used by the internal File manager in QNAP, it is an App, as this NAS has all kinds of apps and multimedia type fancy stuff, I never use, QNAP support keeps confusing the two and that gets old, they state that Recycle bin is not support under NFS, who cares, if it is working it will go to the trash can.

.Trash-100 has the correct permissions, on LMDE I can move the trash can to trash, and see the .Trash-1000 in the trash can, I can not do that in Ubuntu, and like I said, I am sure other distributions have this same bug,  and it only effects QNAP NAS drives, not my Dlink NAS drives, so this bug is unique to QNAP.

I do not believe this has anything to do with how you setup NFS or Samba, I always took the default install and it worked prior to 1 year ago.

I have changed my permissions on the drive and exhausted all of QNAP's support efforts, so I am at a stand still, I can not delete files from Ubuntu without bypassing the Trash can.

All I really want from others is to determine if this bug exists on Ubuntu, which QNAP has confirmed it exists on Manjaro, and I requested they confirm it on Ubuntu, but I also want to know if it exists on other QNAP NAS's, and how many people are effected by this bug. 

I ask that this Bug be tracked so that all QNAP users can be informed about this Bug, but I have no idea how to make this happens, so I need help to get this Bug Check out to all QNAP users, since this Bug may affect all of QNAP's NAS drives as far as I know, but I can only test this one, and I did some googling and did not find many people reporting his Bug, my guess is that they just do not care it bypasses the Trash Can, and I do.

Thanks

---

### Post by TheFu on 2019-03-29
Nobody here works for Canonical. 

I wouldn't expect the Trash to work across file systems, ever. I would consider that a huge bug. Imagine everyone with a NAS deleting thousands of files on the NAS, but having those all be moved to ~/.local/share/Trash/ , filling up their HOME.

Most GUI file managers have an option for **not** using trash.  You can use any file manager you like. Perhaps there is one that works the way you like?  caja has a preference in the "Behavior" tab that says, "include a delete command that bypasses Trash"  If it didn't work correctly, that would be a bug against caja, not the OS.  I don't see what any storage or driver would have to do with any of this.  But perhaps I'm missing something. Happens all the time.

To file an ubuntu bug: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

We are just volunteers here.

---

### Post by jeff-myremoteaccess on 2019-03-29
This is a Bug that only effects QNAP NAS drives, it does not effect my other NAS drives, and it has nothing to do with the file manager, it does not matter how you delete the file, it always bypasses the trash can, and so far this bug does not effect LMDE, it works fine, but one day they will upgrade to the same code that is causing this bug, then it i will not work on any Debian OS, this bug affects Arch Linux Manjaro as well.

All I ask is that other QNAP users need to know about this bug, and report it, I reported it here and at Manjaro, and QNAP, and will report it to the link provided, but I have no way of knowing what is causing this bug, I just know it is now a confirmed bug that only effects QNAP NAS drives.

---

### Post by TheFu on 2019-03-29
Shell commands, like rm, mv, rmdir, don't pay any attention to GUI settings, like the Trash.  Just discovered a package called trash-cli which is supposed to move files to the trash directory (I suppose).  [https://www.tecmint.com/trash-cli-manage-linux-trash-from-command-line/](https://www.tecmint.com/trash-cli-manage-linux-trash-from-command-line/) has lots of details.

[https://specifications.freedesktop.org/trash-spec/trashspec-1.0.html](https://specifications.freedesktop.org/trash-spec/trashspec-1.0.html) is the specification for how Trash should be handled. You've probably already read this.

> 
The implementation MAY also support trashing files from the rest of the system (including other partitions, shared network resources, and removable devices) into the &#8220;home trash&#8221; directory . This is a &#8220;failsafe&#8221; method: trashing works for all file locations, the user can not fill up any space except the home directory, and as other users generally do not have access to it, no security issues arise.

However, this solution leads to costly file copying (between partitions, over the network, from a removable device, etc.) A delay instead of a quick &#8220;delete&#8221; operation can be unpleasant to users.

**An implementation MAY choose not to support trashing in** some of these cases (notably on network resources and removable devices). This is what some well known operating systems do.

I'm more lost than ever, but that isn't important provided others understand.

---

