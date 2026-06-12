---
title: "apt-get update trouble"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by lordbux on 2009-08-31
hai 
when i tried apt-get update
i am getting this error 

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_IN.bz2  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_IN.bz2  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://moonbase-beta.openpanel.com/pkg/debian4/i386/dists/openpanel/Release.gpg  Could not resolve 'moonbase-beta.openpanel.com'

W: Failed to fetch http://moonbase-beta.openpanel.com/pkg/debian4/i386/dists/openpanel/main/i18n/Translation-en_IN.bz2  Could not resolve 'moonbase-beta.openpanel.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```:confused:

please help
thanks in advance

---

### Post by slakkie on 2009-08-31
Looks like you have DNS issues. Or change the gb.archive lines to uk.archive lines and see if that works. Although I suspect something fishy with your resolv.conf file..

---

### Post by ibutho on 2009-08-31
Is your internet connection working properly? If it is, it could be that the mirror you are trying to access is down or not working properly. You could wait a few hours and try again or change your mirrors.

---

### Post by lordbux on 2009-08-31
thank you friends.. i think it is a mirror problem..
connection is perfect.... 
i will wait and see.
then try changing mirrors

---

