---
title: "request md5sum hash for edubuntu 8.10"
date: 2008-11-26
forum: General Help
---

### Post by guatebus on 2008-11-26
Hi, does anyone know if there's a md5sum hash for edubuntu 8.10 ?

There isn't one  @  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

this is the hash from my iso file  7944aaaaf645571dd6e0a9db700394e9

Thanks.  :-\"

---

### Post by taurus on 2008-11-26
Looks about right.

```

45c572d3bc95db05ed8ab37bae75b750 *edubuntu-8.10-addon-amd64.iso
**[COLOR="Blue"]7944aaaaf645571dd6e0a9db700394e9 *edubuntu-8.10-addon-i386.iso[/COLOR]**
3231c37e95a4facf4106ddb6ed560981 *edubuntu-8.10-beta-addon-amd64.iso

```

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edubuntu/8.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edubuntu/8.10/)

---

### Post by guatebus on 2008-11-26
Thanks Taurus. The strange thing is this md5sum checks out OK, as well as the md5sum for the burnt cd - checked it with:

```
md5sum -c md5sum.txt | grep -v 'OK$'

```

When I tried to install, however, I got an error (cd read) 

Error output by synaptic:

E: Could not open folder /media/cdrom0/dists/intrepid/main/binary-i386/Packages - open (2 Directory does not exist)
E: Unable to determine the file size - fstat (9 Invalid file descriptor)
E: Could not open folder /media/cdrom0/dists/intrepid/main/debian-installer/binary-i386/Packages - open (2 Directory does not exist)
E: Unable to determine the file size - fstat (9 Invalid file descriptor)

W: Hash mismatch for: main/binary-i386/Packages


Comments/suggestions are expected and welcome!

Thanks again!

---

