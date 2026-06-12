---
title: "Touchpad detected as both PS/2 mouse and ALPS Glidepoint...uses PS/2 mouse settings"
date: 2011-10-19
forum: Hardware
---

### Post by Croutoncc on 2011-10-19
I have an alps touchpad on my laptop.   It never got detected as a toupad in ubuntu <= 11.04.  Finally with 11.10, it finds it as a touchpad and in the mouse config I can see a touchpad tab.  

Changing the settings in the mouse config do nothing.  xinput -list gives:
```
 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HP Wireless Optical Mobile Mouse            id=9    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]

```(HP optical is my external mouse)

When I :
```
xinput set-int-prop 12 252 8 3.5
```It changes the touchpad sensitivity.  So I gather the system is using the PS/2 mouse driver to control the touchpad.  Disabling the PS/2 mouse disables the touchpad.  Disabling the AlpsPS/2 glidepoint does nothing.  

When I do:
dmesg | grep -i input I get:
```

[   17.613230] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   17.638723] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
```So this makes me thing the PS/2 mouse drivier is loading first, thus using those drivers instead of the touchpad drivers.

blacklisting psmouse disables the touchpad.

I am now out of ideas on how to get my touchpad behaving as a touchpad.  More specifically I want to disable it as I type, increase sensitivity and have side scrolling back.

Unless someone has other thoughts...how can I change the order it loads the devices...make it load the touchpad first?  Or is there another solution?

Much thanks and appreciations ahead of time!!!

---

### Post by Croutoncc on 2011-10-21
morning bump

---

### Post by dixoncx on 2011-10-21
Same problem here... :(:(
My laptop is Sony vaio VPCEH15, with ubuntu 11.10.

my xinput list output:
```

dixon@dixon-vaio:~$ xinput list
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; OM                                          id=11   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer             id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12   [slave  keyboard (3)]

```Any solutions...?

---

### Post by enrich on 2011-11-16
stuck on the same problem... any solution?

---

### Post by scarleo on 2011-11-16
There is a driver here: [http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb]("http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb")
Install and then restart. 
I have tested this with 11.10.
It works for me and gave me mulitouch with my ALPS touchpad, I can have edge scrolling or two finger scrolling, set sensitivity and speed. Didn't try anything else.

As per: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/737051]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051")

---

### Post by sir4taye on 2011-11-22
The driver install fixed my issue. Just download and let the software center do its thing. Restart. Works like a charm now. 
Lenovo G550 touchpad ubuntu 11.10 working well now.

---

