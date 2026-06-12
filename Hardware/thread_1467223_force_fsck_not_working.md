---
title: "force fsck not working"
date: 2010-04-30
forum: Hardware
---

### Post by zeroti on 2010-04-30
When I run "sudo fsck -n" on my laptop with lucid installed, I get messages saying that there are errors on my file system.

When I "sudo touch /forcefsck" and reboot, I get a message during boot-up that the disk is being checked for errors, as expected. However, when I run "sudo fsck -n" once it's booted-up, I can see that they are not resolved.

When I run fsck from a 9.10 live cd, it says that the system is clean...

What I would really like to do is boot-up without mounting the filesystem (like you can do on os x in single user mode) and then run "fsck -y" or something and see the output.

Is there a way to do this, or some other way to fix my file system? Or is there something that I'm misunderstanding? :confused:

Thanks for any help.

---

### Post by zeroti on 2010-05-01
Well I tried setting FSCKFIX=yes in /etc/default/rcS as well as touching /forcefsck and I think that may have reduced the number of errors I'm getting, but I'm afraid my newish hard drive might be dying. :(

---

