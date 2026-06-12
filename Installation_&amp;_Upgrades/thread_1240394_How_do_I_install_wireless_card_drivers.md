---
title: "How do I install wireless card drivers"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by davidmorgen on 2009-08-14
My wireless connection is not working after having installed Ubuntu 9.04. If I have found my windows wireless card driver, how do I install and activate it in Ubuntu?

Thanks!

---

### Post by raymondh on 2009-08-14
> **davidmorgen said:**
> My wireless connection is not working after having installed Ubuntu 9.04. If I have found my windows wireless card driver, how do I install and activate it in Ubuntu?

Thanks!

What kind of file is it?  When you right click on it, do you have the option to install (using your built-in package manager)?

Here's a  [link]("http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm") for .deb files (just in case).

---

### Post by davidmorgen on 2009-08-14
Raymond, I actually referring to having found a Windows driver on the Net.  Can I install it and use it with Ubuntu, or do I have to find the equivalent Linux driver?

---

### Post by raymondh on 2009-08-14
> **davidmorgen said:**
> Raymond, I actually referring to having found a Windows driver on the Net.  Can I install it and use it with Ubuntu, or do I have to find the equivalent Linux driver?

Some members have used ndiswrapper in their ubuntu/linux machines to use windows' based drivers

[url]http://ubuntuforums.org/showthread.php?t=885847[/url

You can, as well, browse the homepage of the card manufacturer and see if they offer a linux driver to download.  That will be better, IMHO.

---

### Post by jeb800e on 2009-08-14
Go to System -- Administration -- Synaptic Package Manager

Type in "NDISWrapper" after pressing the "Search" button. 3 files should come up. Install all 3. One of the files is a graphical interface of NDISWrapper, making it much, much easier to use! 
Hope that helps!

---

