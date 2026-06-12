---
title: "password reset  jumper"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by benner on 2006-09-27
I just inherited 7 HP e-vectra mini desktops for my classroom.  they all have a password setup to get into the BIOS.  i tried taking the batteries out (for 20 minutes) but it didn't work.  does anyone know ho i can figure out which jumper to pull to reset the passwords?

---

### Post by em3raldxiii on 2006-09-27
You are looking for the CMOS jumper, and it is usually located relatively close to the battery on a motherboard.  All you have to do (usually) is remove the jumper and place it on the "other" pins (there are 3 pins, and if 1-2 are connected with the jumper, change it to 2-3).  If your board only has 2 pins (wierd), then just pulling it should work.

Most motherboards will have the word CMOS printed very near what you are looking for.  Alternatively, some boards will have a legend printed on it, and will indicate a number for the jumpers.  For example, your CMOS jumper could be labelled something like jp-1 or something similar.

After the jumper has been moved for a minute or five, then switch it back to the original position before booting.  In some cases, you may have to try to boot while the jumper is in the reset position.  This may be specific to your board.  Try *without* booting while resetting first, and only boot it when the jumper is back in the correct position.  If that fails, then try booting with it in the reset position.

---

