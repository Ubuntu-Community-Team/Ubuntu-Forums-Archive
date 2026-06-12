---
title: "ndiswrapper help..."
date: 2005-12-04
forum: General Help
---

### Post by emerick7 on 2005-12-04
Thanks for the help with ndiswrapper HokeyFry... that worked, but when I restart the computer, I have to go through the process again to set my wireless USB with ndiswrapper. How do I change it so the wlan is setup permanently?

Thanks in advance,
Ty

---

### Post by cydec on 2005-12-04
```
sudo gedit /etc/modules
```

Then add to the list of words in a new line:
ndiswrapper

That worked for me, hope i didn't make a mistake here.
And that it works for you.

---

### Post by Anomaly on 2005-12-04
You made no mistake but to me it seems easier just to type

sudo ndiswrapper -m

which does the same thing:D

---

