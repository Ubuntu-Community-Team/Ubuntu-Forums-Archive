---
title: "Installing Ubuntu on ASUS A6RP-AP069 notebook"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by chopeen on 2006-11-27
You can read about problems encountered and solved (!) while installing Ubuntu 6.10 (Edgy Eft) on ASUS A6RP-AP069 notebook here:

[http://chopeen.blogspot.com/2006/11/installing-ubuntu-on-asus-a6rp-ap069.html](http://chopeen.blogspot.com/2006/11/installing-ubuntu-on-asus-a6rp-ap069.html)


Or you can read a raw (no formatting and no links! just copied&pasted it) version below:

There were three problems that me and my girlfriend encountered while installing Ubuntu 6.10 (Edgy Eft) on ASUS A6RP-AP069 notebook.

   1. Starting the installation
      There was no problem to boot the laptop from the Ubuntu CD, it showed the available option, but after choosing any of them it... froze after a few seconds.
      We tried 3 or 4 different version of Ubuntu and Mandriva. Every time it hung as soon as Using hpet for high-res timesource message showed. (It is worth noticing that Ubuntu 6.10 does not show such information to the user by default, while its older version do.)
      We found the solution here - adding hpet=disable to the kernel parameters worked like a charm.

   2. Connecting to the wireless network
      Ubuntu correctly detected the wireless card. We entered all necessary configuration parameters (SSID, key, etc.), activated the card and... it couldn't connect to the network no matter how many time we re-checked its configuration and restarted it.
      Finally, we found this post. It's really great! We followed the instructions and the WiFi network was up and running in no time.

   3. Enabling sound
      That was the hardest part. Everything looked fine - Ubuntu detected the sound card, Amarok looked like it was playing a song, but... there was no sound. We tried to play files in different formats, we checked the headphones, we found countless posts telling to uncheck some External Amplifier option in KMix, but we found no such option.
      Late at night after a lot of googling I (my girlfriend went to sleep earlier) found this post. Another great post! I recompiled alsa-driver, alsa-lib and alsa-utils packages and the sound problem was gone.

---

