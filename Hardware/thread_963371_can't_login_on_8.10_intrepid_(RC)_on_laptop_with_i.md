---
title: "can't login on 8.10 intrepid (RC) on laptop with intel 82845G graphics"
date: 2008-10-30
forum: Hardware
---

### Post by honda on 2008-10-30
Anybody else affected by this bug? Launchpad entry for the bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277373]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277373")

---

### Post by kayvee on 2008-10-30
I had the same problem. I upgraded from Hardy to Intrepid RC. Login window appears; when I enter user ID and password the screen just turns black and this is the case with both KDE and GNOME versions. I read somewhere in this forum that removing Compiz will fix it. So, logged in using the Terminal and removed compiz and compiz-core
```
sudo apt-get remove compiz compiz-core
```
I hope this helps you too. 

More importantly, I wonder if this problem will ever be fixed? If yes, what the status is...

---

### Post by honda on 2008-10-31
Thank's, that fixed it for now. Sadly the desktop effects were working fine on Hardy, even on lousy graphics like this.

---

### Post by kayvee on 2008-10-31
Exactly. I had no issues with desktops effects on the exact same computer with Hardy. I hope I will able to have effects again in Intrepid too. and I guess the way things are going, i might not even upgrade to jaunty - my graphics card would be even more legacy by the time jaunty comes out...

---

