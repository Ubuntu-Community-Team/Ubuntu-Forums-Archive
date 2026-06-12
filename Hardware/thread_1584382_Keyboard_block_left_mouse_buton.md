---
title: "Keyboard block left mouse buton"
date: 2010-09-29
forum: Hardware
---

### Post by bitpt on 2010-09-29
my old keyboard broke and a quick replace  i only have option to buy a Microsoft Digital Media 3000 keyboard, is not bad, il tried using it.

work ok until press special keys, then left mouse buton is pressed.Until reboot or CTR+ALT+BACKSPACE.

I try diferent keyboards, keytouch new config, X11 conf changes nothing seems work.

Try diferent keyboards work well, logitech, and old usb kbd no problems.

Anyone can help me with this issue ?

Thanks in advance.

Ubuntu 10.10, same problem in 10.04

---

### Post by P4man on 2010-09-29
Hmm.. odd.  You can try install keytouch to define the multimedia keys:
[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

But frankly, without that I would expect the keys at worst to do nothing. Are you sure the keyboard is not defective? Did you try on a windows machine?

---

### Post by bitpt on 2010-10-01
Keyboard is ok i replace it in store they give me new one (first i think some hardware problem even work ok in windows os).

Keytouch assume key when i touch in it and block left mouse buton after.

CTR+ALT+BACKSPACE or reboot is the only solution to gain control again.

i use synergy and, for a moment, i think problem can be synergy, but it isn't, turn off synergy and same problem.

This model isn't in list for keytouch, however, i turn off all special keys, try diferent models for diferent manufacturers, same problem.
Work ok until one special key is pressed, even turned off, i can't put it in keytouch, after press special key, kbd block left mouse button.

Change mouse, usb mouse, same ... today i'll test old mouse with PS2 (if i find one in scrapt) i'll reply  

Someone have Bill Gates phone number ? maybe he know what kind of keyboard is this :popcorn:

---

### Post by P4man on 2010-10-01
you could also try opening a terminal and run

```
xev
```

Position your mouse pointer in the white area and then look in the terminal what events are generated when you press the keyboard buttons.

---

### Post by bitpt on 2010-10-01
Thanks for your reply P4man.
using old ps mouse.. same 

running XEV, when key is pressed, same... block 
( i don't understand information in window, i got a error, all special keys give a address, even with mouse already blocked, tomorow i put error here)

after this, i run terminal CTR+ALT+F1, this keys do nothing, all others work fine even, prtscn etc etc.

with a search i try dmesg , i get a thousand of symlinks.....

i'm tired, let me see if tomorow i understand whats up, let me see if i can do something with  setkeycodes or whatever wich can solve this.

sorry my bad english.

---

### Post by bitaljus on 2010-10-01
I have almost the same problem. My keyboard is Genius brand and my mouse is A4Tech XL-755-K. I have not had problems with Ubuntu 10.04, but in Ubuntu 10.10 when I press the Backspace or special mouse buttons, left mouse button freezes and does not record more clicks.

---

### Post by P4man on 2010-10-02
can you post the output of dmesg? 
As a wild guess, you could try booting with no noapic and/or nolapic kernel options. I think this is a kernel issue with the motherboard, not just a keyboard driver issue. More info here on boot options here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by bitaljus on 2010-10-02
I tried noapic and/or nolapic kernel options but the same freezes. Here in noproblem.txt is the dmesg output from the stable Linux Mint 9 Main and in problem.txt is the output from Kubuntu 10.10 RC.

---

### Post by bitpt on 2010-10-03
the problem is in 10.10 only, fresh install 10.04, keyboard work well.

Change keyboard to microsoft digital media in keytouch, delete key freeze mouse too, a change to logitech, only specials keys block mouse (even disable in keytouch)

dmesg log

---

### Post by KatsumeBlisk on 2010-10-13
Has this been solved? I have the exact same problem in Ubuntu 10.10 only. I have the Microsoft Digital Media 3000 keyboard as well. At the moment, I'm avoiding the keys, but I'd really like to get them operational again in Ubuntu.

---

### Post by IcarusR on 2010-10-13
It would appear that you are affected by this bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311")

Read through it all there are several fixes.

---

