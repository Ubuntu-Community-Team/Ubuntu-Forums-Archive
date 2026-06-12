---
title: "Radeon open source drivers for laptops+gaming"
date: 2014-03-09
forum: Hardware
---

### Post by molgrum on 2014-03-09
Hi.

I'm wondering what Radeon card with open source drivers I should get for my new laptop. I have one in my desktop (HD 5770) which is noisy unless I force low profile, and i have one in my current laptop (Mobility HD 3450/3470) which is silent but gives me only 20-30 FPS in 3D games.
Are there any that work flawlessly with open source drivers or should I go with Intel Haswell chips?

---

### Post by Mark Phelps on 2014-03-09
Are you sure your laptop will accept a separate video card? Asking, because nearly ALL laptops come with the video chipset permanently soldered to the motherboard -- and do NOT have the abiility to add a video card.

My guess is that the one in your laptop is NOT a separate card but an onboard processor -- and that processor will not run the fglx drivers (which are needed for Gaming) with any Ubuntu version newer than 12.04.1 due to conflicts with the X-server versions present in the newer Ubuntu releases.

---

### Post by molgrum on 2014-03-09
> **Mark Phelps said:**
> Are you sure your laptop will accept a separate video card? Asking, because nearly ALL laptops come with the video chipset permanently soldered to the motherboard -- and do NOT have the abiility to add a video card.

My guess is that the one in your laptop is NOT a separate card but an onboard processor -- and that processor will not run the fglx drivers (which are needed for Gaming) with any Ubuntu version newer than 12.04.1 due to conflicts with the X-server versions present in the newer Ubuntu releases.

Oh, I didn't mean to add a card, I meant the one already in the laptop (didn't know it was burned into the motherboard). I intend not to use fglrx because it's proprietary, but thanks for the heads up that it doesn't work with the latest Ubuntu version!
Is the open source driver for laptops that bad still? I guess I have to choose an Intel chip in that case.
About Intels graphics chips, does Haswell work good with 3d games?

---

### Post by Mark Phelps on 2014-03-09
My own experience has been that, with Radeon video chipsets, you really need the fglrx drivers in order to get the hardware acceleration and feature controls needed for Gaming.  The open-source drivers have been getting better year after year, but my most recent experience with an AMD HD 8850 showed that you still can't beat the fglrx drivers for real-time performance.

As to Intel, there aren't any restricted drivers; instead, the available ones are installed as part of initial setup.  But, I don't have a current Intel chip PC, so I can't comment on their performance.

---

### Post by molgrum on 2014-03-11
It would be very handy for me if there was a list of well supported  Radeon chips for laptops using the open source driver. I don't need it  to be extremely fast, just decent FPS and good power management. Battery  life before good FPS is my priority since I don't play games much, but  when I do I want it to be at least "playable".
Does anyone know where  I can find such a list, or can you recommend any chips for me that are  in laptops in retail stores right now?

---

### Post by Yellow Pasque on 2014-03-11
For your desktop card, have you tried DPM?
[https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by molgrum on 2014-03-12
> **Temüjin said:**
> For your desktop card, have you tried DPM?
[https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

I can report that (so far) this works good for HD 5770. I have scrapped the low-profile force in my init scripts. Temperature in idle mode is ~50 and in OpenArena @ 85 maxfps it's ~60.
I also found this to check support for cards: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)
I tried it on my current (very old) laptop also and I can say that I don't recommend it, black screens at boot and lockups when launching games are encountered and it didn't increase my FPS at all.

---

### Post by Yellow Pasque on 2014-03-12
Yeah, I don't think DPM works well for RadeonHD 2000 and 3000 series. AMD's open source team seems to be focused on RadeonHD 4000 series and later.

---

### Post by Mark Phelps on 2014-03-12
Sorry I can't be of much more help ...

I used a Radeon HD 4290 for years, and got really good performance out of it.

Then, AMD relegated it (along with all the other HD 2x/3x/4xd-series cards) to the "scrap heap" by dubbing it as "legacy".

Even so, for a while the Radeon drivers seemed to work pretty well for the 2D graphics I use (don't do 3D gaming).

But, when the chip started to go bad (major artifacts on the display!) I replaced it with a new AMD HD 8850 -- and then discovered that the Radeon drivers for THIS card are really awful!

As to Temujin's comment > AMD's open source team seems to be focused on RadeonHD 4000 series and later.  that's news to me.  I hadn't seen any recent improvements in the HD 4290 Radeon drivers.

---

