---
title: "setting gid and uid for internal and external ntfs drives"
date: 2009-02-03
forum: Hardware
---

### Post by bulwynkl on 2009-02-03
Hi folks,

where/how can I set the gid and uid for attached ntfs drives?

I know I can set the gid and uid using mount, ntfs-3g or via /etc/fstab (it's one of the ntfs-3g options)

but how do I get whatever program that does the dynamic loading of e.g. USB2.0 drives to set the gid and uid?


the reason I want to do this is that it used to but now does not set it to something usefull - now it sets it to uid=o and gid=0 - i.e. root.

I want to set it to 65534 - i.e. nogroup and nouser

or atleast something accessable by everyone who will use the machine - 65534 will do OK for now... maybe set to the admin (115) group at a later stage.

---

### Post by Yashiro on 2009-02-03
If you let the HAL mount the drive then look into System>Prefrerences>Authorizations.

If you try manually, check the ntfs3g web site help. You may have to set suid root on the binary.

---

