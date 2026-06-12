---
title: "mouse pointer gone mad"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by satbunny on 2006-07-02
Hi.

I have a Compaq EVO 400c which I have been using for about two weeks with Xubuntu 6.06.

Last week the mouse pointer started to drift to the right of the screen. I could just about conuter the drift with the keyboard 'joystick/nipple' but today it has got quite bad and I can't counteract the drift. I have removed and cleaned the keyboard nipple and I have also plugged a USB mouse in as an alternative.

1: do people think this is a software or hardware issue?
2: can I calibrate the mouse? altho Xubuntu is a stripped version of Ubuntu I can install any normal Ubuntu app and use it if you can suggest one?
3: can I disable the keyboard mouse althogether and start using an external one wholly?

All help appreciated, I just bought extra memory for this laptop just before this problem emerged, typical eh?

:(

PS: any help in driving my way around the desktop without a mouse might help as well..

---

### Post by LeisureDroid on 2006-07-04
Got a similar mouse problem on Toshiba Libretto L5/080TNLN mini notebook.........  except the mouse cursor drifts from right to left continously until it reaches the leftmost side. My setup is Ubuntu/Gnome rather than Xubuntu.

Only thing I've changed since problem started was to install Azureus (along with a bit of a list of dependencies). Install was very clean otherwise - done via network using PXE since Libretto L5 has no floppy, cdrom etc.

Anyhow, I guess this mouse drift thing is fixable via X config but I'll reseach a little further - probably same issue sometimes happens in other distros.


- LeisureDroid

---

### Post by cracker on 2006-07-04
Well, I own an IBM Thinkpad 600 with this type of mouse, and it started to do this, and later broke right off the keyboard. I'm inclined to say it is the hardware itself, but I'd suggest booting a liveCD to see if the problem persists with a different OS/setup.

---

### Post by radekw on 2006-07-06
I rebooted today after upgrading xserver-xorg-input-mouse package yesterday. Using the keyboard nipple on Thinkpad T30 was a nightmare - every click put the mouse cursor in random position on the screen. At the same time the touchpad below worked perfectly.

I've noticed that in my /etc/X11/xorg.conf file the mouse protocol was set to "ExplorerPS/2". I recalled that protocol I've used before was "IMPS/2". After changing and restarting X all returned to normal.

---

