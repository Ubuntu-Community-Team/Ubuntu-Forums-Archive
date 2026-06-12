---
title: "[SOLVED] rsync memory usage"
date: 2008-08-30
forum: General Help
---

### Post by infraction on 2008-08-30
Hello...I use rsync as my backup tool to backup my machine to an external drive.  Here is my command line.....

sudo rsync --force --ignore-errors --delete --delete-excluded --exclude-from=/media/disk/UbuBackup-exclude.txt --backup --backup-dir=`date +%Y-%m-%d` -av / /media/disk/RsyncBackup

I am seeing rsync claim and use memory during its run, but it is not releasing the memory when it is finished.  That is not really a big deal, but it is annoying and I'd like to stop it if I can.  

Have I missed a parameter or something??  I've been through the man page to no avail.

Any help is greatly appreciated...thank you in advance.

---

### Post by infraction on 2008-09-11
Never mind.  No replies after a week.  Forget it...I'll just live with it.

---

### Post by bingoUV on 2008-09-11
> **infraction said:**
> 
I am seeing rsync claim and use memory during its run

Where are you seeing this? 
1. Gnome System monitor?
2. top?

Run 'top' in a terminal, press shift+m, and copy whatever is shown on the screen. Post this here.

top is like a command line system monitor, and shift+m sorts processes with the highest memory consumer at the top.

---

### Post by infraction on 2008-09-18
Thank you for your interest, but this is really pointless.  I'm getting my information from a Conky display that I assume is correct.  TOP does not really tell anything worthwhile.  Maybe I'm just seeing a Conky anomaly here.  Let's just let it go....my problem.  Again, thanks.

---

