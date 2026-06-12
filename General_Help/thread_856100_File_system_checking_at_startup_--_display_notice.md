---
title: "File system checking at startup -- display notice?"
date: 2008-07-11
forum: General Help
---

### Post by dansan on 2008-07-11
I'm still fairly new to Ubuntu (Gutsy - Ubuntu Studio), so I don't know where to post this question: 

When Linux does file system checking at startup, how can I display text like "33 startups without checking file systems -- now checking" to let me know that startup is working normally and not hung up? If I have been making changes, like adding a drive to fstab, it's easy to think something is wrong when startup black screen goes on longer than usual, so a message like the above would be useful. 

Hardy, which I set up on my laptop, displays such a message, so I know it's possible. Could someone tell me how to do this in Gutsy?

---

### Post by vanadium on 2008-07-11
For me in Gutsy, the system would switch to displaying a text console when there was an extended file check. It is only since hardy that the output is being directed to the graphical boot-up splash screen.

---

### Post by ajgreeny on 2008-07-11
Mine did the same as vanadium's machine and automatically switched to a text console when fsck was in progress.  Does your machine use the usplash normally at boot time, ie the growing orange bar with the word "ubuntu" above?  If so I think you will also get the same effect when fsck comes into life.

The same happens in Hardy as well, though the display is different now and does not tell me at the end how much the system is affected by non-contiguous files.  It just says "OK" now, whereas it used to say "x% non-contiguous".  Just out of interest, does anyone know if there any way now to still see that figure?  Just curious.

Just for information, there is a useful cli utility that allows you to see and change file system parameters called tune2fs.  You can change filesystem items such as boot number count before fsck.
examples:
sudo tune2fs -c60 /dev/hda2             will check hda2 every 60 mounts.
sudo tune2fs -l /dev/hda2                  will show all the file system item details for that partition.

---

### Post by dansan on 2008-07-11
First, thanks to vanadium for telling about regular Ubuntu.

> **ajgreeny said:**
> Mine did the same as vanadium's machine and automatically switched to a text console when fsck was in progress.  Does your machine use the usplash normally at boot time, ie the growing orange bar with the word "ubuntu" above?

No, I get the Ubuntu Studio splash screen, and it tells me nothing about what's going on after its progress bar completes. If I could get text to appear about file system checking being in progress, that would be enough to tell me that Ubuntu hasn't derailed during startup. I hope somebody out there can tell how to do this.  

> **ajgreeny said:**
> Just for information, there is a useful cli utility that allows you to see and change file system parameters called tune2fs.  You can change filesystem items such as boot number count before fsck.
examples:
sudo tune2fs -c60 /dev/hda2             will check hda2 every 60 mounts.
sudo tune2fs -l /dev/hda2                  will show all the file system item details for that partition.

Thanks for the tip.

---

### Post by vanadium on 2008-07-11
> I hope somebody out there can tell how to do this.
I believe that you can switch to the first console to see the messages during boot up. Thus, if it takes a while, you should press Ctl+Alt+F1. Ctrl+Alt+F7 brings you back to the splash screen. As soon as the login screen appears, you will automatically switch back to the graphical screen.

---

### Post by drs305 on 2008-07-11
There is also an app called *autofsck* that can run on shutdown instead of on boot. The advantage being that you can let it run when you don't need your computer rather than when you might want to log on quickly. It may display what you are looking for as well as having the advantage of checking at shutdown.

Autofsck:
[https://wiki.ubuntu.com/AutoFsck/Doc](https://wiki.ubuntu.com/AutoFsck/Doc)

To download the .deb:
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

