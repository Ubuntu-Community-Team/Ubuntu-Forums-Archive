---
title: "3G on Vaio P stopped working"
date: 2009-08-21
forum: Hardware
---

### Post by BOYerchen on 2009-08-21
Hey there,

on my Vaio P I was surprised, when I started the Netbook Remix for the first time, a popup dialog for 3g configuration came up and I was able to set up the connection and pick it in the NetworkManager. Unfortunately I didn't remember the correct PIN at this time.

Now, after the installation, the 3G connection is no longer detected. Instead I see a "Wired" connection, even though the Vaio P doesn't have one. I looks like the sky2 module, that is responsible for the 3g connection, registers the eth0 interface and NetworkManager detects it as wired connection.

The really weird thing is that booting from the live USB stick, now yields the same results!

Any suggestions, log files to post or anything else?

Sincerely
Pascal

---

