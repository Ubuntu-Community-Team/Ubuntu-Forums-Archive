---
title: "Issue with installing scanner drivers for Epson XP-245"
date: 2019-01-08
forum: Hardware
---

### Post by netsurfau on 2019-01-08
I'm getting an "Origin Value" error while trying to install the scanner drivers for my Epson XP-245 Printer/Scanner (All-in-One)

I've managed to track down where Epson "hide" their linux drivers for various products. From their Support Page go to their Developer Page:
[http://www.epsondevelopers.com/product/ink-jet-printers-and-all-in-ones/](http://www.epsondevelopers.com/product/ink-jet-printers-and-all-in-ones/) Select the Download link under "Linux Printing & Scanning".
It will tell you that you're been taken to another site where you have to put in your printer model:
[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) you then click on the Download button for your required drivers. You're
then given a new page that list various Linux distributions and their 32bit or 64bit variants. Hope this info can help others.

My issue arose while trying to install the drivers ( I downloaded the latest version dated 20 Dec 2018). I got the following error message:

E: Repository 'http://dl.google.com/linux/chrome/deb stable Release' changed its 'Origin' value from 'Google, Inc.' to 'Google LLC'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.

I did read the manpage for apt-secure, but I didn't really understand what I need to do to fix my issue.
Hence my logging to post this where infinitely smarter Ubuntu users can hopefully help:redface:[-o<

---

