---
title: "Lucent modem problem"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by Heretic09 on 2005-12-29
I followed the steps listed under the "modems supported by lucent" section here:

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=forum%2Fhardware%2Fmodem]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=forum%2Fhardware%2Fmodem")

The problem is when I get to modprobing the lt_serial and lt_modem I get
lt_serial FATAL: module lt_serial not found.

and

lt_modem FATAL: module lt_modem not found.

I have the restricted modules for 2.6.11 which should have the non free lucent drivers. Any one know why it is unable to locate them?

---

### Post by edemark on 2006-01-19
Yes
They are not there. Silly isnt it. So you have to compile yourself 
this thread may be helpful

[http://www.ubuntuforums.org/showthread.php?t=93852&highlight=lucent+modem](http://www.ubuntuforums.org/showthread.php?t=93852&highlight=lucent+modem)

good luck

---

