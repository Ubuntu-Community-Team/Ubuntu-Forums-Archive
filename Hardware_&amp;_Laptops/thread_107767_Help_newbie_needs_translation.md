---
title: "Help newbie needs translation"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by ShortE on 2005-12-23
I have been trying to get my wireless cards working, but I'm really a newb on this stuff.  I got this info off of the hardware support page for wireless cards from the Wiki, but I don't really understand it.  I can run cardctl ident, but I'm not really sure what it does and I don't know what info to add to the file they mention, or what the other instructions mean.  Any help in very small words and simple sentences would be wonderful.  Thanks.

 Linksys
	

WPC 11 (Ver.2.5)
	

orinoco_cs
	

No
	

Yes
	

No
	

run "cardctl ident" and add info to /etc/pcmcia/config under wireless network adapters section. Be sure to include manfid and bind to orinoco_cs. Then just reboot and run "gksudo network-admin" in console and configure eth0...works like a champ!

---

### Post by ShortE on 2005-12-24
Surely there is someone who can't tear themselves away from Ubuntu for last minute X-mas shopping!:smile:

---

