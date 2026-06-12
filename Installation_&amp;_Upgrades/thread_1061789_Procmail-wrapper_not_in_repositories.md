---
title: "Procmail-wrapper not in repositories?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by bluntknife on 2009-02-06
Hi,

I need to install and configure procmail-wrapper in order to enable spam filtering in virtualmin.
I've tried;
'apt-get install procmail-wrapper' but i receive;

'E: Couldn't find package procmail-wrapper'

I've found a couple of threads stating that they have successfully installed procmail-wrapper in this way on Ubuntu 8.04 but I am using 8.10.

Can it be installed?

Thanks.

---

### Post by Partyboi2 on 2009-02-06
That package is not in the Ubuntu repostories, You would need to find a deb package for it or compile it from source.


Edit: looks like you might be able to download the deb from [http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-hardy/main/binary-i386/](http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-hardy/main/binary-i386/)[]("http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-hardy/main/binary-amd64/")

---

### Post by bluntknife on 2009-02-06
Thanks for your quick reply.

Is it likely that if I install this 3rd party package I could break something in my Ubuntu build?

Thanks.

EDIT:  Sorry for 3rd party I should have said different version of Ubuntu.  This is a hardy package and I'm running Intrepid.

---

### Post by Partyboi2 on 2009-02-06
You might be ok using the hardy package generally you will have problems when you try installing packages from a later release, not so much with early releases.

---

### Post by bluntknife on 2009-02-06
Okay thanks.  I'll give it a go!

---

