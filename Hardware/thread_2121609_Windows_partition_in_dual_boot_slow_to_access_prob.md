---
title: "Windows partition in dual boot slow to access problem"
date: 2013-03-02
forum: Hardware
---

### Post by Rgibbons on 2013-03-02
I have dual booting of Windows 7 and Ubuntu 12.04 on my HPMini. Both share the same "Documents" folder which resides on the Windows partition. The "Documents" folder is also linked to "Dropbox". I have the Windows partition set to auto mount on bootup into Ubuntu.

The problem: When I access a file directory in the Documents folder via the desktop or application (in Ubuntu), there is about a 5 second delay before the directory list will appear. It as if it is waiting for the Windows partition to spin up. This doesn't happen with I access a directory on the Ubuntu partition. Is "Dropbox" causing this? if not, what is?

---

### Post by Mark Phelps on 2013-03-02
> **Rgibbons said:**
> I have dual booting of Windows 7 and Ubuntu 12.04 on my HPMini. Both share the same "Documents" folder which resides on the Windows partition. 
BAD idea -- if this is the same partition in which Win7 is installed (not a data-only partition).  Making changes to files in a Win7 partition that also contains the OS runs the risk of rendering Win7 unbootable.  If you want to share files, you need to have a separate data-only partition.  

> I have the Windows partition set to auto mount on bootup into Ubuntu. Mounting read-only is OK; mounting a Windows OS partition read/write is asking for problems.

> The problem: When I access a file directory in the Documents folder via the desktop or application (in Ubuntu), there is about a 5 second delay before the directory list will appear. It as if it is waiting for the Windows partition to spin up. 
Drives spin-up;partitions do not (as you probably already know), and since this directory shares the same physical drive with the rest of the filesystems, the disk is running at a constant speed from when it first starts up. 
> This doesn't happen with I access a directory on the Ubuntu partition. Is "Dropbox" causing this? if not, what is?
My guess is that you're accessing it from "outside" Windows is giving the windows filesystem problems and it's doing some kind of internal consistency checks before it's letting you access the folder.

If you keep doing it this way, do not be surprised if one day, when you go to boot into Win7, you get a bluescreen, or the selection menu just sends you right back.

---

### Post by Rgibbons on 2013-03-02
Thanks for the valuable advice. That all makes sense.




> **Mark Phelps said:**
> BAD idea -- if this is the same partition in which Win7 is installed (not a data-only partition).  Making changes to files in a Win7 partition that also contains the OS runs the risk of rendering Win7 unbootable.  If you want to share files, you need to have a separate data-only partition.  

 Mounting read-only is OK; mounting a Windows OS partition read/write is asking for problems.


Drives spin-up;partitions do not (as you probably already know), and since this directory shares the same physical drive with the rest of the filesystems, the disk is running at a constant speed from when it first starts up. 

My guess is that you're accessing it from "outside" Windows is giving the windows filesystem problems and it's doing some kind of internal consistency checks before it's letting you access the folder.

If you keep doing it this way, do not be surprised if one day, when you go to boot into Win7, you get a bluescreen, or the selection menu just sends you right back.

---

