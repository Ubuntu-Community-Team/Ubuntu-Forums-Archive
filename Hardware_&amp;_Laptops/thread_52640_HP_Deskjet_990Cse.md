---
title: "HP Deskjet 990Cse"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by Reducer on 2005-07-28
I've got an HP Deskjet 990Cse installed on LPT1 on mmmmy Hoary AMD64 machine.  Ubuntu detects it and I install the proper drivers (HP DeskJet 990C), but printing anything results in pages and pages of gibberish.

The printer works fine with FC4 AMD64, and Hoary i386, as well as Windows.

Any ideas?

Jason

---

### Post by David Haas on 2005-07-28
jason--I see that Ubuntu Hoary contains 5 PPD files labelled as 990C: HP-DeskJet_990C-cdj550.ppd.gz
HP-DeskJet_990C-cdj970.ppd.gz
HP-DeskJet_990C-chp2200.ppd.gz
HP-DeskJet_990C-hpijs.ppd.gz
HP-DeskJet_990C-pcl3.ppd.gz

They are located at :/usr/share/cups/model/foomatic-ppds/HP.

I don't know which one would work best with your AMD64, but you could try each in turn.

David

---

### Post by Reducer on 2005-07-31
Thanks for your response.  On your advice, I did try all of them in turn, with similar results.  The PCL3 driver seemed to work the 'best' since it only printed one page of gibberish instead of 20. :)

Jason

---

