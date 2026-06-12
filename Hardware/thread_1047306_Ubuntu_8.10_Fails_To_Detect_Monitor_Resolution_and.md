---
title: "Ubuntu 8.10 Fails To Detect Monitor Resolution and Refresh rate"
date: 2009-01-22
forum: Hardware
---

### Post by Adarzh on 2009-01-22
Hi,
   My ubuntu 8.10 doesn't detect my monitors resolution and refresh rate. Each time, i need to manually change the screen settings through xorg.conf file. I tried on many other monitors(crt) all have the same problem. Is there any remedy. 

  Btw I'm not using any video cards.

Adz

---

### Post by Kumagoro on 2009-01-22
> **Adarzh said:**
> 
  Btw I'm not using any video cards.

Adz

You're stil using an integrated card, post it's name.
Most likely it's some Intel

Did you try to change drivers?

---

### Post by AKADAP on 2009-01-22
Are you using a video cable that breaks out the signal into a bunch of BNC connectors? If so, the video card will be unable to detect the monitor type, and you will have to put the monitor information into the xorg.conf file.

---

