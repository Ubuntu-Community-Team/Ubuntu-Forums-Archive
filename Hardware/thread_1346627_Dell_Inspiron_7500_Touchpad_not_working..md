---
title: "Dell Inspiron 7500 Touchpad not working."
date: 2009-12-05
forum: Hardware
---

### Post by G1DRP on 2009-12-05
Hi All,
      I've just dug my old Dell laptop out. It runs reasonably well on XP, but it's way too slow.
I have installed Ubuntu 9.10 and the touchpad doesn't work. I can't move the cursor at all, even with an external mouse plugged in.
I beleive it uses a Synaptics touchpad. 
I am not very computer literate, so I need help please.;)

---

### Post by G1DRP on 2009-12-06
Any help would be greatly appreciated please :)

---

### Post by oooh on 2009-12-06
Hi there

For a start, you could post your file content of /etc/X11/xorg.conf. Touchpad is usually setup there.

Then you can :

Try this: tpconfig, it will tell you if the touchpad is there.
Then cat /proc/bus/input/devices will tell you if there are touchpad devices in there
And in addition dmesg | egrep -i 'input|touch|track' will also give you information about the state of the touchpad

If you tell us the outputs of these commands, then we can maybe go furhter !
:)

---

### Post by G1DRP on 2009-12-06
> **oooh said:**
> Hi there

For a start, you could post your file content of /etc/X11/xorg.conf. Touchpad is usually setup there.

Then you can :

Try this: tpconfig, it will tell you if the touchpad is there.
Then cat /proc/bus/input/devices will tell you if there are touchpad devices in there
And in addition dmesg | egrep -i 'input|touch|track' will also give you information about the state of the touchpad

If you tell us the outputs of these commands, then we can maybe go furhter !
:)
Thanks for your reply.
The problem is, that I can't move the cursor even with a PS2 mouse plugged in. In XP, everything works as it should but slowly.
The Touchpad is enabled in the BIOS.

---

### Post by oooh on 2009-12-06
Finally I got it working ! 

As usually, by Reading the F***** Manual :)

Check this out and try all possibilities, it must do the trick in a way or another.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

In my case I did this:

I added this section to the /etc/X11/xorg.conf:

Section "InputDevice"
    # generated from default
    Identifier     "Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

They key was the SHMConfig being ON.

After restart, the touchpad was working.
Hope that this helps!

---

### Post by G1DRP on 2009-12-06
Thanks for going to so much trouble. I'll have a play.

---

### Post by deburau on 2009-12-21
> **G1DRP said:**
> Hi All,
      I've just dug my old Dell laptop out. It runs reasonably well on XP, but it's way too slow.
I have installed Ubuntu 9.10 and the touchpad doesn't work. I can't move the cursor at all, even with an external mouse plugged in.
I beleive it uses a Synaptics touchpad. 
I am not very computer literate, so I need help please.;)

To make the touchpad working for the Dell Inspiron 7500 I had to do two things:

[LIST]
[*]configure shm as discribed [here]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig"), i.e. creating the file 
*/etc/hal/fdi/policy/shmconfig.fdi*
[*]doing a "Load Factory Defaults" in the BIOS
[/LIST]
Cheers, Werner

---

### Post by daneland on 2010-01-05
I followed the instructions in the thread (xorg.conf and shm configuration). My touchpad still didn't work, even after reboot.

I needed a couple of reboots before it finally, magically started to work. I ran 9.10 from CD in-between a couple of reboots.

Guess the old 7500 will get one more chance.

---

