---
title: "Puma based HP tx2500z having trouble with thermal"
date: 2008-07-05
forum: Hardware
---

### Post by AstronomyDomine on 2008-07-05
I just got my tx2500z in the mail and I'm having some problems getting it running properly.  The main problem is that whenever I boot into a generic kernel I receive the error "ACPI Critical Trip Point" "Critical temperature reached (## C) Shutting Down"  Where ## is a number >65.  This is obviously an error, as nothing can instantly go from ~20 C to 65 C.

Booting with acpi=off fixes this problem, but it also creates a few more of its own.  With acpi=off the integrated wireless internet, bluetooth, and touchscreen all fail to work.

I tried compiling a vanilla kernel without thermal, and that seemed to fix most of the problems, however the touchscreen still doesn't work because linuxwacom only seems to want to work with kernels up to 2.6.24.  

So my only current idea is to find a way to boot the generic kernel without the thermal module.  Hopefully that will prevent ACPI from shutting down the computer.

I've tried adding thermal to /etc/modprobe.d/blacklist, but apparently because thermal is loaded in the initrd, this won't work.  I've also tried adding noload=thermal to the boot line, but this also didn't work.

Does anyone have any idea how to fix this?

Thank you.

---

### Post by vocalstud69 on 2008-07-05
It's funny, because I'm actually thinking of buying one of these, and I actually ran the liveCD on one at OfficeDepot, and it started fine.  It seems impossible for your hard drive to have that big of a temp difference that quickly, from what I know about physics in general.  It would be like taking a plate of chicken from the freezer where it had been for three days and then putting it into the oven on 500 degrees (Would never recommend doing that.  Plate goes boom.)

On the subject of the acpi, have you tried appending the following options?

```
noapic nolapic
```

I had to do that with this Averatec laptop I had.  I couldn't even start the thing with a liveCD.  I did get that laptop to work completely by putting in:

```
noapic nolapic vga=771 acpi=off
```

You can find out the resolution by getting rid of; 

```
ro quiet splash
```

from the boot parameters at GRUB, and just read the resulting lines that appear at startup.  They won't be permanent until you change the menu.lst kernel options.

That worked for me and I could install with the alternate install CD.  From reading it, it seems that you got it installed alright, and I didn't have a problem running the liveCD in OfficeDepot (boy was that fun leaving that there), so maybe trying the noapic nolapic thing might work.

I'm only worried about the touchscreen issue with evtouch.  Did you get that to work, as well as compiz-fusion?

Another option is compiling a system with Gentoo, but that is very, very hard, and not something I would want to do, mainly because it took me two months to figure out completely, to the point where I could get a working system.  Gentoo is complicated and time consuming, setting up USE flags and dealing with Dependecies, which is why I use xubuntu right now.  It was a good learning experience, though.  I had to have my friend talk me through it, but with Gentoo, you can compile your own specific kernel with the modules you want, so you could leave out the acpi modules if you really wanted to; and I know they have evtouch in portage (they're version of APT).  

Let me know if everything works.  I'll be buying it about the end of next month, probably.  Thanks.

---

### Post by AstronomyDomine on 2008-07-05
My biggest problem right now is that I can't boot to a generic without acpi=off.  With acpi=off the wireless, bluetooth, and touchscreen don't work. Booting into a custom kernel without acpi=off bluetooth and wireless work, but the I can't compile the touchscreen driver.  I can compile them in the generic kernel, but the touchscreen still doesn't seem to work.

Did the touchscreen work when you ran the livecd?  Did you have to use any boot options?  I couldn't even run the alternate install CD without acpi=off.

---

### Post by isachan on 2008-07-09
How do you get the sound to work ?
I have installed Kubuntu 8.04 in HD and must boot with acpi=off.
So I don't have any sound.

I have similar thread here :
[http://ubuntuforums.org/showthread.php?p=5335161](http://ubuntuforums.org/showthread.php?p=5335161)

Isao

---

