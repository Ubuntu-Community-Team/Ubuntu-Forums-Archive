---
title: "Will ubuntu work well on this laptop?"
date: 2010-06-12
forum: Hardware
---

### Post by asbjornfridberg on 2010-06-12
Hi all,

I'm thinking of buying this laptop (HP G62-140SS: I3), and install ubuntu on it:

[http://www.pontreyes.es/es/productos.php?dir=16&sel=79&prd=2014](http://www.pontreyes.es/es/productos.php?dir=16&sel=79&prd=2014)

Does anyone have experience with this machine or a similar configuration, and Ubuntu? Will I have problems with drivers etc?

Thanks a lot in advance!
Regards,
Asbjorn Fridberg.

---

### Post by Bucky Ball on 2010-06-12
[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=HP+G62-140SS+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?fr=altavista&itag=ody&q=HP+G62-140SS+ubuntu&kgs=0&kls=0)

---

### Post by sanderj on 2010-06-12
If online info doesn't help, go to their shop with a Ubunut live USB stick (or live CD), and boot it. Things to check: screen (resolution) and Wifi.

That's how I bought my netbook at J&R ...

---

### Post by asbjornfridberg on 2010-06-13
Ok thanks to both of you, I might try the idea of asking to boot with a live-cd to make sure I don't get problems with the wi-fi, which I had lots of with my last laptop.

Asbjorn.

---

### Post by Bucky Ball on 2010-06-13
Warning: You need to install driver for wifi which you CAN'T do when running off the LiveCD. Nowhere to install them to. ;)

You might be lucky and it works 'out of the box' with open-source drivers already included in Ubuntu. Do you know what your wireless card is?

---

### Post by asbjornfridberg on 2010-06-15
> **Bucky Ball said:**
> Warning: You need to install driver for wifi which you CAN'T do when running off the LiveCD. Nowhere to install them to. ;)

You might be lucky and it works 'out of the box' with open-source drivers already included in Ubuntu. Do you know what your wireless card is?

No, yesterday I went to the shop and asked them, they looked and could not find any specification (!!) and they told me to look on the web, which I have done without luck. So I guess I will try my luck and hope to solve problems as they come.  Thanks a lot!

---

### Post by Bucky Ball on 2010-06-15
If you can run off a LiveCD before installing, open a terminal (Applications->Accessories->Terminal) paste in this command:

```
lspci
```

Near the bottom of that list you should find your network card. Post that or the whole result from that command. Most wireless cards work with Ubuntu nowadays. Catch 22 is you usually need to plug a cable in first which picks up your wireless card and offers to install the appropriate drivers or firmware if they are not already included in the kernel you are using.

Good luck.

---

### Post by Bucky Ball on 2010-06-15
> **wrigilis said:**
> Running live CD on your machine may first need to install Wifi driver for easy navigation.

There is nowhere to install it when you are running a LiveCD so this is not an option. You might find the right drivers are part of the running kernel anyway. Get a cable or install if you need to install wifi drivers.

---

### Post by asbjornfridberg on 2010-06-19
Ok, thanks a lot for the tips, I will post on the thread when I have tried the installation.

---

