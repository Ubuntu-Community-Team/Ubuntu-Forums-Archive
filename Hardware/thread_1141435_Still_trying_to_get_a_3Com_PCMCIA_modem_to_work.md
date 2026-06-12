---
title: "Still trying to get a 3Com PCMCIA modem to work"
date: 2009-04-28
forum: Hardware
---

### Post by poltr1 on 2009-04-28
Last year, I posted [a thread in the beginner forum]("http://ubuntuforums.org/showthread.php?t=729528") about trying to get a 3Com 3CXEM556B PCMCIA modem/LAN card to work under Ubuntu.  Since then, I've learned that the LAN portion of the card works, and my wireless card works.  But the modem portion of the card doesn't appear to work.  This would be a nice-to-have feature, especially when I'm in a place that doesn't have high-speed internet.

I ran scanModem and it didn't detect the modem.  :(

Here are the vital stats:
Laptop: Dell Latitude CPxJ 650 GT
Flavor and version of OS: Ubuntu 8.04.2 (Hardy Heron)
PCMCIA card: 3Com 3CXEM556B combination modem/LAN

---

### Post by poltr1 on 2009-04-28
I looked up the info and directions for pcmciautils, which I had previously downloaded, and ran a couple of commands.  Here's the output.  Looks like the card is detected.  I think I'll just need the drivers.  Too bad 3Com doesn't provide drivers for their products for Linux systems.  :(

jim@tardis:~$ pccardctl info
PRODID_1="3Com"
PRODID_2="Megahertz 3CXEM556 B"
PRODID_3="LAN + 56k Modem"
PRODID_4=""
MANFID=0101,0035
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
jim@tardis:~$ pccardctl ident
Socket 0:
  product info: "3Com", "Megahertz 3CXEM556 B", "LAN + 56k Modem", ""
  manfid: 0x0101, 0x0035
  function: 6 (network)
Socket 1:
  no product info available

I also found a copy of 3CXEM556.cis on the koders.com web site and copied it to /lib per gordintoronto's suggestion.

---

