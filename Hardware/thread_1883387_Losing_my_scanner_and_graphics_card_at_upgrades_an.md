---
title: "Losing my scanner and graphics card at upgrades and updates"
date: 2011-11-19
forum: Hardware
---

### Post by shimanotaka on 2011-11-19
I'm running Ubuntu 11.10 and I have an Epson Perfection V300 Photo scanner for which I use a driver from Avasys ([http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)) and my graphics card is the ATI Radeon HD 4200, integrated on my M4A785TD-M EVO motherboard, for which I use the fglrx driver.

I've been using Ubuntu since 9.04 I think and _every_ upgrade and major update (usually when the kernel is updated and sometimes in between), my computer will be booting to a blank screen or the prompt. It's getting a bit annoying...

I haven't worked out a clear recovery process, but it usually involves purging the fglrx driver and reinstalling it.

Same thing with my scanner. It works fine and then suddenly, after some update, it's not found by any scanning programs. That also involves reinstalling drivers and some other steps that I haven't worked out yet. I just keep trying stuff, and banging my head on the desk and then I somehow manage to make it work again.

Does anyone have any idea why this is happening and the easiest way to avoid it or get through it? I've started thinking about buying an Nvidia graphics card instead to get around that part, but I want to keep my scanner.

---

### Post by mikewhatever on 2011-11-19
Such things usually happen when drivers are built against a specific kernel version. When the kernel is updates, you have to rebuild. In case of the ATI Radeon HD 4200, you can use the driver from the Ubuntu repositories. As for the printer driver, there is probably nothing you can do.

---

### Post by Mark Phelps on 2011-11-22
Whenever you do an upgrade that changes the kernel version, that "breaks" the restricted drivers.

If you installed them from source, or built .debs from source, you will have to reinstall them every time.

However, if you remove them, default to the open-source drivers, and then install them using Additional Drivers, that does so in such a way that driver updates are applied with kernel updates -- and you won't have to reinstall them again.

---

