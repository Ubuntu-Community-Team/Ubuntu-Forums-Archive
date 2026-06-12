---
title: "Making a script run when a USB key stick is inserted"
date: 2008-06-14
forum: Hardware
---

### Post by randysparks on 2008-06-14
Making a script run when a _**particular**_ USB key stick is inserted (not just ANY USB stick)... Is it possible?

---

### Post by hyper_ch on 2008-06-14
yes it is... somehow... the usb stick will have a partition and that partition will have a UUID and you need to check somehow if the stick insered has the UUID... there is a way but I forgot where that is... something with dev rules or so...

---

### Post by randysparks on 2008-06-14
> **hyper_ch said:**
> yes it is... somehow... the usb stick will have a partition and that partition will have a UUID and you need to check somehow if the stick insered has the UUID... there is a way but I forgot where that is... something with dev rules or so...

:) That's exactly what I was thinking, but I'm in the same boat. I need to get the UUID and then create a UDEV rule. But how?

---

### Post by hyper_ch on 2008-06-14
well, go to /dev/disk/by-uuid --> there you have all devices listed. For my usb stick its:

```

lrwxrwxrwx 1 root root  10 2008-06-14 11:25 3025-6247 -> ../../sde1

```

And for writing UDEV rules, there's information out there ;)

---

### Post by randysparks on 2008-06-14
> **hyper_ch said:**
> well, go to /dev/disk/by-uuid --> there you have all devices listed. For my usb stick its:

```

lrwxrwxrwx 1 root root  10 2008-06-14 11:25 3025-6247 -> ../../sde1

```

And for writing UDEV rules, there's information out there ;)

Thanks, but I'm not sure how much closer I am to solving this with that information. All you've given me are the UUID numbers. I can get that by inserting the USB stick and searching log files. 

And I can try creating UDEV rules from scratch but I still don't know where they're stored, or how they should be structured. And there's little point in struggling if somebody else has already discovered how to do this. So I'm still looking for help, if anybody has it.

---

### Post by lswb on 2008-06-15
Here's a pretty good tutorial on writing udev rules: 

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

You can look in /etc/udev/rules.d to see the rules that are already on your system.
By using the uuid that a previous poster mentioned, in an appropriate udev rule, a script for just that particular disk can be run.

---

### Post by madgrt on 2008-11-11
> **randysparks said:**
> Making a script run when a _**particular**_ USB key stick is inserted (not just ANY USB stick)... Is it possible?

Did you workout a solution Randy? I was having a look at the same thing today.

---

### Post by cudjoe on 2008-12-22
A simple way to do it is to put a "autorun.sh" file in the USB hard drive root folder.

If you want to keep your main script on your computer, then just put this on your USB key :

autorun.sh :
```

#! /bin/sh
cd ~
yourscript.sh

```

---

