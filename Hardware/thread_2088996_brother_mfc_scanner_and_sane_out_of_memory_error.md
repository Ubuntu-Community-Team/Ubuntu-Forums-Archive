---
title: "brother mfc scanner and sane: out of memory error"
date: 2012-11-28
forum: Hardware
---

### Post by lykwydchykyn on 2012-11-28
Here's my setup: 

 - Brand new brother mfc-j280w 
 - connected by USB to Debian squeeze server running sane.d
 - Two Ubuntu laptops running 12.04 and 12.10 respectively

The systems were setup to scan over the network using sane.d with the old scanner and this worked without a hitch.

I installed the brscan and brscan-skey drivers on the server and configured according to brother's instructions.

What works:

 - Scanner is detected by scanimage, sane-find-scanner, and xsane both on the server and the clients
 - I can acquire images at low (< 300 dpi ) resolution on the server using xsane or scanimage
 - I can acquire images at *lower* resolutions (~100 dpi) on the clients using scanimage

What doesn't work:
  - I can't acquire images at high resolution from anywhere; on the server I get "sane_read: Error during device I/O" and then the scanner is messed up until reset.

  - I can't acquire images from xsane on the network clients, I get "out of memory" errors, even when the resulting scan is fairly small (~10-30Mb).

  - I can't get a preview.  On the server it takes forever (much longer than the actual scan).  On the clients it gives an "out of memory" error.

Can anyone give me any advice on this?

---

### Post by lykwydchykyn on 2012-12-04
Submitted my problem to Brother and got this useless typical response:

[quote=Brother Support]
Brother Customer:

We have reviewed your request and we would be glad to offer you the 
assistance you need. Unfortunately, brother does not support scan 
sharing on any OS. 

We hope this information will be useful to you.  If we can be of further
assistance, please let us know.

Sincerely,


Fax/MFC Software Support
Customer Service
Brother International Corporation, USA
[email]swsup@brother.com[/email]

[/quote]

They conveniently ignored all the issues I was having on the machine to which the device was actually attached.  I replied asking for help with those issues, no response yet.

I shoulda got an HP.

---

