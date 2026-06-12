---
title: "Ubuntu 7.10 and Matrox Parhelia problem."
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by ant0ny on 2009-02-09
I have installed Ubuntu 7.10... then installed the latest Matrox Driver and all went fine.

Run > # matroxconfig

Configured the card with 3 monitors and saved all well and works a treat.

At this point I have a very good setup with desktop spanning over 3 screens (TripleHead Card).

The issue is when I reboot the graphics isa little screwy... The mouse is like 3 pointers overlayed and when I login it all is wrong like the refresh rates are incorrect. If you open say > Places > Computer > Filesystem you get the icons and labels screwy untill you run the mouse pointer over it and it displayes correctly.

If I do Ctrl > Alt > Backspace and restart X then login the graphics is right and even before you login you notice the mouse pointer is drawn correct and all is good again.

As the OS is starting you get the Video Cards Splash Screen and even at this point you notice the screen is screwy before the Login Window is up... do Ctrl > Alt > Backspace and restart X and the Splash Screen is drawn right and login as well.

I can't work out how or where to start to find out why X is not configured correctly untill I restart it.

I hope this makes sence...

Antony

---

### Post by ant0ny on 2009-02-09
Well to answer my own questions.

This is not the known bug "Ubuntu 7.10 Bootup Resolution Problem" as seen with this flavour.

If you are looking for a solution look here. [http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

This seems to be a problem with X as it starts it doesn't finish executing correctly.

The fix I used to get around this may help others.

To run something immediately after startup:

Create /etc/rc2.d/S99custom script

```
#!/bin/bash
/etc/init.d/gdm restart
```

.. then make it executable in Terminal:

```
me@here:~$ sudo chmod 755 /etc/rc2.d/S99custom
```

reboot

The "S99" bit should cause that script to be run last in runlevel 2
startup sequence and gdm should already be started by then.  

If it needs a bit more delay before the gdm restart, try:

```
#!/bin/bash
sleep 10s && /etc/init..d/gdm restart
```

Antony

P.S thanks Sean for the help!

---

