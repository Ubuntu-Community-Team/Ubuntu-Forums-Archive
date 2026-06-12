---
title: "Keyboard layout resets when usb plugged in"
date: 2009-07-01
forum: Hardware
---

### Post by sjv on 2009-07-01
I use a Colemak keyboard layout, and I have a usb switch that I use to toggle between two computers. When I switch from my other machine, to the ubuntu machine it resets the keyboard layout to US English, and changes the caps lock back to caps lock from being backspace. 

I have a bash alias to fix the problem, but the requires me to run it each time I switch can sometimes be quite frequently.

alias fixkb='setxkbmap colemak && xset r 66 && xset r rate 290 30'

Any idea what I can do so that it won't keep changing each time I switch over?

Thanks,
Steve

---

