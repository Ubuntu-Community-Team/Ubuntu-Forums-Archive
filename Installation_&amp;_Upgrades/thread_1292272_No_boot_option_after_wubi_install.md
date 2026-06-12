---
title: "No boot option after wubi install"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by mmulqueen on 2009-10-15
Hello,

I got a new laptop last week.  I formatted the drive, made a few partitions, and installed Windows 7 Enterprise 64bit on the first partition C:\.  Yesterday, I installed Ubuntu 9.04 32bit via wubi.exe to the F:\ partition not even thinking that the ISO file I'd downloaded months ago wasn't the 64bit edition.  So, wanting to take advantage of all my RAM, I just formatted the F:\ drive, opened a command prompt, and removed the Ubuntu entry from the boot options using "bcdedit /delete {id}".  I rebooted my PC and logged back into windows.  Then, I mounted the newly downloaded, 64bit ISO file and ran wubi.exe as administrator.  The installation completed and asked me to reboot.  After restarting, however, I was not given the option to boot into Ubuntu.  Using "bcdedit" from the command prompt I found that there had been no change to the boot record.  Windows 7 was still the only option.  I've formated the drive several times now and tried installing via mounted ISO file and CD.  I get the same result each time.  Anyone have a resolution for this?

Thanks,

Matt

---

### Post by puvijain on 2011-02-23
check if this works
[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

---

### Post by s.fox on 2011-02-23
Thread Necromancy.

Thread Closed.

---

