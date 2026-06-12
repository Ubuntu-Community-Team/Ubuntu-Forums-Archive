---
title: "[SOLVED] Connecting to the internet with an embedded 3G card"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Liet_Kynes on 2008-02-03
Hi.

I am using a Dell Latitude D620 with an embedded 3G/HSDPA card(mini-card). How would I go about using it to connect to the internet.

I have used it before while using windows so at least i know the card works. I don't sem to see it anywhere in linux though. I'm currently having to connect via ppp with my phone via GPRS. (I'm in South Africa and the power just went out again so no DSL :( )

Can anyone help me to get the card set up?

Thanks

---

### Post by bwhite82 on 2008-02-03
What is the specific manufacturer/model of the card?

---

### Post by Liet_Kynes on 2008-02-03
Is there a way to check in Ubuntu? Or i'll have to boot into XP to check.

---

### Post by bwhite82 on 2008-02-03
> Is there a way to check in Ubuntu? Or i'll have to boot into XP to check.

lspci

---

### Post by Liet_Kynes on 2008-02-03
here it is

---

### Post by bwhite82 on 2008-02-03
Ok, it looks like a driver is available for this card. I can help you out with Ubuntu at least recognizing the device and making use of it.

First check to see whether the driver is on your machine:

> modinfo airprime

If you see output, its there.

Now to see if its loaded or not:

> lsmod | grep airprime

If you get nothing, then load it:

> sudo modprobe airprime

Now as far as making use of it...thats where I am unsure of, I believe you have to treat it as a PPP device. After doing the above, see if it shows up as a network device:

> ifconfig -a

Hopefully, its listed as "ppp0", if not you need to configure it to be one with the 'gnome-ppp' package or the already-installed, CLI program pppd.

---

### Post by bwhite82 on 2008-02-03
Aha, found it for ya:

[http://www.net42.co.uk/os/linux/d620_3g_datacard.html](http://www.net42.co.uk/os/linux/d620_3g_datacard.html)

These directions apply to you because you have the same chipset as the card in the link. Just follow exactly the directions given in the link.

He uses the KPPP program however, which you can install via the repos.


-Cheers

---

### Post by Liet_Kynes on 2008-02-03
Well all the steps went well except that it doesn't get registered as a ppp interface :(

---

### Post by bwhite82 on 2008-02-03
Thats good! Sometimes it takes a little work for some devices in Linux. Now all you have to do is configure it as a PPP device, see my link above.

---

### Post by bwhite82 on 2008-02-03
Oh, and because I have ran into issues myself with a 3g card, be sure other networking devices are disabled or unplugged. I had to disable my wireless card in Ubuntu before my 3g card would connect.

---

### Post by Liet_Kynes on 2008-02-03
Thanks for the link to a great article/howto. I guess I need to improve my googling skills :)

Still trying to figure out how to configure the PPP but at least I've gotten the device up and running automatically at boot. :D

---

### Post by Liet_Kynes on 2008-02-03
Yay its all up and running :D

Thanks again soldierboy. 

Another step closer to deleting Windows ;)

---

### Post by bwhite82 on 2008-02-03
No problem, glad you got it working. :D

---

