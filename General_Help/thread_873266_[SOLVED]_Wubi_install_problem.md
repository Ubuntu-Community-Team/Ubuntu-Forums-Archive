---
title: "[SOLVED] Wubi install problem"
date: 2008-07-28
forum: General Help
---

### Post by hansmax on 2008-07-28
I am trying to install Hardy Heron, (the 32-bit version) on a machine with a 64 bit AMD processor.  Perhaps that may be contributing to the problem I'm having, but I chose the 32-bit version because I have come across some advice while researching that stated that the 64bit version does not work as well because it is not as well developed as the 32-bit version.  I did have the 64 bit version installed, but uninstalled it because I didn't want to deal with any more problems than necessary at this point.  While it was installed I did very little with it.  I installed with Wubi.  The installation of the 32-bit version starts out OK, but stops with the error message:  "The download was interrupted with the error:"  That's all it says - no error message.  There is an Ubuntu folder on my C drive, but no files in the disk, boot, shared, docs, or grub folders, but there are files in the install folder.  I am running WindowsMediaCenter version.  Any thoughts would be appreciated.

---

### Post by Sef on 2008-07-29
Moved to Wubi forum.

> , but I chose the 32-bit version because I have come across some advice while researching that stated that the 64bit version does not work as well because it is not as well developed as the 32-bit version. I did have the 64 bit version installed, but uninstalled it because I didn't want to deal with any more problems than necessary at this point

Must have been either an old article or someone did not know what they were talking about.  64-bit works just fine.  I have no problems with it.  The only two programs that are needed by most people have ways of being installed:  see the 64-bit forum stickies for advice on installing flash and java.

---

### Post by hansmax on 2008-07-29
Thanks for the quick reply, Sef.  I found the advice in something called Linux Forums (blue penguin on the mast).  I think I will go with your advice and attempt to reinstall the 64-bit version.  I will post back.

---

### Post by hansmax on 2008-07-29
Well, I installed the 64bit version, and it seemed to install OK, then rebooted into Ubuntu, where it seemed to complete installing, but when it rebooted, the progress bar on the Ubuntu splash screen went up to about 70% and froze there.  I had to do a hard reboot to get out of it.  Offhand I can't really think of any way to troubleshoot this, unless the .iso I downloaded is corrupted in some way.  I seem to remember a free utility for checking .isos, but can't remember where I saw it.  Anybody have any ideas?

---

### Post by ago on 2008-07-30
> **hansmax said:**
> Well, I installed the 64bit version, and it seemed to install OK, then rebooted into Ubuntu, where it seemed to complete installing, but when it rebooted, the progress bar on the Ubuntu splash screen went up to about 70% and froze there.  I had to do a hard reboot to get out of it.  Offhand I can't really think of any way to troubleshoot this, unless the .iso I downloaded is corrupted in some way.  I seem to remember a free utility for checking .isos, but can't remember where I saw it.  Anybody have any ideas?

Press ESC at boot and go for rescue mode, at the very least it will show more info.

---

### Post by hansmax on 2008-07-30
It booted up in the recovery mode, and it booted up this time when I started it in regular mode.  That's the good news.  The bad news is that I can't log in.  I recall establishing a password when I did the Wubi installation, but I don't recall be asked to establish a user name.  I tried leaving it blank, but it gives me an "incorrect user name or password" error message.  Is there a generic user name that I should be using?

---

### Post by minhmeoke on 2008-07-31
Earlier versions of Wubi had a similar bug, but if you are using the latest version (8.04.1), then the installer should have prompted you for a user name if you left it empty. If the migration-assistant worked, then the user name should be the same as your windows user name.

Anyway, the default username and password in older versions were both "ubuntu". Are you using a non-us keyboard or special characters in the username or password? If the problem persists, contact ago or file a bug report.

---

### Post by hansmax on 2008-07-31
You are absolutely correct, minhmeoke, the user name was the same as my Windows user name.  I found this out the hard way, by uninstalling and reinstalling, but that's what I get for not paying attention the first time.  Thanks for the feedback, all. I will mark this solved, but I'm sure I will be back often.

---

