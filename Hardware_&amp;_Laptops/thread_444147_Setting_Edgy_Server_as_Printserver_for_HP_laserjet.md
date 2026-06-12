---
title: "Setting Edgy Server as Printserver for HP laserjet 1022"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by vladk2k on 2007-05-15
Hello. I have read several posts on the HP LaserJet 1022 on lUbuntu and it still leaves me scratching my head.
I am pondering between 1022 and 1022n, since I will not use the printer on its host computer (which is a rather beaten up 900MHz Duron on a rubbish mainboard, but runs Ubuntu 6.10 server like magic). 1022n has the printswerver incorporated but costs 50% more, so I am trying to get a 1022 and make it work on ubuntu. Right now, I am using my very old HP LaserJet IIIp (15 years old) with cups and it works seamlessly.

I should tell you how it want to use it: The printer will be attached tot the computer, but the said computer will never in its lifetime print anything. It will only act as a "media converter" from ethernet to USB. On the other end of the twisted pair cable sit three machines with Windows XP (in the future maybe a Vista, seeing how theese printers tend to live a long time) and one of them dual-boots Ubuntu Feisty. The most important thing is that the HP driver on the WindowsXP machines works with the printer without any fuss. The people that will be using it need it to work without my intervention every time.

When I configured the LJ IIIp, I just went to [http://myserver:631](http://myserver:631), Add printer, LPT1, and in the list there was something like "old laserjet with PCL5". And it was done! But since this is a new printer, I am trying to figure out how things work.
The firs impediment I see is that there is no "USB" option when choosing how the printer is connected. It asks for, LPT, LPD/LPD, some internet based based stuff (http, ipp), and HP JetDirect (which is a standalone printserver hor HP printers). So, where is USB?
The next thing is, I installed the packages hplip, hpijs, hpijs-ppds (which replaced hplip-pdds) and now I see two more options in cups management: Backend Error Handler and hp no_device_found (which I presume will change once it detects the printer, but still i'd call it a long shot).

After that, from what I've read, I need a driver, and people seem to recommend foo2ijs. I have downloaded it, make'd it and now I should get "extra stuff" with ./getweb 1022. but! there is no entry for 1022, only 1000, 1005, 1018 or 1020. Is hplip and/or hpijs sufficient?

So, in as few words as possible, what do I need to make a non-printing print-server out of cups for HP laserjet 1022?

---

