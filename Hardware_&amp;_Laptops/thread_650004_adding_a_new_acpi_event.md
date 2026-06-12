---
title: "adding a new acpi event"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by IBG on 2007-12-25
hi.
I'm trying to add a new acpi event :when the wlan key on my laptop is pressed this shoud execute a script to turn the wlan off/on 

i knew from dmesg that the key have the code 6a:
```
atkbd.c: Use 'setkeycodes 6a <keycode>' to make it known.
[  601.929128] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0)
```
so i created a file in /usr/share/hotkey-support/ 
```
setkeycodes	6a	$KEY_WLAN
```
and modified the hotkey-setup script to notice my laptop 
 i've written this 
```
# /etc/acpi/events/pb-wireless
event=hotkey ATKD 0000006a
action=/sbin/wlan.sh
```

the problem now is that when i press the key nothing happens and nothing shows up in /var/log/acpid

---

### Post by ModelM on 2007-12-25
Where the "instructions" say...

'setkeycodes 6a <keycode>'

it means to add your requested keycode *after* 6a... so it might look something like this...

setkeycodes 6a 0x82

This is just an example, I don't know the proper format of the keycode, but it should point you in the right direction...

...seeya

---

### Post by IBG on 2007-12-25
thanks for your reply
```
cat /usr/share/hotkey-setup/key-constants | grep WLAN
KEY_WLAN=238 

```
in the top of the /etc/initi.d/hotkey-setup you can find 
```
. /usr/share/hotkey-setup/key-constants
```
this means that the definition in the key-constants file are imported 

so this not the issue since the keycode message doesent show up in dmesg anymore

---

