---
title: "Refresh Rate Problem ATI HD 4670 - Build Xorg.conf How?"
date: 2010-09-13
forum: Hardware
---

### Post by 1antares1 on 2010-09-13
[CENTER][COLOR="DarkOrchid"]More than 1 month with this problem.[/COLOR]
:([/CENTER]

Hi community! Good night. My problem presented here, I hope you can help this problem:

Wish to change the screen refresh, and that before installing the drivers, were in **1440x900 75hz** and then install the proprietary, all good and perfect. But the only problem is that it runs at 75hz.

It gives me no choice, because only appears 60 hz. Is it a problem or a bug in Xorg ATI drivers?

It is a **ATI HD 4670** - [COLOR="DimGray"]_Drivers 10.8_[/COLOR].

**Sample images:**

-I go to Catalyst Control Center and find that information on the card, the maximum frequency is 75 Hz:

[IMG]http://i55.tinypic.com/9v9ow7.png[/IMG]

But in trying to change, both here and in "Monitors", leaving only 60 Hz, no more there.

**A sampling:**

[IMG]http://i53.tinypic.com/2im9rhj.png[/IMG]

Besides, my Xorg, I see very simple, as compared to others. (It is identical as this one).

**How I can generate an automatic Xorg ATI?**

**How to add frequencies to Xorg?**

This really is annoying me, I hope you can help me, I would be grateful in advance.

Thanks.

[COLOR="Red"][CENTER]Xorg.conf[/CENTER][/COLOR]

[HTML]Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection[/HTML]

---

### Post by 1antares1 on 2010-09-14
Would anybody be arranged to help or take advice? :neutral:

---

### Post by 1antares1 on 2010-09-14
**How I can generate an automatic Xorg ATI?**

**How to add frequencies to Xorg?**

---

### Post by 1antares1 on 2010-09-15
:oops:

---

### Post by dino99 on 2010-09-15
nowadays, kernel directly deal with X, so dont worry about frequency that dont matter, and your xorg.conf is ugly, let the system run as it might

sudo rm -f /etc/X11/xorg.conf

then reboot and install this ppa: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade, then check driver activation: system admin additional drivers

note: better to use ubuntu genuine packages than ATI ones which often breaks the system (not fine tuned for ubuntu config)

---

### Post by realzippy on 2010-09-15
[I]nowadays, kernel directly deal with X, so dont worry about frequency that dont matter, and your xorg.conf is ugly, let the system run as it might
sudo rm -f /etc/X11/xorg.conf
[/I]

Sure that he should remove xorg.conf????????
He is using fglrx.....so why is his xorg.conf ugly?

---

### Post by 1antares1 on 2010-09-16
Let's see. I can not understand very well.

**What I worry about the refresh rate?** But I want to upload it to 75hz, as I could on Windows (last time) and my monitor stand it.

Why I can not upload it here if it is compatible? Is there any way?

Why delete the xorg.conf? **Does not need FGLXR xorg.conf?**

And for serving this command? "_Sudo rm-f / etc/X11/xorg.conf_"

I welcome your responses and help me find the solution. Thanks.

---

### Post by realzippy on 2010-09-16
I do not know much about ATI fglrx driver.
If you run 
**man aticonfig**
you should see an option to add hsync and vsync to xorg.conf,resulting
to more valid modes.Maybe there is  a command for setting the refresh rate directly to a given resolution.
EDIT:
Do you know the exact name of the monitor?Or its hsync/vsync values?

---

### Post by 1antares1 on 2010-09-16
Thanks for responding.

My monitor is a 19-inch Hypson (something old), but it is LCD.

It is well known, and q I bought a TV shop. But that worked in the resolution **1440x900** at **75 hz**.

But now only reaches 60 hz. And the other resolutions if they change frequently.
[B]
How I can add frequencies to this resolution by the Xorg?[/B]

**Could you give me an example of Xorg?**

**Or is there some program the graphics that you can configure it without touching the Xorg?**

Thank you for your help.

---

### Post by Claus7 on 2010-09-16
Hello,

you can find millions of xorg.conf files in the net. 

Since refresh rate is your problem let us see if you can configure just this. Keep a backup copy of your xorg.conf file and reboot (just do not have xorg.conf in /etc/X11, you can have though xorg.conf_*whatever*...).

Now reboot. Are things progressing normally? If affirmative go to System-> Preferences-> Monitors and see if you are able to fix your refresh rate from there.

If not, then you have to test other things...

Regards!

---

### Post by coffeecat on 2010-09-16
> **1antares1 said:**
> It is well known, and q I bought a TV shop. But that worked in the resolution **1440x900** at **75 hz**.

But now only reaches 60 hz. And the other resolutions if they change frequently.


What's the problem with 60Hz? 60Hz is fine for LCD displays. Do you see any flickering? If not, why worry?

---

### Post by realzippy on 2010-09-17
I added hsync/vsync to your xorg.conf...
test if now  more refresh rates are available.

```
ection "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
        HorizSync       28.0 - 83.0
        VertRefresh     56.0 - 75.0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection
```

---

### Post by pyroclastic on 2010-11-07
i might be wrong but where u see 75 mhz its the max what ur monitor or TV can take. it might be at lower MHZ my monitor shows max rate 75 Mhz, but at 1920X1080 resolution i can get only 60Mhz

---

