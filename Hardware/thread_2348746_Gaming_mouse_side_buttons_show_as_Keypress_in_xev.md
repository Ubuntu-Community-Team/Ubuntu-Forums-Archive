---
title: "Gaming mouse side buttons show as Keypress in xev"
date: 2017-01-06
forum: Hardware
---

### Post by cheroka4 on 2017-01-06
I am banging my head on this one and would appreciate some help. Running Kubuntu 16.04.

Recently, I purchased a UtechSmart Venus gaming mouse ([this one]("http://www.utechsmart.com/product/show/id/477/US-D16400-GM")). For when I'm not gaming under Windows 10 I would like to map those nice 12 extra buttons on the side.
So I gathered some knowledge and went ahead to try and detect the ButtonPress via ```
xev
```, as instructed in [URL="http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse"]this askubutu thread.
[/URL]The idea would be to later on use ```
[xbindkeys]("http://www.nongnu.org/xbindkeys/xbindkeys.html")
``` to some mappings like volume up, volume down, pause/play, next track for Amarok (as a start).

The problem I am having is that those buttons seem to be confused with keyboard buttons 1...12. So when I fire up ```
xev | grep -A2 ButtonPress
``` those side buttons on the mouse 1...12 do not appear (but left- right click do, as the wheel).
Then, I tried to use ```
xev | grep -A2 KeyPress
``` instead, but the output I get from pressing the mouse's 1 and the keyboard's 1 is almost identical:

```

KeyPress event, serial 39, synthetic NO, window 0x1800001,
    root 0x1e7, subw 0x0, time 1393186, (-114,509), root:(850,538),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,
--
KeyPress event, serial 39, synthetic NO, window 0x1800001,
    root 0x1e7, subw 0x0, time 1394880, (-114,509), root:(850,538),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,

```
[B]
Is there a way around this issue, to have a unique ButtonPress for my mouse's side buttons?[/B]

---

