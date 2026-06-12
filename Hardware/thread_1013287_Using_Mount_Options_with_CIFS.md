---
title: "Using Mount Options with CIFS"
date: 2008-12-16
forum: Hardware
---

### Post by dbsoundman on 2008-12-16
I have two CIFS shares that I added to my /etc/fstab to automount, however I want to use some mount options on them. The problem is, I can't seem to get the syntax right.

Here are the /etc/fstab entries I'm looking at:
//192.168.2.2/dan /remote/blackdiamond/files cifs username=dan,password=xxxxxx 0 0
//192.168.2.2/brandesky20 /remote/blackdiamond/brandesky20 cifs username=dan,password=xxxxxx 0 0

What I want to do is add the "user" and "noauto" mount options to each, so that they do not automatically try to mount, and a regular user can choose to mount them by double-clicking the folder icon. I had the noauto option in before, at the end after the password, and it worked fine, but I couldn't mount the share as a user, I had to be root. So I need to work in the user command to get it all straightened out. Any suggestions?

Thanks,
Dan

---

