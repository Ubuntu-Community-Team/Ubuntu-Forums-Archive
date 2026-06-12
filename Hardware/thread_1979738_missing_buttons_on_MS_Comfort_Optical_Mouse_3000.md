---
title: "missing buttons on MS Comfort Optical Mouse 3000"
date: 2012-05-14
forum: Hardware
---

### Post by gallysam on 2012-05-14
I have a MS Comfort Optical Mouse 3000 that used to work with no poblems on 11.10 then after a fresh install of 12.04 all was going "not so bad" ... scroll wheel works just fine. Rigth after install the left and right tilt were scrolling to te sidees as they should. Tumb button was not working but that was no a problem...
Now, today tilt stop working!! 
tried setting the mouse via xorg.config but no luck

In the past I were able to set tumb button using btnx but sees that there is not sutch thing in 12.04 

more:
ximput reports mouse as 
Microsoft Microsoft Optical Mouse with Tilt

xorg.0.log shows 
[  1109.834] (--) evdev: Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons

but xinput test-xi2 shows tilts as butons  4 & 5 just the same ones that scroll up and down

Any help would be apreciated

---

### Post by tkod on 2012-05-28
Same here since 12.04 install.

---

### Post by Beef Eater on 2012-07-02
Same problem here with Ubuntu 12.04 i386 - left and right tilt buttons do not work anymore. Xorg.0.log shows:

[FONT="Courier New"]Xorg.0.log:[  4314.415] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons[/FONT]

But then rebooting into Ubuntu 11.04 on the same desktop results in the tilt buttons working properly!

So far I have not been able to find any solution, and the problem is really annoying. I will keep looking and will post here if I find any workaround.

---

