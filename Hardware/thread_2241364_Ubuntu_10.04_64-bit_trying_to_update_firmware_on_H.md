---
title: "Ubuntu 10.04 64-bit trying to update firmware on HP smart array E200i"
date: 2014-08-25
forum: Hardware
---

### Post by peter133 on 2014-08-25
I downloaded an executable file from the hp website, CP012811.scexe
at first I got the following errors, popd not found, pushd not found, ccissflash not found.
after searching for an hour on google someone suggested to change the first line from /bin/sh to /bin/bash.
this removed the errors above. but instead I get gzip: stdin: unexpected end of file
./CP012811.scexe: cannot decompress ./CP012811.scexe

the file can be found at [http://support.valetech.net:8080/Public/G5%20ml350%20firmware/hp/swpackages/CP012811.scexe](http://support.valetech.net:8080/Public/G5%20ml350%20firmware/hp/swpackages/CP012811.scexe)
or somewhere at downloads.linux.hp.com 

I need help with this. please

---

### Post by Mark Phelps on 2014-08-25
Perhaps the info in the link will let you see what's in the file: [http://www.popmartian.com/tipsntricks/2014/01/17/how-to-extract-the-contents-of-a-scexe-file/]("http://www.popmartian.com/tipsntricks/2014/01/17/how-to-extract-the-contents-of-a-scexe-file/")

---

### Post by peter133 on 2014-08-26
Thank you! now I have something to play around with.

---

