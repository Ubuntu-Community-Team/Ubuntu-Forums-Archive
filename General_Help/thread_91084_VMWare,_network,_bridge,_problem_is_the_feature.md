---
title: "VMWare, network, bridge, problem is the feature?"
date: 2005-11-16
forum: General Help
---

### Post by klaim on 2005-11-16
I have installed VMware-workstation-5.0.0-13124.tar.gz on my Ubuntu Breezy (with using vmware-any-any-update95.tar.gz ) and have got the problem :???: - i'm not able to networking between my ubuntu and guest_win_xp. 
But! i have noticed :rolleyes: ... when i put on the network cable into my real network card everything is ok. So, can somebody explain me this bug/feature? In case is the feature i would to know, how i can make networking between linux and winxp without real network... only local connections. Maybe i need something like loopback cable? Just link RX and TX lines :) ? Somebody will have sed like "use host-only option" but it is not work too.

It is possible to use vmware without real network?

some logs:
Nov 16 22:28:17 localhost kernel: [4301020.504000] eth0: Promiscuous mode enabled.
Nov 16 22:28:17 localhost kernel: [4301020.504000] device eth0 entered promiscuous mode
Nov 16 22:28:17 localhost kernel: [4301020.504000] bridge-eth0: enabled promiscuous mode
Nov 16 22:28:17 localhost kernel: [4301020.504000] /dev/vmnet: port on hub 0 successfully opened
Nov 16 22:28:29 localhost kernel: [4301029.680000] r8169: eth0: PHY reset until link up
Nov 16 22:28:36 localhost kernel: [4301039.680000] r8169: eth0: PHY reset until link up
Nov 16 22:28:46 localhost kernel: [4301049.680000] r8169: eth0: PHY reset until link up
Nov 16 22:28:56 localhost kernel: [4301059.680000] r8169: eth0: PHY reset until link up
Nov 16 22:29:06 localhost kernel: [4301069.680000] r8169: eth0: PHY reset until link up
Nov 16 22:29:16 localhost kernel: [4301079.680000] r8169: eth0: PHY reset until link up
Nov 16 22:29:26 localhost kernel: [4301089.680000] r8169: eth0: PHY reset until link up

---

### Post by lol on 2006-01-20
I recently realised that I have the same problem... No networking between the host and the guest OS when the network cable is unplugged.

I am a little bit surprised, because I used VMWare for about 1 year, and never realised this before! I cannot access the vmware forums right now, which doesn't help looking for answers, but here is an interesting link:
[http://www.sklar.com/blog/archives/55-Wrangling-CoLinux-Networking.html](http://www.sklar.com/blog/archives/55-Wrangling-CoLinux-Networking.html)

---

### Post by lol on 2006-01-20
VMWare forums are up again, check out this link:
[http://www.vmware.com/community/thread.jspa?messageID=337682&#337682](http://www.vmware.com/community/thread.jspa?messageID=337682&#337682)

---

