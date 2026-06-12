---
title: "(Ubuntu/kubuntu 9.10 higher) Issues installing Canon mp240(and other product)"
date: 2010-04-02
forum: Hardware
---

### Post by robocap on 2010-04-02
Resource : [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

In the Ubuntu 9.04 release, cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (iP1900_debian_printer.tar) to desktop; there should be 3 files produced from there. cnijfilter-common_3.00-1_i386.deb; cnijfilter-mp240series_3.00-1_i386.deb; and common_3.00-1.tar.gz
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
Quote:
$ dpkg-deb -x cnijfilter-common_3.00-1_i386.deb common
$ dpkg-deb --control cnijfilter-common_3.00-1_i386.deb
4. You should now see two new folders - common and DEBIAN. What we need to do is to change the file control in DEBIAN to reflect libcups2. So go ahead and type:
Quote:
$ cd DEBIAN
$ gedit control
5. In the file that opens, look for the line
Quote:
Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1), libpopt0 (>= 1.7)
and change libcupsys2 to libcups2. Save the file.
6. Now, copy the entire DEBIAN folder into common. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where common is, and go ahead and type in the terminal:
Quote:
$ dpkg -b common cnijfilter-common_3.00-1_i386.deb
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6 for cnijfilter-mp240series_3.00-1_i386.deb, with the exception that you should type in cnijfilter-mp240series_3.00-1_i386.deb and substitute mp240 for common wherever it appears above.

Hope this helps you all out!


also i attached new packages for mp240 printer.(just command pack.)you must rebuild package for mp240 .

---

### Post by paleoGeek on 2010-08-28
Worked great. Thanks.

---

### Post by Pogo1 on 2011-04-16
> **robocap said:**
> Resource : [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

In the Ubuntu 9.04 release, cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (iP1900_debian_printer.tar) to desktop; there should be 3 files produced from there. cnijfilter-common_3.00-1_i386.deb; cnijfilter-mp240series_3.00-1_i386.deb; and common_3.00-1.tar.gz
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
Quote:
$ dpkg-deb -x cnijfilter-common_3.00-1_i386.deb common
$ dpkg-deb --control cnijfilter-common_3.00-1_i386.deb
4. You should now see two new folders - common and DEBIAN. What we need to do is to change the file control in DEBIAN to reflect libcups2. So go ahead and type:
Quote:
$ cd DEBIAN
$ gedit control
5. In the file that opens, look for the line
Quote:
Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1), libpopt0 (>= 1.7)
and change libcupsys2 to libcups2. Save the file.
6. Now, copy the entire DEBIAN folder into common. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where common is, and go ahead and type in the terminal:
Quote:
$ dpkg -b common cnijfilter-common_3.00-1_i386.deb
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6 for cnijfilter-mp240series_3.00-1_i386.deb, with the exception that you should type in cnijfilter-mp240series_3.00-1_i386.deb and substitute mp240 for common wherever it appears above.

Hope this helps you all out!

Help! I got stuck half way through. Unpacking altering, repackaging and installing cnijfilter-common_3.00-1_i386.deb common worked pretty much as described (the files were a layer deeper in a tar.gz file which I had to extract first).

Step 7 didn't work, and I can't find a way to make it do so. The "substitute mp240 for common wherever it appears above" is too vague, and things like step 1 having already been completed, and step 2 put me off.

Can you work through the last steps with real file names and folders so that it is as clear as the first section? :confused:

EDIT: I used gedit to replace all instances of 'common' with 'mp240series' (mp240 alone did not work). I then had a printer security fault that I fixed following this thread <http://ubuntuforums.org/showthread.php?t=1313291>.



Cheers;

Pogo.

---

