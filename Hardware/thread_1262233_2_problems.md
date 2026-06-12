---
title: "2 problems"
date: 2009-09-09
forum: Hardware
---

### Post by Andreei on 2009-09-09
i have installed netbook remix on a eee pc from asus. but i have two problems with it:
1. i can;t change the resolution. the current resolution i think is 640x480 and i can't change it because i can't see the ok button. i want it to be 640x350 but i can't resize and i can't see that damn button.. the windows doesn;t fit the screen.
2. when i open the pc, the front page of it uses my cpu to the max. if i enter mozilla or simply browse through the hard drive its ok but the front page interface is killing me 
please help.thx.

---

### Post by kerry_s on 2009-09-09
1. hold the alt key & tap drag or left click mouse hold if you have a external.

2. sounds like you need to turn on the reduced resources.
in gconf-editor, use alt+f2 to run it if you haven't enabled it in the menu.

**alt+f2**
type-> **gconf-editor**
[B]click-> apps-> metacity-> general, check "reduced_resources"
click-> netbook-launcher, check low_graphics
[/B]
what are the specs of your eee? sounds to me like your running the 700, if so you need to use a lighter setup/distro.

---

### Post by Andreei on 2009-09-09
630MHz/512 ram
Eee PC 4G-W

i didn't understand your solution for changing the resolution.. i need to connect another monitor  ?

---

### Post by fela on 2009-09-09
Run in terminal:

```
xrandr -s 800x480
```

Or whatever the right resolution is. It might be 1024x600.

Now goto the display properties thingy and make sure it's set at the right resolution. You should logout and in again to make sure it doesn't reset the resolution.

---

### Post by kerry_s on 2009-09-10
> **Andreei said:**
> 630MHz/512 ram
Eee PC 4G-W

i didn't understand your solution for changing the resolution.. i need to connect another monitor  ?

i didn't have a solution, what i said is if you hold down the "alt" key & the left mouse button, you can move the windows so you can reach the apply.
if you don't have a external mouse its "tap & drag" on the touchpad.

given your specs though you should find something lighter than ubuntu.

---

### Post by snakeman21 on 2009-09-10
You may want to try Eeebuntu.  It's Ubuntu, but specifically tailored for the eee pc.

---

### Post by Andreei on 2009-09-11
Thanks a lot. I managed to reduce the graphic details and now it works great.. only uses ~20% of the cpu. Changing resolution also works but it doesn't remain at that value after restart.

---

### Post by sandy8925 on 2009-09-11
I think you've got the CPU speed wrong. As far as I know most eee pc's use an Intel Atom CPU that can run at 1.6 Ghz. Most newer CPU's have a power management feature where they run at a lower frequency to save power. I think 630 Mhz is the lower frequency state and your CPU's actual speed is most probably 1.6 Ghz or something like that. (hopefully.otherwise kerry_s is right and you need to get something lighter)

---

