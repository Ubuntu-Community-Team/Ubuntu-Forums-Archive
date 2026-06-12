---
title: "Wacom Tablet personnal X setup"
date: 2009-06-18
forum: Hardware
---

### Post by simonced on 2009-06-18
Hello everybody,

I upgraded to the 9.04 (i'm ubuntu user since 7.04) and discovered some problems when reading on the forums.
My laptop is an acer TravelMate 2350 with the ugly Intel i315 graphic card.
I solved some grahical problems and everything works well, but the random X crashes are still.
I discovered it's that because I have set up manually some settings in the XConf about the buttons for my pen tablet (wacom graphyr 2). Now it seems it's HAL dealing about that, but HAL is swaping the buttons order, and it's not convinient at all !

How to swap the buttons 2 and 3 for my tablet using HAL (this way I won't have random X restart I think).

Thank you for your help.

---

### Post by Favux on 2009-06-18
Hi simonced,

Are you talking about the stylus buttons?  If so you would add to the 10-wacom.fdi in "/usr/share/hal/fdi/policy/20thirdparty/" something like:

       <merge key="input.x11_options.Button2" type="string">3</merge>

It would go in the usb or serial section, near the bottom, depending on whether your Graphire2 is usb or serial.  And a similar line if you have two stylus buttons only you would use "Button3" for the second stylus button.

---

