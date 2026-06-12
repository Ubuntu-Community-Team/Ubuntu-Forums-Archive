---
title: "Brightness laptop (associate to keyboard shortcut)"
date: 2010-09-17
forum: Hardware
---

### Post by Saiot on 2010-09-17
hello,
i have got a acer 5732z and i cant change the brightness nor from keyboard shortcur nor from the gnome applet, the only way to do it is 
sudo setpci -s 00:02.0 F4.B=00
sudo setpci -s 00:02.0 F4.B=FF

where values from FF to 00 change from complete darkness to sunshine... (rain and snow not avaible for now...;) )

now what i want to do is to associate in some ways a script that changes the brigthness to the keyboard shortcut Fn+rightArrow and Fn+leftArrow,
the Xev output is

rArrow:
MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 38, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

lArrow:
FocusOut event, serial 40, synthetic NO, window 0x4c00001,
    mode NotifyNormal, detail NotifyNonlinear

MappingNotify event, serial 40, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248


what can i do??

thankyou in advance and sorry 4 my BAD english!!

---

