---
title: "installation problem"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by wpshooter on 2005-09-23
Yesterday, I tried to install this Ubuntu O/S on 3 different laptop computers, 2 Compaqs and 1 Dell. 

I have yet to get it to install.

What am I doing wrong ?

Thanks.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=wpshooter]Yesterday, I tried to install this Ubuntu O/S on 3 different laptop computers, 2 Compaqs and 1 Dell. 

I have yet to get it to install.

What am I doing wrong ?

Thanks.[/QUOTE]

Why didn't it work? Did the installer fail? Did you get some output? I need something to work with here. :P

---

### Post by wpshooter on 2005-09-23
[QUOTE=fordfan753]Why didn't it work? Did the installer fail? Did you get some output? I need something to work with here. :P[/QUOTE]
 Yes, let me give you a bit more info.

Actually, this is the live CD version I am trying to run.  And these laptops are all Pentium II.

It seems to work fine, except for one error that I see during the installation regarding name resolution, it gets to the screen where it is apparently installing some programs and/or utilities in a rectangular windows and then the screen just goes to blank and there is just continued CD and hard drive access back and forth but nothing appears on the screen.  I have waited for an hour or more.

---

### Post by fordfan753 on 2005-09-23
When the screen goes blank can you use the virual terminals to see what is going on? (ctrl + alt + f1, f2, f3, f4, f5 and f6)

Also, are you using the same disc on every laptop? Did you burn this disc yourself? If you did try burning it at a lower speed. I recommend 16x just to be safe.

---

### Post by wpshooter on 2005-09-23
[QUOTE=fordfan753]When the screen goes blank can you use the virual terminals to see what is going on? (ctrl + alt + f1, f2, f3, f4, f5 and f6)

Also, are you using the same disc on every laptop? Did you burn this disc yourself? If you did try burning it at a lower speed. I recommend 16x just to be safe.[/QUOTE]
 These are CD that came directly from Ubuntu.  I have 10 of them.  I have tried 3 different copies so far.

When I decided to try to stop one of the installations, I was going to try alt,ctl,del combination and I noticed that when I hit the alt & ctl combination, I got a screen that just had a white bar across the top and bottom of the screen, everything in between was blank.

I also, tried on one of the installation attempts to use the parameter:  live vga=771 & then something like apic lapic.   Still the same result.

---

### Post by wpshooter on 2005-09-23
[QUOTE=wpshooter]These are CD that came directly from Ubuntu.  I have 10 of them.  I have tried 3 different copies so far.

When I decided to try to stop one of the installations, I was going to try alt,ctl,del combination and I noticed that when I hit the alt & ctl combination, I got a screen that just had a white bar across the top and bottom of the screen, everything in between was blank.

I also, tried on one of the installation attempts to use the parameter:  live vga=771 & then something like apic lapic.   Still the same result.[/QUOTE]
 Any further thoughts ?

---

### Post by tiamet on 2005-09-23
[QUOTE=fordfan753]Why didn't it work? Did the installer fail? Did you get some output? I need something to work with here. :P[/QUOTE]
 Hello Fordfan753,  I also am a newbies and tried the "live" disk.  It seemed to load, got the gui screen but the resolution was so high that I could barely see the small icons and pointer for the mouse.  Movement of the mouse was erratic.  I have the NVIDIA GeForce2 MX/MX 400  video card and use a GATEWAY EV900 Monitor (17.7"vis, September 1997).  Other than the screen problem everything seemed OK.  Is there a way to correct this in the "live" 5.04 Unbuntu version?
Thanks.

---

### Post by fordfan753 on 2005-09-24
[QUOTE=tiamet]Hello Fordfan753,  I also am a newbies and tried the "live" disk.  It seemed to load, got the gui screen but the resolution was so high that I could barely see the small icons and pointer for the mouse.  Movement of the mouse was erratic.  I have the NVIDIA GeForce2 MX/MX 400  video card and use a GATEWAY EV900 Monitor (17.7"vis, September 1997).  Other than the screen problem everything seemed OK.  Is there a way to correct this in the "live" 5.04 Unbuntu version?
Thanks.[/QUOTE]
 The resolution is changable....
System > Preferences > Screen Resolution

Mouse options can be changed in...
System > Preferences > Mouse
You are probably looking at using the Motion tab, which is stuff like acceleration, and speed.

---

