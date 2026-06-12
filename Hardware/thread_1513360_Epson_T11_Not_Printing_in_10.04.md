---
title: "Epson T11 Not Printing in 10.04"
date: 2010-06-19
forum: Hardware
---

### Post by MichaelBKK on 2010-06-19
It seems quite a few people have had a similar problem, but I can't find any posts which have solved my problem:

I have an Epson Stylus T11 connected by USB.  It was working just fine in 9.10 but after upgrading to 10.04 it no longer prints anything.  It configured the first time I turned it on, and when I try to print a test page (or anything) the light blinks as if it's getting data, but then nothing comes out.  Everything in the CUPS log files looks normal - no errors reported.

I've tried removing the printer and adding it back.  I haven't tried re-installing CUPS yet, but it doesn't look like that will work.  

Any ideas?

---

### Post by davidmohammed on 2010-06-19
Hi there,
  have you tried using epson's driver for your printer model from [here]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do")?

---

### Post by MichaelBKK on 2010-06-19
Thought of that, but none of the driver packages there are for Debian distros.  They're all for Red Hat (RPM) variants, and all fail during installation without, apparently, leaving any usable PPD files behind.

Any more ideas?

---

### Post by davidmohammed on 2010-06-20
I have read somewhere that your printer will work with the T20 driver from [http://sourceforge.net/projects/gimp-print/files/](http://sourceforge.net/projects/gimp-print/files/)  .  The only issue is that it will not display ink levels.

---

### Post by MichaelBKK on 2010-06-20
Yes, it worked just fine with the T20 Gutenprint driver distributed in 9.10, but now it doesn't work in 10.04.  I don't think this is a driver problem, exactly.  Looks more like a configuration problem.

---

### Post by nugencs on 2010-06-29
check this out: [http://pinoy-computing-tips.blogspot.com/2010/05/how-to-make-epson-t10-printer-work-in.html]("http://pinoy-computing-tips.blogspot.com/2010/05/how-to-make-epson-t10-printer-work-in.html")

or if you're looking for a distro (ubuntu-based) with epson tXX printers working out-of-the-box: [http://pinoy-computing-tips.blogspot.com/2010/06/ubuntu-tutik-remix-1004.html]("http://pinoy-computing-tips.blogspot.com/2010/06/ubuntu-tutik-remix-1004.html")

---

### Post by MichaelBKK on 2010-06-29
Thanks, those instructions worked perfectly, although I **really** don't like have to install downgraded versions.

---

### Post by Karthix on 2010-07-27
Hi,

Thanks a lot for the instructions. They work like a charm.
Was fiddling with the Avasys drivers but even they were not working for my Epson T11.

thanks,
Kart

---

