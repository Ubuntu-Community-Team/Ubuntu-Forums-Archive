---
title: "CDROM drive does not open"
date: 2008-07-02
forum: Hardware
---

### Post by DougAlder on 2008-07-02
Dell latitude D620
Hardy heron - all updates

The CDROM drive lights up when I push the open button but it does not open. I have no icon for the CD-ROM drive on the desktop and it doesn't show up listed in file manager so I'm assuming here it isn't mounted except that if I go into the Brasero Disk Burner app it correctly identifies the CD-ROM drive as a TS-L462C. I found a driver over on Dell's FTP site and downloaded it (btw how do I use apt-get to pull a file off their server? I tried apt-get [http://www.dell-drivers.com/R147358.EXE](http://www.dell-drivers.com/R147358.EXE) but that didn't work :) ) - anyway I now have this file, R147358.EXE, sitting on my desktop and I don't know how to install it, or even if that's the right thing to do.

---

### Post by dominiquec on 2008-07-02
You can't install the EXE file via apt-get.  The EXE file is not a Debian package.

You might want to try this: open a terminal and type "eject"  See what message comes out.

---

### Post by DougAlder on 2008-07-02
Perfect thanks - that works

---

