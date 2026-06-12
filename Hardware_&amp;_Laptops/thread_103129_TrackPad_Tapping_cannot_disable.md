---
title: "TrackPad Tapping cannot disable"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by prakity on 2005-12-13
Running ubuntu on syon vaio --  I edited /etc/X11/xorg.conf

I tried 
Option "MaxTimeOut" "0"
and
Option "TapButton1" "0"

neither work.  -- synaptics touchpad --

Anyone know what SendCoreEvents does ?

regards,

Philip

---

### Post by prakity on 2005-12-13
I commented out SendCoreEvents  === things are  better 
now 

tapping still works BUT automatic focus and enter does not 
eg (as in moving mouse over firefox button no longer "clicks into" the button

---

