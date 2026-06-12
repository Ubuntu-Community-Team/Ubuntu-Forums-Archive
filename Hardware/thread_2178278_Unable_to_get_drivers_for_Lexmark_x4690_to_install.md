---
title: "Unable to get drivers for Lexmark x4690 to install properly"
date: 2013-10-02
forum: Hardware
---

### Post by nesretep on 2013-10-02
I am running 13.04 Kubuntu, and have downloaded the linux printer driver from the website.  I followed the instructions on some older forum posts to no avail.  Basically I am extracting the ZIP file and executing the script file it contains using:
```
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh

```
The installer opens, has me agree to terms and conditions, and starts extracting files.  It then pops up a msg saying "Failed to install" and an OK button.  After clicking OK, everything related to the installer closes.

Any help would be appreciated.

PS: Called Lexmark and they just said it wouldn't work on any version newer than 11.04.  My guess is that is just the latest it has been tested on.

---

### Post by nesretep on 2013-10-03
I was finally able to get the printer part to work by following these commands I found elsewhere online:
```
sudo apt-get install ia32-libs-multiarch xz-lzma 
wget [http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz) -O lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz 
tar xzvf lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz 
./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark 
cd lexmark 
tar xJvf instarchive_all 
dpkg-deb -I lexmark-08z-series-driver-1.0-1.i386.deb 
mkdir raw-lexmark-archive 
dpkg-deb --raw-extract lexmark-08z-series-driver-1.0-1.i386.deb raw-lexmark-archive 
sed -i "/^ $/d" raw-lexmark-archive/DEBIAN/control 
cat raw-lexmark-archive/DEBIAN/control 
dpkg-deb -b ./raw-lexmark-archive fixed-lexmark-08z-series-driver-1.0-1.i386.deb 
sudo dpkg -i fixed-lexmark-08z-series-driver-1.0-1.i386.deb 
```


Basically it looks like it builds a new .deb package from the files in the original package. After I installed the new "fixed" version, the drivers were listed in the add printer dialog under Lexmark.

---

