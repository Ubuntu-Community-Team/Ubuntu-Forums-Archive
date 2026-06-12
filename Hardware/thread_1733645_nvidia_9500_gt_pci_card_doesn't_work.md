---
title: "nvidia 9500 gt pci card doesn't work"
date: 2011-04-19
forum: Hardware
---

### Post by DonutFUN on 2011-04-19
I'm trying to install Ubuntu on here, and it lest me install with my on board video card, and when it boots it comes up with proprietary drivers for my video card, and when I install them it then wont startx after I boot again. It asks me to boot into the text prompt, and when I say startx it say "no monitors available" or something

Its a Jaton Corporation video-498pci-dlp PCI Nvidia 9500GT

and when I use the program system info it says its PCIE, but I don't even have PCIE in my computer.

By the way I'm new to linux, I know some stuff, but not a lot, so go easy on me.

---

### Post by xtjacob on 2011-04-19
You could try running this command then try startx:
```
sudo nvidia-xconfig
```

---

### Post by DonutFUN on 2011-04-19
I tried that, didn't work, it came up with some error, but I can't remember what it was

---

### Post by SeijiSensei on 2011-04-19
Run it again and report the error here.

---

