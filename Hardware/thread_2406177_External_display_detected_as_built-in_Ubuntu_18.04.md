---
title: "External display detected as built-in Ubuntu 18.04"
date: 2018-11-17
forum: Hardware
---

### Post by carusoswi on 2018-11-17
I have run a dual display setup on my Asus G74SX for years without problems.  This morning, when I plugged in my external display (via my laptop's VGA port), the external came on , but no laptop display.  I went into 'device' where I noticed that Ubuntu is showing my external display as the built-in display.  

I joined the displays and moved the "TV" icons so that the order matched my setup, but now the resolution on my laptop is wrong (everything is squashed).  

Having the built-in mix-up would not bother much if I could correct the resolution on the laptop, but I see no method of doing that via the GUI.  Additionally, there is no way via the GUI that I can correct Ubuntu's assumption that my laptop display is the built-in.

I have made no changes to my Ubuntu system recently, haven't even spent much time in Ubuntu lately due to my work schedule.

My display card is Nvidia if that matters.

Advice would be most appreciated.

Thanks.

Caruso

---

### Post by 23dornot23d on 2018-11-17
You can try

[B]$ sudo apt install arandr
[/B]
**$ arandr**

it brings up a graphical display that shows your setup and allows resolution changes under [B]Outputs

Hopefully you will be able to change the resolution in the drop down by picking the screen you are currently using.
[/B]
if you still have problems - show a screen shot of what it shows ..... and explain a little more about your
system and desktop you are using to help others understand a little more about what your own
system is .......

**$ sudo apt install inxi**

**$ inxi -F**

---

