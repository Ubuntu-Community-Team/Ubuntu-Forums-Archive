---
title: "Brother HL 2170w stopped printing"
date: 2017-05-14
forum: Hardware
---

### Post by antipodesman on 2017-05-14
I have been using this printer since 2014 on Ubuntu 14-04.  Several months ago I switched to Ubuntu Mate 16-04 and continued to use the printer but a few weeks ago it stopped.  The printer test page runs fine from the printer but nothing gets sent to the printer.  I deleted the printer driver and re-installed it but with the same result.  It is connected by usb as localhost.

---

### Post by pdc on 2017-05-15
if you open the PRINTERS folder; on the top menu bar is a HELP area; with troubleshooting: if you press the F1 button it opens a troubleshooting wizard; I wonder if that offers any help: if you could let us know how it runs for you; 

on the Mint forum several weeks ago a thread ran [https://forums.linuxmint.com/viewtopic.php?f=51&t=242497](https://forums.linuxmint.com/viewtopic.php?f=51&t=242497) where there was a problem with a CUPS update

if you paste ```
dkpg -l cups*
``` into a terminal; it will list what of the various cups files are installed; and you could check through from the above thread and see which ones you have got; 

__________________

ubuntu has a wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) on printing problems; it may well go through many of the steps the troubleshooting wizard covers; you could have a go through that if you are not progressing the issue

---

