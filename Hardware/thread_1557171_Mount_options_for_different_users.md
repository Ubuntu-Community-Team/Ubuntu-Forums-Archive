---
title: "Mount options for different users"
date: 2010-08-20
forum: Hardware
---

### Post by Kom-Si on 2010-08-20
I use Storage Device Manager to auto-mount an NTFS drive at boot time. Now, suppose I have 3 users on my machine: AAA, BBB, and CCC.

I want the NTFS drive to auto-mount for AAA & BBB, but make it unavailable for user CCC. How should I configure Storage Device Manager to achieve this?

I played around with settings quite a bit, but all I could manage is either block the drive for ALL users (except root) or make it visible to ALL users.

Please help.

Thanks.

---

### Post by IcarusR on 2010-08-21
I don't know how you can prevent some users from mounting drives, but you can set group access of drives & files then only allow certain users to be in that group. 

This may help you...

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html")

---

