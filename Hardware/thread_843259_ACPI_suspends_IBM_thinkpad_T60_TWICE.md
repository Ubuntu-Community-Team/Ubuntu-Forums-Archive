---
title: "ACPI suspends IBM thinkpad T60 TWICE"
date: 2008-06-28
forum: Hardware
---

### Post by Grizzlitiger on 2008-06-28
Hi there,

I just upgraded to Ubuntu 8.04 and I was very pleased to see that suspending finally seems to work out of the box:)
There is a small problem now; I have a Thinkpad T60 and I used to suspend using a suspend script which I put under 
/etc/acpi/actions/suspend.sh
calling it using the file 
```

# /etc/acpi/events/ibm-sleepbtn
# Called when the user presses the sleep button

event=ibm/hotkey HKEY 00000080 00001004
action=/etc/acpi/actions/suspend.sh

```
and also 
```

# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/actions/suspend.sh

```

why I have two files doing the same thing I don't remember. 

Now when I suspend using the suspend option in the shutdown menu it suspends fine, but when I press the sleep button it suspends it TWICE, ie on resuming it suspends it again...

I therefore replaced the two above files by:

```
# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

# event=button[ /]sleep
# action=/etc/acpi/sleepbtn.sh
```

and

```
# /etc/acpi/events/ibm-sleepbtn
# Called when the user presses the sleep button

event=ibm/hotkey HKEY 00000080 00001004
action=/etc/acpi/sleepbtn.sh

```

but it still suspends TWICE..I don't seem to see why:confused:? I don't think it will be anything too subtle I just don't see what it is..

Thanks a lot!

---

### Post by Grizzlitiger on 2008-06-28
OK it's resolved now, I just deleted my file under /etc/acpi/actions :)

---

### Post by 1jackjack on 2008-07-15
hey, im using a dell xps m1330, with ubuntu 8.04 and looking for a suspend/sleep command that i can attatch a hotkey to...

is /etc/acpi/sleep.sh an executable that puts your computer to sleep? or do you have to do something weird with event=xxx action=xxx ?

thanks,
Jack

---

