---
title: "Installing KScope"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by harezmi on 2009-06-05
Hello
I use Ubuntu 9.04 and tried to install KScope application but when I search it, there's no kscope packege in Ubuntu 9.04.
Anybody could install it?

Thanks

---

### Post by harezmi on 2009-06-08
> **harezmi said:**
> Hello
I use Ubuntu 9.04 and tried to install KScope application but when I search it, there's no kscope packege in Ubuntu 9.04.
Anybody could install it?

Thanks

Any help, please?

---

### Post by ikki wang on 2009-06-19
> **harezmi said:**
> Any help, please?
 Kscope is removed from Ubuntu 9.04, but I want to give Ubuntu 9.04 a try with Kscope....just for fun :)

Reference web page:
_[http://zhubangbing.blog.163.com/blog/static/52609270200941915459486/](http://zhubangbing.blog.163.com/blog/static/52609270200941915459486/)_
_[http://blog.verycd.com/yoyopub/showentry=22855](http://blog.verycd.com/yoyopub/showentry=22855)_
_[http://adrianhuang.blogspot.com/2007/09/trace-code-gvimctagscscope.html](http://adrianhuang.blogspot.com/2007/09/trace-code-gvimctagscscope.html)_



The .deb can be download here:

1.9.4(Not recommend, de-feature too many, not stable version) :
[https://launchpad.net/~nizamov-shawkat/+archive/ppa/+files/kscope_1.9.4-0ubuntu1_i386.deb](https://launchpad.net/~nizamov-shawkat/+archive/ppa/+files/kscope_1.9.4-0ubuntu1_i386.deb)

1.6.0 :
[http://archive.ubuntu.com/ubuntu/pool/universe/k/kscope/kscope_1.6.0-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/kscope/kscope_1.6.0-1_i386.deb)

Reference procedures (I did them all):

[COLOR=#E36C09]wget ftp.debian.org/debian/pool/main/k/kdebase/kate_3.5.9.dfsg.1-6_i386.deb[/COLOR]
[COLOR=#E36C09]ar x kate_3.5.9.dfsg.1-6_i386.deb[/COLOR]
[COLOR=#E36C09]tar xzf data.tar.gz[/COLOR]
[COLOR=#E36C09]sudo cp usr/lib/libkateinterfaces.so.0.0.0 /usr/local/lib[/COLOR]
[COLOR=#E36C09]sudo ldconfig[/COLOR]
[COLOR=#E36C09]sudo cp usr/lib/libkateutils.so.0.0.0 /usr/local/lib[/COLOR]
[COLOR=#E36C09]sudo ldconfig[/COLOR]

My install procedures:

1). Install vim (with X support)

2). Install plugins (ctags, cscope)
2.1). download taglist and extract to ~/.vim/
2.2). download cscope.vim and put to ~/.vim/plugin/

$ sudo apt-get (-f) install exuberant-ctags
$ sudo apt-get (-f) install cscope

3). QT libraries:
$ sudo apt-get install libqtcore4
$ sudo apt-get install libqtgui4

4). Kate support
$ sudo apt-get install kate

5). Install libqscintilla2-5
$ sudo dpkg -i libqscintilla2-5_2.3.2-1.1_i386.deb

6). Install kdelibs4c2a
$ sudo apt-get install kdelibs4c2a

7). Install graphviz
$ sudo apt-get install graphviz

8).  Install kscope
$ sudo dpkg -i kscope_1.6.0-1_i386.deb

Congratulations!! Kscope is shown in your Application menu.

---

### Post by lysisius on 2009-08-15
this is very comprehensive and helpful. thanks a lot

---

### Post by adyp2003 on 2009-08-21
Thank you very much for writing this tutorial.
You saved me a lot of time.

---

### Post by panange on 2009-11-19
a billion thanks......:D

---

### Post by pkchill88 on 2010-09-27
Nice. Thanks to this post, i was able to install kscope. 
For some reason, the link to download kate deb package is obsolete. 

Here is the working link: [ftp://ftp.debian.org/debian/pool/main/k/kdebase/kate_3.5.9.dfsg.1-6+lenny1_i386.deb](ftp://ftp.debian.org/debian/pool/main/k/kdebase/kate_3.5.9.dfsg.1-6+lenny1_i386.deb)

---

