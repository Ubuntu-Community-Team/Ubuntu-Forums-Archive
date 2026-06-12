---
title: "usb mouse trouble"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by metuwi on 2006-01-01
Hello,

I have a creative wired optical mouse, and its not working properly. Every once in a while the mouse pointer will suddenly disappear and reappear in one of the screen corners, where it will get stuck for a second or so. this happens every couple of minutes.

this is in my xorg.conf:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

(Is it correct to have  "Protocol" "ImPS/2" when its a usb mouse?)

there was already a thread about something like this, but no solution there.

do you know of a solution?

---

### Post by markthecarp on 2006-01-01
[QUOTE=metuwi]Hello,

I have a creative wired optical mouse, and its not working properly. Every once in a while the mouse pointer will suddenly disappear and reappear in one of the screen corners, where it will get stuck for a second or so. this happens every couple of minutes.

this is in my xorg.conf:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

(Is it correct to have  "Protocol" "ImPS/2" when its a usb mouse?)

there was already a thread about something like this, but no solution there.

do you know of a solution?[/QUOTE]

Metuwi,
That's identical to the mouse section on my laptop where I often use a Logitech optical mouse. Of course there's an additional section for the touchpad. I've noticed the behavior you describe when using an optical mouse on a wood grain surface, fake or real. If you haven't already, you may want to try using a solid color mouse pad. Terribly low tech but it worked for me.

-mark

---

### Post by metuwi on 2006-01-01
haha!
yes, actually, my mouse is on a fake wood grain surface. im trying out your solution now, still waiting if itll occur again. looks like it might be that.
i guess the wood grain is too repetitive or something.
thanks!

---

### Post by the_person0 on 2006-01-01
I have noticed that a few surfaces will put any optical mouse to shame such as the white sams club plastic tables (nicknamed 'evil tables') which are entirely unreadable by optical mice.  Even the Logitech MX 1k has some trouble with them.  But even as such they are still the best for lan parties.

---

