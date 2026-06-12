---
title: "Internet connection"
date: 2012-07-15
forum: Hardware
---

### Post by Priyank Kaushal on 2012-07-15
I have a problem in connecting to the net on ubuntu.I want to know if I can download packages for omnet++ on windows itself and try to install it on ubuntu.Is it possible..actually I have done it but it showed not compatibility issues..I have Reliance modem which works on windows but how to connect to the net on ubuntu..I don't know..I have recently installed the ubuntu...so plz helpas soon as u can.

---

### Post by Deepak J on 2012-07-15
What kind of modem do you have...?

A wireless USB modem, or a 3G one...?

Or the usual ethernet modem...

And also do you need a separate software to connect to the Internet, like for eg you select some kind of software in windows and then you select connect which connects it to the net, or is it just the windows that identifies the IP, DNS etc addresses and connect to the ethernet modem...?

---

### Post by Priyank Kaushal on 2012-07-18
> **Deepak J said:**
> What kind of modem do you have...?

A wireless USB modem, or a 3G one...?

Or the usual ethernet modem...

And also do you need a separate software to connect to the Internet, like for eg you select some kind of software in windows and then you select connect which connects it to the net, or is it just the windows that identifies the IP, DNS etc addresses and connect to the ethernet modem...?

Thanx for reply. but it was easy to connect to the net..i did some setting ..now its working.

---

### Post by Deepak J on 2012-07-22
Oh thats good to hear...

Also make sure you mark this thread as solved....
:KS

---

### Post by Kreaninw on 2012-07-22
If you're using wireless modem and on Ubuntu you're using Broadcom driver for your wireless device. Ubuntu will not connect to your modem if your modem channel > 11(normally it will random from 1-13). You have to go to your modem's configure page and set channel to 1-11. Otherwise, you won't always connect to your modem successfully on Ubuntu.

---

