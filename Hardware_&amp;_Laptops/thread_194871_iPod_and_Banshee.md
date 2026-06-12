---
title: "iPod and Banshee"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by DrSturgeon on 2006-06-12
My iPod

1. Mounts
2. Shows up in RhythmBox

My iPod does not show up in Banshee.  This would seem to indicate a problem with ipod-sharp, but I am unsure how to debut it.  Any ideas?

---

### Post by bdrevn on 2006-06-25
The same things happens to me as well.  The stranger part is that it hasn't always happened.  All of a sudden it just started to not recognize my ipod.    I have uninstalled banshee and reinstalled it, and even then it doesn't take.

---

### Post by exiledsoul on 2006-06-26
I have the same problem. I don't know what caused this, because it actually worked in the beginning.

---

### Post by FoxxyZoe on 2006-07-24
I was having the same problem.  It turned out that when I reset my iPod with the Apple Update utility, my SysInfo file was blanked.

I haven't looked yet to see how Amarok, GtkPod and Rhythmbox work around not knowing exactly what model you have.

Do this:
```
$ gedit /media/ipod/iPod_Control/Device/SysInfo
```

If it is empty, you will need to track down a valid file.  For my 1GB Nano, it is this:

> pszSerialNumber: xxxxxxxxxxxxx
ModelNumStr: A1137

Both pieces of info can be found on the back of your iPod.  The normal file is much more extensive.  You may be able to find an old firmware updater and use that.  [Here]("http://ipodlinux.org/forums/viewtopic.php?t=1583") is a list of some people's SysInfo files.  [This]("http://www.ipodwizard.net/showthread.php?t=12733") discussion repeats a rumor that the SysInfo file was removed on *purpose* (to what end?).

Hopefully I can pass along some more information soon but this seems like enough to get it running again!

---

### Post by itsdaveperdue on 2006-10-09
I'm able to get around this by letting iTunes (on a windows machine) read the iPod and assign it a name.

---

