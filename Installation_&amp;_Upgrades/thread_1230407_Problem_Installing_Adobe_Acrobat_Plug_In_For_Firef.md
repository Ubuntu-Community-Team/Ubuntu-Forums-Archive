---
title: "Problem Installing Adobe Acrobat Plug In For Firefox"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by loweehahn on 2009-08-03
I have a problem while installing Adobe Acrobat Plug In. This message: bash: ./AdbeRdr9.1.2-1_i486linux_enu.bin: No such file or directory will appear every time I try to install by typing ./AdbeRdr9.1.2-1_i486linux_enu.bin. How to overcome this problem or anyone can suggest another idea to install?

---

### Post by oldos2er on 2009-08-03
Are you in the directory where the Adobe file is? If so, try running
```
chmod a+x AdbeRdr9.1.2-1_i486linux_enu.bin
```
then retry the command.

---

### Post by loweehahn on 2009-08-04
What do you mean the directory where the adobe file is? I downloaded it onto my desktop.

---

### Post by lykeion on 2009-08-04
First of all, the desktop is a directory, and second of all like oldos2r says you have to make the file executable to be able to install it.

But if you'd like the adobe reader plugin I'd suggest you install it with synaptic instead like this:

First add the repository. Go to System > Administration > Software Sources > Third Party Software Tab and check the [http://archive.canonical.com](http://archive.canonical.com) lines.

Close down Software Sources and start Synaptic (System > Administration > Synaptic Package Manager). Search for package **acroread** and install it. You'll get Adobe Reader v9.1.2

---

### Post by loweehahn on 2009-08-05
I did as you told but in the Synaptic Package Manager acroread doesn't produce any result. However after I checked both the carnonical links there are a few downloading errors.

---

### Post by oldos2er on 2009-08-05
Open a terminal, and run these commands one at a time:
```
cd Desktop
chmod a+x AdbeRdr9.1.2-1_i486linux_enu.bin
sudo ./AdbeRdr9.1.2-1_i486linux_enu.bin
```

---

### Post by nnorman on 2009-08-05
archive.canonical.com appears to be functioning again ... not sure what was wrong with it.

I recommend you try lykeion's solution.

---

### Post by loweehahn on 2009-08-08
It worked!! Thanks a lot.

---

