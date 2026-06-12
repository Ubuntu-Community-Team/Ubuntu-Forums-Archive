---
title: "Wireless problems"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Jameson on 2005-09-11
I installed ubuntu at work and the wireless network there is open and I have no problems there.  My home wireless network is is also open but I can't get it to recognize it the wireless network at home.  I've tried everything under the network configuration module and nothing seems to work to get it to connect to the internet/network.

Anybody know why this is?

---

### Post by bysse on 2005-09-13
What hardware are you using and what's your laptop model?

---

### Post by Jameson on 2005-09-14
The modem is a DSL Actiontec with wireless capabilities.  The laptop is a Compaq Presario 1600 series.  The wireless network at my university works with it and the wireless network at my office also works with it.  But at home it doesn't work which is weird because it worked just fine when my laptop was Windows based.  It must have something to do with the signal from my modem not being read by the Linux networking software...any tips on how to configure it?

---

### Post by bullpa on 2005-09-14
[QUOTE=Jameson]But at home it doesn't work which is weird because it worked just fine when my laptop was Windows based.  It must have something to do with the signal from my modem not being read by the Linux networking software...any tips on how to configure it?[/QUOTE]

Can you see your wireless router by iwlist scanning? if so, check your router's security settings, i.e. WPA. Try to disable the encryption or use WEP.

---

