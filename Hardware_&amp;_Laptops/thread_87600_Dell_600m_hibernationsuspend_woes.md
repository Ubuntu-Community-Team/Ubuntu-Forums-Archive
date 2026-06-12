---
title: "Dell 600m hibernation/suspend woes"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by SethD on 2005-11-08
Dear Forum,

I have recently switched to Ubuntu from Gentoo and find that I like it very much. I've got everything working that used to work in Gentoo except for hibernate/suspend. I was using suspend2 in Gentoo, but was attracted to Ubuntu's claim of laptop support out of the box.

My question is this: Does anyone have Ubuntu suspend/resume working on a Dell 600m without having to reinstall their own patched sources with suspend2? Is suspend2 the only way to get the 600m to resume under linux?

Thank you kindly.
Seth

---

### Post by sciurus on 2005-11-09
Standy and hibernate both work for me in Kubuntu on an Inspiron 600m. Suspend does not. System performance profiles and cpu scaling also seem to be working (ie they don't cause any errors), but I don't know how to test their effects.

My main issue is that standby does not turn off the display. Instead, it displays ACPI messages. Normally when I close the laptop, the display turns off (I can tell by pushing the lid switch with my finger). However, if I set the lid switch closing to activate standby, it goes into standby, but the display stays on. I'd like to find a way for the laptop to go into standby **and** turn off the display when it is closed. Any ideas? Hibernate is not an option, because it takes minutes instead of seconds to resume (nearly as long as a full boot).

Alternately, which do you think is better for the life of the laptop?
1) Having it in standby, but with the display still on?
2) Having the display off, but the system performance profile set to something else (conservative? powersave?) and/or the cpu scaled down as much as possible>  (87%)?

I haven't been able to find documentation on the system performance profiles. I can't find them in the system setting Handook, and googling returns KDE's CVS.

---

### Post by SethD on 2005-11-09
sciurus,

Thanks for the reply. How are you accessing standby and hibernate on your 600m? What version of the BIOS are you running? I'm on A17 which may have some problems.

Regarding your backlight issue... the command "xset dpms force off" works fine for me to turn off the backlight. If things are stubborn on your computer, there's a hack called radeontool that's available: [http://packages.ubuntu.com/breezy/utils/radeontool](http://packages.ubuntu.com/breezy/utils/radeontool)

Thanks for the reply, Seth

---

### Post by sciurus on 2005-11-14
The BIOS is version A02. I'm using KDE Control Center's laptop applet to access the power features. Thanks for the backlight tip.

---

### Post by ispiked on 2005-11-15
Seth, try this: 

(from [https://wiki.ubuntu.com/HoaryPM](https://wiki.ubuntu.com/HoaryPM))

"To enable suspend to disk on Hoary, edit /boot/grub/menu.lst and go to the line starting #kopt. Add resume=/dev/hda2, replacing hda2 with the name of your swap partition. For reference, mine looks like this:

# kopt root=/dev/hda1 resume=/dev/hda2 ro

Now run sudo update-grub and reboot."

---

### Post by adamonduty on 2006-01-16
I was also having problems getting my 600m to hibernate (sleep works fine if you enable it). I finally solved the problem by adding nolapic and noapic to the grub line. So mine looks like this:

# kopt=root=/dev/hda5 resume=/dev/hda6 ro nolapic noapic

Did a sudo update-grub, rebooted and it worked! I of course get all kinds of funny colors and weird messages but it seems to work. I read somewhere (I think it was on a ubuntu development webpage) that you need those options with Dell's A17 BIOS.

---

### Post by SethD on 2006-04-07
Excellent! Thanks so much. Working great in Dapper Flight 6 w/o the extra apic options.

---

