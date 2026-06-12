---
title: "Fujitsu ScanSnap S510???"
date: 2008-08-20
forum: Hardware
---

### Post by psless on 2008-08-20
I am trying to install software so that I can use my Fujitsu scanner (S510).  Has anyone had luck using this awesome scanner in Ubuntu?  I can get single pages to scan but nothing like the Windows application.

Any help would be greatly appreciated.

Patrick

---

### Post by psless on 2008-08-20
Anyone?

---

### Post by angrylittleman on 2008-08-20
I am considering pulling the trigger on one of these, so I will be watching this thread.

Was the scanner automatically recognized when you plugged it in?

What are you using to scan?  Give scan2pdf a shot.

Also, if you would give this a shot:

[http://jduck.net/2008/01/05/ocr-scanning/](http://jduck.net/2008/01/05/ocr-scanning/)

You might have to make a change to the scanning file to enable full duplex scanning (which the scanner should do on its own)

[http://www.awe.com/mark/blog/200709161530.html](http://www.awe.com/mark/blog/200709161530.html)

I plan on using that script with the 510.  I believe this will replicate the functionality of the windows software.

Please post back and let us know if it works!  I am about two seconds from buying one.

ALM

---

### Post by flamacue on 2008-08-30
> **angrylittleman said:**
> I am considering pulling the trigger on one of these, so I will be watching this thread.
Me too.

> What are you using to scan?  Give scan2pdf a shot.
I think this is a relevant link:

_[color=blue]http://gscan2pdf.sourceforge.net/[/color]_

It is in the Utilities section of the Universe respository--on Gutsy (7.10), anyway.

EDIT:  Maybe this will help too?

[_[color=blue]Scanning with sane’s scanimage from an ADF scanner to PDF and OCRed Text[/color]_](http://jduck.net/2008/01/05/ocr-scanning/)

EDIT2:  Apparently XSane has multipage mode, and can work with ADF scanners...

[_[color=blue]Multipage mode_[/color]](http://www.xsane.org/doc/sane-xsane-multipage-doc.html)
[_[color=blue]Scan options_[/color]](http://www.xsane.org/doc/sane-xsane-scan-options-doc.html)

If I'm not mistaken, XSane is included with ubuntu-desktop.

---

### Post by btbluesky on 2008-09-07
Seems someone got it working fine?

[http://www.awe.com/mark/blog/200709161530.html](http://www.awe.com/mark/blog/200709161530.html)

Still, no update from SANE project device page.

---

### Post by Jimmy The Clown on 2008-10-11
I just bought a s510 and it seems to work with gscan2pdf in 8.10. Might work in 8.06, didn't work properly for me in 7.10

There are a few caveats that I haven't figured out yet. It autodetected fine, but I can't get it to duplex properly. So for now I'm just scanning one page at a time

-JTC

---

### Post by CapnCaffeine on 2009-06-03
To duplex scan with this scanner, go to the Edit-->Preferences setting in gscan2pdf and choose the "scanadf" frontend instead of "scanimage". Then use "Extended Page Numbering" with an increment of "1" to prevent numbering by 2. 

gscan2pdf is intelligent enough to advance the starting number of the next batch to the next number in the scans.

I am really digging my scanner!!
:)

---

### Post by dmp2010 on 2010-06-16
I love ScanSnap S510. Everything in Ubuntu seems to work but the scanner. For that, I continue to use Windows. I will be waiting for resolution also. Thanks.

---

