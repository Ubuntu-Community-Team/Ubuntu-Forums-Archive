---
title: "HP 845c prints garbage"
date: 2008-09-10
forum: Hardware
---

### Post by tipp98 on 2008-09-10
Hello all, I have an essentially fresh, updated install of Kubuntu 8.04.1 installed which appears to have installed the hplip driver by default, which looks good. I can print a test page through the HP Device Manager, and through the CUPS web interface. They both print fine aside from printing in 100% magenta as the color cartridge is about out of ink. However, when I try to print from Firefox, or Open Office, I get miscellaneous black characters along the boarders. It's usually the top boarder, and ranges anywhere from a whole line to one character to none. It doesn't matter how small the document or how few pages are printed, it just keeps feeding paper until it runs out and I have to turn the thing off to get rid of the job. I'm at a loss for ideas as to what the problem might be. Any help would be greatly appreciated.

---

### Post by tipp98 on 2008-09-10
Success!!!  For whatever reason, CUPS was using the cdj670 driver for this printer, which I noticed while inspecting the "Printers" tab in the CUPS web interface. So I changed it to the hpijs driver using the modify printer option.

---

