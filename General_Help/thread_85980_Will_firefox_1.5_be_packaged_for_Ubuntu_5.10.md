---
title: "Will firefox 1.5 be packaged for Ubuntu 5.10?"
date: 2005-11-04
forum: General Help
---

### Post by realwhz on 2005-11-04
Hi,

I'm not familiar with the policy of Ubuntu.  So I wonder if a software with newer version in upstream will be packaged for current release of Ubuntu.  For example, firefox 1.5 candidate (1.5 may come soon) has released in upstream, will it be packaged for Ubuntu 5.10 in future.  Or will it be provided only in next release of Ubuntu?  Another example is OpenOffice.org 2.0.

Thank you.

---

### Post by Sykil on 2005-11-04
I'm sure a fan will package it, but I don't think you'll see it in Ubuntu's official repositories.

---

### Post by Manny C on 2005-11-04
When the Backports repositories open, v 1.5 will probably be released for Breezy. However the breezy-updates repos will not ship it afaik.

---

### Post by realwhz on 2005-11-04
Oh, I see.  Thank you all :-)

---

### Post by sb73542 on 2005-11-25
What are the breezy-updates repos used for?  I gather that they are not used for upgrading major releases of the apps shipped with a release of Ubuntu.

---

### Post by zlogic on 2005-11-26
I think it will appear in breezy-backports

---

### Post by cbudden on 2005-11-26
It is VERY easy to install by following the article in the wiki.

---

### Post by `GooZ´ on 2005-11-26
As for the OOo2, you can add these lines to your /etc/apt/sources.list:
```
#OpenOffice 2.0 final, not beta like ubuntu repos
deb http://people.ubuntu.com/~doko/OOo2 ./
```
You do this by typing in the terminal:
```
sudo gedit /etc/apt/sources.list
```
then you add those lines, and you save the file

---

