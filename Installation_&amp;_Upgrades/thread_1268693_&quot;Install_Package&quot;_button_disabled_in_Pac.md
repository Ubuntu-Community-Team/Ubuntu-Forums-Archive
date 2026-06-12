---
title: "&quot;Install Package&quot; button disabled in Package installer for TrueCrypt"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by vladu on 2009-09-17
Hi,

I was trying to install TrueCrypt the other day, but the *Install Package* button is disabled in the package installer. You can check it out on [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) where you will download a binary which extracts the deb file.

Does anyone have a workaround this issue?

---

### Post by Soul-Sing on 2009-09-17
Try this: [http://ubuntuforums.org/showthread.php?t=1190053&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=1190053&highlight=truecrypt)

---

### Post by vladu on 2009-09-18
I had run the script with
```
sudo sh truecrypt-6.2a-setup-ubuntu-x86
```
but i forgot to mention. Even so, the package installer behaves the same, it keeps the install button disabled.

---

### Post by Soul-Sing on 2009-09-18
You should not use the "deb" file.

---

### Post by vladu on 2009-09-19
> **leoquant said:**
> You should not use the "deb" file.

The installer is really weird - it's easier to see why if you try it yourself. Anyway, it gives you two options:

1. You can either extract the .deb file and it then puts it into /temp or
2. You can "install" TrueCrypt which first leads you to a message showing you the license. If you accept, it automatically launches the same .deb file which I presume it also extracts in /temp.

So basically there's no way around the disabled install button.

---

### Post by Soul-Sing on 2009-09-19
I did several truecrypt installs, can't remember this as an issue.
Sorry...Maybe someone else?

---

### Post by vladu on 2009-09-20
Should I report this as a bug in Package installer - gdebi-gtk? After all, the TrueCrypt installer only unpacks a .deb file and launches it.

---

### Post by ChrisWebb on 2009-09-24
I can confirm the same behaviour - Ubuntu Jaunty 64 bit. Guess it's a problem with the deb file.

---

