---
title: "Upgrading from 6.10 to 8.1 32 bit"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by rollerworld on 2009-03-06
Upgrading from 6.10 to 8.1 32 bit.

When I upgrade I want to retain the original desktop format, programs  and links.

I want to retain the evolution e-mail inbox and sent folders, in short, just
using the new o/s with everything still intact from the old o/s. Is this possible?  AJ

---

### Post by Skripka on 2009-03-06
Backup your hidden files/folders in your /home directory-as these should contain all your app settings....depending on what version of apps you're using now and what version you upgrade to-there's a chance your old config /database files might not work, as the apps (may have) changed their formatting....also check to make sure your apps don't have buried config/data files in the root directory.

There is no direct "upgrade" path to Ibex from 6.X, short of reinstalling....which is relatively painless if root and /home being are on seperate partitions.

---

### Post by lundholmj on 2009-03-06
Guess you can always try it.  I would think it should work.  You might hit some problems.  All you settings are kept in your home directory so that should be no problem.


      Download the alternate installation CD

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

---

### Post by Elfy on 2009-03-06
I would in addition to backing up > your hidden files/folders in your /home directory also make an evolution backup - there's an option for it in the file menu I believe - I had some issues with a copied evolution folder once.

Not saying that it wasn't my fault - but as evolution is the one thing you specify keeping I thought I would pipe up :)

---

