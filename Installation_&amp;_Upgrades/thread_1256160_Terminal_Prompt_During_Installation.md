---
title: "Terminal Prompt During Installation"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by RwandaTim on 2009-09-02
I've had success installing Ubuntu on multiple computers - old and new.  But, when I try to install from disk on a five year old Dell desktop, the installation begins, I choose my language, I select to install the OS, then the installer (seems) to go through a lengthy analysis of drivers, etc..., after which I end up with a screen which explains Ubuntu (no support, no copyright, etc...) with (what appears) to be a terminal prompt at the bottom which reads:

ubuntu@ubuntu :~$

I'm not sure what to do after this.

---

### Post by wojox on 2009-09-02
Type:

```
cd /.
```

Then:

```
ls
```

See what it says.

```
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var

```

Look like above?

---

### Post by Augsburg on 2009-09-02
you could type startx to open gnome (if it's installed), then troubleshoot graphically. I've also entered shells in setups where the thing needed is a ctrl-alt-delete or typing "exit"

---

### Post by RwandaTim on 2009-09-14
Nothing has worked so far.  I tried the suggestions above, after which I no longer get even a terminal prompt.  Now I just get a black screen.  I've noticed within other threads that folks have problems with Dell Dimension 2400.

---

