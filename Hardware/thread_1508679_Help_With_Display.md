---
title: "Help With Display"
date: 2010-06-13
forum: Hardware
---

### Post by rsouthard on 2010-06-13
So I was recently given an HP Pavilion n5415. Yeah its old, but it was free. The charger was bad and I had a spare one so I thought I would throw Ubuntu on it. Well I succeeded with the install (10.04), but I am having a problem with the display. The display is using only about 2/3rds of the monitor space. Does anyone know of a fix for this? I have it on max available resolution, but can not find a way to fill the screen.

---

### Post by mistersleep on 2010-06-18
Yeah me too.  I've got the same problem with my P3 Toshiba Satellite.  I'm giving Lubuntu at try with some (really) low end hardware. It's like there's a 2 inch wide border around the edge of the screen on all 4 sides that the computer refuses to acknowledge. 

Cheers,
Mike

---

### Post by overdrank on 2010-06-18
Hi and what is the model of the graphics card?
You can use the command in the terminal ```
lspci | grep VGA
``` to identify the hardware.
You may also look under system, administration, hardware drivers to see if any drivers are available for the graphics.

---

### Post by mistersleep on 2010-06-20
I've got a Trident Microsystems Cyberblade XPAil (Rev 82). Don't see any drivers.

---

### Post by overdrank on 2010-06-20
Hi and I have no experience with that model but this [thread]("http://ubuntuforums.org/showthread.php?t=1509556&highlight=Trident+Microsystems+Cyberblade") may help. Good Luck :)

---

### Post by mistersleep on 2010-07-01
I'm running Lxde the solution for xorg didn't help me so much.  Hey rsouthard, have you made any progress?  I may not see this thru to the end as Lubuntu may not fit my needs like I thought it would.  Thanks though!

Cheers,
mistersleep

---

