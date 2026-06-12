---
title: "Canon PIXMA MG5320 Print Driver"
date: 2011-11-16
forum: Hardware
---

### Post by mrcpuhead on 2011-11-16
Greetings - I've had to revert back from Ubuntu 11.10 to 10.04 LTS due to stability problems.  Now in 10.04, I can't find a suitable printer driver for my Canon PIXMA MG5320.  It worked fine in 11.10.  I still have the 11.10 and 11.04 installations available, but they will no longer boot - can someone tell me how to identify the specific driver from that installation's file structure, so I can search for it online to try to install in 10.04?

My search so far yielded nothing - no normal driver, no PPD file...

Thanks for your help!

---

### Post by mrcpuhead on 2011-11-19
With enough digging around, I finally found the right driver on Canon's Ireland site.  (I know it's also on the Japan site, but hey, I can't read Japanese!).

Here's the link:

[Canon Ireland - PIXMA 5300 Series Driver - Debian Pkg]("http://www.canon.ie/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG5340.aspx?DLtcmuri=tcm:24-863341&page=1&type=download")

:guitar:

---

### Post by chmegr on 2011-12-12
Where did you get the drivers for 11.10?

---

### Post by pdadad on 2012-03-09
Thanks mrcpuhead!  That driver worked for me in PinguyOS 11.04 x86_64

---

### Post by xyodune on 2012-06-04
hey meyhus, i tried your second method but when i started the setup i got this with a big fat red circle with a minus sign, what do i do?


Archive:  /tmp/setup.exe
[/tmp/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/setup.exe or
          /tmp/setup.exe.zip, and cannot find /tmp/setup.exe.ZIP, period.

---

### Post by jerrynolan on 2012-06-29
** easy instructions **

The first method above worked for me. Very easy. Download the file, uncompress it, run the install script, and you're done.

[LIST=1]
[*]Before doing the installation on my ubuntu laptop I followed the instructions from Cannon that came with the printer on how to add it to my wireless network.
[*]Then I downloaded driver from cannon Ireland site. The link above takes you directly to it. Saved it to some random directory under home. The file is a tarball - cnijfilter-mg5300series-3.60-1-deb.tar.gz
[*]From my gui file browser (Nautilus in my case) double clicked the file, and it opened with my default archive manager.
[*]Extracted the whole thing to the same random location.
[*]Inside were a couple of directories and also a install.sh script.
[*]Ran the install.sh script from the terminal.
[*]For every question the install script asked (except how the printer was connected) I just selected the default answers, so yes I was just hitting enter.
[*]When the install script asked if printer was connected directly or network, I answered network, and it found it (or course I had turned on the printer before doing this)
[/LIST]
That was it, the install script took care of everything.  After the script ran, I didn't have to do anything at all, I could now print via the wireless network from my apps.

---

### Post by cjfleet on 2012-07-18
:confused: I was able to install the printer with no problem but this is a multi-function unit and I can't find a way to scan an image via ip address wirelessly as I could when i had windows.  I am not very good with the command line stuff so i would prefer a GUI.  Can anyone help with this issue?

---

