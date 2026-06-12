---
title: "[SOLVED] Fujitsu Siemens Lifebook E8410, Brightness in Hardy"
date: 2008-08-08
forum: Hardware
---

### Post by Parama on 2008-08-08
[COLOR="Red"]**Nevermind this thread. I upgraded to Intrepid. Now the brightness is stuck on 100% but it's usable even thought the batteries run out in no time now.**[/COLOR]

Hi all,

I have a fresh install of Hardy on my Lifebook E8410 but I can't set the brightness which is too low - unless the surroundings are almost pitch black and my colleagues tell me I've taken the privacy filtering too seriously :)

From browsing these forums it seems a very common problem but none of the solutions seems to apply to my hardware.

Maybe I'm jumping to conclusions here but I guess I should get an array of digits showing the valid brightness levels when I do a 
```
sudo cat /proc/acpi/video/GFX0/LCD/brightness
```
but it just gives me a 
```
<not supported>
```
I don't have the directory /proc/acpi/video/VGA which is normally mentioned in the solutions.

I'm not sure if I should report this as a bug in launchpad.net.

Any input is apreciated.

---

