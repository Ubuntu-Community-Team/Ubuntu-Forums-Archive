---
title: "Installing Open Office 3"
date: 2008-10-17
forum: General Help
---

### Post by Bablefish on 2008-10-17
I noticed on another forum that there was a newer version of Open Office was available for download, namely Open Office 3. I downloaded it and when I unzipped the file I was confronted with something I was expecting 2 folders with 46 deb files that needed to be installed. Since it came with no install instructions so I turn to you for HELP. I know I have in uninstall the Open Office I already have installed. But is there any one file I needed to start with? Those 46 files sorta overwhelmed me.

---

### Post by Kimm on 2008-10-17
> **Bablefish said:**
> I noticed on another forum that there was a newer version of Open Office was available for download, namely Open Office 3. I downloaded it and when I unzipped the file I was confronted with something I was expecting 2 folders with 46 deb files that needed to be installed. Since it came with no install instructions so I turn to you for HELP. I know I have in uninstall the Open Office I already have installed. But is there any one file I needed to start with? Those 46 files sorta overwhelmed me.

Nope, as long as you uninstall the "standard" Open Office, you can install those packages in any order.

I suggest doing this (in terminal, in the directory with the packages):
```

sudo dpkg -i *deb

```
Since that will install every single package in the directory :)
Then install the menu-items package afterwards.

---

### Post by scouser73 on 2008-10-17
> **Bablefish said:**
> I noticed on another forum that there was a newer version of Open Office was available for download, namely Open Office 3. I downloaded it and when I unzipped the file I was confronted with something I was expecting 2 folders with 46 deb files that needed to be installed. Since it came with no install instructions so I turn to you for HELP. I know I have in uninstall the Open Office I already have installed. But is there any one file I needed to start with? Those 46 files sorta overwhelmed me.

This tutorial will show you how; [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

---

