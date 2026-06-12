---
title: "Ubuntu 10.04 64bit + microsoft x4 gaming keyboard"
date: 2010-07-13
forum: Hardware
---

### Post by _salem_ on 2010-07-13
Hi there,

I just bought a microsoft x4 gaming keyboard for my computer, mostly because it was the cheapest backlit keyboard I could find.

However, it has some macro buttons down one side, and I wouldn't mind being able to use them.
It also has multimedia buttons, and these work as expected. But the macro buttons I am unable to bind to anything. Running xev, the keypresses on the macro buttons report nothing.

In windows, you need to use the microsoft software to program the macros. I thought maybe it would just store some keypresses into some flashram on the keyboard itself or something, so I booted into windows and recorded a macro there. But then back in ubuntu, the keypress still gives no output.

I know people have written stuff to get the macro buttons on the Logitech G15 working, I was wondering if anyone had any way to get the buttons on the microsoft x4 working? (yes, i tried the g15 utilities, they didn't work. i also tried installing microsoft's keyboard software under wine, but it wouldn't install). 

Thanks in advance.

---

### Post by _salem_ on 2010-07-18
No one? I guess that'll teach me to buy microsoft.... :(

---

### Post by BritishEmperor on 2010-07-18
> **_salem_ said:**
> No one? I guess that'll teach me to buy microsoft.... :(

Please don't be pessimistic and switch over to microsoft.... don't you value your freedom?? :P

---

### Post by _salem_ on 2010-07-22
Oh no, I'll never go back to windows software again. Well, aside from the xp partition i have so i can load my BlackBerry desktop manager once every 6 months or so when a new firmware comes out. Stupid RIM and their lack of linux support.

But what I meant was that my mistake was in buying microsoft _hardware_, which if i had thought about it I probably could have assumed would need proprietary windows software to work with full functionality.

but if people have the logitech g15 working, why not the microsoft x4?

maybe i should look at the g15tools source code and see if there's anything i can do. which i doubt, since i am not really a programmer.

---

### Post by raelbsd on 2010-07-26
Hi, I'm facing the same issue with this keyboard. I've tried all the steps in the troubleshooting guide ([https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)) and I'm resigned to the fact that this keyboard it doesn't work (yet).  
I've tried xev, acpi_listen and udev's keymap with no luck. Maybe can we try with a USB port sniffer? Or wait for some kind of kernel patch to support this keyboard ..?
I hope someone could shed some light on this issue.
Thanks

---

