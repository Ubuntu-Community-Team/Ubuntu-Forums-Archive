---
title: "Screen brightness"
date: 2011-04-08
forum: Hardware
---

### Post by bmoreno on 2011-04-08
when my computer boots up i have to click my brightness up button on my laptop in order to see the screen. Is there any way to make it that my computer boots up with some brightness?


some computer specs: Hp Envy 14, 50 gb ocz vertex2 ssd, intel i5 580m, 4 gigs ram, ATI Mobility Radeon HD 5650 graphics card.

---

### Post by guakeke on 2011-04-09
Hi bmoreno,

You can have your screen light up when the login window appears by adding the following line to your rc.local file:

```
echo 3 > /sys/class/backlight/acpi_video0/brightness
```

The 3 represents 30% brightness. The command to edit rc.local is: 

```
gksu gedit /etc/rc.local
```

However, you still have to wait for the login screen till this kicks in, I still find myself pressing the brightness key. 

Credit to mpdava for this tip. He gives a lot more advice on the Envy 14 in [this thread]("http://ubuntuforums.org/showthread.php?p=10235323").

---

