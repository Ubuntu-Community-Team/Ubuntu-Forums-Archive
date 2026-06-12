---
title: "gscan2pdf scans for half a second only"
date: 2008-10-12
forum: General Help
---

### Post by ewy on 2008-10-12
I'd like to be able to scan images into relatively small PDF formats, especially multi-page PDF. I have tried xsane but it seems to give PDF sizes upwards of 10M per page, which is pretty large for sharing / emailing.

I have heard that gscan2pdf is very useful, and the interface looks great, but I can't get it to work. I attempt to scan, and the flatbed scanner head will start up, scan for half a second (perhaps two steps), then stop. I have a completely blank (white) page as output.

scanimage seems to work fine from the command line.

Running the command ```
scanimage -L
``` gives the following output:
```
device `lexmark:libusb:001:006' is a Lexmark X1100/rev. B2 flatbed scanner
```

I am using gscan2pdf 0.9.21. The output from ```
gscan2pdf --debug
``` is attached.

I would love to get this fixed, as gscan2pdf appears to be a great utility (and is rumoured to produce pdfs of manageable size).

-Elliott.

---

