---
title: "Asus ACPI Utility &quot;ATK&quot;, leds, tactile keys."
date: 2009-02-05
forum: Hardware
---

### Post by Shinkan on 2009-02-05
Hi everyone !

I just bought a laptop which uses an ASUS motherboard and its **ATK ACPI**.
I don't really know what it is, but as you have to setup Drivers in Windows called "ATKHotkey" and "ATK ACPI" to make some hotkeys working, I guess my problem is about that.

On the laptop keyboard, I have some **tactile hotkeys + a tactile sound volume scroll-bar**.
I just want theses fancy things to work, even if functions are also available with Fn keys (and are working).

I tried to load a module called "asus-laptop", and it says it detects my motherboard :

```
$dmesg | grep asus
[   13.880310] asus-laptop: Asus Laptop Support version 0.42
[   13.884881] asus-laptop: BSTS called, 0xfd7f returned
[   13.884958] asus-laptop:   H13VV model detected
[   13.902898] Registered led device: asus::touchpad
```

Now the sound-mute tactile hotkey seems to work, but the others don't.

I tried to play with "acpi_listen", and it's receiving things ... so everything is good ... except that playing with hotkeys doesn't change anything ... How could I map ACPI events to sound volume, Wireless LAN switching ... ??!

_Tactile volume scroll-bar :_
```
$ acpi_listen 
hotkey ATKD 000000b9 00000027
hotkey ATKD 000000b9 00000028
hotkey ATKD 000000b9 00000029
hotkey ATKD 000000b9 0000002a
hotkey ATKD 000000b9 0000002b
hotkey ATKD 000000b9 0000002c
hotkey ATKD 000000b9 0000002d
hotkey ATKD 000000b9 0000002e
hotkey ATKD 000000b9 0000002f
hotkey ATKD 000000b9 00000030
```
Each time I touch the tactile bar (to left side or to righ side), code seems to be incremented.

_Touchpad deactivation tactile hotkey :_
```
$ acpi_listen 
hotkey ATKD 0000006b 00000002
hotkey ATKD 0000006b 00000003
hotkey ATKD 0000006b 00000004
hotkey ATKD 0000006b 00000005
```
Same thing. It's a toggle hotkey, but each time I touch it, the code is incremented.

_Sound mute tactile hotkey :_
```
$ acpi_listen 
hotkey ATKD 00000032 00000000
hotkey ATKD 00000032 00000001
hotkey ATKD 00000032 00000002
hotkey ATKD 00000032 00000003
```
Same thing as above. But this key HAS AN EFFECT, it does make my GNOME pop a sound mute icon. But it doesn't really mute.

The same goes for _Wireless LAN kill switch_, and _Battery Save Mode hotkeys_.

Can you please give me some advices ... I really don't know how to proceed ...

---

