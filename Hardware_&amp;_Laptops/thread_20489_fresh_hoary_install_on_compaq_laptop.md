---
title: "fresh hoary install on compaq laptop"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by andyk on 2005-03-17
well i've been a devoted ubuntu user for oh....3 weeks now.  and i'm a total convert.  started with warty, and with how easy it was i went for hoary.  and for a preview release it is far more stable then some companies, ahem "service packs"  this is a quick overview of the install.

compaq 2108us
amd athlon xp-m 2.1ghz
512mb ram / 40gb hd
broadcom wifi (94306 chipset)

1-during warty install i had to turn acpi off.  hoary installed with acpi on
2-network config for eth0 gave me issues because i had no eth.cable plugged in soi skipped it.
3-no other issues during install.

the two really non issues i had were with ndiswrapper and restart.

**for ndiswrapper:  **go to /etc/apt/sources.list and uncomment the extra repositories.  

in terminal do an apt-get update.

apt-get install ndiswrapper-utils

ndiswrapper -i "your driver.inf"

ndiswrapper -m

modprobe ndiswrapper

network settings and configure wlan0 and activate.

edit /etc/modules and add ndiswrapper to the bottom of the list.

now for me this next step was needed for hoary but not warty:

edit /etc/ndiswrapper/"yourdriver" config file.  find "radio state" and change to 0.
(thanks to munki for showing me that one !!)

save and restart.

i also had restart issues.  for some reason logout --->restart wasn''t working, it would just hang.  i had to go to the hotplug blacklist and add pciehp to it.  save and restart.

i know this is basic and doesn't say alot but i think that it's a testiment to ubuntu.  somebody finally got linux right.  bill is finally put on notice.

andy

---

### Post by munki on 2005-03-25
> 
edit /etc/ndiswrapper/"yourdriver" config file.  find "radio state" and change to 0.
(thanks to munki for showing me that one !!)


Glad I could help you :)

---

### Post by fizgig on 2005-03-25
That ndiswrapper post helped me out too.

---

