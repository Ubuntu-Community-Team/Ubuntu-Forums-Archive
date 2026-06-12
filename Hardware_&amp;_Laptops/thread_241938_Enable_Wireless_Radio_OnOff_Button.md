---
title: "Enable Wireless Radio On/Off Button?"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by chagrins on 2006-08-23
There's lots of ways to enable the "special" buttons Toshibas and ThinkPads, but there don't appear to be any for the rather obscure VIA Twinhead.

How would I go about enabling the wireless radio button on this laptop? It's intended to turn the radio on and off quickly. Pressing the button lights an LED, and pressing it again turns the LED off. The LED works fine, but the wireless radio remains on even when the LED is off.

Is there some way I can get this button-press recognized and make it run a script or something?

---

### Post by smelly_sox on 2006-08-23
If U R using Gnome then
System / Preferences / Keyboard Shortcuts
There are any number of options for configuring special keys.
Otherwise you will have to get geeky-techno & start editing files by hand,  to assign your own special commands. Sorry don't know which one/s. I imagine an enquiry at [www.Gnome.org](www.Gnome.org) might help though.

Regards

---

### Post by chagrins on 2006-08-23
Thanks a lot for your reply. I checked this out, but Keyboard Shortcuts didn't seem to recognize me pressing the wireless on/off button.

Following this line of investigation, I tried fooling around with xkeycaps, but I wasn't able to get anywhere.

I can only conclude that the wireless button isn't really part of the keyboard as such, and probably needs a special driver. Is anything like that available?

On a related note, how would I just disable the wireless radio to save battery life?

So, I found this page: [https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch) ...and followed the steps there. My wireless radio key doesn't appear to generate a magic number, or an ACPI event.

The output of dmidecode:

```
To Be Filled By O.E.M.
E12BL
1.0
```

It's a VIA Twinhead notebook. Any suggestions? The button is marked with an icon that looks like the attachment.

---

