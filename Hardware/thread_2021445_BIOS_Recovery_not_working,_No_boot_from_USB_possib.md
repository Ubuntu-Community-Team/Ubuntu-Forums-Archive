---
title: "BIOS Recovery not working, No boot from USB possible on Aspire One 110"
date: 2012-07-09
forum: Hardware
---

### Post by schlichtblau on 2012-07-09
I tried to flash the BIOS, since my Acer AspireOne A110 does not show any boot activity on startup (no HD light, no screen). However, even with two different USB pendrives correctly formatted and many different BIOS versions (as explained in [http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html?commentPage=2#comments](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html?commentPage=2#comments) ), it doesnÄt work. Booting keeping Fn + Esc pressed doesn't result in any USB drive activity. All that happens is the power LED blinking.

Appreciating your suggestions!

schlichtblau

---

### Post by Redblade20XX on 2012-07-09
Can you tell us how the computer became unresponsive before your BIOS flash attempt? 

It seems as if something bricked the BIOS since you get no screen activity of hdd.

- Red

---

### Post by schlichtblau on 2012-07-09
it is a common issue that the aspire one's BIOS crashes once in a while. usually, the method described in the link resolves the problem easily (installing new BIOS via USB boot). 
however, today, when the problem appeared, i first tried installing a different ubuntu (ubuntu mini remix 11.10) from USB, which failed with a flashing caps lock crash. after this, neither the BIOS flash from USB, nor the ubuntu mini remix boot from USB did work anymore. i formatted the USB drive with FAT and FAT 32 and tried two different drives, nothing worked. the netbook didn't read the USB drive.

---

### Post by Redblade20XX on 2012-07-09
Do you get a manufacturer's screen when starting up the laptop or is it just plain blank? Ie. Do you get a BIOS screen?

- Red

---

### Post by wnelson on 2012-07-09
Make sure that your USB support in the BIOs is Legacy.

Walt

---

### Post by wobblyandflo on 2012-07-09
Hi all, first post for me and I might be able to help...

Press function and escape, at the same time press power button.
At this point the power button starts blinking. Press the power button
again...ONCE.
It should now access the files on the flash drive and reflash the bios.
After a while the power button stops flashing, and should reboot by
itself. Wait PATIENTLY.
If it doesn't reboot, go have a cup of tea/coffee, come back after a few
minutes and try again.

Fingers crossed for you.

Cheers, Richard.

---

### Post by ahallubuntu on 2012-07-09
A BIOS doesn't "crash."  The CMOS values could get corrupted (very unusual), and you can generally clear them by removing the CMOS battery, the main battery, and the AC power adapter and holding down the power button for say a minute or two.  Many desktop computer motherboards also have a "clear CMOS" jumper to do that more easily.

Motherboards can and do fail, and they can exhibit symptoms like the OP described: power light might come on but no display, no indication the computer is really "on" just "power on."  It has nothing to do with the BIOS.  It means a hardware failure.  If some component on the motherboard itself has failed, it's probably not worth fixing.

---

### Post by wobblyandflo on 2012-07-10
Bios problems are well known on the aspire one, I've had to reflash mine at least 3 times in the 2 years I've had it. Why does it happen? I don't know but it is common and curable. Keep trying and don't forget, walk away when you get frustrated.
Good luck.

Cheers, Richard.

---

### Post by schlichtblau on 2012-07-12
Richard, you are so right. I tried everything you said before, but nothing worked. However, after a few days (drinking lots of coffee in the meantime), suddenly the USB boot worked again, bios was flashed and everything is allright now.

thanks everyone!

EDIT: So everyone who runs into the same problem: your fortune cookie will be right; patience is the key to success ;) !

---

