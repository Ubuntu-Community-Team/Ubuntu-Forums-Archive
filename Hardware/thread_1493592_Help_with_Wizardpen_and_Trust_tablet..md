---
title: "Help with Wizardpen and Trust tablet."
date: 2010-05-26
forum: Hardware
---

### Post by kihon on 2010-05-26
**UPDATE: Found solution. Im using the xorg-edgers ppa, and it appears that the new XOrg version looks for the xorg.conf.d folder in the /usr/share/X11 folder rather than /usr/lib/X11. Moved the 70-wizardpen.conf to /usr/share/X11/xorg.conf.d/ and everything worked again.**


Hi all,

I had my Trust TB 5300 tablet working fine under lucid until recently. Then all of a sudden, it stopped working. Now when I move the pen, the cursor sticks in the top left corner.

I noticed that xinput -test shows that the x,y pos info are now in the a[2] and a[3] values, rather than the a[0] and a[1] values. 

When I run modprobe -l it does not show up the wizardpen driver, and I cannot install the driver by calling modprobe -i wizardpen or modprobe -i wizardpen_drv. I installed wizardpen using the ppa. 

I also noticed that in my Xorg.log I see the following(Note it does not seem to apply the wizardpen driver):

[  2828.379] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event6)
[  2828.379] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[  2828.379] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[  2828.379] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  2828.379] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event6"
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found 10 mouse buttons
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found relative axes
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found absolute axes
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[  2828.392] (--) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[  2828.392] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[  2828.392] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[  2828.392] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2828.392] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[  2828.392] (WW) UC-LOGIC Tablet WP5540U: touchpads, tablets and touchscreens ignore relative axes.
[  2828.392] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.

Any ideas what Im doing wrong?

Thanks in advance,

Kihon.

---

### Post by Amaterasu80 on 2010-06-03
I'm having a similar problem, in my /usr/lib/X11/xorg.conf.d/ folder I have the "05-evdev.conf" file. If I remove that file my Tablet works fine but without mouse or keyboard input, but while that file is there my mouse and keyboard work fine but my tablet sticks up in the top left-hand corner. I'm really confused O.o

P.S  Sorry for this post not being an answer. :P

*OOPS sorry, didn't see the update. . .i'll try that now

***Nope, I don't seem to have a /usr/share/X11/xorg.conf.d/ folder???**

---

