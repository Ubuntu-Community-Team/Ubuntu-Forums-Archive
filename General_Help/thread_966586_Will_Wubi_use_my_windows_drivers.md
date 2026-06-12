---
title: "Will Wubi use my windows drivers?"
date: 2008-11-01
forum: General Help
---

### Post by Suilenroc on 2008-11-01
Hey all. So, I used to be a major Ubuntu/Linux fan, but recently switched back to windows. The reason behind this was the Sound Card I bought, a Creative Elite Pro. It just doesn't work in Linux, and I can't live without it.

This prospect of a Wubi install, however, is exciting. I was wondering if this would go through my windows drivers, instead of using drivers of it's own, so that I could use my sound card in it.

Does anyone know?

---

### Post by Rhubarb on 2008-11-01
The answer would be no, windows drivers are not compatible with Linux.(there's a few that are, like wireless drivers, but in general, no).

There may be specific drivers for that sound card for Linux out somewhere - though I haven't heard of such drivers for that specific sound card myself.

---

### Post by Suilenroc on 2008-11-01
Well, I was under the impression that Wubi was just a glorified virtualization. If that were the case, then all of the instructions would run through windows, thus passing through windows' drivers. 

Am I wrong in this assumption?

---

### Post by Rhubarb on 2008-11-01
Wubi doesn't do any visualization.
All it does is it creates a big file on your windows ntfs partition (and installs Ubuntu to that file).
Then it changes your windows boot loader to give you the option of booting into Ubuntu.

It also gives you an option to uninstall Ubuntu from within windows.

It's actually very similar to traditional dual-booting.
So, having windows drivers will not help you get sound in Ubuntu.

But, if you try a virtual machine product (like virtualbox) in windows, then yes, sound should work from within Ubuntu if you install Ubuntu inside the virtual machine.

---

