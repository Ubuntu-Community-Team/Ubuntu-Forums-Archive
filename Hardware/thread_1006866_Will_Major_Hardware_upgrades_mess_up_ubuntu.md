---
title: "Will Major Hardware upgrades mess up ubuntu?"
date: 2008-12-09
forum: Hardware
---

### Post by eweb100 on 2008-12-09
How will Ubnutu 8.10 64 bit react to MAJOR hardware changes?

1. will be upgrading from 2 gigs of ram to 4
2.2.4 duel core processer to 3.1 duel core
3.400 wat power to 900 watt
4.Posible a whole new motherboard.
5.and the big one.. a 1500 raidon graphics card to TWO 9800 raidon graphics card using sli.

WIll it just continue like normal? or will it phail?

Also can you sli in unbutu? Does it suport it?

---

### Post by capn_hector on 2008-12-09
ok the power supply will be no problem neither will the ram, the processor as long as its a faster processor of the same family (1.5 p4 for a 2.0 p4 for example) might be a problem but prolly not  the places youll run into problems is the video cards but if you have the right drivers on your system all ready that will be some configuration.  the motherboard is one thing if you run a stock kernel it should pick up the change but i would back up and reinstall if you do add the new motherboard. for the other changes ubuntu will handle them just fine

---

### Post by cariboo on 2008-12-09
I would suggest you move to either 64bit or a server kernel if you want to get the full benefit of 4Gb ram.

The rest of the changes, except for the video cards won't have any affect on Ubuntu at all.

You may have to do some searching to get SLI to work.

JIm

---

### Post by eweb100 on 2008-12-09
So. If there new graphics card is already suported by ubuntu i dont have to wory about it

---

### Post by capn_hector on 2008-12-10
> **eweb100 said:**
> So. If there new graphics card is already suported by ubuntu i dont have to wory about it


correct however as cariboo stated the sli will have to be set up right

---

### Post by markbuntu on 2008-12-10
I had no problems with major component upgrades with Hardy i386 and amd64, this includes a new HD3650 graphics card that replaced an onborad gpu, a new motherboard/cpu/ram upgrade and ps upgrade. 

Radeon does not use sli that is a nvidia thing so are you planning for 2 nvidia 9800 cards?

If you are using a restricted driver you should change to the VESA driver and remove any restricted driver before you make the graphics card changes as a precaution. Once you get all your new hardware working in VESA you can install the restricted drivers and set them up.

---

### Post by eweb100 on 2008-12-10
Yes i will by using 2 nvidia 9800 graphics cards

---

### Post by markbuntu on 2008-12-11
YOu should have no problems then.

---

