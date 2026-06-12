---
title: "Dell Inspiron 6000 wireless connection problems"
date: 2010-03-01
forum: Hardware
---

### Post by lukekirstein on 2010-03-01
I'm relatively new at all of this, and while I have some Linux experience, I can't do it without a walthrough :).

I've been trying to get wireless working on my Dell Inspiron 6000 all night now. I don't have integrated wireless but a card that I purchased from Amazon (the internal card was water-damaged and needed to be replaced). 

I've followed the thousands of Wiki's and guides online for ndiswrapper and thought I had it down. However, while Ubuntu picks up the card, it won't connect to any networks. I see networks in the top left but it hangs on connecting to any of them, asking for passwords repeatedly but never getting any farther. 

Any ideas?

---

### Post by efflandt on 2010-03-02
It may help you get more help if you say what wireless card you have and how it is connected (PC card or cardbus card, or USB?).  But it is impossible to suggest what command to use to see what Linux sees for it without knowing what type of device it is.

Does **sudo iwlist scan** show wireless APs?  In Network Connections are you checking Connect automatically and All users?  Sometimes when initially configuring a connection it seems like I have to bring it up again and make sure that security is set properly, or hit Apply again.

---

### Post by jpl888 on 2010-03-02
Perhaps if you posted the output of ```
lspci
``` and ```
lsusb
``` that would give us somewhere to start to help you.

---

