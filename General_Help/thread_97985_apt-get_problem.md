---
title: "apt-get problem"
date: 2005-12-02
forum: General Help
---

### Post by davebradford on 2005-12-02
i can't get updates i keep getting this message..

apt-get: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

---

### Post by aysiu on 2005-12-02
I've never encountered that error, so I can't help, but [Google's encountered it 666 times](http://www.google.com/search?num=100&hl=en&safe=off&q=libstdc%2B%2B.so.6:+cannot+open+shared+object+file:&spell=1)

---

### Post by teaker1s on 2005-12-02
A failed installation blocks further operations in synaptic 	

Under some rare circumstances the actual installation or removal of a package can fail. As a consequence all other marked changes are canceled, too.

Synaptic Package Manager requires a clear environment with no half installed packages to perform additional changes. But at the moment there is no way to continue canceled installations within Synaptic Package Manager.

To fix this situation type the following command in a terminal, then press Return:
apt-get install -f

---

