---
title: "iphone 3.0 syncs"
date: 2009-12-01
forum: Hardware
---

### Post by sudo panda on 2009-12-01
I've managed to follow Marcan's blog to get iphone 3.0 syncing with ubuntu.
After a minute or two of "updating library" however, i can't seem to see the songs on the iphone.
When i plug my iphone into a window's computer and load itunes... the iphone is updated and the changes are able to be seen.
MY question is, does anyone know if there is a way to eliminate the need to plug my iphone into itunes?

I'm using ubuntu 9.10, the latest source tarballs of libgpod, etc.

[Marcan's Blog Here]("http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/")

---

### Post by sudo panda on 2009-12-01
Got it working! nevermind! :D

In order to get it working i just needed to compile libiphone, ifuse and usbmuxd as the ubuntu packages provided by marcan didn't work properly. Should have known that, it does say it in the ubuntu help guide for iphone. ;)

---

### Post by Johnny19734 on 2009-12-04
I cannot compile the usbmuxd package via cmake.(I dont know how) and this package is not in the Ubuntu repo's Even if you include the software source its still not there! what the hell? Do you know where you can download the .deb form of this? :cry:

---

