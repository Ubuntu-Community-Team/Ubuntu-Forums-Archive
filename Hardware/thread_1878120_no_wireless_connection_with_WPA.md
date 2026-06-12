---
title: "no wireless connection with WPA"
date: 2011-11-09
forum: Hardware
---

### Post by nunny on 2011-11-09
I have installed Ubuntu 11 on my laptop and my netbook. Both are  Toshibas. I have connections on both with wired network.  My router is a  D-Link 625. It is configured with WPA-Personal.  it works perfectly  with Windows Vista and 7 Starter.  The wireless does not work with  either Laptop or Netbook.  I have installed all the latest drivers I can  find, to no avail. When I disable the security in the router, the  laptop and the netbook connect right away, no problem.  As soon as I  enable the security, I lose connection.  The router logs inform me of my  computer trying to connect but is sending wrong PassPhrase.  The  PassPhrase is correct.  I have entered it several times and have even  done copy/paste scenerio to ensure no typos.

Is it possible Ubuntu is sending PassPhrase in different format ie hex,bin,ascii???

Ken

Can anyone help me.

---

### Post by MoreOrLess on 2011-11-09
If your passpharase has spaces or special characters, you have to enclose it in quotes (") to make it work with wpasupplicant.

---

### Post by nunny on 2011-11-10
My PassPhrase contains only UC and LC letters and numbers.  Having said that, I still tried your suggestion.  Unfortunately it did not work.

---

