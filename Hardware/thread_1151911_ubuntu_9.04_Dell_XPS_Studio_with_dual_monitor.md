---
title: "ubuntu 9.04 Dell XPS Studio with dual monitor"
date: 2009-05-07
forum: Hardware
---

### Post by bougui on 2009-05-07
Hi,

I have a very weird issue, with my laptop ubuntu 9.04 dual display setup.

My X setup has been done with the nvidia-driver version 180.44 and I have selected xinerama.

Everything works fine when I use my usb mouse, but from my laptop mouse pad I can only exit my laptop display to my external monitor.  So I can only use my mouse pad on the external display.

From my laptop mouse pad I can not come back to my laptop screen :-( If I use my external mouse I can go back to my laptop OK

Is there any key that will switch my mouse from my external monitor to the laptop display ;-) ?

OR do I need to configure something with my laptop mouse ?

My laptop is a Dell Studio XPS 13 with nvidia 9500 video card

I'm using ubuntu 9.04 and have apply all the update from RC till today.

here her the mouse section in my xorg.conf file which seem normal to me 

...[FONT=Courier New]
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0" 
    Driver         "mouse"  
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"  
EndSection[/FONT]

...

Any help would be very appreciated.

---

