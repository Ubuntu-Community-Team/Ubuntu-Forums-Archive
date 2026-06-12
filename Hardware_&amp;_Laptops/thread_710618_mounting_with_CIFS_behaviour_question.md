---
title: "mounting with CIFS behaviour question"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by captkirk on 2008-02-28
I posted again in networking, where it seems more applicable.  I would delete, but I don't see how.

I originally mounted a cifs drive with the /noperms option.
#//bigdrive/public /media/bigdrive cifs   noperm,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I used /noperms because I could not read and write to the drive any other way.

At some point, I realized I did not set an owner and thought that might be my problem.  I then used the /gid option to make my group the owner of the drive.  I removed /noperms and tried /gid but that did not work.  Nobody in the group could read and write to the drive.

I then added myself as the owner of the drive using the /uid option.  Now, both the /uid and the /gid option work as documented.  All of the users can read and write to the drive.

I think I am missing something about setting up cifs drives that I have not seen.  Can someone point me to something to help me out, or explain what I am overlooking?  I doubt this is a bug, but I am confused!

Thanks!

---

