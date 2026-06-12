---
title: "ATI graphic card driver not found on Lucid Lynx"
date: 2010-10-13
forum: Hardware
---

### Post by Arsenal_86 on 2010-10-13
Hi.
I've installed 10.04 on my DELL studio 15 notebook and saw the **driver not found **symbol on upper-panel.
I checked on that and came to know that my **ATI Mobility Radeon HD 4570** graphic card has proprietary driver and thus graphic card is not finding driver in 10.04 ! :(

What I've to do? How can I find ATI driver which works on 10.04?

Please help.
Pranav

---

### Post by xircon on 2010-10-13
Can you connect to your router with a cable? Update and run the hardware drivers tool from the menu

---

### Post by mastablasta on 2010-10-13
Go to menu System->Administration->Hardware Drivers
 
select the driver after the scan and enable it.
 
more on this here: [http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html) or in Ubuntu manual.

---

### Post by gudurukarthik on 2010-10-13
hey , i understand what u said but i cant find hardware drivers no where in that region . im also using ati mobility radeon graphics with 512 mb vram in my sony , i do face graphics problem and can not activate them through additional drivers . 
hey do u have any code for opening the hardware drivers through terminal ?

---

### Post by xircon on 2010-10-13
@gudurukarthik - have you tried to download from the ATI website?

---

### Post by gyussz on 2010-10-13
Try this: [http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)

EDIT:
I'm using the same graphic card without any trouble

---

### Post by Arsenal_86 on 2010-10-13
> **mastablasta said:**
> Go to menu System->Administration->Hardware Drivers
 
select the driver after the scan and enable it.
 
more on this here: [http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html) or in Ubuntu manual.

SOLVED!!! Just upgraded to 10.10 Maverick and i go to **System->Administration->Additional Drivers** and found ATI driver listed there. Clicked on that and it installed properly! the same thing I did in 10.04 Lucid but it didn't work there. Maverick Rocks!!! :):)

Thanks mastablasta and all the guys who supported! Kudos to all!! :)

---

