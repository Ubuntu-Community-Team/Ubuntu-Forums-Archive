---
title: "Screen occasionally blackens"
date: 2015-07-30
forum: Hardware
---

### Post by plkoij on 2015-07-30
I have a Lenovo G50 running Ubuntu 15.04 (I've udpated 14.04 -> 14.10 -> 15.04) and had this problem in all 3). Sometimes, the screen will go black for a few seconds. I think moving the mouse may help, but I'm not sure. 

Would it be worth trying a fresh install? Are there packages or drivers I should try installing?

---

### Post by Simon_Tomoko on 2015-07-30
Check your DPMS and quite possibly the screen saver. Drop to terminal and run; xset -q

The last few lines should read something like: 
DPMS (Energy Star):Standby: 600    Suspend: 600    Off: 600
DPMS is Disabled

If power manager is enabled you can toss out; **xset -dpms ** I have this in my start up login so it never powers down.

---

### Post by plkoij on 2015-08-01
Thanks, but I'm still having the problem. I've tried xset -dpms, xset s noblank, and xset s off. The output of xset q is now

```
Keyboard Control:  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x22    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled

```

I feel like it might not be a screensaver issue though, because it doesn't only happen when the computer's been idle; the screen will blacken even if I'm in the middle of doing something.

---

### Post by NoWayWin8 on 2015-08-02
Go to System Settings > Brightness and Lock and change the value for "Turn Screen Off When Inactive for" X minutes. Set it to a longer amount of time or "Never" if you want.

You can also uncheck the "dim screen to save power" box.

---

