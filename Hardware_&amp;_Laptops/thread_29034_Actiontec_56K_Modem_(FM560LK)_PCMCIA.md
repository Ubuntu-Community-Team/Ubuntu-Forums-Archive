---
title: "Actiontec 56K Modem (FM560LK) PCMCIA"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by wwwolf on 2005-04-22
I have a LC2430 laptop from Linux Certified. Last spring, my onboard modem Uniwill 82801DB AC'97 was struck by lightning. After looking at various modems I decided to go with the Actiontec 56k PCMCIA modem (FM560LK) since it even says it works with Linux on the outside of the box. I have never been able to get it to work.

I emailed Actiontec and they stated:

The reponse to this issue is below:
=================================================================
Install as you would any modem in LINUX using the generic drivers built
into LINUX. Once installed, you use the same settings to set the modem to your dialup application that you would use for any controller based modem in LINUX.
=================================================================

Cardinfo just shows:

Serial or Modem
IO 0x3f8 - 0x3ff
IRQ 3, Dev ttys0

and cardctl info shows:

PRODID_1 = "PCMCIA"
PRODID_2 = "56k v.90 Fax Modem (LK)"
PRODID_3 = "FM560LK"
PRODID_4 = ""
MANFID = 0175,0000
FUNCID = 2

I use KPPP and choose dev/ttys0 in the menu and query the modem and it says modem is busy, I also try dev/modem, and everything else in the menu as well.

I'm really lost as what I should do next to get this to work.

Thanks for your help,
wwwolf

---

### Post by az on 2005-04-22
"Dev ttys0"

Be very specific.

/dev/ttyS0

That is a capital "S" and a zero.

Lemme know if it works...

---

### Post by wwwolf on 2005-04-22
Thanks for the response. Actually I have been selecting the device from a dropdown menu as /dev/ttyS0. I have also used the menu selection /dev/modem. It _is_ a capital S in the menu, I had just made the mistake of typing a small s when posting the question.

What do you think my next should would be?

Thanks for the help,

wwwolf

---

### Post by wwwolf on 2005-04-22
Actually, for what its worth, I stuck it in my mother's winXP laptop and it works using the MicroSoft drivers modem.sys and serial.sys. Since Actiontec assures me that this modem will work under linux I guess it is just a matter of manually assigning a generic driver for it. I don't know how to do this though.

I really like kubuntu (installed today!!!) and I hope I can get this modem to work so I can start using apt-get that I have heard so much about.

Thanks

wwwolf

---

