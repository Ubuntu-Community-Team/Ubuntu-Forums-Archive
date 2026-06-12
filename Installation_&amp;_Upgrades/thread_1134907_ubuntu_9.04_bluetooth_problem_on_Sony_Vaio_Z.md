---
title: "ubuntu 9.04 bluetooth problem on Sony Vaio Z"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by stefanhong on 2009-04-24
I just installed ubuntu 9.04 on Sony Vaio Z15 notebook. The number one show stopper for me at the moment is that it cannot pair with my logitech bluetooth mouse V470. It was working correctly with 8.10. Any ideas?

Stefan

---

### Post by stefanhong on 2009-04-24
I solved the problem myself. It requires BlueZ 3.x compatibility binaries to work. Do the following:

sudo apt-get install bluez-compat

Then pair the mouse using gnome bluetooth applet. It works for me now.


Stefan

---

