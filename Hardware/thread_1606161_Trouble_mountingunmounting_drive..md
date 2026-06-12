---
title: "Trouble mounting/unmounting drive."
date: 2010-10-26
forum: Hardware
---

### Post by Fender89 on 2010-10-26
I'm having a bit of trouble mounting and unmounting an external hard drive. When I try mount, I get a variety of differnet error messages, the most recent being:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/Expansion Drive

When I unmount, again I get a few different messages but it's usually something along the lines of "the drive is currently in use" or "does not agree with fstab".

I want to know, Is there a file somewhere that keeps settings on drives such as this, I was thinking I could find out what it is and edit it back to default so it can detect the drive again as new? Any other advice would be much appreciated because I really have no idea where to start with this.

---

### Post by msaravanan77 on 2010-10-26
are you trying from regular user OR root user?
try refer: /etc/udev/udev.rules

---

### Post by Fender89 on 2010-10-26
I'm logged in as a regular user. I just tried to unmount, I get the same message saying that only root can do that.

---

### Post by Fender89 on 2010-10-26
bumping for help

---

