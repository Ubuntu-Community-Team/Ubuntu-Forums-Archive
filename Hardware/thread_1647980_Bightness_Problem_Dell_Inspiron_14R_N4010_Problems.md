---
title: "Bightness Problem Dell Inspiron 14R N4010 Problems"
date: 2010-12-18
forum: Hardware
---

### Post by luckysanj on 2010-12-18
[FONT=Times New Roman][SIZE=2]**Brightness Problem ****Dell Inspiron 14R N4010 Problems **[/SIZE][/FONT]             
                                                                [FONT=Times New Roman][SIZE=2]Hey Guys,
I freshly installed Ubuntu 10.4TL on my laptop Del Inspirion 14 N4010 but in my laptop there is Brightness controll problem.
I read all of forum posted matter for brightness but it didnt work.

Brightness up down keys moves the brightness slider around but doesn't change the actual brightness.
I am also not able to change the brightness using the power management tool.
This problem is draining my battery life crazy.[/SIZE][/FONT]

                      p { margin-bottom: 0.08in; }  [FONT=Times New Roman][SIZE=2]System Information[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Model: INSPIRON N4010[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Service Tag:97P3ZL1[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2]Express Service Code: 200-564-807-41[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]CPU: i3 processor [/FONT][/SIZE]


[SIZE=2]Help will be appreciated Thank You.
[/SIZE]

---

### Post by bcbc on 2011-07-06
It's a long time since you posted this... but I have the same laptop.

This ppa fixes the brightness controls, but only on 10.10 and 11.04: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

edit: I haven't tried 10.04 but on the dev release (oneiric) I've had to use the boot option: dell_laptop.backlight=0 (that doesn't allow adjustment but it seems to reduce the brightness sufficiently).

---

### Post by TheThakur on 2012-05-07
Hi,
    i am able to adjust the Brightness of the **Dell Inspiron 14R N4010**., but after the restarting of my Lapi Brightness setting again goes to 100% of its setting.

so again need to set the same.

so please help.....

Regards,
Shiv Rajawat

---

### Post by bcbc on 2012-05-07
On 12.04 it remembers my brightness setting - except in certain circumstances (new kernel, some updates).

Edit: sometimes it doesn't remember the setting even with no updates. So, basically, it's inconsistent. I haven't spent a lot of time trying to figure it out.

---

