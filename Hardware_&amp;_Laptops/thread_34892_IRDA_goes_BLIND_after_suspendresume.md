---
title: "IRDA goes BLIND after suspend/resume"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by ksaling on 2005-05-16
I use irda to sync my cellphone with Evolution on my laptop (Thinkpad T40).  Works fine as long I don't suspend the laptop.

As soon as I resume the laptop from suspend, irda continues to broadcast in "discoverable" mode, but it is COMPLETLY BLIND to other irda devices (my cellphone).  In other words, `irdadump` only sees itself.  It does not see the other device like it normally does.

22:51:35.037893 xid:cmd 65e98b78 > ffffffff S=6 s=0 (14)
22:51:35.127877 xid:cmd 65e98b78 > ffffffff S=6 s=1 (14)
22:51:35.217861 xid:cmd 65e98b78 > ffffffff S=6 s=2 (14)
22:51:35.307846 xid:cmd 65e98b78 > ffffffff S=6 s=3 (14)
22:51:35.429522 xid:cmd 65e98b78 > ffffffff S=6 s=4 (14)
22:51:35.562636 xid:cmd 65e98b78 > ffffffff S=6 s=5 (14)
22:51:35.695751 xid:cmd 65e98b78 > ffffffff S=6 s=* jet hint=0400 [ Computer ] (19)

I tried removing and reinserting the following modules in the following order
  rmmod irtty_sir
  rmmod sir_dev
  rmmod irda
  rrmmod crc_ccitt
  -----
  modprobe crc_ccitt
  modprobe irda 
  modprobe sir_dev
  modprobe irtty_sir

I tried /etc/init.d/irda-utils restart

Nothing works, except a reboot.

I even pointed the cellphone at the infrared eye on the laptop and attempted to send a picture via infrared while watching with `cat /dev/ttyS1` and there was nothing.

Any thoughts?  What is being reloaded during the boot sequence that I am missing?  If I can figure that out I can add the appropriate commands to the apmd_proxy.

---

### Post by jasmuz on 2005-05-19
[QUOTE=ksaling]I use irda to sync my cellphone with Evolution on my laptop (Thinkpad T40).  Works fine as long I don't suspend the laptop.

As soon as I resume the laptop from suspend, irda continues to broadcast in "discoverable" mode, but it is COMPLETLY BLIND to other irda devices (my cellphone).  In other words, `irdadump` only sees itself.  It does not see the other device like it normally does.

22:51:35.037893 xid:cmd 65e98b78 > ffffffff S=6 s=0 (14)
22:51:35.127877 xid:cmd 65e98b78 > ffffffff S=6 s=1 (14)
22:51:35.217861 xid:cmd 65e98b78 > ffffffff S=6 s=2 (14)
22:51:35.307846 xid:cmd 65e98b78 > ffffffff S=6 s=3 (14)
22:51:35.429522 xid:cmd 65e98b78 > ffffffff S=6 s=4 (14)
22:51:35.562636 xid:cmd 65e98b78 > ffffffff S=6 s=5 (14)
22:51:35.695751 xid:cmd 65e98b78 > ffffffff S=6 s=* jet hint=0400 [ Computer ] (19)

I tried removing and reinserting the following modules in the following order
  rmmod irtty_sir
  rmmod sir_dev
  rmmod irda
  rrmmod crc_ccitt
  -----
  modprobe crc_ccitt
  modprobe irda 
  modprobe sir_dev
  modprobe irtty_sir

I tried /etc/init.d/irda-utils restart

Nothing works, except a reboot.

I even pointed the cellphone at the infrared eye on the laptop and attempted to send a picture via infrared while watching with `cat /dev/ttyS1` and there was nothing.

Any thoughts?  What is being reloaded during the boot sequence that I am missing?  If I can figure that out I can add the appropriate commands to the apmd_proxy.[/QUOTE]
 I recomend you read this [http://www.hpl.hp.com/personal/Jean_Tourrilhes/IrDA/IrDA.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/IrDA/IrDA.html) and after ask some questions, because its a well known error in the IrDa.

---

