---
title: "HAL on NEC Versa L2200"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by Triorph on 2007-11-01
Hi, I'm having some problems with HAL on my laptop. 

Originally this problem occurred to me in feisty when i was using ubuntu-backports repositories. For some reason my acpi's battery settings don't show straight away, you have to unplug (or plug in) the adaptor AFTER you boot, so if its already in when you boot, it doesn't show in the gnome-icon. Kind of annoying but not the big problem here. When the feisty-backports updated to a new version of HAL, whenever i did this it would make all the inputs (touchpad, keyboard) grind to a halt and be impossible to use. Simple solution was to remove the backports-repository and downgrade the version of HAL. 

However now i've done a fresh install of gutsy on my laptop and the version of HAL it comes with seems to cause this problem to happen aswell. 

When running hal-device-manager it shows both the ac-adaptor and battery as not present even when it is, however if i unplug it, the console has loads of output talking about all kinds of things being suddenly disconnected (inputs aswell as battery and ac-adaptors)

any thoughts on how to fix this (I'd prefer not to have to downgrade to feisty again)

---

### Post by Triorph on 2007-11-01
Playing around with this some more, it doesn't happen at all when acpid is turned off. I can also have it happen then turn HAL off, then reload HAL (have to have the command to turn HAL off ready otherwise its too laggy to do)

I've tried playing around with the event files from acpid, but disabling to plain removing all of its ac adaptor plugged in and battery mode enabled events hasn't fixed this issue. Can anyone think of any events that may be caused from removing or plugging in an ac-adaptor apart from /etc/acpi/events/ac and /etc/acpi/events/battery

Even though i've deleted all the events, the battery meter will only say thats its changed from charging to discharging mode in the speech bubble if acpid is on.

---

