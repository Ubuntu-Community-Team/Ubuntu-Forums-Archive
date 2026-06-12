---
title: "GPU not detected"
date: 2017-05-19
forum: Hardware
---

### Post by loganshowell on 2017-05-19
I just installed 16.04 LTS onto a new motherboard and when I tried to get the GPU working, it is not being detected by Ubuntu at all. I have installed the latest drivers from the AMD website but the display will only come through onboard graphics even though the BIOS is set to pcie. I could not find the graphics card with the lspci command or lshw either. I honestly have no clue what to do at this point.

Specs (all new):
Motherboard ASRock H81 Pro BTC
CPU: Intel Celeron G1840
GPU: Sapphire RX 480 4gb

---

### Post by Bucky Ball on 2017-05-19
Welcome. Is it detected by the BIOS? Try having a look in there and while you're in there, there is usually an option to switch off internal graphics (the video chip on the board). I have a seperate NVidia card and have my internal graphics off in the BIOS. Not sure that's making any difference in your case but the system should still pick up that the card is there either way. :-k

---

### Post by loganshowell on 2017-05-19
As far as I can find looking through the BIOS, there is no sign of it recognizing anything except the CPU, RAM, and SSD. I have the primary graphics adapter set to PCI Express but am not sure how to completely turn off internal graphics.

---

### Post by Autodave on 2017-05-19
Simply installing a PCIe card should divert the graphics to that card: there should be no reason to even have to tell the BIOS. Have you double-checked to make sure that the card is fully seated?

---

### Post by loganshowell on 2017-05-19
Yeah, I have even tried multiple different cards and none of them were recognized

---

### Post by Bucky Ball on 2017-05-20
Might be pointing to a dead slot if no cards are being detected in it. Have any cards worked in it before?

---

### Post by Yellow Pasque on 2017-05-20
1. Make sure you update the BIOS
2. Select PCI Express as Primary, disable IGPU multi-monitor (this will completely disable integrated graphics according to manual), and for the heck of it, manually set the PCI-e link speed to 2.x
3. Make sure your PSU has enough Wattage/Amperage and that any auxiliary power connector(s) on your GPU card are connected.

---

### Post by Bucky Ball on 2017-05-20
> **Temüjin said:**
> 
3. Make sure your PSU has enough Wattage/Amperage and that any auxiliary power connector(s) on your GPU card are connected.

+1. Good point. If in doubt, might be an idea to check a PSU calculator. There are a few available online where you can choose your components and it will give you a suggested PSU size.

---

