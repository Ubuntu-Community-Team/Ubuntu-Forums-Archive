---
title: "autostart script after network manager"
date: 2008-09-22
forum: General Help
---

### Post by wh4tup on 2008-09-22
hey there!

i have to set a static arp route to connect to the internet over wireless. my script contains:

```
#!/bin/sh
sudo arp -s 192.168.0.1  00:19:$$:$$:$$:e3
```

right now i'm clicking on the script and entering my pass everytime i want to connect to the internet. 


running it as a normal startscript within /etc/init.d/ didn't work because the my wlan stick associated to my router afterwards (must be network manager).  the association overwrites my static entry. the router has the same IP as the modem (both 192.168.0.1). the funny thing is when I'm associated with the router i got a network connection but no i-net. after I entered the static entry including the MAC of the modem i-net worked(but my wlan card is still associated to the router!). adding it to sessions in the menu didn't work either. 

i need to find a way run the script automatically after everything is loaded.

---

