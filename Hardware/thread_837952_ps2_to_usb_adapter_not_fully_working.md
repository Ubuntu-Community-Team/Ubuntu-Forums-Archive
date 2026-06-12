---
title: "ps/2 to usb adapter not fully working"
date: 2008-06-23
forum: Hardware
---

### Post by cha0s on 2008-06-23
Hey there, I have a ps/2 to usb adapter to plug my desktop mouse and keyboard in because I don't like coding on a laptop keyboard.

Anyways, it works fine if I reboot after I've plugged the adapter and peripherals in. If I use the laptop keyboard for a while, then plug the kayboard and mouse in (using the adapter) then only the mouse works; the keyboard won't until I reboot.

Is this a known issue? Anything I can do about it?

---

### Post by lisati on 2008-06-23
> **cha0s said:**
> Hey there, I have a ps/2 to usb adapter to plug my desktop mouse and keyboard in because I don't like coding on a laptop keyboard.

Anyways, it works fine if I reboot after I've plugged the adapter and peripherals in. If I use the laptop keyboard for a while, then plug the kayboard and mouse in (using the adapter) then only the mouse works; the keyboard won't until I reboot.

Is this a known issue? Anything I can do about it?

<EDIT>I just noticed the problem described wasn't exactly the same as what I experienced. What I had was that the usb mouse & usb keyboard would stop working after a while, and the following solved it<END OF EDIT>

I had a problem too for a while on my laptop using a USB keyboard and a USB mouse (mine's one of the  Toshiba Steallite A100 line running Feisty 7.04)

The solution I discovered (which I don't fully understand) meant doing the following:

1) From a terminal, type:
```
sudo gedit /boot/grub/menu.lst
```and enter your password. (Your password will remain invisible for security reasons)
2) scroll down the menu.lst file untile you find the line which reads > # defoptions=quiet splash3)Change it to read ```
# defoptions=quiet splash acpi=force irqpoll
```4)Save the file and exit the editor
5) at the terminal again, enter ```
sudo update-grub
```6)restart your computer

Hope this helps.

---

### Post by cha0s on 2008-06-25
Nah... that one didn't work unfortunately (just rebooted and tried it). I noticed the line you had me change has a # in front of it, does that mean it's a comment? If so, do you advise me removing the hash symbol from the beginning of the line? I don't wanna do that and screw anything up so a reply would be appreciated. Thanks!

---

