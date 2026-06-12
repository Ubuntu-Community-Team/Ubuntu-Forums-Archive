---
title: "Floppy drive (3.5&quot; variety) support"
date: 2014-06-05
forum: Hardware
---

### Post by rbmoler on 2014-06-05
I've been using Ubuntu 12.04 for about 6 months now and have had no significant issues.  Folks helped me take baby steps to get Ubuntu to mount my separate "data" drive and to use DosBox for an old program that I wanted to keep.

My MB is a new one but still supports IDE and floppy drives.  I have a 3.5 inch "stiffy" installed in the box but until recently didn't actually need it.  Now I do.  I learned that 12.04 has a bug that makes my floppy not work.  It shows up in the Home folder, but when I tell it to mount and read the floppy nothing happens.

I can access the drive with the following terminal command:

udisks --mount /dev/fd0.

So the drive works, as I expected, but I rebooted to XP in order to make a copy of the disk and make a copy to my "data" disk.  Still I'd like to have the OS mount the drive without having to run that command every time I boot up.  I've searched for the appropriate change to fstab and found two that are supposed to make that work.  They are the following:

/dev/fd0 /media/floppy-disk rw,user 0 0
/dev/fdo auto rw,user,noauto,exec,utf8 0 0

I think I've seen at some place a list of all the elements(what are they called?) and their meanings that can be used in fstab, but have lost the location.   

I saved a copy of fstab to the desktop just in case, before I rebooted the system.  In both cases I get an error message at boot up that  says that something is wrong and asks if I want to cancel and open Ubuntu without mounting the FD.  Subsequently I went back to fstab and removed the line involving the FD.  I also recall that for my HD when I modified fstab there was a separate line I could use to determine if the added line was correct.  A similar diagnostic line for the FD line would be handy.

Can anyone diagnose what is wrong and/or provide a correct line in fstab that will make the floppy recognized and working?

Thanks much for any help or advise.

---

### Post by rbmoler on 2014-06-06
I found the answer on another thread.  Bug #441835 has to do with floppy support.  It will not be fixed and there is no useful work around for it.  I'll just have to use udisks to mount the FD until i upgrade to Ubuntu version 13 (or 14?) where a new version of the FD support code has been incorporated.

I'll close this thread.

---

