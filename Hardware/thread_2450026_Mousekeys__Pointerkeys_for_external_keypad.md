---
title: "Mousekeys / Pointerkeys for external keypad"
date: 2020-09-06
forum: Hardware
---

### Post by lb111 on 2020-09-06
Hello, 

I use Lubuntu 20.04 and I have a got a bit stuck with enabling mousekeys / pointerkeys on an external keypad.

I have an external usb numeric keypad to the left of my main standard dell keyboard. 

```

Bus 005 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 003: ID 413c:2113 Dell Computer Corp. Dell KB216 Wired Keyboard

```

I like to use the main keyboard for numeric keypad number input, and the external usb keypad on the left as mousekeys / pointerkeys to mouseclick using "5" or "+"

I can get both keypads to work independently and both can be toggled independently from numbers to pointerkeys by running the following command *twice* : 

```
setxkbmap -device 003 -option keypad:pointerkeys 
``` ( please note using device 002 or 005:002 does not do anything )

I'm not sure why this works since 003 is the device number for the main keyboard only :)

However this setup times out and resets after just a few minutes so it isn't practical to keep using it during the session.

I have edited the contents of /etc/X11/xorg.conf.d/00-keyboard.conf  -- to try and make this a permanent change.

```

# Read and parsed by systemd-localed. It's probably wise not to edit this file
# manually too freely.
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "gb"
        Option "XkbModel" "pc105"
        Option "XkbOptions" "keypad:pointerkeys"
EndSection


Section "InputClass"
        Identifier "SmallKeypad"
        #MatchIsKeyboard "on"
        MatchUSBID "1c4f:0002"
        Option "XkbOptions" "keypad:pointerkeys"
EndSection

```

This works perfectly to enable mousekeys / pointerkeys on the standard keyboard upon loging in, but I cannot get mousekeys / pointerkeys to work on the external keypad at all. 

I have tried combinations of MatchIsKeyboard "on" or "off" also commenting it out with #, but it never works. 

Any advise would be greatly appreciated. 

Many Thanks :)

---

