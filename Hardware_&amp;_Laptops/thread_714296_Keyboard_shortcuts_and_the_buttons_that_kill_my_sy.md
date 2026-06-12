---
title: "Keyboard shortcuts and the buttons that kill my sytem"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by Aiello on 2008-03-03
I have a few questions regarding keyboard short cuts:
1. When I press the button I wish to use for launching the web browser, (it is a dedicated web browser button), in the Keyboard Shortcuts menu, it doesn't seem to register it. How can I get it to work?
2. I also have a dedicated open/close disc tray button on my keyboard. Just like the web browser button, it also doesn't seem to register it. Same question.
3. When I press Ctrl Alt F9, it kills my system. I mean, it takes my to a black screen and the only way to get out of it is to press Ctrl Alt Delete, which then restarts the computer.

Any suggestion on how to enable the keys to start the web browser and open the disk tray and disable the button combo (Ctrl Alt F9) that kills my computer?

-Thanks!

---

### Post by diaa on 2008-03-03
> **Aiello said:**
> 
3. When I press Ctrl Alt F9, it kills my system. I mean, it takes my to a black screen and the only way to get out of it is to press Ctrl Alt Delete, which then restarts the computer.


Ctrl Alt F9 doesn't kill your system it just takes you to a different place(known as virtual terminal), to go back to your graphical tty(which is the 7th) press Ctrl Alt F7.

---

### Post by Whiffle on 2008-03-03
First, open up a terminal and run "xev".  It will bring up a white window.  Move your mouse over the window and then press one of the buttons that doesn't work.  In the terminal window, it hopefully will register a key press, and should look a little like this:

```


KeyRelease event, serial 32, synthetic NO, window 0x2e00001,
    root 0x55, subw 0x0, time 1801312, (215,346), root:(740,766),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False

```

Does it give you a keycode like that?  (that one above says keycode 39 for the s button).  If so, then its simply an issue of mapping it to a shortcut in your window manager.  

IF not...What kind of computer are you on?  It might be helpful to figure out the buttons.

---

### Post by Aiello on 2008-03-03
1. Thanks to diaa. That worked

2 Whiffle:. It unfortunately does not bring up a key code. I am using a HP Pavilion a6200n. The keyboard I am using is the one that came with the computer.

---

### Post by Aiello on 2008-03-10
Any suggestions?

---

### Post by Whiffle on 2008-03-10
Hopefully they're acpi buttons then.  Run acpi_listen in a terminal and then press some buttons, hopefully it will bring up some information.  If so, then we can edit the scripts in /etc/acpi/events to point to a script every time a button is pressed.

EDIT: This assumes that your ACPI is working correctly as well.  If the acpi drivers aren't loaded for your laptop, then no events will be created.  On mine i have to use the thinkpad_acpi module, although I'm not sure which one it is for an HP.

---

