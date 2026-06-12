---
title: "Xerox Phaser 6128MFP"
date: 2014-05-23
forum: Hardware
---

### Post by Gatignol on 2014-05-23
Hi there,

Experience sharing :

How to install a Xerox Phaser 6128MFP on debian ubuntu x86 or x64 ?

Grab the drivers from [support.xerox.com]("http://www.support.xerox.com/support/phaser-6128mfp/downloads/enus.html?operatingSystem=linux&fileLanguage=en")
Extract all files (including rpm using alien for exemple)
As root, copy the files from the archive to your filesystem (*/usr/share/cups* **and** */usr/lib/cups/filter*)

Add the printer from cups (JetDirect socket://my.xerox.printer.ip:9100/)
Use the provided PPD file
```
 /usr/share/cups/model/Xerox/en/Xerox_Phaser_6128MFP_N.ppd
```

Try to print the test page...

If you run into an error like "***/usr/lib/cups/filter/Xerox_Phaser_6128MFP/XRM_PF failed***" and you are on _**x64**_, add the missing libraries :

```
sudo apt-get install ia32-libs
```

Vincent

---

