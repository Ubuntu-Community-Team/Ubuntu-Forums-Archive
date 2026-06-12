---
title: "Keyboard assist request."
date: 2009-04-15
forum: Hardware
---

### Post by Capt_Zaphod on 2009-04-15
Hello everyone;

  I have a 2003 Toshiba Satellite laptop.  The keyboard stopped working ... at least, its stopped working for me.  You see I bought a USB keyboard, but fairly frequently, it pics ups ghost signals from the built in key board (ie the cap lock activates, the CTRL key starts, and everything I type becomes a cntrl+letter command. As well as other random letters appearing on the screen.  Mainly ; and M.  My question is, how do I disable the laptops keyboard, so that the laptop only accepts commands from the USB keyboard?

  It 's like there's a gremlin in my machine, fighting me.  It's getting worse daily.  Took me 10 minutes to type this.  

Thank you,
Z

---

### Post by Capt_Zaphod on 2009-04-15
> **Gambitt said:**
> It looks like some keys of your laptop's keyboard are stuck (or atleast they are short circuiting from inside). Check Windows Key, Ctl or Alt keys.
If its an old laptop then it could just be wear & tear, or dirt under the keys or something. Get it cleaned.
Finally if your laptop keyboard has some life left then try fn + f11 or f12. Usually this disables the keyboard. 
I am sure you have checked the BIOS settings for any keyboard disabling option.
Thank you Gambitt
But:

Nothing appears to be stuck, as actually trying to use the built in keyboard does nothing.
I already cleaned it our with compressed air.
fn+f11/f12 does nothing.

The BIOS settings have nothing about the keyboard.

---

### Post by roger_1960 on 2009-04-15
Hi

You could open it up and remove the keyboard ribbon cable from the motherboard....

---

### Post by Capt_Zaphod on 2009-04-15
> **roger_1960 said:**
> Hi

You could open it up and remove the keyboard ribbon cable from the motherboard....

Worth a shot.  
Thank you.

---

### Post by Windsurfer619 on 2009-04-16
This is a bit technical, but...

If you go into /dev/input/by-path/, you'll see a bunch of devices. One of them is probably like "platform-i8042-serio-0-event-kbd" (that's mine). If you set the permissions to what it's pointing to (type ls -la to see which event the symlink is pointing to) to be something like 000 (sudo chmod 000 /dev/input/event0, or something like that), nothing *should* be able to read from it.
Of course, all this is assuming these "hiccups" are caused by software and not by hardware.
PS you can really mess up your system by fiddling with stuff in /dev/. You've been warned!

---

