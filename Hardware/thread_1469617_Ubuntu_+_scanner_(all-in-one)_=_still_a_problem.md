---
title: "Ubuntu + scanner (all-in-one) = still a problem?"
date: 2010-05-02
forum: Hardware
---

### Post by flyver on 2010-05-02
Hi,

I have Ubuntu 10.04 LTS. My printer/scanner/photocopier is an Epson Stylus NX115. Ubuntu found a suitable driver for the printer function.

For the scanner, Simple Scan didn't detect it. Found a way to install Sane (wasn't able to open it though, but then I installed XSane) and with **X**Sane I was able to run the program and it doesn't find my Epson either.

Is there any way to make scanners (especially tricky for all-in-one machines, perhaps...) work in Ubuntu?

I searched in forums and that's where I found out that I should use Sane, but... Hmm now I don't know what to do anymore.

Thank you!

---

### Post by ellgor on 2010-05-02
Hi,

Go to this site "Avasys" and get the Imagescan package, not the all-in-one, for your printer, its right down the bottom of the downloads page called Imagescan-deb, or like that, install with gdebi and may need a reboot to work properly.

Regards, Ellgor.

---

### Post by flyver on 2010-05-02
Wow thanks a lot! It works perfectly.

Seems I have to review my googling-abilities. Did so much searching but never found that site...

Thank you!

---

### Post by jay941 on 2010-05-07
i went to the avasys site and tried to download the drivers for the scan part of the epson nx110, but it asks for a model and the nx110 is not listed. which model did you use?
thanks

---

### Post by geovino on 2010-07-03
> **ellgor said:**
> Hi,

Go to this site "Avasys" and get the Imagescan package, not the all-in-one, for your printer, its right down the bottom of the downloads page called Imagescan-deb, or like that, install with gdebi and may need a reboot to work properly.

Regards, Ellgor.

Where is that file? I can't find it on the download page.

---

### Post by HighInBC on 2010-10-04
These instructions no longer lead to the drivers. The website does not seems to have what is described.

I found drivers for the printer, but nothing for the scanner. The "Image scan!" drivers do not list an option for the NX series.

Not sure what to download. Can this be marked as no longer "Solved"?

---

### Post by flyver on 2010-10-04
I just checked that out again, and it stills seems OK. Go to [this page]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/"), then scroll about mid-way down, and there will be a list of packages for the NX115...

I didn't check the "deb" now, but I guess it still works...

---

