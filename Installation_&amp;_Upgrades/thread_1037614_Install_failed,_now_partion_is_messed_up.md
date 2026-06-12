---
title: "Install failed, now partion is messed up"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by chougard on 2009-01-11
Hello.

My friend was attempting to install Ubuntu when the installer locked up for a really long time so he crashed his computer. Ever since then his partitions have been really messed up and he doesn't want to loose his windows install. He had ubuntu install itself by resizing the windows partition down 20gb.

When he boots the computer normally he gets a partition error. So we tried to install ubuntu again but it wont let us resize the windows partition. 
Attached are some pictures of the error and other things that might help.
Is there any way that we can fix the windows partition?

Thank you for any help!

---

### Post by Partyboi2 on 2009-01-12
Try using [[COLOR=Blue]testdisk[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk") to fix the partition.

---

### Post by aeronotix on 2009-01-12
Your Master Boot Record sounds like it is either missing or Ubuntu got half way through changing it, there are a couple of fixes out there. But the one I know of requires that you can still get into the Windows partition.

That test disk program looks promising, try that.

---

### Post by frost151n on 2009-01-12
Just incase you wanna follow aeronotix's advice and repair the MBR

Here's a link-

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by aeronotix on 2009-01-12
The one I meant was something called MbrFix.exe, it's extremely simple to use but I am unsure if he has access to the windows drive anymore. 

But I suppose he should do, I've screwed mbrs before.

---

### Post by meindian523 on 2009-01-12
Or you could use Super Grub Disk,in case Ubuntu has been installed but didn't finish setting up Grub.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by chougard on 2009-01-13
Thanks Partyboi2!

Took a few tries but that program fixed it.

---

