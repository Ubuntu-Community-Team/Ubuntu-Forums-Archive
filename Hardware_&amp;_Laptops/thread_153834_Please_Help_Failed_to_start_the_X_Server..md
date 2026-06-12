---
title: "Please Help: Failed to start the X Server."
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by Killabrew on 2006-04-01
When ever I boot this message comes up:


--------------------------------------------------------------------------
Failed to start the X server (Your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

                          <YES>                  <NO>
 
--------------------------------------------------------------------------\

If you need more information please let me know. I couldnt type it right now because I have to get to work. I would apreciate any help. This is the first time I use linux.

My specs:
HP Pavillion A1210N
ATI Radeon Xpress 200

PLEASE HELP ME. THANK YOU IN ADVANCE. IF YOU NEED ANYTHING ELSE LET ME KNOW.

---

### Post by sto6ma9ch on 2006-04-03
The exact same thing happened to me after building a new computer. The motherboard uses the ATI Radeon Xpress 200 video adapter. Ubuntu will recognize the chipset as ATI, but the card seems to have trouble with this driver. I had to use the generic "vesa" driver. Here's what you'll need to do:

[LIST]
[*]Boot into Recovery Mode
[*]Type:
```
dpkg-reconfigure xserver-xorg
```
[*]When asked for the driver, select "vesa"
[*]Complete the X server setup
[*]When you're back to the shell, type:
```
reboot
```
[/LIST]

This should get X working for you. I'm still searching for a better solution to this, but these steps should get you working. Keep us posted!

---

