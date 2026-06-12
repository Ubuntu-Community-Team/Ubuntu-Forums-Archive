---
title: "Ubuntu doesn't remeber SSID"
date: 2008-07-18
forum: General Help
---

### Post by alistair23 on 2008-07-18
I used to use the gnome network manager and it was pretty good except everytime i restarted i had to re-enter my SSID and WEP key. I think i messed up the keyrings. So then i installed WICD, and that doesn't remeber my SSID but when i re-enter my SSID my WEP is already there (Maybe because now it is in the keyrings). My network is a Hidden so that could be the problem but does anyone know what i can do so it remebers mhy SSID and WEP in either WICD or Gnome Network manager.

---

### Post by imdano on 2008-07-18
Wicd remembers your network, but because of the way your hidden essid is handled by your wireless driver it doesn't realize its available to autoconnect.  This bug *might* be fixed in the newest release, 1.5.0.  Whats the output of iwlist scan before you connect to your network (meaning when the essid is still hidden).

---

### Post by alistair23 on 2008-07-18
When does the new software come out?

---

### Post by imdano on 2008-07-18
You can get the most recent release candidate now at [http://www.wicd.net/latest](http://www.wicd.net/latest).  The official release isn't too far off, and so far it seems like this latest rc is very stable, probably more than 1.4.2 is.

---

### Post by alistair23 on 2008-07-18
Thnks i am now using tthat

---

