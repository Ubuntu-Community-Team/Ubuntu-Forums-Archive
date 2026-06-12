---
title: "not all mouse buttons work on Lucid"
date: 2010-07-13
forum: Hardware
---

### Post by aeon.flux on 2010-07-13
hello,

im using ubuntu 10.04 and i used to use all 8 mouse buttons with Karmic Koala on my Logitech mx510 mouse. I was using it with Compiz - some buttons couldn't be set as 1-9,(1-5 worked ok, 6-9 didn't) so i writen there "Button11" for example and it worked with my other buttons, so i could use ALL 8 buttons.

Since i have lucid this is not possible, don't know why. I bought a new mouse - Razer Orochi and i have the same problem. First 5 buttons work too (right, left, wheel, back, forward) but the other buttons don't work as any of 6-9. The Button10,11,12.... can't be set, when i write there "Button11" and click OK, it shows empty : (

---

### Post by Dr_Willis on 2010-07-13
I recently discovered a 3rd party set of drivers/utils for most Logitech devices at the web site [http://www.hidpoint.com/](http://www.hidpoint.com/) They seem to have a nicer gui for configuring  these often very complex keyboards and mice we have these days.

You may want to try them out. Im sure theres proberly other tweaks to get the extra buttons working, but the hidpoint software seems the 'closest' to what you would normally encounter in  windows.

---

### Post by bikertappy on 2010-10-26
Is the mouse PS/2 or USB? I had my cordless USB Logitech MX610 plugged in via a PS/2 adaptor.
I ran xev from the terminal window and found that it wasn't recognising any of the special buttons.
I plugged it directly into a USB port and it now recognises them all.

I'm running 10.04 Lucid and the mouse now controls volume automatically, but as yet doesn't do other functions.

I tried the HIDpoint software but it didn't seem to recognise the special buttons either.

---

