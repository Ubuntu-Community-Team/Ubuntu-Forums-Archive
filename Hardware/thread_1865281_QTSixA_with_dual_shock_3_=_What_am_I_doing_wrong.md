---
title: "QTSixA with dual shock 3 = What am I doing wrong?"
date: 2011-10-19
forum: Hardware
---

### Post by glug101 on 2011-10-19
Ok, 

I have QtSixA installed on my computer.  

I can get the gui to recognize the controller through both USB or Bluetooth.

However, I have the following problems:

Bluetooth manager intermittently asks for permission to allow controller access to some arcane service.  Despite checking the box to always allow access, the prompt returns in seconds.

Lights on the controller continue to flash.  It never seems to detect a slot as seen in a certain howto video I've seen.

Even when connected through USB, there doesn't seem to be any interface with the controller and my games.

Help?

---

### Post by mariourk on 2012-03-03
I have the same problem. Did you manage to solve this problem? If so, I'm curious to know how you did it... :)

---

### Post by xREDEMPTIONx on 2012-04-02
Assuming you've correctly paired your dualshock with qtsixa try this. Open a terminal and type sudo service bluetooth stop.Then type sudo service sixad start. Then press the PS button on your controller. Let me know if it works.

---

### Post by mariourk on 2012-04-03
I figured out that I have to run sixad instead of regular bluetooth and that I have to pair the controllers with sixpair, while it is conencted to the PC with a USB-cable. After this it worked fine.

---

### Post by blackangelpr on 2012-06-30
> **mariourk said:**
> I figured out that I have to run sixad instead of regular bluetooth and that I have to pair the controllers with sixpair, while it is conencted to the PC with a USB-cable. After this it worked fine.

it works for me but even if i unchecked the freaking axis in  supertux2 do not allow me to select anything and in supertuxkart after configure the buttons do not even move (>_<)~!
if you guys know or have tested with other games please let me know,..

---

### Post by Falfor on 2013-01-20
glug 101, I have the exact same problem. 

On terminal I write "sudo sixpair", the bluetooth address appears. after I write "sixad --start" it tells me to press ps button but when I do, nothing happens. 
The bluetooth manager open to tell me if I want to allow permission, I do, and the LED continue to flash on the controller.

It doesn't connect and I can't use it.

It used to work. The other day, the controller was working just fine but the day after, it stop connecting.

If someone out there could help me, I would be very grateful.

---

