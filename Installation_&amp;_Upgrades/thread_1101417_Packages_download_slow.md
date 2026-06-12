---
title: "Packages download slow"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by farahf on 2009-03-20
Hi, I'm currently using  intrepid ibex. The download speed of packages is dramatically slow. The download starts fast (256KB) but dies down for long time spans until the burst comes again. Installing packages is becoming frustrating.
Any ideas what the problem can be?

---

### Post by adzik on 2009-03-20
Try an alternate mirror. I had this situation so I found another local mirror and now I get consistent 750 Kb/s rates when installing/updating anything.
Maybe this is the issue, but maybe not. Give it a try.

---

### Post by Therion on 2009-03-20
Open your Software Sources menu.
Click on “Other”.
Click on “Select Best Server”.
Let it do it's groove thaaaang.

The location selected when this process is done should be the fastest available mirror for you currently.

---

### Post by kidux on 2009-03-20
> **Therion said:**
> Open your Software Sources menu.
Click on “Other”.
Click on “Select Best Server”.
Let it do it's groove thaaaang.

The location selected when this process is done should be the fastest available mirror for you currently.

Hmm, learn something new everyday. Thanks!

---

### Post by cottfcfan on 2009-03-20
Hi,
I had exactly the same problem the other day.
Eventually I tried a couple of terminal commands and it fixed it.
apt-get -f install
dpkg --configure -a
This will try and fix any broken packages.
Then try:
apt-get autoremove
This will remove obsolete packages.
You might need to use sudo before these commands not sure.
Let me know if it works.

---

### Post by farahf on 2009-03-20
I tried the find best server method suggested by Therion above. Guess it worked fine (Thanks Therion). I dont think its a broken package because I'm using a relatively fresh install.

I'll let you know if anything comes up.

---

### Post by Therion on 2009-03-20
Welcome guyz...  Glad that little tip is working out for you.  

I've learned that the *closest* server is not always the *fastest* server since I can get reeeeeeally impatient with updates.

---

