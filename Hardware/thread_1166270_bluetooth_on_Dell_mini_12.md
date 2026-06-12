---
title: "bluetooth on Dell mini 12?"
date: 2009-05-21
forum: Hardware
---

### Post by TomaszC on 2009-05-21
Dell mini 12 is supposed to have bluetooth - has anybody managed to get it to work?

---

### Post by tyroeternal on 2009-05-21
The mini 12 does come with bluetooth.  I've not tested it myself, but I've never heard any complaints yet.

Which version of Ubuntu are you using?

---

### Post by TomaszC on 2009-05-21
> **tyroeternal said:**
> The mini 12 does come with bluetooth.  I've not tested it myself, but I've never heard any complaints yet.

Which version of Ubuntu are you using?

I have Ubuntu 9.04.

I don't see bluetooth when I i.e. do "hciconfig".

Also "find /sys -name bluetooth" doesn't seem to show any bluetooth devices.

---

### Post by tyroeternal on 2009-05-22
If bluetooth is not showing up properly it may be because it was turned off before you installed Jaunty.  Try installing the aircraft manager program and using that to turn it on.  When I installed jaunty I was unable to use wireless or bluetooth for this reason.

[http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)

---

### Post by TomaszC on 2009-05-22
> **tyroeternal said:**
> If bluetooth is not showing up properly it may be because it was turned off before you installed Jaunty.  Try installing the aircraft manager program and using that to turn it on.  When I installed jaunty I was unable to use wireless or bluetooth for this reason.

[http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)

Yes, I installed it and it was enabled (in aircraft-manager). I disabled it, re-enabled it... but any other programs don't show bluetooth.

---

### Post by TomaszC on 2009-05-23
Well, mini 12 has bluetooth setup in BIOS, which I had disabled ;)

---

### Post by tyroeternal on 2009-05-25
Oh, well it is good to hear you found it!  I was definitely at a complete loss, because my system seemed to be doing fine.

---

