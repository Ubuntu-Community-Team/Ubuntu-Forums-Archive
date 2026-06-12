---
title: "Failed to start the X server. Installed new video card."
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by lex on 2006-04-21
Firstly I put a longer cable from my Philips LCD monitor to my computer and the screen resolution adjusted from 1280 by 1024 to 800 by 600. I tried to readjust the settings but there were no other sizes available but when i put the old cable back in every thing is ok.

I installed a new graphics card " Radenon 9550, R955 series graphics accelerator" into my system no problem with windows (same with cable) but when I boot Ubuntu I get, " Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I look at "X server output" screen but couldn't understand anything.

Could someone please advise me how to go about fixing this problem. I have no idea on how to set up "graphical interface" especially with a graphical interface on Ubuntu to work with.
Thanks:roll:

---

### Post by dermotti on 2006-04-21
Well, first of all. Run

**sudo dpkg-reconfigure xserver-xorg** and select **vesa** as your driver, then restart X and reboot.

That should work no matter what.

If you want, you can try selecting **radeon** as your driver, but its not guaranteed to work.

---

### Post by NoWhereMan on 2006-04-21
sudo dpkg-reconfigure xserver-xorg
from a terminal then reboot 

bye :)

---

### Post by dermotti on 2006-04-21
U R 2 slow :-)

---

### Post by lex on 2006-04-21
thanks

---

### Post by dermotti on 2006-04-21
Lol no, i was talking about **NoWhereMan**, i beat him to the response :-P

---

### Post by NoWhereMan on 2006-04-21
rotfl :lol:

---

### Post by lex on 2006-04-21
[quote=dermotti]Well, first of all. Run

**sudo dpkg-reconfigure xserver-xorg** and select **vesa** as your driver, then restart X and reboot.

That should work no matter what.

If you want, you can try selecting **radeon** as your driver, but its not guaranteed to work.[/quote]

Could you please explain how to open a terminal without a graphical interface. (I can only log in to command line like prompts) I hope you can understand what I'm trying to say.
Thanks

---

### Post by dermotti on 2006-04-21
run the command from command line, it should work.

If some reason you arent getting a command line, try pressing  cntrl + alt + f3

---

### Post by lex on 2006-04-21
_**Thanks**_ I got it to work. I had to use another driver though ati rather than vesa. Vesa made the graphics unseeable.
Thanks again

---

