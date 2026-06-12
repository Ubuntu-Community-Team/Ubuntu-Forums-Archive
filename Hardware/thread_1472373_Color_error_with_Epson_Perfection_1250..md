---
title: "Color error with Epson Perfection 1250."
date: 2010-05-04
forum: Hardware
---

### Post by negora on 2010-05-04
Hello:

I use Ubuntu 10.04 and an Epson Perfection 1250 scanner. I'm experiencing a weird problem which is related to colours.

Regardless I use Simple Scan or XSane, after doing at least 1 scan (complete or partial) or a few previews, the programs start to act goofy and show a wrong colour composition:

[Click here to watch a sample!]("http://negora.com/ubuntu/scanner.jpg")

As you can see, each half of the scan show 2 different colour tones. Sometimes the colours varies, depending on the scanned document.

**It gets fixed as soon as I close and open the program again,** so I've discarded that's a hardware fault. Besides, my scanner works fine on Windows, no matter how many scans I do.

I've tried to change the temporal folder and uncheck some options (on XSane), just to discard theories. But if it were because of something like that, it would affect the first scan too, obviously. I wonder if it has something to do with some kind of temporal "content" which the Sane libraries generate. Any idea, please?

Thank you very much in advance :) .

---

### Post by ellgor on 2010-05-04
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by negora on 2010-05-04
**ellgor:** Thank you for that information. I had no idea about this driver from Avasys. Why hasn't the Sane  project integrated the open source part of this software (the improved version of "libsane-epkowa") into its code? Or does it depend on the copyrighted "libesmod"?

Speaking about iScan, I've tried to compile the version 2.10.0-1 on Ubuntu 10.04 64-bit but I'm facing some problems. I've been able to solve the first one, which was the absence of these packages during the configuration:
[LIST]
[*]libgtk2.0-dev
[*]libimlib2-dev
[/LIST]

But now, during the actual compilation, it throws an error:
```
imgstream.cc: In static member function 'static lt__handle* iscan::imgstream::find_dlopen(const char*)':
imgstream.cc:262: error: invalid conversion from 'int (*)(const void*, const void*)' to 'int (*)(const dirent**, const dirent**)'
imgstream.cc:262: error:   initializing argument 4 of 'int scandir(const char*, dirent***, int (*)(const dirent*), int (*)(const dirent**, const dirent**))'
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1

```

I guess that I'll have to wait until Avasys updates iScan again.

PS: I've just read that the Sane support for Epson Perfection 1250 depends on that external copyrighted module, so it's already answered ;) .
PS2: Ouch, this version of iScan have not been updated since 2007. My hopes are broken, he he he.

---

### Post by negora on 2010-05-06
I've been thinking about this issue and got a conclusion. If the Sane website states that this model of scanner needs from an external and copyrighted module (redirecting to the Avasys website), that means that the Ubuntu programmers have used such module in their distributions, Right? Otherwise I hadn't been able to scan just "out of the box". Because the Sane project by itself doesn't provide an alternative way.

So, in other words, if I were able to compile the Avasys software, I would be in the same situation I guess. Can anyone confirm this? Thanks.

---

### Post by negora on 2010-05-19
Investigating a little more I've found out that my Epson Perfection 1250 works with Ubuntu thanks to the Plustek backend for SANE, not because it's using Epkowa, which seems to be the official one from Epson/Avasys and also require the GT 7200 plugin to work.

Since I'm using the 64 bit edition of Ubuntu and the plug-in is ONLY available for 32 bits, even if I were able to compile iScan (or "lie" Avasys and download the latest 64 bit build), I couldn't do anything.

So I guess that my efforts must be put on the Plustek backend and try to guess why it fails after some time of use. I've re-tried to use this scanner on a virtual Windows XP and it works fine.

---

### Post by negora on 2010-11-19
After having moved to Ubuntu 10.10 I've tried to use the command line application "scanimage" from the SANE project and everything works fine. If I use XSane or Simple Scan, the problem persist. I guess that it has to be with the cache or maybe the parameters which these GUIs pass to the backend application? Really I've no idea.

Anyway, using the command line option is faster and cleaner, once the options become familiar. I use ImageMagick to manipulate the resulting images as I need (colour tones, bright, etc.). So I guess that it's done :) .

---

### Post by JRBASTIEN on 2013-01-18
I have the same problem as described here.  No problem on first scan (or preview) then I get some stripes of different colors in subsequent scans.  The only workaround is to shutdown XSANE and to restart it.   And of course, never use the preview function.

My scanner is an Epson Perfection 1260 and used to work well before.  Perhaps it is the first time I tried since I upgraded to Ubuntu 12.04 64 bits.  Previously I was on 10.10 32 bits.

Does anybody have this issue or knows how to resolve this?

---

### Post by overdrank on 2013-01-18
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

