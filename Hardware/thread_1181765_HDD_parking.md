---
title: "HDD parking"
date: 2009-06-08
forum: Hardware
---

### Post by msutton86 on 2009-06-08
My hardrive is parking quite a bit so I issue 'sudo hdparm -B 255 /dev/sda' and the apm is turned off.  This fixed the over active clicking without a problem.  The problem is making this command register on boot.  I've tried multiple lines in hdparm to make this register on boot, but still nothing.  The following is a sample of my code both tried together and separate.

Changes in hdparm.conf
```

command_line {
   hdparm -B 255 /dev/sda
}
```

```
/dev/sda {
   apm = 255
}
```

I know the HDD isn't about to die like they are telling me on IRC, because I'm dual booting and in windows I'm not experiencing the parks.  Also I've tried multiple live boots and still no outrages parks like in ubuntu.  Anyone have any ideas because I'm stumped.

---

### Post by platinumriver on 2009-06-11
Did you ever figure this out? I am having the same problem. Can't Ubuntu be setup to park the drive only after X minutes of inactivity? Even Windows can do that :)

---

### Post by zgornel on 2009-06-11
> **platinumriver said:**
> Did you ever figure this out? I am having the same problem. Can't Ubuntu be setup to park the drive only after X minutes of inactivity? Even Windows can do that :)

Well, that's what the -B parameter does: adjusting the value adjusts the time of inactivity after wich the head is parked. Still, the time - parameter value relation is not quite documented :|

To run the hdparm command, try putting ```
hdparm -B 255 /dev/sda
``` in /etc/rc.local and reboot.

---

### Post by platinumriver on 2009-06-11
Hi zgornel,

The command works fine and it does stop the drive from clicking and parking itself. I tried to research a bit the hdparm -B parameter and you are right; I couldn't find the correlation between the parameter and the time. Is "hdparm -B 255 /dev/sda" persistent across reboots?

---

### Post by zgornel on 2009-06-12
> **platinumriver said:**
> Hi zgornel,

The command works fine and it does stop the drive from clicking and parking itself. I tried to research a bit the hdparm -B parameter and you are right; I couldn't find the correlation between the parameter and the time. Is "hdparm -B 255 /dev/sda" persistent across reboots?

It is not persistent unfortunately. If you put it inside /etc/rc.local, it should become 'persistent' (by executing it everytime at boot).

---

