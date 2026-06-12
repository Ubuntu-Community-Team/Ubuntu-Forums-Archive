---
title: "PCMCIA double function card (LAN+modem): only LAN recognized?"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by r_mano on 2006-07-12
Hi all. 

I have a 3com/megahertz LAN + modem card:
Socket 1:
  product info: "3Com", "Megahertz 3CXEM556 B", "LAN + 56k Modem", ""
  manfid: 0x0101, 0x0035

It worked perfectly in my old distro, a Mandriva 2005. Now I changed to dapper (which I do not regret) and my card simply stopped to work. After a bit of digging, I discovered that I should do (as root, obvioulsy):

cp /etc/pcmcia/cis/3CXEM556.dat /lib/firmware/3CXEM556.cis

and now the card is detected, but _only_ the LAN interface. The modem has disappeared. Anyone knows how to tell pcmciautils to bind serial_cs module to the second function of the card? I really need that modem...

I have posted a dmesg from the old Mandriva distro (working card) and the new sad situation in the linux-pcmcia mailing list, but had no luck...

[http://lists.infradead.org/pipermail/linux-pcmcia/2006-July/003794.html]("http://lists.infradead.org/pipermail/linux-pcmcia/2006-July/003794.html")

Can anyone help me? 
Thanks in advance,

---

