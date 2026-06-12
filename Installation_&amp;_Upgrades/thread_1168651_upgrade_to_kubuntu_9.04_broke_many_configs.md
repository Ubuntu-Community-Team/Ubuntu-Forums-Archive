---
title: "upgrade to kubuntu 9.04 broke many configs"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by radiohacker on 2009-05-24
i've been running a kubuntu 8.04 system (which was originally ubuntu 8.04) and decided i wanted to use kde4 so i upgraded from 8.04 to 8.10 and then right away to 9.04.  it seems the upgrade broke just enough things to make it really annoying.  here's my list of broken things:

1. dual soundcards no longer work.  according to /dev/sndstat both cards are recognized but i can't set any apps to use anything other than the default alsa device.  and sometimes that doesn't even work.

2.  i no longer can modify my network settings.  before i had an static ip address.  when i rebooted networking didn't work.  the only way i was able to get networking to work was to delete all references to eth0 in my /etc/network/interfaces file.  now my system uses dhcp to get an ip address and i can't change it, when i bring up the "manage connections" dialog there isn't any connection listed.

3.  changing screensaver values has no effect.  even though the screensaver timeout is set to start after 120 minutes, the screensaver still kicks in after 15 minutes or so.  i've tried disablling the screenserver and turning off power management but all of these settings have no effect.

has anyone else seen these problems ?  

thanks.

craig

---

### Post by doomsword2001 on 2009-05-24
i had lots of problems on audio. from bad output till no output at all. i tried lot of things.
when i had no sound i uninstalled pulse audio, and now everything is ok.

i will have to inform you that if you uninstall pulse audio, ubuntu-desktop might be unistalled aswell, not a big deal and also you may install it again. i also think that compiz will be uninstalled automaticly aswell.

---

