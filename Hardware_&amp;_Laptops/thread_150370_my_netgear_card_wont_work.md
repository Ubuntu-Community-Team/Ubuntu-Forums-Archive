---
title: "my netgear card wont work"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by jimbob01us on 2006-03-25
i have a netgear wg311v2 wireless card and when i installed the ubuntu program i could not get online.  can anyone help me as i am new to ubuntu

---

### Post by jethro10 on 2006-03-26
Hi,
I have the same problem.
Both nativley and using NDIS wrapper.

Hope someone can help us.
I also looked at Linuxant.com but the trial version of a commercial NDIS wrapper (?) is not compatible with ubuntu.
Strange as the hardware page for WIFI cards says this "works out of the box"
I took mine from another PC rather than a box so maybe thats the problem :) 

J

---

### Post by jml on 2006-03-26
I have a few Ideas for you.  When you open up Network Manager do you see the wireless card listed as one of the network device choices?  If you do, then you are half way there.  Ubuntu does not automatically configure or activate wireless cards, that has to be done manually.  Now in Network manager highlight the wireless card.  Then click on the properties button.  When finished, close out the dialog box, and make sure the card is still highlighted.  Then click on the activate button and wait a bit.  It may take several minutes for the device to be activated.  Once that is done, colse down the Network Manager and you should be good to go.  

A bit of advise, try to establish an unencrypted wireless connection first.  Turn off encryption on the access point you are trying to connect to.  Once you have that setup working properly, go back in and set your WEP encryption keys.  WPA encryption is not natively supported in Ubuntu, so if you need WPA encryption, search this forum using WPA as a search term and you should find several posts, including a few of mine, that describe the process of set up.  Hope that this helps.

Joe

---

