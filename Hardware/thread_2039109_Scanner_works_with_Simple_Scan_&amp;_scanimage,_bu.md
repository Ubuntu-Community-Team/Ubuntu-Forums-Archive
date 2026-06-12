---
title: "Scanner works with Simple Scan &amp; scanimage, but xsane output skewed"
date: 2012-08-08
forum: Hardware
---

### Post by PaulEdwards on 2012-08-08
My wife was successfully able to use a "NeatReceipts Scanalizer" USB portable scanner (which is a supported model with a functional [backend]("http://www.sane-project.org/sane-backends.html#S-GT68XX") and [good documentation]("http://www.sane-project.org/man/sane-gt68xx.5.html")) on her PC running Ubuntu 11.10 for quite a while since I set it up according to the [directions I found online]("http://www.meier-geinitz.de/sane/gt68xx-backend/#FIRMWARE").


However, she advised me this evening that it hasn't been working properly for a while.
I had a look and can't quite figure it out... :confused:

When using xsane, the image output is horizontally skewed and unusable, but it comes out fine when using Simple Scan or the command line scanimage utility (which is included with sane-utils). I get the same results when running xsane & scanimage as root, so permissions aren't the problem.

Here's some grayscale scans:
Good:
[IMG]https://lh6.googleusercontent.com/-kqTUwu2hqWQ/UCIP3ZcqgEI/AAAAAAAAF6Q/eGGHfeF-CA0/s800/image.good.jpeg[/IMG]

Bad:
[IMG]https://lh5.googleusercontent.com/-4daVWza_Nhk/UCIP3O3SK1I/AAAAAAAAF6I/e05WM0U7t1k/s800/image.bad.jpeg[/IMG]

Has anyone:
[LIST=1]
[*]seen anything like this before?
[*]fixed it?
[/LIST]


I've searched the web and the forums and haven't found anything relevant or helpful thus far, but I'd be pleased to be presented with a URL I missed that contains the solution.

Thanks in advance for any relevant advice or suggestions you may be able to provide to get this scanner working again. My wife thanks you, too.

---

### Post by aikishugyo on 2012-08-09
Switch on the debug options for the backend (read the man page, e.g., "man sane-pixma" for the pixma backend) and set the debug environment variable. 
Then run scanimage and xsane again, and see if the same libraries are being used. Since the front-ends do not do the actual scanning, maybe there is a mismatch of libraries?

Example for pixma backend:
> # SANE_DEBUG_PIXMA=3 xsane
[sanei_debug] Setting debug level of pixma to 3.
[pixma] pixma is compiled without pthread support.
[pixma] pixma version 0.17.0
[pixma] pixma_collect_devices() found Canon PIXMA MP450 at libusb:007:003
/../

---

