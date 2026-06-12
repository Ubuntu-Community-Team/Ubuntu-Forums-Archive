---
title: "media controll buttons on inspiron 6000"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by Andrew12106 on 2006-09-07
there are these little buttons for play/fastforward etc. on the front of my laptop. is there a package that will make these useable with totem or totem-xine?

---

### Post by daller on 2006-09-17
Use Keytouch:
 
 [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)
 
 .deb packages are available from sourceforge!

 There's an extensive HOWTO on the site to help you. 
 It worked for me.

---

### Post by Jawbreaker4Fs on 2007-05-03
This also works:
```
sudo apt-get install keytouch
```

---

### Post by xflbret on 2007-05-27
confirmed NOT WORKING on a Dell Imspiron 6000. Did everything the video told me to do, no good

---

### Post by Jemson on 2007-10-04
> **xflbret said:**
> confirmed NOT WORKING on a Dell Imspiron 6000. Did everything the video told me to do, no good


Confirmed WORKING on a Dell Inspiron 6000. Default settings did not work, but setting "Special Action" that was the same setting as the default worked fine.

Ie.
Default: "Amixer - Mute"
Change to: "Special Action" - Plugin: "Amixer" - Function: "Mute"

Works great! :-)

---

