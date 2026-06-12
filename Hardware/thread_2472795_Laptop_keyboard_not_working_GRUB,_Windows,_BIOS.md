---
title: "Laptop keyboard not working GRUB, Windows, BIOS"
date: 2022-03-12
forum: Hardware
---

### Post by claven123 on 2022-03-12
[FONT=arial narrow][SIZE=2]I have dual boot laptop with Ubuntu 20.04 LTS and Windows.  I don't remember what happened before this ie an simple routine update or nothing.  I did not do a major upgrade. The keyboard does not work in bios, grub or ubuntu or windows.  I can use the track pad, external keyboard and mouse.  I have run to run this: sudo apt-get install xserver-xorg-input-all. I tried [COLOR=#3a3a3a]Insert “/bin/bash” before $vt_handoff and press Ctrl + X or F10 to reboot. Once you in the command, run the following command and reboot back the system again.[/COLOR]

[COLOR=#3a3a3a]None of these seemed to help.  I'm assuming my keyboard may physically be broken/disconnected. 

Is there a way to check to see IF a keyboard is connected?  I did order a replacement keyboard, it was pretty cheap, so I will take it apart and check the connection then, since it's a pain to get at.

Dennis[/COLOR][/SIZE][/FONT]

---

### Post by #&amp;thj^% on 2022-03-12
> **claven123 said:**
> 
Is there a way to check to see IF a keyboard is connected?  I did order a replacement keyboard, it was pretty cheap, so I will take it apart and check the connection then, since it's a pain to get at.

```
 hwinfo --short
```
I have 2 connected ATM
```
keyboard:
  /dev/input/event7    Integrated Technology Express ITE Device(8910)
                       Logitech Unifying Receiver
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
                       Logitech Unifying Receiver
  /dev/input/mice      MSFT0001:00 04F3:3140 Mouse
  /dev/input/mice      MSFT0001:00 04F3:3140 Touchpad

```

---

### Post by claven123 on 2022-03-12
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard

---

### Post by #&amp;thj^% on 2022-03-12
> **claven123 said:**
> keyboard:
/dev/input/event3    
AT Translated Set 2 keyboard
If that's all that shows, then there is an hardware issue somewhere.

---

### Post by claven123 on 2022-03-12
I didn’t copy n paste all the output only the keyboard part.

Dennis

---

