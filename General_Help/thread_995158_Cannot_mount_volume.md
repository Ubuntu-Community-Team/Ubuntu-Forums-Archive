---
title: "Cannot mount volume"
date: 2008-11-27
forum: General Help
---

### Post by mickdoe on 2008-11-27
When I plug in my usb memory stick, an alert box pops up saying:
Cannot mount volume.
Error org.freedesktop.DBus.Error.AccessDenied.

Details
A security policy in place prevents this sender from sending this messge to this recipient. see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "mount" error name "(unset)" destination "org.freedesktop.Hal")

It may be coincidence, but I get this message when trying to run Administration>Users and Groups:

The configuration could not be loaded
You are not allowed to access the system configuration.

This was all working fine until recently. Any ideas?

I'm also having trouble finding my scanner. This too was working fine until recently.

---

### Post by cariboo on 2008-11-27
It sounds like you have a problem with groups. In a Applications-->Accessories-->Terminal type:

```
groups
```

the output should look something like this:

```
groups
jim adm dialout cdrom plugdev lpadmin admin sambashare vboxusers
```

In your case you should also have a scanner group. If any of the groups are missing you will need to boot into recovery mode and add the missing groups. To do this at the prompt type:

```
useradd -G {group-name} username
```

insert the group names without the curly brackets separated by spaces.

Jim

---

### Post by mickdoe on 2008-11-28
Thanks Jim. I tried groups and this is the output I got:

mick adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare

This looks ok compared with your list. There's no scanner group. When I tried sudo scanneradd -G {scanner} mick I got the message: no such group. I didn't do this from recovery mode. Is that going to make a difference?

---

### Post by mickdoe on 2008-11-28
I fixed it! Not sure how or why exactly, but when I tried running the update manager I got an error message and an instruction to run dpkg --configure -a. I did this and now my memory stick and scanner access seems to be back to normal.

---

