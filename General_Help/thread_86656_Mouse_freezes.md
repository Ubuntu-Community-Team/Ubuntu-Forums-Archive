---
title: "Mouse freezes"
date: 2005-11-06
forum: General Help
---

### Post by alley on 2005-11-06
I was waiting for an update that fixes my problem, but since it seems it will not come... I'll try my luck with some experts here...

I have a amd64 desktop machine with a logitech usb optical mouse.
On every cold boot of ubuntu, the mouse freezes after seconds. As long as I keep moving it around, it won't freeze, but if I leave it alone for a few seconds, it freezes.

If I switch to another shell (ie. ctrl+alt+f5) and then back again, the mouse works again for a few seconds.

I also tried booting with acpi off, but if I do that, my system completely freezes as soon as the login screen appears (the little sound that plays at the login screen gets in a loop and nothing else works then).

---

### Post by nightfly on 2005-11-06
What is the make/model of your motherboard ?

Does this problem occur in other Linux distributions or is it specific to Ubuntu ?

When the mouse is in the freezing state. Is the optical light underneath the mouse still lit ?

> I also tried booting with acpi off

This is not sufficient to turn off power management, as the APM subsystem will be used in this case instead.

---

### Post by alley on 2005-11-07
[QUOTE=nightfly]What is the make/model of your motherboard ?
[/QUOTE]
It's an asus a8v-e
[QUOTE=nightfly]Does this problem occur in other Linux distributions or is it specific to Ubuntu ?
[/QUOTE]
I haven't tried other distro's but it didn't happen in hoary.

[QUOTE=nightfly]When the mouse is in the freezing state. Is the optical light underneath the mouse still lit ?
[/QUOTE]
Yes. If I try to reboot hotplug from the commandline, most of the times it fails and then the light does stay out. However, the very few times it *does* restart, the mouse won't freeze any longer for that session.

[QUOTE=nightfly]This is not sufficient to turn off power management, as the APM subsystem will be used in this case instead.[/QUOTE]
Ok, just read that some guys had some success with mouse-weirdness when they turned this off.

---

### Post by nightfly on 2005-11-07
The source of the problem is possibly Xorg. 

There are chances the kernel is cutting off the mouse, here is how to verify:
Open up a terminal, type the following
```
sudo cat /dev/input/mice
```

Then move the mouse, you should see some gibberish on the terminal as you are moving any of the mice attached to your computer. Hit CTRL-C to close. Then you might want to reset the terminal (Terminal -> Reset).

Test the above before the mouse freezes and when the mouse freeze. Even though the pointer is not moving, you might still see some gibberish as in the first time.

Please report.

---

### Post by alley on 2005-11-12
Hi, sorry for my late response, been away for a couple a'days.
I tested the cat .. when the mouse works I indeed see garbage on my screen.
When it's frozen, nothing happens at the terminal.... no garbage.

---

### Post by stormoog on 2006-01-16
I have the same problem with the mouse, and I do get the garbage. I read somewhere that it might be a kernel problem, but I'm not sure if it applies to my situation.

---

