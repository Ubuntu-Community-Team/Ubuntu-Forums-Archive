---
title: "turning off touchpad via special keys (fujitsu siemens xa1526)"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by _Stevie_ on 2007-12-30
hello community!

i want to use the keys fn+f6 to turn off the synaptics touchpad.
this combination isnt yet registered so i had to add it via setkeycodes.
i launched xev and pressed the combination and had a look at /var/log/messages.

the output was the following:

```
atkbd.c: Unknown key released (translated set 2, code 0x65 on isa0060/serio0).
atkbd.c: Use 'setkeycodes 65 <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0x65 on isa0060/serio0).
atkbd.c: Use 'setkeycodes 65 <keycode>' to make it known.
```

i did a getkeycodes | grep 101 to check if the keycode 101 is still unassigned, which was
the case. so i configured the key with:

```
setkeycodes 65 101
```

i created the file /etc/acpi/events/touch with the following content:

```
event=hotkey ATKD 00000065
action=/etc/acpi/touch.sh
```

and a file /etc/acpi/touch.sh with the following content:

```
#!/bin/bash

STATUS=`synclient -l | grep TouchpadOff | cut -d = -f2`

if [ ${STATUS} == 1 ]
then
synclient TouchpadOff=0
else
synclient TouchpadOff=1
fi

```

i made it executable with chmod a+x touch.sh and executed it
but i cant change the status of the touchpad. any ideas how i could make it work?

i tried different values for event=hotkey ATKD 
but i dont know what format the value has to be, hex or decimal?
and is the 65 for the fn+f6 already a hex value?

any help appreciated!

---

### Post by _Stevie_ on 2007-12-31
no one can help? :(

---

