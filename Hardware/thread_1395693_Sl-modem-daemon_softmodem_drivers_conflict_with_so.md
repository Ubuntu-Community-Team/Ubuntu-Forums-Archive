---
title: "Sl-modem-daemon softmodem drivers conflict with sound hardware"
date: 2010-02-01
forum: Hardware
---

### Post by PCA on 2010-02-01
Hello guys,
             I have a problem with my modem drivers. Whenever I activate the softmodem driver in 'hardware drivers' tool, my sound system stops working. I have a HP nx7300 laptop with Agere systems modem. 

             I had made a post earlier regarding the same problem which I incorrectly diagnosed as a problem with some other software. But now I'm pretty sure that the modem driver is the cause. The sound starts working when I uninstall sl-modem-daemon. Everything else works perfectly fine. But I need the modem to work too. What can I do about this?  Currently I'm using Karmic Koala 64bit

---

### Post by PCA on 2010-02-03
hello... what to do about this? I have tried the scanModem executable, should I post the report?

---

### Post by Whoopie on 2010-02-03
You need to install the pulseaudio packages from ubuntu-audio-dev PPA. It's fixed there (see LP bug report 394500 and 450222).

---

### Post by PCA on 2010-02-03
Thanks Whoopie, It worked. :P

---

