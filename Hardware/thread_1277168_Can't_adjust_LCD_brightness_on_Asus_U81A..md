---
title: "Can't adjust LCD brightness on Asus U81A."
date: 2009-09-28
forum: Hardware
---

### Post by CloverChan on 2009-09-28
hello,
I can't adjust the backlight on my new Asus U81A laptop. I'm using Ubuntu 9.04. when I try lowering the brightness with the keyboard, I get the panel display bar, but that's it. right now the display is stuck at 100% brightness. any advise?

---

### Post by CloverChan on 2009-09-28
Bump. Any help would be much appreciated.

---

### Post by CloverChan on 2009-09-28
Bump. still remaining hopeful...

---

### Post by xonecas on 2009-10-01
bump, Any solutions ?

---

### Post by amaru01 on 2009-10-28
Hi,
try pressing the blue fn key at the lower left hand of the keyboard at the same time that you press the F5 ot F6 keys.  The F5 and F6 keys are marked with little blue icons that clearly indicate more or less bightness on the screen.
Good luck

---

### Post by schmickey on 2009-10-31
> **amaru01 said:**
> Hi,
try pressing the blue fn key at the lower left hand of the keyboard at the same time that you press the F5 ot F6 keys.  The F5 and F6 keys are marked with little blue icons that clearly indicate more or less bightness on the screen.
Good luck

That doesn't work.  That's why he posted, the brightness controls are not working on this model. Another post suggested enabling the backports repository.  I have the same model and the same problem.  Brightness stays at 100% and there is no way to adjust it. And I'm using 9.10 Final (Karmic) x86.  I'm going to try the AMD64 version next since it has been reported that it solves some of the problems.  I'm really disappointed in Asus for not supporting Linux on this model.

I hope some developer can fix this and put the patch into the updates.

Asus U81A-RX05
4GB / 320GB / T6500 Core2 Duo / Intel 4500MHD Graphics

---

### Post by salacious_crumb on 2009-10-31
I'm having the same issue with my LCD backlight on an Asus M70SA with the x86_64 version of 9.10. 

Anybody find a fix yet?

---

### Post by schmickey on 2009-11-01
Bump.  Anyone find a fix for this?  Please, I don't want to go back to Windows.

---

### Post by bstine on 2009-11-02
Using Gentoo on a U81A-RX05 (BestBuy), but this should apply to Karmic as well.

After updating to U80A bios 210 (available on the Asus support site), I now have backlight control working with no extra steps needed on the OS side.

Note that the U80A bios should be identical to the U81A bios as the hardware is largely the same (with some removals from the U81A due to BestBuy customization). Therefore it is safe to use U80A bios versions with the U81A. In fact, in this case it is necessary as the Asus U81A downloads site has not yet been updated.

The Asus U80A download page is at [http://support.asus.com/download/download.aspx?model=U80A(BestBuy)&os=30&SLanguage=en-us]("http://support.asus.com/download/download.aspx?model=U80A(BestBuy)&os=30&SLanguage=en-us").

Hope this helps you.

---

### Post by roboteed on 2009-11-10
Thanks for pointing me to the BIOS update!  I can confirm that updating the BIOS on an ASUS U81 to the BIOS for the U80A, version 210, fixes the screen brightness issues with this laptop in Ubuntu.

---

### Post by castete on 2010-03-21
Han encontrado la solución para el brillo en este laptop para Ubuntu, si alguien lo ha encontrado que de la SOLUCION :)

Saludos.-

---

### Post by wickstopher on 2010-10-13
Well, I stumbled upon this thread a bit late, but I can confirm that it did NOT fix my screen brightness issues with my U80A.  I updated to BIOS 211, the most recent version available for the U80A (not the Best Buy version on the link provided, as I didn't buy mine from Best Buy).

---

