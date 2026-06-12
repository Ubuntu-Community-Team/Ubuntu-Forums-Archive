---
title: "rapidshare mirror for ubuntu-9.04-desktop-i386.iso"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by weehawky on 2009-04-23
each file besides d is 191MB. (200000 KB split -b)

use type xaa xab xac xad > ubuntu-9.04-desktop-i386.iso 

MD5sum should be "66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso
"

[http://releases.ubuntu.com/9.04/MD5SUMS](http://releases.ubuntu.com/9.04/MD5SUMS)

or use cat instead of type.

File downloaded from  [http://ftp.tu-chemnitz.de/pub/linux/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso](http://ftp.tu-chemnitz.de/pub/linux/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso) originally.

[http://rapidshare.com/files/225025245/xad](http://rapidshare.com/files/225025245/xad)
[http://rapidshare.com/files/225025806/xaa](http://rapidshare.com/files/225025806/xaa)
[http://rapidshare.com/files/225025937/xab](http://rapidshare.com/files/225025937/xab)
[http://rapidshare.com/files/225026139/xac](http://rapidshare.com/files/225026139/xac)

for proof..

public_html/ubuntujaunty$ rm ubuntu-9.04-desktop-i386.iso
public_html/ubuntujaunty$ cat xaa xab xac xad > ubuntu-9.04-desktop-i386.iso
public_html/ubuntujaunty$ md5sum ubuntu-9.04-desktop-i386.iso
66fa77789c7b8ff63130e5d5a272d67b  ubuntu-9.04-desktop-i386.iso

---

