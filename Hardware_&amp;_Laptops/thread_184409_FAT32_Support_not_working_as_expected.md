---
title: "FAT32 Support not working as expected"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by kvgeorge1 on 2006-05-29
I installed Ubuntu 5.10 on a Toshiba Tecra 9100 laptop.  I have WinXP running on a 5 Gig partition (NTFS), a 5Gig partition running FAT32 for sharing data between the 2 environments, and Ubuntu on all of the rest.

When I copy files to the FAT32 partition, if there are some capitalized characters in the file name (ie.  'My Folder' or 'TestData') everything is fine. BUT, if I have a file that is all caps (ie. 'WEB-INF' or 'MY-DATA'), it is treated as all lowercase in Ubuntu, but correctly as all uppercase in WinXP.

I have tried several times to rename some of the lowercase folders in LINUX to all uppercase folders on the FAT32 partition, but they always come back as lowercased displayed in LINUX, uppercase displayed in WinXP.

Any suggestions?]

---

### Post by jgoguen on 2006-05-29
Add this to your options for that partition in /etc/fstab:
```
shortname=mixed
``` And then unmount/mount the partition.

From the mount(8) man page, vfat section:
> shortname=[lower|win95|winnt|mixed]

              Defines the behaviour for  creation  and  display  of  filenames
              which fit into 8.3 characters. If a long name for a file exists,
              it will always be preferred display. There are four modes:

              lower  Force the short name to lower case upon display; store  a
                     long name when the short name is not all upper case.

              win95  Force  the short name to upper case upon display; store a
                     long name when the short name is not all upper case.

              winnt  Display the shortname as is; store a long name  when  the
                     short name is not all lower case or all upper case.

              mixed  Display  the short name as is; store a long name when the
                     short name is not all upper case.

       The default is "lower". 
Does that help?

---

### Post by kvgeorge1 on 2006-05-29
Yes, that fixed it completely.

Thanks again for such a quick and accurate response.:D

---

### Post by prince_niceguy on 2008-01-16
thank you so much.. it solved lot of my build problems in eclipse.

---

