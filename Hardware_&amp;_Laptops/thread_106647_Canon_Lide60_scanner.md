---
title: "Canon Lide60 scanner"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by vector on 2005-12-21
Hi 
Ok im totally lost.
I checked sane yesterday to be sure it supported a lide60 which it does.
So I purchased the scanner plugged it in and got notin.
I started reading the Sane page and became very insane.
however i tried a few things but dont claim to understand what i was doing :(

*~$ sudo sane-find-scanner -v*
.......lots of fails
[I]checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
found USB scanner (vendor=0x04a9 [Canon], product=0x221c [CanoScan], chip=GL841) at libusb:005:004[/I]
that must be good?

[I]~$  scanimage -L
No scanners were identified.[/I]

[I]~$ cat /proc/filesystems
nodev   usbfs[/I]
but no mention of *nodev   usbdevfs*

at this point im way confused some lend a guiding hand?
BTW i whipped over to the dark side and tested the scanner on a winxp box,,its fine)

---

### Post by vector on 2006-01-11
surely someone has some ideas? i still cant get it to work
its driving me mad to have to boot the windows box just to scan some stuff in
 pretty please

---

### Post by ihristov on 2006-02-18
I installed my LiDE 50 yesterday and it works great.

The issue is that the Cannon LiDE scanners use the **genesys** backend, which is not included in the version of sane that comes with the standard Ubuntu packages. At least not for Hoary [Ubuntu 5.04] (which is what I have).

To check if you have the **genesys** backend simply 
```

# search for the word on your system
locate genesys
# or see if you can open the manual
man genesys
# or for the config file
ls -l /etc/sane.d/genesys.conf

```

If you don't have it, which you probably don't, you have to install it from source. To do so I did the following:

[COLOR="Blue"]Prepare to compile[/COLOR]

Make sure you have installed the usblib-dev package, otherwise ./configure below will not configure the genesys backend for compiling
```

sudo apt-get install libusb-dev

```

If you don't have the packages for compiling (you will get errors that it can't find make, etc) you will need to install the meta development package
```

sudo apt-get install build-essential

```

Get sane source and compile it
```

mkdir sane
cd sane
wget http://alioth.debian.org/download.php/1347/sane-backends-1.0.17.tar.gz
tar -xzf sane-backends-1.0.17.tar.gz 
cd sane-backends-1.0.17

./configure
make
sudo make install

# now your scanner should show up
/usr/local/bin/scanimage -L

```

If you leave the defaults in ./configure (like I did above) the new sane will be installed in /usr/local. Now we have 2 different versions of sane installed on our system. The old Ubuntu deb distribution which resides in /etc/sane.d/ and /usr

I don't know what is the correct way to remove the old version. I was afraid that if I use apt-get to remove the package it will remove all the packages that depend on it, including xsane. I am not even really sure which package is the sane backend. Maybe it's sanelib, which has a large number of dependents (apt-cache showpkg libsane). Maybe it's possible to force apt to only remove the files, but I don't know how. Anyhow, here is what I did to manually replace the files.

```

cd /etc
mv  sane.d  sane.d-ubuntu
ln -s /usr/local/etc/sane.d sane.d
cd /usr/bin
mv sane-find-scanner sane-find-scanner.ubuntu
ln -s /usr/local/bin/sane-find-scanner sane-find-scanner
cd /usr/lib
mkdir libsane.ubuntu
mv sane/ libsane.* libsane.ubuntu/
ln -s /usr/local/lib/sane sane
ln -s /usr/local/lib/libsane.la libsane.la
ln -s /usr/local/lib/libsane.so.1.0.17 libsane.so.1.0.17
ln -s libsane.so.1.0.17 libsane.so
ln -s libsane.so.1.0.17 libsane.so.1

```

Again, note that this is probably not the correct way to do this. I would appreciate if someone can comment on how is this normally done. Maybe would have been sufficient to simply configure with the appropriate folders, something like
./configure --prefix=/usr --sysconfdir=/etc

I am not sure.

Anyhow, this works for me with no problems that I can see so far.

Edit 19-Jul-2007 - my LiDE 50 works out of the box in Ubuntu 7.04 and I think it did in 6.06 as well, I can't remember this for sure

---

### Post by vector on 2006-03-07
thanks for that ill give it a try when i have this other problem solved.
I wonder how long it will take for the ubuntu breezy to update to the latest sane and save all this hassle??

---

### Post by rayburn on 2006-03-10
ihristov

Thank you! I have just followed your instructions above to get my Canon Lide 30 scanner working for the first time under Linux, many, many thanks.

There is one flaw in the above code:

'usblib-dev' should read 'libusb-dev'

This caused me a little bother at first, however, I stumbled across the solution and everything now works. Great work on your part.

One other point, for my scannner I used the Plustek back end rather than the genesys.

---

### Post by Shampyon on 2006-03-20
Tried out this fix, and "scanimage -L" now shows my scanner. YES. Still won't show up when I run the XSANE GUI (scanner not available), but this is one step closer to getting this thing working.

Should I continue on to the step "removing old version" step? Or is there something I should be aware of before I do?

---

### Post by Omnios on 2006-12-28
> **Shampyon said:**
> Tried out this fix, and "scanimage -L" now shows my scanner. YES. Still won't show up when I run the XSANE GUI (scanner not available), but this is one step closer to getting this thing working.

Should I continue on to the step "removing old version" step? Or is there something I should be aware of before I do?


 Try running sane as root, This may be a similar problem that used to happen with gnome2 where it would not detect the usb without running it as root.

---

### Post by Omnios on 2006-12-28
Um quick question My Dad has dapper and I have edgy. I would like to make a deb of the backend for him. Is it possible to use checkinstall in Edgy that would work with dapper?

 And does anyone have a dapper deb for the backend?

---

### Post by bratliff on 2007-07-19
How is the quality of the scans using the sane driver?

bobinpanama, where getting hardware is a problem


> **rayburn said:**
> ihristov

Thank you! I have just followed your instructions above to get my Canon Lide 30 scanner working for the first time under Linux, many, many thanks.

There is one flaw in the above code:

'usblib-dev' should read 'libusb-dev'

This caused me a little bother at first, however, I stumbled across the solution and everything now works. Great work on your part.

One other point, for my scannner I used the Plustek back end rather than the genesys.

---

### Post by ihristov on 2007-07-19
> **bratliff said:**
> How is the quality of the scans using the sane driver?

bobinpanama, where getting hardware is a problem

I would say excellent, but I am using it only for documents.
For pictures, I cannot say. I suspect it will be quite good.

BTW: This thread is kind of old. The scanner is plug-n-play in the latest version (Ubuntu 7.04), I suspect it is also in 6.10. I did run 6.06 for a while and if I remember correctly a Lide 50 worked out of the box there as well.

---

### Post by ihristov on 2007-07-19
> **rayburn said:**
> There is one flaw in the above code:

'usblib-dev' should read 'libusb-dev'

I fixed the typo in the original post.

---

