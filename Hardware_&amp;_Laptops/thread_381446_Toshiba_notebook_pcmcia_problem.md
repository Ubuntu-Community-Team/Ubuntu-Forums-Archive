---
title: "Toshiba notebook pcmcia problem"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by fishymark27 on 2007-03-10
Hi, I have just installed **Xubuntu** via the alternative dist. cd onto a **Toshiba portégé 3110CT** notebook, with a docking station (through which I successfully connected to the LAN) and a **pcmcia cdrom drive**. 

It installed fine from the cd, but I now can't get access to the cdrom at all, the power light is off on the cdrom, plus it doesn't register at all when I run *lspci*. It seems to not even realise that the pcmcia slot exists. I have got pcmciautils installed I think, but I'm not really sure what to do with it, and have been surfing around for ages trying to make it work. I've read the mini-howto guide etc. but I still can't figure out what to do.

If you need more info please let me know.

The cdrom still works in windows 98, which I have currently still got dual booted, while I sort out the glitches.

---

### Post by fishymark27 on 2007-03-15
I finally worked out how to do it. The pcmcia socket wasn't loaded correctly. This can be fixed by doing 

*sudo modprobe i82365 *

Where i82365 was my particular socket module. Now the only grumble I have is that it hot boots, but I can't eject the card.

Or by updating the BIOS from the TOSHIBA website, and then changing the bios settings to cardbus. which should then mean that Yenta-socket starts automatically.

---

