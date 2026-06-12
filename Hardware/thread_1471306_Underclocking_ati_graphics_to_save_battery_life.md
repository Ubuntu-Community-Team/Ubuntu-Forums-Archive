---
title: "Underclocking ati graphics to save battery life"
date: 2010-05-03
forum: Hardware
---

### Post by Vladimir_BG on 2010-05-03
I have a dell laptop that uses x1300 graphics. If I don't underclock the graphics card, battery life drops from around 5 hours to under 3!

On [http://manpages.ubuntu.com/manpages/lucid/en/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/lucid/en/man4/radeon.4.html) there is a way to use low power state or dynamic clock.

To set that, I need to edit xorg.conf.

Xorg.conf does not exist in 10.04. I looked for it in /etc/X11 but it just isn't there.

When I used older versions of ubuntu with fglrx, there was a command that I could use in terminal to reduce the clock.

I believe it was fglrx -set-powerstate that showed 3 power states number from 1 to 3, and offered me to select one.

example: fglrx -set-powerstate=3

Is there a way to do this in 10.04 using radeon driver?

Important note:
I'm not Linux expert, so try to keep it simple please...

---

### Post by Yellow Pasque on 2010-05-03
There is basic support for open-source power management right now in 2.6.34 kernel, which you can get here if you want to experiment: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/) (you need the image and headers packages for your architecture and the headers-all package). A lot of improvment is expected in 2.6.35 kernel: [http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg)

You can create the xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
Here's a generic xorg.conf that I use (modify to your liking):
```
Section "Device"
	Identifier	"Configured Video"
	Driver		"radeon"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video"
EndSection
```


From radeon manual, you can try these options in the 'Device' section of xorg.conf
```
       Option "ClockGating" "boolean"
              Enable dynamic clock gating.  This  can  help  reduce  heat  and
              increase  battery  life  by  reducing  power  usage.  Some users
              report reduced 3D performance with this enabled.  The default is
              off.

       Option "ForceLowPowerMode" "boolean"
              Enable  a  static low power mode.  This can help reduce heat and
              increase battery life by reducing power usage at the expense  of
              performance. The default is off.

       Option "DynamicPM" "boolean"
              Enable  dynamic power mode switching.  This can help reduce heat
              and increase battery life by reducing power usage when the  sys&#8208;
              tem is idle (DPMS active). The default is off.
```

---

