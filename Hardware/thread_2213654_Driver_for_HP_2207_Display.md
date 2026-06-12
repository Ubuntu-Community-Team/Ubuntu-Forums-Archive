---
title: "Driver for HP 2207 Display?"
date: 2014-03-27
forum: Hardware
---

### Post by riverguy99 on 2014-03-27
Does anyone know where I can find a driver that will work with the HP 2207 display?  I'm running 12.04.

---

### Post by Frogs Hair on 2014-03-27
If there are any display/video  drivers available for your computer they would be displayed in additional drivers.

---

### Post by oldfred on 2014-03-27
It usually is not the monitor that needs drivers but the video card.
What video card/chip do you have?
       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

### Post by houstonbofh on 2014-03-28
I have never installed a monitor driver in Linux.  Why do you feel you need to?  What is not working for you on that monitor?

---

### Post by riverguy99 on 2014-03-29
This is a dual monitor setup.  The computer is a Dell D620 laptop and the monitor is an HP 2207.  I need both for my work.  Right now, the 2207 is working fine, but setup will not allow me to extend the desktop onto the laptop.  All I get is a mirror; the same info on both screens.  Maybe I don't need a different dirver, but some way to expand my options in setup?  If so, I'll move to that thread.

Thank you!

---

### Post by Mark Phelps on 2014-03-30
This is generally a video driver limitation.  

When I installed Mint 16 on my desktop, I could only get one of my monitors to display.  With previous Mint versions and Ubuntu versions, I could get BOTH monitors to display.  When I then installed the AMD fglrx drivers, I could get BOTH monitors to display.

---

### Post by houstonbofh on 2014-03-30
Yep.  This is your video card.  What do you have?  And what are you using to configure your displays?

Note:  This works fine and as you need on my laptop with an Intel vidoe chip, and the stock monitor config from Gnome.

---

### Post by riverguy99 on 2014-03-30
Well, this is a bit strange.  I installed Ubuntu Tweak and played around with the setting in there and all of a sudden my two displays work great and the laptop is now an extension of the HP2207 display.  I will NEVER change anything in Tweak again!

Thank you for your kind assistance!

---

### Post by Yellow Pasque on 2014-03-31
Mark thread solved.

---

### Post by riverguy99 on 2014-04-02
One more detail on this, it seems that what actually fixed the issue was not installing Ubuntu Tweak, but it was actually switching to 2-D mode.  I did the same thing on another laptop I just installed to a remote display and it worked again.

---

### Post by Frogs Hair on 2014-04-02
Ubuntu Tweak is GUI for settings already found in the dconf editor or compiz CCSM if installed .2D has lesser graphis requirements so uses less graphics memory resorces.

---

