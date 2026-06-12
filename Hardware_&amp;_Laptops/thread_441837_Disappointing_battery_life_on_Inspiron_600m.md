---
title: "Disappointing battery life on Inspiron 600m"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by Cap'n Refsmmat on 2007-05-13
I just managed to install Ubuntu today and I've been disappointed by the way the battery on this laptop (Dell Inspiron 600m) has been behaving. On Windows, I can usually get 2.5hrs; now, it's been perhaps half an hour, and power manager says "46 minutes remaining."


I don't know if it's a real problem or if power manager is just confused. Is there something in the power configuration I can to do extend the battery life?

---

### Post by ccesare on 2007-05-13
This seems to be a fairly common problem. (I just Googled "ubuntu battery life" earlier today and found lots of recommended hacks to extend battery life.)

Like you, in Windows I was getting a much longer life for my battery (~4 hrs) and in Ubuntu I'm only getting maybe half as much.

I'd really like to know if anyone's gotten their battery life up.

Please help!

---

### Post by Cap'n Refsmmat on 2007-05-13
It looks to me like it's because of heat. The fan is now running continuously, even with the lid closed and the screen off. Nothing's eating the CPU... odd.

---

### Post by huygens on 2007-05-16
My battery is getting old (that's a bit less than 4 years I have my laptop). I could get before up to 4 hours, while now I'm stuck around 2h30 to 3 hours... I'm speaking under Windows. I only have Linux running on it since a year and a half. But today I can say that Ubuntu 7.04 saves almost as much power as Windows.
Under Windows, I get from 2h30 to 3h. With Ubuntu, I get 2h15 to 2h30.
I wanted to get a bit more, and I found out a way to increase slightly my battery by [allowing Ubuntu to dim the screen after a short period of inactivity]("http://www.berthon.eu/ice_and_fire/?p=84"). I did not use my laptop since that too often, but on one test I was a bit more than 2h15 using it and it shows 27 min. remaining charge. So it seems help a bit :-)

Note: I hace CPU throttling working fine, and I configured Gnome Power Manager to change the CPU throttling policy to be more energy saving when on battery (so it rises the CPU frequency much more slowly than on AC). Furthermore, as this is just a laptop and not a critical system, I have removed the "atime" facility on my file systems. The atime is the last time a file was accessed. When activated (the default) each time a process read a file, its atime is updated. So even when reading only, the hard disk is writing too. I have removed this feature, and I guess it helps a bit: multiple reads are faster (though as a user I do not see the difference) and consuming less power.

Note2: the [biggest consumer of energy in a laptop is the screen]("http://www.gentoo.org/doc/en/power-management-guide.xml"). So if the screen does not automatically dim (the brightness decrease) when you unplug the AC adaptor, then it will drain lots of energy.

---

### Post by Cap'n Refsmmat on 2007-05-17
I do not see where in GNOME Power Manager I have the option to adjust CPU throttling. Or anywhere, actually.

---

### Post by huygens on 2007-05-18
You are right because **Gnome Power Management (GPM)** does not offer yet this functionality (though, I'm sure to have seen it once in the past, perhaps on another distribution than Ubuntu or on another desktop environment than Gnome...)

Anyway, I was recently expending my wiki on power management matters and wanted to include information about [how to set CPU throttling policy (or governor) for GPM]("http://www.berthon.eu/wiki/foss:wikishelf:gpm:hacking").
This is now done :)


I hope you will understand this guide, feel free to give me feed back or ask for further help, clarification.

---

### Post by Cap'n Refsmmat on 2007-05-18
Ah, thanks, that's a nice guide.

I'll see if the battery lasts longer now under "conservative" mode...

---

### Post by Cap'n Refsmmat on 2007-05-19
Nope. It's an hour later and the battery is on "critical."

Hrm. Time to play with the settings a bit more...

---

