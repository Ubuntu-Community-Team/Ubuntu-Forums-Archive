---
title: "How to make VI open gzip files"
date: 2008-08-27
forum: General Help
---

### Post by jambalaya on 2008-08-27
Hi.
At work, we have a machine that runs linux (I forgot which flavour). I had to do some stuff recently and I noticed by accident that VI that is installed there supports automagic gz file edition. By that I mean that when the file contains text, and it is gzipped, and I open it with VI, it displayes the uncompressed text data. This is quite handy. Do you know how one can confgure / tweak his VI to do sth like that?
Cheers.

---

### Post by arch0njw on 2008-08-27
Do you have the vim-common package installed?  From what I understand, if that is installed, this functionality it supported.

Also, to ID your distrubution, try this command:  cat /etc/issue

---

### Post by sdennie on 2008-08-27
You should be able to get this behavior just by installing vim-full:

```

sudo apt-get install vim-full

```

(That's generally the first command I run on a new install)

---

### Post by jerome1232 on 2008-08-27
I always extracted to standard output and piped it into vim, looks like I don't even have to do that!

---

### Post by jambalaya on 2008-08-29
vim-full package is all I had to do to make this work.
Thank you for your help.

---

### Post by rabalthazar on 2009-02-16
If you want to make vim open gz files on a server edition with no graphical gui, just install the vim package:

```
sudo apt-get install vim
```

---

### Post by drwhitt on 2011-03-25
> **jerome1232 said:**
> I always extracted to standard output and piped it into vim, looks like I don't even have to do that!

Great tip, thanks!  But for those unfamiliar, this implies using a command like:
```
zcat filename.gz | vi -
```

---

