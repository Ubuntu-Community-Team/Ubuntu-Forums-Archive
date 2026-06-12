---
title: "COM port was not found via my system - I think."
date: 2009-07-28
forum: Hardware
---

### Post by CrAzYoNi on 2009-07-28
Hi all,
I'm having on my old computer (P4 2.4Ghz) an old main-board, Intel Silver-Reef (D485PESV), I'm a linux newbie, I should note.

Any way, I wanted today to configure my Cisco SOHO router via a serial connection... so I plugged the serial cable into my (only) COM port at my PC & downloaded GtkTerm, Minicom & Putty.

I tried those 3 to connect to my COM port (I noted that I'm having inside /dev directory access to /dev/ttyS0 - /dev/ttyS3) though without any luck.

I've tried as a regular user (that has access to the dialout group) & via Root priv though still I didn't have a luck.

I saw after some searching in Google that as Tip I should enter the command (dmesg | grep ttyS) and look for some results about my COM port though no luck, while trying: dmesg | grep tty, I got information related to tty0 only.

How can I make sure that I'm having COM port installed via kernel on my system? how can I reinstall it?:\

Thanks for your help.

Cheers,
Yoni D.

---

