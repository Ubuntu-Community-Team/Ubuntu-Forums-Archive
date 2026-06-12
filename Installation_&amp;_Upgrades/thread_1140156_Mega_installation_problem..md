---
title: "Mega installation problem."
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by HybridWarrior on 2009-04-27
Hi all,
I recently attempted to install ubuntu 8.10 onto my sony vaio laptop after the windows vista broke down. During the installation i did a complete format and deleted vista, i'm fine with that. However the installation then failed while it was at 5% creating ext3 file!
I then went on to do a manual installation, deleting partitions ect.. and just about every other option the installer has and each time the installation would freeze at 5% when its trying to create ext3 file, sometimes the mouse and keyboard even become unresponsive.

I've installed ubuntu from the same disk successfully onto my much older tower computer with no problems, however that computer is currently not working either so as you can imagine im pretty desperate to get my laptop up and running again, any help anyone could offer would be very much appreciated!

---

### Post by Mark Phelps on 2009-04-27
You didn't say what "broke down" Vista, but from what you wrote, it looks like you can't create files or directories on your laptop hard drive. Could be a general hard drive failure.

The unresponsiveness could be the system waiting on a hard drive write that is being attempted over and over and over.

Would boot from a LiveCD, and once inside Ubuntu, try mounting and writing to the hard drive to rule that out.

---

