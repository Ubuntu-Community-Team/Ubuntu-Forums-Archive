---
title: "fan stopped working"
date: 2012-04-20
forum: Hardware
---

### Post by frrobert on 2012-04-20
I am running  Ubuntu 10.04 on a 1000HA eee.  Everything has been fine but now my fan does not run at all.

If I do sensors my fan is listed but if I do a pwmconfig I get a There are no working fan sensors, all readings are 0. error.

 The fan has worked fine in the past and its speed always showed in conkey.

Any ideas on what I need to change to get the fan to turn on?

---

### Post by newbie-user on 2012-04-20
Before changing stuff in the OS, I'd recommend opening up the case to see if the fan is clean and that it's power cable is still connected to the motherboard. That way you can rule out stuff that's easy to fix and you don't have to worry about messing with the system settings.

---

### Post by Yellow Pasque on 2012-04-20
> **frrobert said:**
> Everything has been fine but now my fan does not run at all.
Did this happen after a kernel update?

> If I do sensors my fan is listed but if I do a pwmconfig I get a There are no working fan sensors, all readings are 0. error.

That is normal for laptops, which generally use ACPI to control fan.

---

### Post by frrobert on 2012-04-20
Yes,

It did stop after a kernel update.

---

### Post by MonkeyPaw on 2012-04-20
More than likely, just sitting at your BIOS configuration screen will trigger the fan, and the fan should spin up at first power-on and then slow down. Can you hear it do that? If not, I think your fan may have failed or clogged with dust.

---

### Post by frrobert on 2012-04-21
I made changes to grub and the fan is now running.
I changed 
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
```

It is running 100% of the time with the change.  The speed does not show up in conky as it has in the past.  So I still have issues but I would rather have a fan running too much rather than not at all.

---

