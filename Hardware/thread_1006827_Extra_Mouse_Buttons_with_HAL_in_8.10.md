---
title: "Extra Mouse Buttons with HAL in 8.10"
date: 2008-12-09
forum: Hardware
---

### Post by nicebloke on 2008-12-09
Hi,

I understand that the xorg.conf isn't used any more for making extra mouse buttons work in 8.10. However, I can't find any simple instructions on making them work with HAL.

I ran xev and get the following data for my "Tempest Habu Mouse"

Button 1 -> Left Mouse Button
Button 2 -> Scroll Wheel Button
Button 3 -> Right Mouse Button
Button 4 -> Scroll Wheel Forward
Button 5 -> Scroll Wheel Back
Button 9 -> Front Thumb Button
Button 8 -> Back Thumb Button
Button 10 -> Front Middle Button
Button 11 -> Back Middle Button

Can anybody help me with setting this up please?

---

### Post by finger51 on 2008-12-20
> **nicebloke said:**
> Hi,

I understand that the xorg.conf isn't used any more for making extra mouse buttons work in 8.10. However, I can't find any simple instructions on making them work with HAL.

I ran xev and get the following data for my "Tempest Habu Mouse"

Button 1 -> Left Mouse Button
Button 2 -> Scroll Wheel Button
Button 3 -> Right Mouse Button
Button 4 -> Scroll Wheel Forward
Button 5 -> Scroll Wheel Back
Button 9 -> Front Thumb Button
Button 8 -> Back Thumb Button
Button 10 -> Front Middle Button
Button 11 -> Back Middle Button

Can anybody help me with setting this up please?

Same here. Using "Microsoft Microsoft IntelliMouse? Explorer"
I tried the suggestions at this [link]("http://ubuntuforums.org/showthread.php?t=967547") but no joy. I've been trying for weeks to find a solution.

---

### Post by finger51 on 2008-12-30
bumpity dangit!

---

### Post by matt.cohenprice on 2009-01-05
> **nicebloke said:**
> Hi,

I understand that the xorg.conf isn't used any more for making extra mouse buttons work in 8.10. However, I can't find any simple instructions on making them work with HAL.

I ran xev and get the following data for my "Tempest Habu Mouse"



I am having the same problem with my Kensington Pilotmouse.

What is xev? I'm not familiar with the command.

---

### Post by Rohan Kapoor on 2009-01-05
> **matt.cohenprice said:**
> I am having the same problem with my Kensington Pilotmouse.

What is xev? I'm not familiar with the command.
xev is an event tester that will tell you the keymaps and response for each mouseclick or keyboard button push.

---

### Post by nicebloke on 2009-01-06
$> man xev

Xev creates a window and then asks the X server to send it events when&#8208;
ever  anything  happens to the window (such as it being moved, resized,
typed in, clicked in, etc.).  You can also attach  it  to  an  existing
window.   It  is  useful  for seeing what causes events to occur and to
display the information that they contain; it is essentially  a  debug&#8208;
ging and development tool, and should not be needed in normal usage.

---

### Post by nicebloke on 2009-01-06
I've just realised that I didn't follow this thread up when nobody responded with an answer. I hacked together a mouse.fdi file and dropped it into /etc/hal/fdi/policy/ then rebooted. I appear to have the use of all of my mouse buttons now - I'm just not sure how to assign actions to them.

Before you ask - here is my mouse.fdi ;)

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_driver" type="string">mouse</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">no</merge>
<merge key="input.x11_options.Buttons" type="integer">9</merge>
<merge key="input.x11_options.ButtonMapping" type="integer">1 2 3 4 5 9 8 10 11</merge>
</match>
</device>
</deviceinfo>

The reason I think my extra buttons are working is that in World of Warcraft I can now use the front and back thumb buttons.

Please let me know if the above is helpful to anybody.

---

