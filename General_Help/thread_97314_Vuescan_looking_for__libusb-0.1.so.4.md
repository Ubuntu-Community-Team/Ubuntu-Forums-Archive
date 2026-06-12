---
title: "Vuescan looking for  libusb-0.1.so.4"
date: 2005-11-30
forum: General Help
---

### Post by Niall Flinn on 2005-11-30
Hi, 

I'm trying to move to Ubuntu from Windows XP, and I really need to get my Nikon Coolscan IV operational, so I've downloaded  a copy of vuescan. When I run it, however, I get the following error:

./vuescan: error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory

I've checked the system, and libusb-0.1.so.4 is in /lib. How do I make vuescan aware of it? I'm currently launching vuescan from a directory on my desktop, because the documentation claims that it can run from anywhere. Is this correct, or do I need to put it somewhere specific?

Thanks,

Niall

---

### Post by BobW on 2006-04-11
I have the same probem on a AMD64 system. There seems to only be a 64 bit version of this library, not the 32 bit version the program is looking for.

---

### Post by dvo on 2007-03-10
Yes, the problem is that vuescan expects the 32bit version of  libusb-0.1.so.4 .

I've been successful providing it to vuescan as follows:
Load libusb-0.1-4_0.1.12-6_i386.deb from e.g.  [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibu%2Flibusb%2Flibusb-0.1-4_0.1.12-6_i386.deb&md5sum=42c0960ee3a9b4b4fc244ab8c271f539&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibu%2Flibusb%2Flibusb-0.1-4_0.1.12-6_i386.deb&md5sum=42c0960ee3a9b4b4fc244ab8c271f539&arch=i386&type=main)
Then execute
```

mkdir tempdir
sudo dpkg -x libusb-0.1-4_0.1.12-6_i386.deb tempdir
sudo mv tempdir/lib/libusb-0.1.so.4* /usr/lib32

```

Hope this helps,
  David

---

