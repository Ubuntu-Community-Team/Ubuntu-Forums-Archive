---
title: "atheros wireless card not working"
date: 2011-10-29
forum: Hardware
---

### Post by elevenuser on 2011-10-29
i am trying to setup ubuntu server 10.04.3 due to my machine not booting into 11.10 unless it is into recovery mode. i am on a dell latitude d410. i have an atheros ar5001x+ card which is replacing the old intel pro/wireless 2100.   i get no wlan0 interface with either card, the intel does give an eth1 for some reasoneven though its a wireless card, this causes issue connecting to a wpa network which is why i replaced it.  when i boot the pc i get told that &quot;ath5k: couldn't wake the mac chip&quot; and i get no wireless device. i do NOT have wired access on this machine so have to use a flash drive to transfe packages. i have even tried this card on arch linux with the same issue. does this mean my card is bad?  can i get the intel working if this is bad? how can i get this fixed? i know the ath5k drivers are built into the kernel itself. modprobe does show the ath5k modules as loaded.

---

### Post by e-tecno on 2011-11-12
Hi.... see: [http://www.linuxquestions.org/questions/linux-networking-3/atheros-card-on-ubuntu-server-x86_64-a-517973/](http://www.linuxquestions.org/questions/linux-networking-3/atheros-card-on-ubuntu-server-x86_64-a-517973/)
 
and:
 
[http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)
 
I had the same problem as you and fix it.   Bye.

---

