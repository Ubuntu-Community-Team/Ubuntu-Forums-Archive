---
title: "Ubuntu Mobile Touchscreen"
date: 2008-11-11
forum: Hardware
---

### Post by yam125 on 2008-11-11
Installed Ubuntu mobile as a car pc and works like a dream... With a MOUSE! Currently the Touch screen(Lilliput) has x&y axis inverted and is not centered.  The default driver is not working for me and the touchscreen calibration program is unusable. 

A) does someone know the Xserver ver for ubuntu mobile?

and/or

B)is there another route to take to fix this issue?

---

### Post by yam125 on 2008-12-14
Bump

---

### Post by yam125 on 2009-01-19
Basically everything i tried previously i threw out the window.

I reinstalled the touchscreen cal tool in the ubuntu Repositories then i was on the ubuntu-mobile mailing list:

[email]ubuntu-mobile@lists.ubuntu.com[/email]

and i was helped out by a guy on the list and i found out about the fdi files (im kind of a noob) and i tweeked it to fit.

opened /usr/share/hal/fdi/policy/10osvendor/50-eGalax.fdi

changed the max/min value (this took the longest to realize somethimg obvious)
after restarting X 50 billion times here is the final file for 

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="eGalax">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">70</merge>
        <merge key="input.x11_options.miny" type="string">70</merge>
        <merge key="input.x11_options.maxx" type="string">1900</merge>
        <merge key="input.x11_options.maxy" type="string">1900</merge>

        <merge key="input.x11_options.taptimer" type="string">30</merge>
        <merge key="input.x11_options.longtouchtimer" type="string">750</merge>
        <merge key="input.x11_options.longtouched_action" type="string">click</merge>
        <merge key="input.x11_options.longtouched_button" type="string">3</merge>
        <merge key="input.x11_options.oneandhalftap_button" type="string">2</merge>
        <merge key="input.x11_options.movelimit" type="string">10</merge>
        <merge key="input.x11_options.touched_drag" type="string">1</merge>
        <merge key="input.x11_options.maybetapped_action" type="string">click</merge>
        <merge key="input.x11_options.maybetapped_button" type="string">1</merge>
        <merge key="input.x11_options.rotate" type="string">cw</merge>
        <merge key="input.x11_options.swapx" type="bool">false</merge>
        <merge key="input.x11_options.swapy" type="bool">false</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```
the rotate needed to be clockwise
and i didnt swap x or y

the MAX abslt edge is is 2000 the min edge is 0
then i bumbed it inside so to give me some room to touch it. still needs a bit of adjustment


I should be given a FREE distro of Ubuntu for doing this. (a joke)

---

