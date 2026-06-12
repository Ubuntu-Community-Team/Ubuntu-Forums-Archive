---
title: "Thinkpad Above Keyboard Buttons"
date: 2013-04-02
forum: Hardware
---

### Post by cbennett926 on 2013-04-02
Ok interesting problem, the buttons (Mute, volume up/down, mic mute) keys are not recognized by acpi_listen or trying to keybind anything, luckily the volume keys all work, however the embedded LED light on the mute key does not light up, nor does the mic key. More interesting is that the mic button does not do anything, does not mute/unmute or is recognized what so ever.  Any help?


Regards,

Cody Bennett

---

### Post by cbennett926 on 2013-04-03
Hooray!!! After some trial and error I have managed to get the LED on the volume mute to work AND get the brightness indicator to change when I change the brightness! Both of which I needed to remove a couple lines of code from my GRUB configuration, now everything is set EXCEPT my darn mic key, it seems as though Ubuntu doesn't recognize that it exists because nothing happens when I press it whatsoever :(

---

### Post by cbennett926 on 2013-04-03
Bump

---

### Post by cbennett926 on 2013-04-08
Final bump and I'll let this die :)

---

