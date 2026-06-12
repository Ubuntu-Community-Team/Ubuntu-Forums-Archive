---
title: "Installing Adobe Reader"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Cuba71 on 2009-03-05
I finished installing Adobe Reader 8.1.3 by converting the RPM to a deb using alien and then installing using dpkg.
Now when I try to change the file associations for pdf files y don't find adobe reader in the list.
Any ideas?
Thank you****

---

### Post by taurus on 2009-03-05
Let's see where it is installed to.

```
whereis acroread
```

---

### Post by 73ckn797 on 2009-03-05
Why go through the trouble of installing via the rpm to deb? It is available through Synaptic Package Manager and installs flawlessly.

---

### Post by taurus on 2009-03-05
> Why go through the trouble of installing via the rpm to deb? It is available through Synaptic Package Manager and installs flawlessly.

It is not in the standard repos, only Medibuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

### Post by Cuba71 on 2009-03-05
Taurus:
it's at /usr/bin/acroread

I tried installing from Medibuntu and I got a dependency error on libstdc++5

---

### Post by 73ckn797 on 2009-03-05
> **taurus said:**
> It is not in the standard repos, only Medibuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)


I stand corrected. I have Medibuntu enabled and was not thinking.

---

### Post by taurus on 2009-03-05
> **Cuba71 said:**
> Taurus:
it's at /usr/bin/acroread

I tried installing from Medibuntu and I got a dependency error on libstdc++5

You need to remove that version and then install the one from Medibuntu's.

```
sudo dpkg -r acroread
```

---

### Post by Cuba71 on 2009-03-06
Thank you all for your help.

I solved the problem by downloading a deb package from Adobe web page.

---

