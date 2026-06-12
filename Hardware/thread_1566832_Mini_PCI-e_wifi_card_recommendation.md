---
title: "Mini PCI-e wifi card recommendation?"
date: 2010-09-02
forum: Hardware
---

### Post by Eil on 2010-09-02
Hello,

I have a Thinkpad T61 with an Atheros AR5212 wifi card. Ever since Ubuntu went to the open source driver for this (ath5k) from the madwifi drivers, I've had issues with wifi connectivity. The problem is that the wifi connectivity basically drops for 5-30 seconds every few minutes. I do a lot of remote command-line and remote desktop work and this is starting to drive me mad. I've scoured the net and have not yet found a good solution. I tried installing the madwifi drivers once, and those worked better, but then the card doesn't work after I wake the machine up from a suspend.

Can anyone recommend a good Mini PCI-e wifi card that works perfectly on Ubuntu (and ideally, other distros) with native drivers? If you have a laptop, are running Lucid, and have zero problems with your wifi, I'd appreciate it if you could take the time to do an lspci and post the output.

Thanks for your time.

---

### Post by Fafler on 2010-09-03
I'd recommend a Intel 5100. They are real cheap of eBay. However, it won't work in a ThinkPad as the BIOS checks if the cards an original IBM/Lenovo card during boot and it simply refuses to boot with another card installed. There are workarounds, but take a look at this before buying anything: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)
It might just be easier to install madwifi.

---

### Post by Eil on 2010-09-05
Thanks for the recommendation. I'll see if I can try to find one of those. I'm not sure if the T61 has the PCI ID whitelist. I thought I read somewhere that they stopped doing that after the T4x models, but I'll check into it some more.

---

### Post by Fafler on 2010-09-05
Nope. I have a T60p and it still have that "feature."

---

