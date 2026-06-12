---
title: "No boot from CD"
date: 2010-07-23
forum: Hardware
---

### Post by mayagrafix on 2010-07-23
Laptop will not boot with Ubuntu Live CD. I switched the boot order in the setup, and also in the start up option screen. After a while of black screen, the windows boot sequence starts.

Do I need to use a diskette? or is there a live CD specifically for laptops?


Here are some stats:
Compaq Presario 2130 with mobile AMD Athlon XP2400+
Phoenix Tec bios KAM1.59
ATI chipset
Mobo: HP model 0024

Thanks for any help:KS

---

### Post by kh1116 on 2010-07-24
I also need help with this

---

### Post by garvinrick4 on 2010-07-24
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

Download to desktop:
Will be an .iso file:
BURN to a CD
Just make sure you are set to boot off of CD in BIOS or choose
to boot in option if have.
All CD's work in desktop or laptop.

Here is a link for installation and use guide.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

---

### Post by varunendra on 2010-07-24
> **mayagrafix said:**
> Laptop will not boot with Ubuntu Live CD. I switched the boot order in the setup, and also in the start up option screen. After a while of black screen, the windows boot sequence starts.

Do I need to use a diskette? or is there a live CD specifically for laptops?

As garvinrick4 said, all (bootable) live CDs work both in laptops & desktops. Yours seems to be a case of defective cd or a read error on laptop-optical drive's part.

Clean both the cd and the optical drive's lens and try again, or write a new cd at minimum possible speed if cleaning doesn't help.

If this doesn't work, try creating a live USB disk using [Unetbootin]("http://unetbootin.sourceforge.net/") and boot from it (your laptop should have option for booting from USB flash drive).

---

### Post by lisati on 2010-07-24
Don't burn the ISO file as a FILE, and don't extract the files. Use the "burn disk image" (or whatever it's called) option in your choice of software.

Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

