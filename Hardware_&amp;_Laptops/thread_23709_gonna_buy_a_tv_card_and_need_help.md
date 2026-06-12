---
title: "gonna buy a tv card and need help"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by chronusdark on 2005-04-03
i was orginally gonna get me a TV for my room so i could watch cable TV and play my xbox etc with out using the tv in the living room but then i got to thinking i dont really have room for it so i decided to get a TV card so i can do the same things on my Computer monitor!!! but i need some help..i want one thats easy to set up under ubuntu and windows if need be and i want it to just have like a coax or RCA inputs

anyone have an idea of what i should get

thanks in advance

---

### Post by matgorb on 2005-04-03
I was in the same situation, and actually I also realise that I could have a free vcr this way, and i did some research, the bt8x8 chipsets are a quite safe bet (from brooktree which now belong to connexant) So i looked arround, the PCTV Rave (Miro or Pinnacle) is the original card that brought the bttv driver for linux but a lot of other cards are based on the same chipset. I personnaly found the Hercules Smart TV 2 Stereo in my local shop, cheaper than the basic pctv rave (which seems to be hard to find these days)  and in stereo, after a quick look on google for linux support, i found this page on the ubuntu site itself, so it should be a safe bet, i will get it next week, i will let you know.

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsMultimedia](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsMultimedia)

---

### Post by chronusdark on 2005-04-03
cool thanks PM me or post in this thread to let me know whats up

---

### Post by matgorb on 2005-04-07
The shop didn't have the hercules, so I bought the Hauppauge WinTV Express.
Plugged in, get Xbox working on the composite, and no tv.
I added the line in /etc/modprob.d/bttv

options bttv tuner=51

and now it works fine

---

### Post by chronusdark on 2005-04-07
i think im just gonna get this one here 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1048731&CatId=1427](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1048731&CatId=1427)
its only 30 USD and it has a remote
also i have read somewhere that the 2.6 kernel should support it out of the box

---

