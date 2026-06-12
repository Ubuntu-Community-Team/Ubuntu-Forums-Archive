---
title: "Feisty breaks SANE"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by jsladek on 2007-06-22
I am using a Benq 620U scanner on Feisty. After a scan (or preview), the next attempt for a scan (or preview) produces an I/O error.  The only way to make a second scan is to shut down and restart the scanner.  

This problem did not exist with Edgy Eft or with a PCLINUXOS2007 live-cd or in Windows XP.  I tried the same process with an Ubuntu Feisty live-cd and the problem occurs there as well.  I tried reinstalling libsane and sane ffrom the synaptic package manager, but there is no improvement.

The Benq 620U uses snapscan:libusb:001:002 (FlatbedScanner_5) driver.

From the above, it appears that the problem is in the distribution itself.

Anybody run into this and have a solution?

Jim

---

### Post by noynac on 2007-06-22
Many people are having scanner problems after upgrading to Feisty. The most common cause of this is a usb-suspend bug in the kernel. You can read about this and about a workaround, which involves installation of the scanbuttond utility, at:

[http://tinyurl.com/25fhdm](http://tinyurl.com/25fhdm)

---

### Post by jsladek on 2007-06-23
Thanks for the link.  I "finally" found the bug listing part of the site and all the posting on this issue.   I'm using the workaround and starting it in Sessions at each bootup.   It seems to work fine, except that a "kluge" better not be the final answer.

At least now I can continue on with my search for Windows apps replacements and continue my transition to Linux.

Consider this thread closed, though the issue itself sure isn't.

Jim

---

