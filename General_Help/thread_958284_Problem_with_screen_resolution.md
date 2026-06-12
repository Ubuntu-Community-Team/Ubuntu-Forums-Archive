---
title: "Problem with screen resolution"
date: 2008-10-25
forum: General Help
---

### Post by rmcellig on 2008-10-25
I hooked up an external monitor to my laptop. The screen resolution changed to 640x480. It was much higher than this on my laptop (can't remember exactly what it was). After detaching the external monitor, and restarting my laptop, the resolution is still at 640x480.

I seemed to have lost my previous higher resolution setting from the resolution pull down menu.

How can I get my resolution back to what it was.

The Nvidia driver is enabled in the Hardware settings window.

I tried launching the Screens and Graphics window but it goes off the screen so I am unable to see it. Please help!!

Thanks!!

---

### Post by roger_1960 on 2008-10-25
Hi

Try in terminal (application-accesories-terminal)

sudo displayconfig-gtk

enter your password (wont appear) and use the model and resolution settings in the GUI.  You may also be able to configure the 2nd monitor display as well.  Use the test option before accepting!  You may need to log in again for this to take effect.

---

