---
title: "How can I apply the Pidgin patch?"
date: 2008-09-19
forum: General Help
---

### Post by Epifrin on 2008-09-19
I have been unable to log onto my icq account on pidgin, found a patch online that fixes the problem but don't know how to apply it since I'm very new to Ubuntu? It's a compressed file that I don't know where to extract/install. Any help is appreciated.

---

### Post by Yellow Pasque on 2008-09-19
A link to the patch would be helpful.

---

### Post by Epifrin on 2008-09-20
The Ubuntu version @: [http://pro.to.co.ls/misc/pidgin-icq-fix/](http://pro.to.co.ls/misc/pidgin-icq-fix/)

Thanks in advance.

---

### Post by howefield on 2008-09-20
It is a compressed file containing a bunch of .deb files.

You can uncompress them by downloading the file to the desktop and in a terminal type

```
gunzip pidgin-2.4.1-icqfix.tar.gz
```

then also in the terminal type

```
tar -xvf pidgin-2.4.1-icqfix.tar
```

This should put the seperate .deb files on your desktop, from there you can install the relevant one(s). I can't see which you need for the icqfix.

I'd rather get the source or even the rpm from the pidgin own website (and use alien to install the rpm).

---

### Post by Yellow Pasque on 2008-09-20
The latest version (2.5.1) is .deb packaged for Hardy here: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) The site looks legit, but I'm always wary of third-party .deb's
Personally, I'd rather build from source. If you go that route, do this first to get the prerequisite development packages:
```
sudo apt-get build-dep pidgin
```

---

### Post by altima on 2009-02-27
and what should be done to a *.patch file?

---

### Post by Brausen on 2009-07-22
> **altima said:**
> and what should be done to a *.patch file?
I have the same question.
No one knows what should be done?

---

### Post by jerome1232 on 2009-07-22
You have to apply them to source code, usually something like

```
patch -p0 <nameofpatch.patch
```

Here is a thread, perhaps you can do the same thing shown in the last post but for pidgin.
[http://ubuntuforums.org/showthread.php?t=324672](http://ubuntuforums.org/showthread.php?t=324672)

---

