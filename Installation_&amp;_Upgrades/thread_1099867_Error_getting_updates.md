---
title: "Error getting updates"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2009-03-18
While I was downloading a slew of updates I received the following error:```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb
  404 Not Found



```

Are these sites down or deprecated?

---

### Post by zvacet on 2009-03-18
It looks like repos are down.Try later and maybe this first

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Therion on 2009-03-18
It's been happening to me off and on over the past couple days.

Try picking a different server in the Software Sources menu and re-run updates.

---

