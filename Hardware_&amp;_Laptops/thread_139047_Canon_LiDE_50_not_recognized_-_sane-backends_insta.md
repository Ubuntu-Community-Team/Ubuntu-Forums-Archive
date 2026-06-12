---
title: "Canon LiDE 50 not recognized - sane-backends installed"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by habrys on 2006-03-03
Ok, I'm pretty lost trying to get my scanner to work.

[I]~$ sudo sane-find-scanner -v
..........
found USB scanner (vendor=0x04a9 [Canon], product=0x221c [CanoScan], chip=GL841) at libusb:005:004
.......[/I]
So the scanner can be seen by Ubuntu, right?
But:
[I]~$ sudo scanimage -L
No scanners were identified.
[/I]

I searched through the forums and found out, that my scanner is not supported by the default Breezy sane-backends and I have to download, build and install the last sane-backends (with genesys backend included). Which I did, like this:

```
mkdir sane
cd sane
wget http://alioth.debian.org/download.php/1347/sane-backends-1.0.17.tar.gz
tar -xzf sane-backends-1.0.17.tar.gz 
cd sane-backends-1.0.17

./configure --prefix=/usr --sysconfdir=/etc
make
sudo make install


```
I have had usblib-dev and build-essential installed before, no errors during configure and make, lots of warnings. The download path could be slightly different, but I downloaded from one of the official sane project mirrors. The sane project site says, my scanner is supported by the 1.0.17 version of backends.
But *sudo scanimage -L* and *sudo xsane* still says "no scanners found".

I tried to check if gensys is installed properly like that:

```
# search for the word on your system
locate genesys
# or see if you can open the manual
man genesys
# or for the config file
ls -l /etc/sane.d/genesys.conf
```

***locate genesys* and *man genesys* find nothing.** But the */etc/sane.d/genesys.conf* file exists. Is the genesys installation corrupted somehow? 

Someone could point me in the right direction, please?

---

