---
title: "Dell D830 Trackpoint (AlpsPS/2 ALPS GlidePoint)"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by MicahCarrick on 2007-11-07
I have a Dell D830 Laptop which has a touchpad AND a trackpoint nub in the keyboard. Both are working, and I can configure the touchpad options using xorg.conf. Does anybody know how I can adjust the sensitivity/speed of the trackpoing? I don't see it in xorg.conf and it's way too fast.

```
I: Bus=0011 Vendor=0002 Product=0008 Version=6337
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=mouse3 event5 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
```

---

### Post by DellCA on 2007-11-14
The trackstick on Dell computers (and probably other brands of notebook as well) is considered to be a standard PS/2 mouse from the operating system's perspective.  This means that the standard mouse-speed setting in the xorg.conf file should be what you need to change to adjust the trackstick's speed.

If you use an external mouse as well, you might want to set up two separate mouse config sections if you want them to have different speed settings.

Larry
Dell Customer Advocate

---

### Post by garif on 2008-06-24
I have the same Latitude D830 and have tried to get the press-to-select functionality to work for some time, but nothing helped so far. 

Indeed it responses to the PS/2 mouse settings but since an ordinary mouse cannot be "pressed" I did not find a solution. There is no /etc/init.d/trackpoint as the system does not even know that there is a trackpoint present. 

However, I get input from /dev/input/event6 when the trackpoint is moved and maybe when it is pressed, though I am not completely sure about this since it moves easily when pressing it a bit harder. 

Does anybody experience the same problem or know how to activate press-to-select for a "PS/2-trackpoint"?

---

