---
title: "Package for &quot;Software Sources&quot;"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ptrico on 2009-10-31
Hi,

I'm currently using Hardy 8.04. I'd like to start the long chain of upgrades to 9.10.

For some reason, I don't have the "Software Sources" GUI tool available in System>Administration and have been unable to find how to install it via google and forums.

Can somebody point me in the right direction? What is the package that "Software Sources" comes with?

Thanks for your help

---

### Post by sliketymo on 2009-10-31
> **ptrico said:**
> Hi,

I'm currently using Hardy 8.04. I'd like to start the long chain of upgrades to 9.10.

For some reason, I don't have the "Software Sources" GUI tool available in System>Administration and have been unable to find how to install it via google and forums.

Can somebody point me in the right direction? What is the package that "Software Sources" comes with?

Thanks for your help

Word of caution: in-place upgrades do not always go well.If at all possible,you will have a much better experience downloading the .iso for the version you intend stopping at,burning it to disk,and doing a clean install.
If ,however,you decide to continue,you should be able to find what your looking for by going to: System>Administration>Software sources from your top panel.
It should be there,unless you have un-instaled it at some point.

---

### Post by Partyboi2 on 2009-10-31
To reinstall Software Sources you can open a terminal and 
```
sudo apt-get --reinstall install ubuntu-desktop
```this should reinstall any packages you maybe missing.

---

### Post by donato roque on 2009-10-31
It's a lot less hassle if you download the [Ubuntu 9.10 iso from this link]("http://www.ubuntu.com/getubuntu/download").
Then do a clean install.  Here are links on [how to do a clean install]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html").

---

### Post by ptrico on 2009-11-01
> To reinstall Software Sources you can open a terminal and 
     Code:
     sudo apt-get --reinstall install ubuntu-desktop 
this should reinstall any packages you maybe missing.     Thanks Partyboi2, with your instruction I was able to determine that the package is [software-properties-gtk]("http://packages.ubuntu.com/karmic/software-properties-gtk")

To sliketymo and donato roque, thanks for your suggestions. This computer is a server without a CD/DVD drive, so a network upgrade was all I could do. In any case, I upgraded to 8.10, 9.04 and finally 9.10. Everything seems to be working fine!

---

