---
title: "Problems with NVidia nForce2 on 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by mkaganer on 2010-05-03
B.H.

Hello, all!

I have an old desktop PC with AMD CPU and nVidia chipset.

It has nvidia nForce2 video card.

I have installed a fresh install of 10.04 which loaded a new Nouveau driver and also has an option for a proprietary nVidia driver.

Both options have their problems: 

Nouveau works and offers 2D acceleration but all the screen is shifted right and down by some 16 pixels so the bottom bar of gnome is almost invisible and also the mouse cursor is misplaced by the same 16 pixels so you constantly miss the buttons in the GUI. Also i didn't find a way to set a display refresh rate higher than 60Hz and with the old good CRT display it causes me a real headaches.

The nvidia restricted driver on the other hand shows the screen without shifts and allows to set any resolution/refresh rate. The problem is that when i try to play a video (with gstreamer and also with mplayer) sometimes the system freezes totally so i have to power off the computer (it has no reset button ;) )

Somebody can help me to solve the problem?

Thank you

---

### Post by tom-pouce on 2010-05-03
Hello, I've got the same problem with the nouveau driver.

Do you have any flickering or horizontal lines randomly happening ?

---

### Post by mkaganer on 2010-05-03
Hi, i don't have flickering, some random horizontal lines appear during the boot (but this is probably a problem with my old good CRT display ;) )

Just the top row of the pixels is "spread" some 16 pixels down like vertical bars, and the mouse is misplaced :-(

Also, probably because nouveau uses kernel mode setting (KMS) there's no old good /etc/X11/xorg.conf so i have no idea where to put the driver options. I wanted to try to set HW acceleration off but didn't figure out where to put it.

---

### Post by mkaganer on 2010-05-03
Thanks G-d, the problem is solved :-)

I had to boot in rescue mode (hold left shift during reboot), then go to the root shell and run:

X -configure

This created a prototype xorg.conf in /root/xorg.conf.new.

Then i copied that file to /etc/X11/xorg.conf and rebooted - then nouveau started to work well. Just i had to edit xorg.conf to set the default screen resolution and refresh rate.

---

### Post by tom-pouce on 2010-05-04
Are you using the proprietary nvidia driver for this solution ?

I thought (with nouveau driver) that it was a bad idea to use a xorg.conf file

Anyway, thanks for the tip

---

### Post by mkaganer on 2010-05-04
I'm using nouveau, not the proprietary.

As i've written, the proprietary driver causes my system to freeze completely each time i try to play a video.

---

