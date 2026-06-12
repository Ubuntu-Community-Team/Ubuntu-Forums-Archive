---
title: "Is DWL-650 on Older Thinkpad Supported?"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by mengd2002 on 2007-10-02
A friend of mine wants to give me her laptop because she is getting a new one through work.  It's not the newest machine in the world, but it still works and it is free.  It's a Pentium 3 class IBM Thinkpad (model# escapes me).  It doesn't have built in wireless support but I have a working Dl-Link Air DWL-650 wireless card.  She borrowed the wireless card for a while so I know everything works under Windows.  My question is, will Feisty or Gutsy support this hardware?  I'm particularly concerned about the wireless card.  Is there a website or documentation that deals with wireless card and networking issues?
Thanks.
Don

---

### Post by linuxwizard on 2007-10-04
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by dinub1 on 2007-10-04
> **mengd2002 said:**
> A friend of mine wants to give me her laptop because she is getting a new one through work.  It's not the newest machine in the world, but it still works and it is free.  It's a Pentium 3 class IBM Thinkpad (model# escapes me).  It doesn't have built in wireless support but I have a working Dl-Link Air DWL-650 wireless card.  She borrowed the wireless card for a while so I know everything works under Windows.  My question is, will Feisty or Gutsy support this hardware?  I'm particularly concerned about the wireless card.  Is there a website or documentation that deals with wireless card and networking issues?
Thanks.
Don

Yes it does. It uses Atheros chip set which is well supported under Linux and Ubuntu. As a matter of fact my laptop lacks a wireless card too. So I am using (when I need) a D-Link DWL-G650 PCMCIA card with it. It works very well with knetworkmanager and supports WPA/WPA-2 encryption. It is automatically detected and driver supplied, also knetworkmanager knows to auto detect available networks. You only need to supply the encryption password and you are good to go.

---

