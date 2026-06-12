---
title: "Mouse scrolling changed to volume control after upgrade"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by dan_c on 2008-03-19
Greetings,

After a recent kernel update (to 2.6.22-14-generic) on my Dell Insprion 9300, the mouse scroll wheel on my Silvercrest wireless mouse (purchased from Lidl) no longer scrolls up and down / changes desktops... Instead it mutes, raises and lowers the volume. This behaviour can be stopped by killing off keytouch, however the buttons themselves to not react after that.

Output from **xev** shows the scoll wheel up/down/press as **KeyPress** events rather than **ButtonPress** events. For example, here's what is output by xev when I scroll up:

[PHP]
KeyPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x5c, subw 0x0, time 3358737766, (893,6), root:(1764,541),
    state 0x0, keycode 176 (keysym 0xfeed, Pointer_Button5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x5c, subw 0x0, time 3358737766, (893,6), root:(1764,541),
    state 0x0, keycode 176 (keysym 0xfeed, Pointer_Button5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
[/PHP]
(the keycode mapping Pointer_Button5 was my attempt at getting it to work again using xmodmap - it didn't)

My xorg.conf mouse section:

[PHP]
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "ZAxisMapping" "4 5"
        Option "Emulate3Buttons" "true"
        Option "Buttons" "7"
EndSection
[/PHP]

I tried installing (and multiple configurations of) imwheel, however there is still no response from the wheel. I'm wondering if a possible fix might be to trigger a **ButtonPress** event for the offending keypress events above so that they mirror what happens when I click one of the working buttons. For example, here's the xev output for the left mouse button:

[PHP]
ButtonPress event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5c, subw 0x0, time 3359150465, (161,4), root:(1032,539),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5c, subw 0x0, time 3359150565, (161,4), root:(1032,539),
    state 0x100, button 1, same_screen YES
[/PHP]

Any clues on how to do this would be sincerely appreciated. I also have the kernel keycodes and scancodes for the wheel buttons, I just have no idea how to hook them up to the desired (or what I would call normal) behaviour.


Cheers,


dan

---

### Post by twelvepin on 2008-04-14
i have the exact same problem, though i am using vista. the mouse used to work fine and then one day, the scroll wheel started to only adjust the volume. dont know what i installed for it to do this do. i first thought it was a glitch so i uninstalled all the mouse drivers and re-installed them..didnt work. played around with the scroll-wheel options to no avail. 

i am hoping you discover something because i am at a loss. tried calling two silvercrest hot-lines, one that was specifically listed for that [mouse]("http://www.mysilvercrest.de/en/artikel.php?a=17&av=2")  but they both told me it was a mistake that their number was listed and that they only deal with other silvercrest products. going to try calling lidl tomorrow. i know they wont have any answers but i dont know whatt else to do. if you do find a solution, please post it.
thanks

---

### Post by catpaule on 2008-05-25
Hi,

remove and plug in the battery.

Greets from Berlin

Catpaule

---

### Post by alexcavaco on 2008-06-22
Hello,

If your mouse is like mine you can change between 2 modes, normal mouse (black symbols on buttons) or media player (orange symbols on buttons).

A button labelled "CPI" is used to change modes. Just keep it pressed until the battery indicator flashes. It works the same way in Ubuntu and in Windows.

BTW, my mouse is Silvercrest OM1007

---

### Post by twelvepin on 2008-06-26
> **catpaule said:**
> Hi,

remove and plug in the battery.

Greets from Berlin

Catpaule

still cant believe the battery hack worked. your a genius. back to my comfy wireless silvercrest. what a simple pleasure.

thanks from (vote "no") dublin

---

