---
title: "Shutdown on battery"
date: 2011-09-26
forum: Hardware
---

### Post by Retor on 2011-09-26
I'd like for the computer to shut down without the need for confirmation when the power source changes to battery. 

I found "battery" in /etc/acpi/events/ - Content: 


```

# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh

```

It points to  /etc/acpi/power.sh: 

```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then
    exit;
fi

pm-powersave $*

```

Not quite sure if this is the right place or what to put in it.

---

### Post by collisionystm on 2011-09-26
Try it and see what happens

---

### Post by Retor on 2011-09-27
But ... I don't know what to put in it :) 

Or what the stuff that is in it now means!

---

### Post by collisionystm on 2011-09-28
> **Retor said:**
> But ... I don't know what to put in it :) 

Or what the stuff that is in it now means!
<code>
#!/bin/sh  test -f /usr/share/acpi-support/key-constants || exit 0  . /usr/share/acpi-support/policy-funcs  if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then     exit; fi  pm-powersave $*
</code>

---

