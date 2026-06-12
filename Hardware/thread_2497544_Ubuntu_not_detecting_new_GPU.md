---
title: "Ubuntu not detecting new GPU"
date: 2024-05-09
forum: Hardware
---

### Post by drew1121 on 2024-05-09
Today i upgraded my GPU to an RX 7600. But when I pull up a neofetch, it seems like it is using my integrated graphics instead. Instead of RX 7600 it says "AMD ATI 08:00.0 Device 7480 ". Is there anyway I can make Ubuntu use the GPU and not the integrated graphics?

---

### Post by #&amp;thj^% on 2024-05-09
What release version are now running? 22.04 won't yet support that card 23.10 and newer is supported though.

The pains of new-ish hardware. ;)

---

### Post by drew1121 on 2024-05-09
I am running 22.04. If i fresh installed 24.04 would I be able to run the card?

---

### Post by #&amp;thj^% on 2024-05-09
> The Radeon RX 7600 is a nice lower-end graphics card for 1080p gamers and has upstream open-source Linux support already -- including the ability to run out-of-the-box already on Ubuntu 23.04 and other newer distributions.
Source: [https://www.phoronix.com/review/amd-radeon-rx-7600-linux](https://www.phoronix.com/review/amd-radeon-rx-7600-linux)

I'm Leary of telling anyone 24.04 is a good choice at this time, but maybe in a few months from now. Still needs some minor bugs ironed out.
I would try a Live 23.10 for now, but that's a choice only you can decide.
Then wait for the upgrade to 24.04.1 hits.
Good Luck

---

### Post by Yellow Pasque on 2024-05-10
> AMD ATI 08:00.0 Device 7480 
That is the RX7600: [https://admin.pci-ids.ucw.cz/read/PC/1002/7480](https://admin.pci-ids.ucw.cz/read/PC/1002/7480)

If you want it to display the correct name, run
```
sudo update-pciids
```

---

### Post by #&amp;thj^% on 2024-05-10
> **Yellow Pasque said:**
> That is the RX7600: [https://admin.pci-ids.ucw.cz/read/PC/1002/7480](https://admin.pci-ids.ucw.cz/read/PC/1002/7480)

If you want it to display the correct name, run
```
sudo update-pciids
```
+1
But the OP was solved here: [https://ubuntuforums.org/showthread.php?t=2497550&p=14189197#post14189197](https://ubuntuforums.org/showthread.php?t=2497550&p=14189197#post14189197)

---

