---
title: "No sound on resume"
date: 2008-08-26
forum: General Help
---

### Post by Lovok on 2008-08-26
I have checked with Google, and the top most links are all out of date.
When I leave my computer be and it goes into sleep mode, I will loose sound on the resume. 
I use Edubuntu 8.04.1, updated, using on board sound with ALSA. Sound works fine on reboot, but doesn't after resuming from sleep.

Doing :
```

sudo mkdir /var/run/alsa
sudo /etc/init.d/alsa force-reload
sudo /etc/init.d/alsa resume

```
doesn't work.

---

