---
title: "fs-driver for Windows problem"
date: 2008-08-13
forum: General Help
---

### Post by emptybox on 2008-08-13
I have a computer dual-booting Ubuntu 8.04 and Windows XP SP3.
These are on seperate hard drives, and I use the ntfs driver in Ubuntu to mount and access the Windows drive.

In Windows I have been using the ext2 driver from [_here_]("http://www.fs-driver.org/index.html") to access the Linux (ext3) drive and have it show up in My Computer.
This has worked fine until last night when some new updates from WU were installed (may or may not be a coincidence?).

This morning I found my Windows XP was giving me blue screen errors about 2 minutes after booting to the desktop. The codes suggested a driver problem. It did this every time I restarted.

Booting into Ubuntu gave no problems except that it insisted on checking the hard drive because of an "Unclean shutdown". Also I noticed that it would no longer mount the Windows drive.
This gave me the idea that it might be connected to the fs-driver in Windows.

I booted up Windows again and tried to do a system restore, but it blue screened before I had a chance. I then tried to uninstall the ext2 driver, and that partially uninstalled before the computer blue screened.
I restarted into Windows again, and this time I had no errors and the computer works fine except that I can no longer see the Linux drive. In 'set program access and defaults' the ext2 driver is still listed, but if I click on the remove button it gives me an error message, so obviously the driver is now not working, but is still there in part.

In Ubuntu I can now mount and access the Windows drive again.

I might try reinstalling the fs-driver later to see if the blue screen errors reoccur, but it's not critical for me to be able to access the Linux drive from Windows, but it would be useful.

Has anyone else experienced the same problem?
If so is it down to the driver being incompatible with a specific Windows Update, or do you think that is just a coincidence, and it is the fs-driver that is faulty?

---

### Post by emptybox on 2008-08-13
As an update to this, I have tried reinstalling the ext2 driver from the installer file on my computer, i.e I didn't download afresh, and the system all seems to be be working again. The driver is working and I haven't had any blue screen errors (not yet anyway).

It seems that it was a corrupted driver rather than anything to do with the Windows Update that was installed the night before (KB 951066).

If I get no more problems after a few hours of working I will come back and mark this solved.
Unless anyone is having similar problems?

---

### Post by alien013 on 2008-11-01
I have the same problem. Whenever I update Vista it does not boot and I got blue screen. Because of that reason i dont update my windows for now.. 
I am using Kubuntu Intrepid and Vista dual boot. On the other hand, every time after using Windows, Kubuntu wants to check drivers due to "unclean shutdown" without asking if I want to cancel..

what can I do ?? I want to be able to read ext2 partition from Vista and I dont want to give up from Kubuntu. :)

---

### Post by emptybox on 2009-02-13
Sorry to bump an old thread.
Just to say I continue to have problems every month when Windows updates.

I have tried redownloading the fs-driver from the site, and it's just the same. If I leave the driver active and try to install any Windows Updates, then I get blue screen problems.

The only conlusion I can come to is that this driver is incompatible in some way with Windows updates,
It doesn't happen when any other software updates.

My solution, is when I'm told Windows has updates to install, I uninstall the ext2 driver, then I install the updates, then I reinstall the driver.
This works, but is a bit of a faff.

---

### Post by HermanAB on 2009-02-13
Don't fix it if it ain't broke...

If Windows works and it is behind a separate firewall, and you don't use it much, disable the updates.

Cheers,

Herman

---

