---
title: "manually(!) set display to sleep?"
date: 2009-03-08
forum: Hardware
---

### Post by m4lte on 2009-03-08
hey there!

**How can I set the display to sleep from the command line?**
I would like to create a launcher to set the display to sleep exactly when I want it, but I couldn't find anything in the forum or on google.
 thx <:

---

### Post by nwadams on 2009-03-08
there's some stuff in /etc/acpi ( i think) that allows you sleeps the display. Just play with them until you found the right one and make a launcher for it.

---

### Post by brianpeiris on 2009-03-20
Thanks nwadams. /etc/acpi/screenblank.sh does the job.

---

### Post by m4lte on 2009-03-20
> **brianpeiris said:**
> Thanks nwadams. /etc/acpi/screenblank.sh does the job.

oh, pretty cool. Thank you!

Now I have the problem that, when I return from display-sleep, the brightness is reduced. That happens whenever the display is set blank. E.g. when the computer wakes up from sleep or when I change the resolution. Anybody has an idea on that?

---

### Post by m4lte on 2009-12-20
I installed Ubuntu on a new system (Lenovo Thinkpad R400),
when I execute etc/acpi/screenblank.sh I get the following message:
No protocol specified
xset:  unable to open display ":0"

Any idea what that means and how I can set my screen to blank?

thanks!

---

### Post by jocko on 2009-12-20
To turn off the monitor, use any of these commands:
```
xset dpms force off
```
```
xset dpms force standby
```
```
xset dpms force suspend
```
In a multi-display setup (with separate x screens), you can control the individual monitors:
```
xset -display :0 dpms force off
```
Or:
```
xset -display :1 dpms force off
```

---

### Post by mikewhatever on 2009-12-20
> **m4lte said:**
> I installed Ubuntu on a new system (Lenovo Thinkpad R400),
when I execute etc/acpi/screenblank.sh I get the following message:
No protocol specified
xset:  unable to open display ":0"

Any idea what that means and how I can set my screen to blank?

thanks!

You are missing a slash in the bigining of the line:

**[SIZE="4"]/etc/acpi/screenblank.sh[/SIZE]**

---

### Post by colmeweb on 2010-08-02
Hi,
I am new to ubuntu and I am having some trouble with putting the monitor to sleep. I am running 10.04 on a Toshiba Satellite. I tried the keyboard shortcut using xset dpms force off/standby/etc. However the screen only goes off for a second and then it turns back on.

I found the /etc/acpi/screenblank.sh but modifying it is a bit beyond me at this time. 

Could anybody explain a little better please. 

Thanks.

---

