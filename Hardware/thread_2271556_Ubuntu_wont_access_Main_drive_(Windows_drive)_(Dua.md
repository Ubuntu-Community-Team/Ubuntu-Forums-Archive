---
title: "Ubuntu wont access Main drive? (Windows drive) (Dual boot)"
date: 2015-03-31
forum: Hardware
---

### Post by Chandler_Powell on 2015-03-31
Hello im currently having a problem with ubuntu whenever i try to access my main windows drive i cannot do it, i get an error saying 



" Error mounting /dev/sda4 at /media/chandler11able/Chandlers Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/chandler11able/Chandlers Drive"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."


Help?

---

### Post by weatherman2 on 2015-03-31
Windows 8.1?  If so, fast startup (or hybrid boot) in Windows.  This mode kind of uses hibernation to save your Windows state so it can startup faster - but that locks the drive so Ubuntu can't access it.

---

### Post by Chandler_Powell on 2015-03-31
WIndows 10 actualy.....

---

### Post by weatherman2 on 2015-03-31
Probably the same solution.

---

### Post by Chandler_Powell on 2015-03-31
Yea i found the fast boot option but that didnt seem to do the trick...i turned it off and turned it back on and turned it off again..nothing still :c

---

### Post by Bucky Ball on 2015-03-31
Turn it off in Windows, leave it off, restart the machine and boot into Ubuntu. Any different?

It is definitely your issue, as outlined by the error output you posted:

```
**_Windows is hibernated_**, refused to mount.Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. [B][U]Please resume and shutdown
Windows fully (no hibernation or fast restarting)[/U][/B], or mount the volume
read-only with the 'ro' mount option."
```

---

### Post by weatherman2 on 2015-03-31
> **Chandler_Powell said:**
> Yea i found the fast boot option but that didnt seem to do the trick...i turned it off and turned it back on and turned it off again..nothing still :c

You'll need to leave it off if you want read-write access to your Windows partition in Ubuntu.  When a drive is hibernated (as is the case with the shutdown from "fast boot,") then Windows does not know about any changes you might potentially make to the filesystem while it is hibernated.  So say you add a new file in Ubuntu, then boot back into Windows.  Windows won't know the file was added - in effect it may be erased.

Your other option is to leave fast boot on in Windows but mount the drive in Ubuntu as read-only.  As long as you can't make changes to a partition, you won't get any inconsistency with Windows.

---

### Post by Chandler_Powell on 2015-03-31
I looked around online and was able to find a solution, you were supposed to enable the drive as read-write only ^-^

---

### Post by weatherman2 on 2015-03-31
> **Chandler_Powell said:**
> I looked around online and was able to find a solution, you were supposed to enable the drive as read-write only ^-^

You mean "read only."  That's what I recommended above.

---

### Post by Mark Phelps on 2015-03-31
> Yea i found the fast boot optionThat's NOT the correct option.  The correct option is FastStartup.  You have to disable that to stop Win10 from hibernating.  Also, be sure to use ShutDown, not Restart -- as the latter automatically forces hibernation.

---

