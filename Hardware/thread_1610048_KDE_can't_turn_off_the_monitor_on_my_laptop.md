---
title: "KDE can't turn off the monitor on my laptop"
date: 2010-10-31
forum: Hardware
---

### Post by kedare on 2010-10-31
Hello,
I have a little problem, I migrated from Ubuntu to Kubuntu some days ago.

Everything works fine except one thing, KDE can't turn off the monitor when I close the lid, I selected the option to do it in power management but nothing..
When I close the lid, the monitor turn off for 2 seconds and is turned on again, then when I open the lid, it turn off for 1 second and turn on again :(

I don't know what can I do to fix this ? Everything worked fine with Gnome...

Here is a sample log of what happens when I close an open the lid :
```
==> /var/log/auth.log <==
Oct 31 12:12:03 mathieu-laptop su[5399]: Successful su for kedare by root
Oct 31 12:12:03 mathieu-laptop su[5399]: + ??? root:kedare
Oct 31 12:12:03 mathieu-laptop su[5399]: pam_unix(su:session): session opened for user kedare by (uid=0)

==> /var/log/Xorg.0.log <==
[  5489.400] (II) intel(0): EDID vendor "SEC", prod id 20293
[  5489.400] (II) intel(0): Printing DDC gathered Modelines:
[  5489.400] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1416  800 801 804 816 -hsync -vsync (48.9 kHz)

==> /var/log/syslog <==
Oct 31 12:12:04 mathieu-laptop kernel: [ 5489.400183] Skipping EDID probe due to cached edid

==> /var/log/kern.log <==
Oct 31 12:12:04 mathieu-laptop kernel: [ 5489.400183] Skipping EDID probe due to cached edid

==> /var/log/messages <==
Oct 31 12:12:04 mathieu-laptop kernel: [ 5489.400183] Skipping EDID probe due to cached edid

==> /var/log/auth.log <==
Oct 31 12:12:04 mathieu-laptop su[5399]: pam_unix(su:session): session closed for user kedare

==> /var/log/Xorg.0.log <==
[  5489.856] (II) PM Event received: Capability Changed
[  5489.856] I830PMEvent: Capability change

==> /var/log/kdm.log <==
I830PMEvent: Capability change

==> /var/log/Xorg.0.log <==

==> /var/log/auth.log <==
Oct 31 12:12:10 mathieu-laptop su[5455]: Successful su for kedare by root
Oct 31 12:12:10 mathieu-laptop su[5455]: + ??? root:kedare
Oct 31 12:12:10 mathieu-laptop su[5455]: pam_unix(su:session): session opened for user kedare by (uid=0)
Oct 31 12:12:10 mathieu-laptop su[5455]: pam_unix(su:session): session closed for user kedare

==> /var/log/Xorg.0.log <==
[  5495.259] (II) PM Event received: Capability Changed
[  5495.259] I830PMEvent: Capability change

==> /var/log/kdm.log <==
I830PMEvent: Capability change

==> /var/log/Xorg.0.log <==
```

Here is the result of "xset q":
```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  250    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  100/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 3600
  DPMS is Enabled
  Monitor is On


```


Using "xset dpms force off" turn the monitor off correctly so I think it's KDE-related

My laptop is a HP 6730s (Core 2 Duo model)

Thank you

---

### Post by Zorael on 2010-11-02
Is this on 10.10?

If you open up **xev** and let it run while you open and close the lid, does it register any phantom keypresses?

---

