---
title: "Compaq Armada E500 Help much appriciated"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by tesseract85 on 2005-07-11
I installed ubuntu over the weekend and it will not recognize the cardbus on my system. I have a Compaq Armada E500 that is about 7 years old.
When i used windows before it recognized it and said it was a texas instruments.....untill i installed my motorola wireless card then it said it used a generic cardbus.
How can I find out what card bus it is.........lspci tells me its unknown.
I need help bad.
If you need to know more let me know and ill tell you everything you need or what I can do to get this working.

I want to use my motorola wireless card.......i konw i kow broadcom........oo well 

Ill cross that bridge when i get this one done first.

thanks for your help



JR

---

### Post by jpaechnatz on 2005-07-11
you could try to update the pci ids, perhaps then the status changes to the correct device names instead of unknown.

open a shell/terminal/console and enter (you should have a working network connection/proxy setup):
sudo update-pciids

then enter lspci again:
lspci

cu joh.

---

### Post by tesseract85 on 2005-07-11
how do i do that if i do not have a working network connection?

---

