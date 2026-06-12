---
title: "scanner installation"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by chudder on 2009-05-08
Hi Everyone,

Long story short, I'm trying to install an Epson NX100 all-in-one.  I have got the printer working as good as it's going to get but the scanner won't work.  I know that XSANE doesn't support this model but I'm trying to install the iscan utility backend from [http://http://www.avasys.jp/english/linux_e/]("http://http://www.avasys.jp/english/linux_e/").  I download the .deb file from [http://http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do").  

But the .deb installation gives the error, "Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)"

I notice from synaptic that have the libltdl7 which for some reason doesn't satisfy the dependency.

Any help would be appreciated

Thanks

---

### Post by albinootje on 2009-05-08
> **chudder said:**
> 
But the .deb installation gives the error, "Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)"


You could try installing this one (From Ubuntu Hardy) :
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

---

### Post by chudder on 2009-05-09
> **albinootje said:**
> You could try installing this one (From Ubuntu Hardy) :
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

okay, thanks.  How would I uninstall it if needed?  Thank you

---

### Post by albinootje on 2009-05-09
> **chudder said:**
> okay, thanks.  How would I uninstall it if needed?

With Synaptic Package Manager you can uninstall it.

---

### Post by chudder on 2009-05-09
> **albinootje said:**
> With Synaptic Package Manager you can uninstall it.

the reason I ask is because I'm running Jaunty and I don't have the hardy backports so i thought I would have to do a manual uninstall.  thanks for your replies.  Let me know if this is the case.

---

### Post by albinootje on 2009-05-09
> **chudder said:**
> the reason I ask is because I'm running Jaunty and I don't have the hardy backports so i thought I would have to do a manual uninstall.  thanks for your replies.  Let me know if this is the case.

This (libtldl3) is an old library from Hardy, it's not a backport.
I just tested it on my Jaunty installation, and it installed without problems. HTH.

---

### Post by todak on 2009-05-09
Nevermind. I need to read more carefully, first!

---

