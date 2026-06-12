---
title: "Stale NFS Handle - USB?"
date: 2010-03-09
forum: Hardware
---

### Post by adzik on 2010-03-09
I have an error message showing up regardless of how I attempt to mount an external USB hard drive.
I was actually copying the contents of the usb external to a different location, then the connection (usb) shut down. I don't know why.
But now when I attempt to re-connect the external HD it only gives me the following error, whether through gui or trying to mount to a different location through cli.
Here's what I get:

Error mounting: mount exited with exit code 32: mount: Stale NFS file handle
(screenshot attached)

I don't have NFS in any capacity on my system. I also tried to connect the external HD to my other laptop, which gives me the same error, so I know this is a problem with the HD.
Has anyone seen this issue before? 
Is there anything I can do? 
My whole purpose for copying stuff off this HD was because it's pretty important stuff.
Any help would be greatly appreciated. I'm a little unnerved by this...:sad:

---

### Post by sikander3786 on 2010-03-09
Check this thread. I hope it will help you perfectly. Post back if problems persist.

[http://ubuntuforums.org/showthread.php?p=8416468](http://ubuntuforums.org/showthread.php?p=8416468)

Regards.

Sikander.

---

### Post by adzik on 2010-03-09
Thanks for the link.
I went through all the info and instructions, and at the end of it all, the drive is still inaccessible. Running e2fsck in any way results in "e2fsck: aborted" every time. Doesn't matter what commands are used.
Is there anything else that can be done to pull the data from the drive?

---

### Post by adzik on 2010-03-09
Anyone??

---

### Post by adzik on 2010-03-12
What I have currently done is backed up the hard drive using dd if=/dev/sdb1 of=/xxxx/sdb1.img
So I now have an image file of the drive in question.
Does anyone know if I can mount/manipulate the drive image file like the physical HD itself, or are there only certain things I can do with it?
I am trying everything I can to recover the data.
I have still been unable to access the drive to this point.

---

