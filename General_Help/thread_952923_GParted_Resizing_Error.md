---
title: "GParted Resizing Error"
date: 2008-10-19
forum: General Help
---

### Post by sirdouglas on 2008-10-19
I have still been messing with my new Ubuntu over the weekend, but will need to install XP or Vista along with it to access some programs.  Unfortunately, the process is not going smoothly.  Using GParted after booting up my live CD of Ubuntu Ultimate 1.4, I unmount the primary partition and resize it (hoping to create an extra 10gb partition), but after applying, an error always appears: "an error occurred while applying the operations."  

Any ideas?

Thanks once again,

Doug

---

### Post by Elfy on 2008-10-20
When you try to do the resize is the swap mounted, the livecd will use the swap that was created during the ubuntu install.

All the drives need to be unmounted, right click on the swpa partition and unmount it, then try again.

Is there an exclamation mark in a triangle against the partitions - would indicate there might be a problem, lastly does the install boot properly?

---

### Post by eohalloran on 2008-11-10
sirdouglas, I too had that problem and disscovered that it was a Windows problem  Try booting into Windows first and from a run command try running chkdsk /f.  Let Check Disk resolve the Windows issues and then hopefully you should be able to partition your drive

---

