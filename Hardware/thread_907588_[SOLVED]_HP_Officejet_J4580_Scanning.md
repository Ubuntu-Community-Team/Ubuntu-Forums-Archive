---
title: "[SOLVED] HP Officejet J4580 Scanning?"
date: 2008-09-01
forum: Hardware
---

### Post by smah77 on 2008-09-01
Hey all, I got an HP Officejet J4580 All-in-One printer/fax/scanner, and printing works great, but XSANE doesn't recognize the scanner.  I've also tried HPLIP, but nothing there either.  Any tips would be appreciated.

---

### Post by KaSKAraS on 2008-09-02
> **smah77 said:**
> Hey all, I got an HP Officejet J4580 All-in-One printer/fax/scanner, and printing works great, but XSANE doesn't recognize the scanner.  I've also tried HPLIP, but nothing there either.  Any tips would be appreciated.
Hi, same problem here.

I thought it was supported but there is no info anywhere about scanning anywhere :(

---

### Post by KaSKAraS on 2008-09-02
Hi again,

after finding out a little bit I remembered hplip tools. After executing hp-check I got the following message:

"Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes sane-utils"

So I installed these packages but I got the same error and this text:

"Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)"

In this page I found a new version (I downloaded the automatic installer from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) which is fine for ubuntu 8.x)

Just execute it and follow the instruction.

Regards & Good luck

---

### Post by smah77 on 2008-11-11
And it works!?  With theJ4580?!  ZOMG awesome!  You've made me the happiest boy in the world!

> **KaSKAraS said:**
> Hi again,

after finding out a little bit I remembered hplip tools. After executing hp-check I got the following message:

"Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes sane-utils"

So I installed these packages but I got the same error and this text:

"Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)"

In this page I found a new version (I downloaded the automatic installer from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) which is fine for ubuntu 8.x)

Just execute it and follow the instruction.

Regards & Good luck

---

### Post by katon on 2009-09-20
hi, im interested in doing the next thing:
merge 2 pdf that were created with scanner with autofeeder (ADF)
from HP J4580 . It has not the DUPLEX option so i need to scan one side of the pages and then the other side.
How can i merge automatically and simple the two PDF the first is the one side pages the second is the back.
Thanks

---

### Post by rick71 on 2009-11-13
katon, 

I scan even pages to an even folder and odd pages to an odd folder. I found this script:

```
#1/bin/bash

j=1
for i in *.jpg;
do
mv $i $j.jpg
j=$((j+2));
done
```

I set j to the number of the first page in the folder. Once the script is run in each folder, I put the scans in one folder, and they're all in numerical order. You can change the file extension to whatever the extension is on your files.

I hope this helps.

---

