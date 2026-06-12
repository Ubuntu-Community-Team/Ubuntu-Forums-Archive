---
title: "MultiSync . BT . Passcode?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by dunai on 2006-06-14
I've tried to pair my SE K700i with MultiSync.
MultiSync does find my phone, but when i hit the "test connection" button, the phone ask for a passcode. BUT, what passcode ?! :confused: 
It's not the one in /etc/bluetooth/pin - i've tried that one out.
Anyone who knows how to solve this problem? or knows how to change the passcode?

---

### Post by bikeboy on 2006-06-14
I had the same problem, got it working for a while (1234 I think was the passcode but I had to do other things as well) but now it doesn't work anymore. I think there is some key stored on my BT dongle and I need to reset that.

Try "man hciconfig" and look at the auth and secmgr options, pretty sure that's what I used when I got it working. Post back if you fix it :)

---

### Post by dunai on 2006-06-14
well.. i tried with 1234 - but it didn't work. and i can't see how to make it work in secmgr :confused:

---

### Post by dunai on 2006-06-14
now i solved the problem with the passcode by reinstalling the bluez-utils etc.
now the phone choose the pin and afterwards multisync is asking for the pin.

i tried to synch with multisync, but with no success: "Failed to get second plugin changes: Not authorized."

anyone who knows how to solve that problem?

---

### Post by jbcola on 2007-08-13
I got the same message with K700i and Feisty :-(

Did someone solve this problem?

---

### Post by feenstra on 2008-02-14
No, but I just encountered it with multisync and my SE W800i.
It has been running without too many problems for a long time, and suddenly stopped working (today, or maybe a few days ago)... I will check for updates that may have interfered here.

---

