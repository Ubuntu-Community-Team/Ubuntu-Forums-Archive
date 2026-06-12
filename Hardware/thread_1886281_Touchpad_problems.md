---
title: "Touchpad problems"
date: 2011-11-24
forum: Hardware
---

### Post by lugaru on 2011-11-24
Hi everyone.
Help me to fix such problem like this. I install Ubuntu 11.10 to my laptop but vertical vertical scroll on my touchpad doestnt work. i searched in internet but i didnt find solution of this problem.

Info
Laptop SONY VAIO ubuntu 11.10

>> sudo tpconfig -i
[sudo] password for lugaru:
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;	 no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

>> xinput list
&#9121; Virtual core pointer id=2	[master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4	[slave pointer (2)]
&#9116; &#8627; AlpsPS/2 ALPS GlidePoint id=11	[slave pointer (2)]
&#9116; &#8627; PS/2 Mouse id=12	[slave pointer (2)]
&#9123; Virtual core keyboard id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5	[slave keyboard (3)]
    &#8627; Sony Vaio Keys id=6	[slave keyboard (3)]
    &#8627; Video Bus id=7	[slave keyboard (3)]
    &#8627; Power Button id=8	[slave keyboard (3)]
    &#8627; USB 2.0 Camera id=9	[slave keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=10	[slave keyboard (3)]

---

### Post by scarleo on 2011-11-25
Try [this driver]("http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb") for ALPS touchpad. Install and then restart.

I have tested this with 11.10. It works for me and gave me mulitouch  with my ALPS touchpad, I can have edge scrolling or two finger  scrolling, set sensitivity and speed. Didn't try anything else.
  Source: [[regression] Alps touchpad detected, but scrolling not working LP bug #737051]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051")

---

### Post by lugaru on 2011-11-25
> **scarleo said:**
> Try [this driver]("http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb") for ALPS touchpad. Install and then restart.

I have tested this with 11.10. It works for me and gave me mulitouch  with my ALPS touchpad, I can have edge scrolling or two finger  scrolling, set sensitivity and speed. Didn't try anything else.
  Source: [[regression] Alps touchpad detected, but scrolling not working LP bug #737051]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051")
Thnx man, thnx a lot!!!!!))))))) its works))))

---

