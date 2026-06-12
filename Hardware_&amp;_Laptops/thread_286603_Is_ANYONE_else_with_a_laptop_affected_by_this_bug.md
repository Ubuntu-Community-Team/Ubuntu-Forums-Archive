---
title: "Is ANYONE else with a laptop affected by this bug?"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by black hole sun on 2006-10-28
I can't be the only one...

[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025)

Basically what happens is this:

[http://librarian.launchpad.net/4903113/Screenshot-1.png](http://librarian.launchpad.net/4903113/Screenshot-1.png)


Notice the percentage left on my battery as reported by acpi, and then as reported by gnome-power-manager. Anybody?!

---

### Post by magicfab on 2006-10-28
What laptops is this ? I would suggest goign to the brand's forums for Linux if there are any and also inviting as much people to confirm the bug.

---

### Post by DarkN00b on 2006-10-28
Nope.  My HP ze2000 updates in 1% increments.

---

### Post by compuguy1088 on 2006-10-30
> **black hole sun said:**
> I can't be the only one...

[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025)

Basically what happens is this:

[http://librarian.launchpad.net/4903113/Screenshot-1.png](http://librarian.launchpad.net/4903113/Screenshot-1.png)


Notice the percentage left on my battery as reported by acpi, and then as reported by gnome-power-manager. Anybody?!
Actually I'm having the same problem when the AC is unplugged, though when the AC is plugged in, the battery meter in G-P-M shows the correct value, though all the time the command acpi, is accurate....The laptop I'm using is a Acer Aspire 3003LCi

---

### Post by Drife on 2006-10-31
Just confirming I have the exact same problem. acpi shows correct status
but g-p-m is totally screwed.
I have an Acer 5672WMLi.

/Drife

---

### Post by Tiede on 2006-11-08
ditto here.
This issue causes my laptop to continuously hibernate when switched to battery mode. Quite frustrating

---

### Post by kleenpwr on 2006-11-19
I also see this problem with an Acer 5002WLMI. When battery is fully charged, and the power is unplugged, immediate notifications are given of 3-8 minutes of battery life. Goes to shutdown mode within 2-3 minutes after notification. Worked fine in Dapper. However bug is inconsistent, does not happen consistently after reboot. Also see same issue with slow updates of battery capacity in applet.

---

### Post by Vaz on 2006-11-24
Same laptop as above (5002), pretty much the same problem.
Jumps from 100% to 66% with nothing in between.

---

### Post by sitedesign on 2006-11-30
Acer 5003WLMI same problem, battery keeps saying critical or 10 minutes left at 80% even though in dapper it lasted for about 4 hours. Sometimes tells me only 2 minutes at 90% etc.
Had to switch off the shutdown at critical battery to keep it going.

There is a patch for HAL which is supposed to fix it we just need it to follow through to Ubuntu updates.

---

### Post by Slasher Fun on 2006-12-24
Same problem with an Aspire 1692 and Edgy, there are 4 battery states while discharging : 100%, 66%, 33% and 0%, and 7 while charging : 0%, 16%, 33%, 50%, 66%, 83%, 100%

This *didn't* fix anything : [http://ubuntuforums.org/showpost.php?p=604504&postcount=72](http://ubuntuforums.org/showpost.php?p=604504&postcount=72)

---

### Post by GoHabsGo on 2007-01-06
I can confirm the bug, I have an HP tc 4400 tablet PC, and the battery status is missing. I'm using Edgy.

---

### Post by Tiede on 2007-01-08
Battery status insight.

I think I know why the battery information is wrong on acer laptops. The battery info is being written in /proc/acpi/battery/BAT1/, while some programs are polling for battery info in /proc/acpi/battery/BAT0/ (I found that reading the output of conky while running in terminal mode). I immediately thought of making a symbolic link to BAT1 from BAT0, but no matter which way I try, the kernel won't let me write to that location. Verily, when I change the polling location in conky from BAT0 to BAT1, my battery info is readily available.
Can anybody else confirm this and/or has an idea (whether it stems or not from this insight)?
acpi -V read the info from BAT1, therefore, it's info is good. I'm thinking gnome-power-monitor is looking for /proc/acpi/battery/BAT0, just like conky is,  and could not find it...

---

### Post by nrKist on 2007-01-11
I've got this bug on a Toshiba Satellite L25-S1194. Acpi -V also reads from battery 1 on my laptop.

---

### Post by kullan&#305;c&#305; on 2007-01-11
Nope. My HP ze2000 updates in 1% increments.
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by Tiede on 2007-01-13
little update:  I just installed E17 on my machine, and enlightenment's battery monitor seems to be working properly...
BTW, I read in the launchpad bug I filed on this issue that it is fixed in Feisty. I wonder why they did not bother fixing edgy too...

---

