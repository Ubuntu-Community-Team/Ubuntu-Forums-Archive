---
title: "Artec Scanner Detected but &quot;invalid argument&quot;"
date: 2009-06-12
forum: Hardware
---

### Post by ricster on 2009-06-12
I have an Artec 48 USB scanner, and have managed to install the firmware, edit the usb rules so non root users can scan and confirm that the conf file is pointing to the firmware too (inc checking for case sensitivity). I even chmoded the firmware file to make sure it didnt have read issues, but still when i start xsane and select the scanner it quits out saying invalid argument... I've attached my config and the firmware if that helps anyone solve my problem... help!

---

### Post by ricster on 2009-06-12
Well i fixed this by editing the config file. Firstly i ran sane-find-scanner at the prompt and it brought back the vendor and product as

0x05d8 0x4004

but the conf file listed these as

usb 0x05d8 0x4003


so i changed that, slao my device claims to be an e+ Pro so i changed the line

option ePlusPro   0

to

option ePlusPro   1


but that caused the scan to be corrupt, changing it back to zero fixed that. Hope this helps people in the future! 

Now i can see the device and run xsane it only scans a portion of the top right of the document, even though the markers say 20cm by 25 (ish) it only actually scans and shows (zoomed in to fill the dimensions) the top 8x6cm ish. could this be a dpi config issue?

---

