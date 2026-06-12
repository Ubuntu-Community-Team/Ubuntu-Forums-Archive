---
title: "Pulse periodically briefly detects a headphone plugged in to the headphone jack"
date: 2015-08-06
forum: Hardware
---

### Post by benjamin45 on 2015-08-06
Hello,

I'm using the Realtek ALC892 audio chipset on a Gigabyte H97M-D3H. Under Windows the sound works fine, but under Linux, every few seconds it detects headphones being plugged in for a fraction of a second when they're not, temporarily muting the back panel audio for that period of time. 

Edit: I tested this in a live USB and it didn't occur there.

---

### Post by Yellow Pasque on 2015-08-06
It could be related: [https://bugzilla.kernel.org/show_bug.cgi?id=42655](https://bugzilla.kernel.org/show_bug.cgi?id=42655)
As a workaround, try turning auto mute off in alsamixer if you can.

---

### Post by benjamin45 on 2015-08-06
This isn't ideal because I often actually use the front panel jacks, but it's good enough temporarily.

---

### Post by nebhead772 on 2016-01-03
Any progress on this issue?  I'm experiencing it on the same mobo and just started my own thread here:  [http://ubuntuforums.org/showthread.php?t=2308438](http://ubuntuforums.org/showthread.php?t=2308438)

---

