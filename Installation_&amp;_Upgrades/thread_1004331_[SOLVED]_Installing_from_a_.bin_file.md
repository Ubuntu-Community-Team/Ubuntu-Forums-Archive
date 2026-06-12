---
title: "[SOLVED] Installing from a .bin file"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by ingeva on 2008-12-07
I had problems with my Java installation. Using the internet bank and verifying my installation both claimed my version was outdated (6.7).

java.sun.com offers a version 6.11, but this was only available as a .bin file and I haven't found any installation program for it.

Help?

---

### Post by Kevbert on 2008-12-07
The easiest way to run the bin file is to go to terminal, go to the directory where it's located and enter
```
sh filename.bin
```

---

### Post by ingeva on 2008-12-07
> **Kevbert said:**
> The easiest way to run the bin file is to go to terminal, go to the directory where it's located and enter
```
sh filename.bin
```

WOW! THAT easy?

I've deleted the file so I can't retry right now, and I solved my problem anyway.
I just didn't even consider that it could be executable! :)

Thanks!

---

### Post by jamesstansell on 2008-12-07
> **ingeva said:**
> WOW! THAT easy?

I've deleted the file so I can't retry right now, and I solved my problem anyway.
I just didn't even consider that it could be executable! :)

Thanks!

In some cases .bin stands for "executable binary."

Just wondering - what did you do to solve your problem?

(BTW, the 6u11 packages have been added to the jaunty ubuntu 9.04 repository.)

---

### Post by ingeva on 2008-12-08
> **jamesstansell said:**
> In some cases .bin stands for "executable binary."
Just wondering - what did you do to solve your problem?


I associate "bin" with binary data ... :)

All I did to get Java working again was to delete the complete ".mozilla" directory.
After backing up the bookmarks, of course.

---

