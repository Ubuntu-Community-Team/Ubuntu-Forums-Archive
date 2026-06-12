---
title: "Desktop CPU fan always on high"
date: 2008-08-20
forum: Hardware
---

### Post by jointstereotype on 2008-08-20
**Update:** My bad; the problem was actually the fan on my nvidia gfx card (GeForce 8500 GT). I uninstalled the Ubuntu accelerated drivers, restarted and the fan was "normal" again. I then tried installing the official nvidia drivers, and they're working beautifully -- 3D / direct rendering seems to work, but without the fan running at full speed all the time. ;)

--

I bought a HP m8187c desktop (based on an Intel Core 2 Duo e6750, according to the GNOME System Monitor) earlier this year, and decided to give Ubuntu 8.04 a go yesterday. Things seem to be running smoothly except for the fact that the CPU fan seems to be "always on" / running loudly regardless of actual CPU load. Running "top" in a terminal shows no strenuous processes -- nothing above 2-3 percent -- and the PC's case is physically cool, not even warm. While running Windows Vista on the same machine, it's VERY quiet unless I'm doing audio/video editing and the like.

I've seen several posts about CPUs not stepping properly. I ran "acpi -V" in a terminal and got "No support for device type: thermal" if it's any help.

Does anyone have any suggestions as to how to get the PC to be quiet while running Ubuntu?

Thanks. :)

---

