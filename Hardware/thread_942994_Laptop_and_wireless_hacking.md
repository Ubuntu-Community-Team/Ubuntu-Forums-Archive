---
title: "Laptop and wireless hacking"
date: 2008-10-09
forum: Hardware
---

### Post by kcirtap on 2008-10-09
Hi
This is a somewhat hard to explain problem. I'm going to get a new laptop soon and I want one with a good wireless card. My current one has useless wireless support in Linux.

The thing is that I want to start hacking with wireless networks, like WEP-cracking and packet sniffing. I've realised that it's not possible to do this with all network cards however. Especially not mine.

Does anyone here first of all, know what kinds of functionality a wireless network card should have in order to have support for programs like aircrack, pcap, dsniff, kismet and similiar stuff? What cards should I stay away from?

I'm thinking about buying a Asus EEE 1000H. It's cheap, portable and has good battery time. The only thing I don't know about is the wireless card. If you know something about it, I would appreciate if you could tell me.

Thankful for any help and information about this.

---

### Post by markmaus on 2008-10-09
I've got an Asus Eee 1000H.  In fact I'm typing this message on it using the Ralink wifi builtin.  This ralink card is not yet supported well in Ubuntu.  This netbook also has an atheros LAN card that is not supported in Ubuntu.  I had to install Hardy, then download the Hardy EEE enabled kernel from a third party web site (on my desktop computer), then transfer the deb package to the EEE on a flash drive and install the new kernel.

[http://www.array.org/ubuntu/setup901.html](http://www.array.org/ubuntu/setup901.html)

 Once the new kernel is installed, everything works.  I don't know about airsnort and that kind of stuff.  I think that those programs are very specific as to what type of wifi chipset you use.  Check out the airsnort site.

---

### Post by sergiom99 on 2008-10-11
all the tools needed to play with wifi are in backtrack3 livecd (no need to install)
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)
and there is a hardware compatability list there, showing chipsets that support packet injection and monitor mode, etc.
[http://wiki.remote-exploit.org/index.php/Hardware_Compatibility](http://wiki.remote-exploit.org/index.php/Hardware_Compatibility)

---

### Post by 7thsky on 2010-10-09
hey, cn anyone tell me to hacking a wireless networking with my laptop plz. step by step plz. thx u

---

