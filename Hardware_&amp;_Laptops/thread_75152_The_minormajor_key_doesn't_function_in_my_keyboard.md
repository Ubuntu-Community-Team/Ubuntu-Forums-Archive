---
title: "The minor/major key doesn't function in my keyboard"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by ThE_nEtTeR on 2005-10-13
Hi mates!!!

   I recently bought an Acer Aspire 1692 WLMI and decided to install Ubuntu because i need it to program in C, but after having installed it I've noticed that the major/minor than key (<>) doesn't go and to use it i've got to go copying/pasting which is time-consuming!!

i've tried to install hotkeys and loading a profile i found for the 1690 series but this alone key is still unwilling to function. i have also used xev to know which is its keycode, which is number 94 but i have made a custom definition of my keyboard including this keycode and isn't working yet.

i dont' know what else i can do to use this key; if you could help i would be very pleased.

Thanks!!! ;)

---

### Post by Chuckaluphagus on 2005-10-15
I'm not entirely sure, but it sounds like you may have the wrong keyboard layout set - your computer is expecting the "<>" keys to be somewhere/something else, and therefore you're not getting the correct response when you hit them.  

Under the System menu at the top of your screen, Choose "Preferences -> Keyboard".  In the Keyboard Preferences window that comes up, choose "Layouts" at the top of the window.  You need to choose the language that you want (mine is U.S. English, not sure where you are) by clicking "Add..." at the right side of the window and choosing whatever is appropriate.  

If you have multiple options for layouts for your language and can't read the lettering on the keyboard diagram that comes up on the "Choose A Layout" screen, drag the side of that window to the right to expand it; it'll enlarge the graphic as well and make it easier to read.

Sorry if you've already tried this.  Hope it helps.

---

### Post by ThE_nEtTeR on 2005-10-16
thanks, i've also tried to do what you said and i got an error when changing my keyboard to generic pc105 and es (from Spain) layout.

it says: x configuration: parse error on line 62 of section InputDevice in file var/lib/xorg.conf. This section must have an identifier line.

i've read a bit and this section should be this way:

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"

    Option "XkbModel" "pc104"
    Option "XkbLayout" "us"
    Option "XKbOptions" ""
EndSection

Mine is:

Section "InputDevice"

    Option "XkbLayout" "es"
    Option "XKbModel" "pc105"
EndSection

so i think i need to add Identifier "keyboard1", what i don't know is if keyboard1 must have been previously defined in another config file...if you could shed a light on me...

Thanks, bye!!;)

---

### Post by Chuckaluphagus on 2005-10-17
Unfortunately, you've now exhausted my limited knowledge of Linux configurations.  Sorry, I'm pretty much an Ubuntu newb as well.  I'm not familiar with keyboard configurations in xorg.conf, but someone around here has to be.  Hopefully you'll get more help shortly.

---

### Post by ThE_nEtTeR on 2005-10-17
dont' worry, i've finally installed opensuse and now everything is fine. the problem was that the X server didn't show on the screen what I was typing, now i'm using kde and i finally got it.

bye!!

---

