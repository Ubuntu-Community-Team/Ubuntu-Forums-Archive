---
title: "Onboard Nvidia 6100 and new Nvidia 9400 GT 512MB ISSUES"
date: 2009-10-25
forum: Hardware
---

### Post by Ausmosis on 2009-10-25
G'day,

Hoping someone might be able to assist. I currently have two PC's one with Jaunty and the other with Hardy. Both PC's have an on-board Nvidia 6100 graphics card and I want to use a new Nvidia 9400 GT 521MB card in both machines.  

The problem I am having is that the on-board card is obviously interfering as one computer will not boot into X and the other gets past the boot up but then flickers horrendously  at the login screen.

Can someone assist me in getting these cards recognized and working properly? I would appreciate an links to documents about how to get a new card working if you currently have an on-board card.

Thanks!

---

### Post by Ausmosis on 2009-10-26
Bump... Really hoping someone can assist me?

---

### Post by Dark_Stang on 2009-10-27
What type of slot are they going into? PCI, AGP, PCI-E, etc. If you're adding a card to a PCI slot you usually have to disable the onboard video first, then put the card in. AGP and PCI-E slots don't usually have this issue. Also, is your power supply powerful enough to handle the extra draw from the video card? If you're running a stock 300w power supply you need to upgrade.

---

### Post by Ausmosis on 2009-10-27
> **Dark_Stang said:**
> What type of slot are they going into? PCI, AGP, PCI-E, etc. If you're adding a card to a PCI slot you usually have to disable the onboard video first, then put the card in. AGP and PCI-E slots don't usually have this issue. Also, is your power supply powerful enough to handle the extra draw from the video card? If you're running a stock 300w power supply you need to upgrade.

Its going into a PCI slot. I went into the BIOS and the settings for the on-baord card was not enabled. Very strange considering its an on-board card. The setting was set to PCI so I tried PCI-E and still got as far as mentioned above. Is there another way to disable the on-board card?

---

### Post by Dark_Stang on 2009-10-27
Do you have a strong enough power supply?

---

### Post by Ausmosis on 2009-10-28
> **Dark_Stang said:**
> Do you have a strong enough power supply?

Yeah power supply is fine. I have a 3rd identical machine which runs Vista and I threw the card in that machine without a hiccup. Power supply definitely seems OK.... In the Hardy machine I was able to finally boot into Ubuntu yesterday after running xfix however it wasn't running the NVIDIA driver which resulted in an 800x600 resolution. I tried to install the latest NVIDIA driver but wasn't able to do so. It was stating I was missing libc libraries which is a load of rubbish.

I am progressing however I'm at a sticking point again as I can't install the driver for the card. I was hoping Ubuntu would have been able to recognise that I was using an NVIDIA 9400 GT card but in the hardware drivers setting it shows nothing.

Any suggestions?

---

