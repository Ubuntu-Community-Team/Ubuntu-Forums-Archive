---
title: "UPower does not register the closed lid"
date: 2011-02-01
forum: Hardware
---

### Post by mitrg on 2011-02-01
I am on Alienware M15X, Ubuntu 10.10. My Gnome Power manager does not work properly because UPower daemon does not register that the lid closed after first suspend/resume. This also contradicts to what acpi says.

> yes "upower --dump | grep lid-is-closed; cat /proc/acpi/button/lid/*/state; sleep 2" | sh  

  lid-is-closed:   yes
state:      closed
  lid-is-closed:   yes
state:      closed

After suspend/resume:

  lid-is-closed:   no
state:      closed
  lid-is-closed:   no
state:      closed

acpi correctly says "state: closed", while upower says "lid-is-closed: no".

Tried to dig for 4 hours, but could not solve this...

---

