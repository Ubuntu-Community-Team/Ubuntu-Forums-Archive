---
title: "Ubuntu doesn't detect my USB router thing..."
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by DJSpazz on 2008-04-07
Hey people!
I've just recently installed Ubuntu (Dual-Boot Vista first) onto my desktop and I've run into a bit of a snag...
I use a 70$ USB Router (Is that what its called?) by Linksys to connect to my father's wireless network.
On Windows, the hardware is detected, it can see access points, and I can connect easily.
On Ubuntu, however, I don't think the hardware is being detected, as the power light on the actual router never lights...
This little thing is my only route to the internet, :P
I'd love to have it work for Ubuntu. :D

I'm off to school in about 20 minutes so, It might take a while for me to respond. :]

---

### Post by DJSpazz on 2008-04-07
Ah, I've just done some searching and come upon **[THIS.]("http://ubuntuforums.org/showthread.php?t=516649")**
I'll try it now and see if it works.

I guess I forgot to mention I have a WUSB5**S**4GC... xD

---

### Post by cjv8888 on 2008-04-07
I have the same USB adapter as yours.  Just run the script as instructed by Hendricks and I got it working after a bit of fiddling.

---

### Post by DJSpazz on 2008-04-07
The old one or the newer SerialMonkey one?
EDIT: Ah, I tried SerialMonkey which failed, then I rebooted and tried the old one, which also failed...
Maybe I was supposed to uninstall the SerialMonkey one?
EDIT2: I uninstalled both old and SerialMonkey. Then I installed old. It failed. I uninstalled old. I tried the SerialMonkey and it also failed... Am I to be stuck without a connection forever?

---

### Post by DJSpazz on 2008-04-07
Also, would you mind telling me what fiddling around you did? Neither one of those worked... D:

---

### Post by cjv8888 on 2008-04-08
I think it was the older one with Ndiswrapper. The first  time I ran the script it went through a lot of things but the adapter did not work then.  I then also extracted the .gz thing in the wusb54gc folder and ran it a second time.  This time it says the Ndiswrapper is already up to date and so and so is already blacklisted.  After re-booting, the network icon is up on the right upper corner and I could detect and choose the  home wireless network and put the password in.

---

