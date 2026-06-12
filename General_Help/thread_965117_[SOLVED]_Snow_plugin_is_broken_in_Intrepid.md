---
title: "[SOLVED] Snow plugin is broken in Intrepid"
date: 2008-10-31
forum: General Help
---

### Post by olavjunior on 2008-10-31
```
/usr/bin/compiz.real (core) - Error: Plugin 'core' has ABI version '20080828', expected ABI version '20080401'
```

Should we file a bug?

---

### Post by loomsen on 2008-10-31
About what? Did you read the output? Different versions obv, you prlly have two different sources for compiz and things messed up.

[[img]http://img518.imageshack.us/img518/4050/screenshot31gg8.th.png[/img]](http://img518.imageshack.us/img518/4050/screenshot31gg8.png)

Elements Plugin working fine here.

---

### Post by olavjunior on 2008-11-03
Well, you're prob not using Intrepid are you? As far as I can see the elements isn't made for compiz fusion 7.8. And the plugins extra nonsupported I'm talking about, is the wrong version in intrepid. 

I fixed it though if anybody wants to know, downloaded the latest source from [http://releases.compiz-fusion.org/0.7.8/](http://releases.compiz-fusion.org/0.7.8/) (plugins unsupported)

Installed dependencies

compiz-fusion-bcop
compiz-dev; witch installed:
(libgl1-mesa-dev
libstartup-notification0-dev
libx11-xcb-dev
libxml2-dev
libxslt1-dev
mesa-common-dev)

Then just ./configure --> make -> sudo make install 
Also installed the broken plugins extra nonsupported in synaptics (just to replace the broken .so-file later)

Afterwards I replaced the original /usr/lib/compiz/libsnow.so with the new compiled /usr/local/lib/compiz/libsno.so

Voila!

---

### Post by loomsen on 2008-11-03
> Well, you're prob not using Intrepid are you?

Since the cutting alpha 3 I am :)

> compiz fusion 7.8

git-compiz here...

---

### Post by olavjunior on 2008-11-04
> **loomsen said:**
> 
git-compiz here...

Witch version do you have then? The "Elements" plugin is also in git?

Mabey I should try it out

---

### Post by loomsen on 2008-11-04
Maybe you should, yeah.

```

foobar@tiffany:~$ uname -r;apt-show-versions compiz-core
2.6.27-7-generic
compiz-core 1:0.7.9+git20080918.shame-0 newer than version in archive
foobar@tiffany:~$ 

```

[url=http://ubuntuforums.org/showthread.php?t=966030&page=2]

Scroll down to the bottom of the page... Tho the title is a little misleading.

---

