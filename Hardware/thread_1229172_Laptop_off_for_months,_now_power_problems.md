---
title: "Laptop off for months, now power problems"
date: 2009-08-01
forum: Hardware
---

### Post by madddonkey255 on 2009-08-01
A few months ago the hard drive on my laptop(HP 530) died.  Due to money problems and having a desktop I just set it aside until last week when I got around to replacing the hard drive.  I did the replacement myself and once it was finally replaced it seemed like there were problems with the battery, the charging light would blink sporadically and it had zero battery life.  I assumed the long rest killed the battery and just used it as a desktop.  Now it won't turn on at all, when I hit the power button the lights turn on and I can hear the fan and such spinning for a few seconds then it turns off automatically.  Was I right to assume this is a bad battery or is there something more seriously wrong, maybe I damaged something replacing the hard drive?
Thanks

---

### Post by aesis05401 on 2009-08-01
Hiya, 

First thing to try is opening the bottom panels of the laptop and locating the cmos battery (it should look like a digital watch battery - a little silver disc).  Try replacing that and seeing if it makes a difference.

---

### Post by lavinog on 2009-08-01
A cmos battery shouldn't die after a couple of months, and I don't think it would cause power up issues...just the wrong time.

Leaving the battery in a semi-charged, or discharged state for a long time will reduce the life of the battery drastically.

Try removing the battery and see if the laptop turns on.
It is possible that the power supply is bad also. My laptop charger had a bad cable caused by frequent storage. The charge indicator was sporatic as the connection went in and out. I was able to find the break and instead of buying a new $60 charger, I just stripped the shielding and zip tied some metal to it. It has been working great for over 4 months now.
I have a spare power supply now, because my sister broke the tip off of hers.

---

### Post by aesis05401 on 2009-08-01
> **lavinog said:**
> A cmos battery shouldn't die after a couple of months, and I don't think it would cause power up issues...just the wrong time. *snip* ...

I disagree.  POST=power on self test.  This cannot be accomplished without CMOS power.  CMOS dying slowly or not recharging fully = wrong time on reboot, CMOS dead = no POST, BIOS resets to defaults including boot orders and flags for types of hardware compat... so unless your BIOS defaults describe your boot order and hardware profile there will be no boot with a dead CMOS.

---

### Post by lavinog on 2009-08-01
> **aesis05401 said:**
> I disagree.  POST=power on self test.  This cannot be accomplished without CMOS power.  CMOS dying slowly or not recharging fully = wrong time on reboot, CMOS dead = no POST, BIOS resets to defaults including boot orders and flags for types of hardware compat... so unless your BIOS defaults describe your boot order and hardware profile there will be no boot with a dead CMOS.

I have booted computers with dead cmos batteries, the battery is only supposed to discharge when the power is off, otherwise cmos is powered by the powersupply.
A dead cmos battery would reset the bios to the defaults. This would be the same as using the reset jumper on many desktops. The default settings should be sufficient to boot a machine. Generally defaults only have issues when custom hardware is installed...not usually an issue with laptops.
Also cmos batteries don't recharge, they are usually a watch battery.

---

### Post by aesis05401 on 2009-08-02
I was wrong about the battery.  

As far as booting without CMOS, I must have tried this only on machines with special hardware, because I have never seen it work.  I believe it can be done, though, just saying :)  My experience was that you would only get beep codes and the power supply fan would run... nothing more without battery in.

Thanks for the info.

---

### Post by madddonkey255 on 2009-08-02
Looks like lavinog is the correct one, I've taken the battery out and it boots without problems, thank you for all the help.

---

### Post by tgalati4 on 2009-08-02
When batteries are flat for a long period of time, the chemistry changes inside the cells.  All it takes is for one cell (out of 6 or 9 cells in a battery pack) to short out and the battery won't hold a charge, nor will it take a charge properly.

The AC charger can only supply so many amps of current (typically ~3 amps).  Just enough to run the computer and charge a healthy battery.  If you have a shorted battery that is drawing all 3 amps, then there is no power left over to boot your computer.  I bet the battery felt warm after leaving it plugged in for a while.  That's the heat from the short.  Most chargers deliver 45-75 watts of power, so it will feel extra warm when shorted and moderately warm when normally charging (20-30 watts or 1/2 of the AC wall wart's total capacity.)

Pulling the bad battery allows all of the charger's current to go to the laptop so it can now boot normally.

---

### Post by lavinog on 2009-08-02
> **tgalati4 said:**
> When batteries are flat for a long period of time, the chemistry changes inside the cells.  All it takes is for one cell (out of 6 or 9 cells in a battery pack) to short out and the battery won't hold a charge, nor will it take a charge properly.


You don't even need a cell to short out entirely. If the voltage across a single cell drops significantly you can have a cell reversal and the other cells use up their energy trying to raise the voltage of the lowest cell.
Most if not all approved laptop batteries (lithium ion type) have an internal protection circuit that will disable the battery if cell voltage drops to low.
For the OP it sounds like the protection circuit didn't trip the battery, so it may be possible to recover the battery by leaving it on the charger for a while. Make sure it has adequate ventilation.
There is the possibility it wont charge again though, but take a look at the serial number and see if there might be a recall on it.

---

