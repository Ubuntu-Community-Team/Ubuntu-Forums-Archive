---
title: "Ubuntu Gnome 17.04 Early 2015 Macbook Pro 5ghz Wifi not working"
date: 2017-07-28
forum: Hardware
---

### Post by ben5345323416 on 2017-07-28
I had this problem with my Early 2015 Macbook Pro running Ubuntu Gnome 17.04, I was only able to see 2.4ghz WiFi networks and unable to connect to 5ghz even by manually entering the SSID.

The solution was to disable "Explicit Beamforming" for the 5ghz interface on my DD-WRT wifi router.

After disabling Explicit Beamforming I was able to successfully connect to the 5ghz network without issues.

Hope this helps anyone else having the same problem.

---

