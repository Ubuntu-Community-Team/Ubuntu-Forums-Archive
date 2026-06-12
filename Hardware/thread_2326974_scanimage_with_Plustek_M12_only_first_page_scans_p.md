---
title: "scanimage with Plustek M12 only first page scans properly"
date: 2016-06-06
forum: Hardware
---

### Post by pumrum on 2016-06-06
Long time Ubuntu 14.04 user, I have a Lenovo W540 laptop running 14.04.4 LTS, and a Plustek OpticSlim M12 scanner (the thin sheet fed scanner that came with NeatReceipts / NeatWorks many years ago - the old silver one). Works perfect. I use scanimage to scan to TIFF with no issues.

I recently bought a Lenovo P50 and built it with Ubuntu MATE 16.04. I didn't take awesome notes when I got my scanner to work on 14.04, but I had enough to get it working on 16.04, or so I thought. I just realized that the first page scans fine on the new laptop, but each subsequent page shifts the image to the left about 1/4", and then wraps the image around on the right side. Very frustrating. I can unplug the scanner and plug it back in and each first image scans fine, but who wants to do that?

I verified that the following files are identical on the old and new system:
/etc/sane.d/gt68xx.conf
/usr/share/sane/gt68xx/cism216.fw (I'm using the latest firmware file from NeatWorks 4, which I own and use for receipts but not documents)

Old system has scanimage 1.0.23, new system has 1.0.25
I ran scanimage -L on both, and both detect the scanner as "device `gt68xx:libusb:001:011' is a Plustek OpticSlim M12 flatbed scanner"
I ran scanimage -T on both, and all tests PASS

The command I use to scan on both systems:
scanimage -d gt68xx --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff

I tried using different USB ports on the new laptop, but they all behave the same. I have a Windows XP VM running NeatWorks on the new laptop, and the scanner works fine inside the VM.

Possibly related: on the old system, after the first scan, the paper detection would start working and when you insert a new sheet, it would draw the page in about 1/8". On the new system, this never happens.

I attached two scans of the same page fed the same way one right after the other. To save on file size I converted the images to line art, but it gives the general idea: page1.pdf is the first scan after plugging in the scanner, works fine. Page is normal. page2.pdf is the second scan of the same exact page, and you can see that the image has shifted to the left a bit, and a small part of it has wrapped around to the right side of the image (though not all has wrapped, some is missing).

**EDIT:** I did some testing, and found that the issue only occurs after you perform a scan without specifying option -y.

If you scan multiple images using the maximum allowable Y value (299), the scanner continues to function normally:
scanimage -d gt68xx -y 299 --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff

If you scan an images without specifying a Y value (which used to default to 299mm, or slightly larger than A4 - the second image and beyond will wrap around the left side, regardless of whether you specify a Y value:

scanimage -d gt68xx --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image fine
scanimage -d gt68xx --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image wrapped

scanimage -d gt68xx --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image fine
scanimage -d gt68xx -y 299 --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image wrapped

scanimage -d gt68xx -y 299 --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image fine
scanimage -d gt68xx -y 299 --format=tiff >scan`date +"%Y%m%d_%H%M%S"`.tiff ==> image fine

I have always used the command without a Y value to scan letter documents since it allows for scanning pages that may be slightly misaligned or mis-fed. I can work around this by always specifying a Y value - but I'm curious what changed?

---

