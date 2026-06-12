---
title: "Finicky Wacom Driver"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by tiglionabbit on 2005-11-07
Every time I start X, the maximum pressure is different.  It should be 255, but the last three times I've started X it has been 256, 831, and 81.  Also, when I press the eraser to the screen it hits "button 52" (using 'xidump eraser') instead of button 1.  Attempting to use xsetwacom to change these things results in this error:
Error (5): WacomConfigSetRawParam: Unknown X error

Everything works perfectly in wacdump ('wacdump -f c100 /dev/ttyS0').  Pressure goes from 0 to 255, it detects touch from the pen and eraser tools, and the button as well.  Why wont X do these things?  Is there any way I can fix these things without having to compile the drivers myself?

This is an Acer Travelmate C300 Convertible TabletPC.

---

### Post by 23meg on 2005-11-07
Not sure about your pressure problem (will look into it later) but for the eraser problem, you should be able map any device button event (Y) to any X event (X) with a ```
    Option	     "ButtonY"	"X"
``` line in your device section in xorg.conf. Quoting the linuxwacom documentation:
>                Option "ButtonM" "N"
                   reports a button N click when button M is pressed,  where M
                   is one of the wacom supported  button numbers,  it can be 1
                   to 16 and N can be an integer between 1 and 19. The default
                   value for button M is M.  When N is less than 17,  button M
                   is  assigned to  the  function of  button N.  When N is 17, 
                   button M is a left-double-click.  When N is 18, button M is 
                   ignored,  i.e.,  no  button  event  will be  reported  when 
                   clicking on button M. When N is 19, button M is assigned to 
                   Mode Toggle,  switching between relative and absolute mode, 
                   which is  especially useful to switch  windows in a  multi-
                   monitor environment.

---

