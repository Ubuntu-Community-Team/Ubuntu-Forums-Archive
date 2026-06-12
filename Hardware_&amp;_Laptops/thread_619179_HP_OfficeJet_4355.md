---
title: "HP OfficeJet 4355"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by NIT006.5 on 2007-11-21
Strange problem here. I have two HP OfficeJet 4355 4-in-1's at work, purchased at the same time. In the beginning they worked fine. However several months after they were purchased, both within days of each other, they started having the exact same problems:

Incoming faxes are printed perfectly. Any printing done from Ubuntu comes out in a range of colours and does not appear to utilize the black cartridge at all. Sometimes prints come out all pink/purple, other times it starts off one colour and gradually changes as it goes down the page. Obviously different cartridges have been tested and it's nothing to do with that. Since faxes still print fine in black, I don't understand why this should happen when printing from ubuntu. This initially happened on Feisty and I was unable to find a solution. I have now upgraded the PC's to Gutsy, hoping that if it was a driver issue this would solve it, but I still have exactly the same problem. Does anyone have any thoughts?

Thanks.

---

### Post by proclaimation on 2007-11-23
I am a HP Officejet 960c that is doing similar thing - It's not using the black cartridge. I hope one doesn't need to buy certain equipment to have linux run properly. otherwise, linux is not a free operating system.

---

### Post by proclaimation on 2007-11-23
I got it working so I hope it helps.

1) you might have faulty cartridges. even if they are new. I replaced by black one as the printer was printing a text file but no ink on the page.

2)go to System>HPLIP Toolbox. go to top and do configure>settings>functions(advanced).
I changed the external command to "Built-in Print Function".

I can print now, which is better than buying a new printer (and probly having the same problems).

---

