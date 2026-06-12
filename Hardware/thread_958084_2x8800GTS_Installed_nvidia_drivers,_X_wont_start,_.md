---
title: "2x8800GTS Installed nvidia drivers, X wont start, ends at CLI screen"
date: 2008-10-25
forum: Hardware
---

### Post by Chookah on 2008-10-25
This has been an ongoing issue for me, both with 8.04 and 8.10

I install the proprietry drivers (tried 173 and 177) and reboot as instructed.  Now X wont start.

'startx' gives an error saying 
[I]kinit: no resume image, doing normal boot.
No devices detected
No screens found[/I]

I check the /var/log/Xorg.0.log file at it does list both of my 8800GTS cards, so why would it say no devices detected?

I really really dont want to have to go back to vista, especially because my housemate is a microsoft fanboy who'll never let me live it down. [-o<

---

### Post by shawnrgr on 2008-10-25
```
sudo nvidia-xconfig
```

---

