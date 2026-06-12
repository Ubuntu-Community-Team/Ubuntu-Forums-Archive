---
title: "display shut off 11 minutes? really??"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by lcaley on 2007-10-19
Ok, I have gutsy running (amazing by the way...) and I'm usually a KDE user, but I'm going to try to gnome this time, unless I can't figure this out ;). Is there not a way to make the display shut off sooner than 11 minutes when on battery power? I take my laptop to classes and lots of places, and if my display stays on for 11 minutes idle, I'm almost positive my battery won't last much longer than an hour and a half. I know in KDE you can set it down to 1 minute. I've even tried ```
gconf-editor
``` and looked through the settings for gnome-power-manager. In the "timeout" section there is an option to make the display sleep after a certain number of seconds when on battery power. The problem is that it's already set to 60 seconds, so obviously it's not working right. If anyone has any ideas on how to do this, any help would be greatly appreciated.

Thanks! :guitar:

---

### Post by jrasmussen0 on 2007-10-19
It looks like 1 minute is the quickest gnome will set turning off your display but that is dependent on how long your screensaver is set for.

If you have gone to System --> Preferences --> Power Management and haven't gotten the screen to shut off then you should start looking at the tail /var/log/messages (or use Gnome's System Log under System --> Administration) log to see if there is any errors when gnome attempts to shut off the display.

---

### Post by flamacue on 2007-12-12
Seems to be a discrepancy between what the Power Manager Preferences displays and what the setting actually is.  The Power Manager Preferences is 10 minutes greater than the truth.

See screenshot below...

whereas "xset -q" shows the following:

```
flamacue@laptop:~$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/flamacue/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/home/flamacue/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
**[COLOR="Red"]DPMS (Energy Star):[/COLOR]**
  Standby: 0    Suspend: 0    [COLOR="Red"]**Off: 60**[/COLOR]
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log
```

Adjusting the slider bar and rerunning "xset -q" shows that there is a consistent 10 minute offset between them.

Is this a bug?  Should we file a bug report?  (If so, how?)

I am running Ubuntu 7.04 (Feisty) on a Dell Inspiron 700m.

---

