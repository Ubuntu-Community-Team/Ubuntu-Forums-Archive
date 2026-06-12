---
title: "Logitech USB headset not working with 12.04/Gnome Classic"
date: 2012-09-27
forum: Hardware
---

### Post by ShadowVegan on 2012-09-27
I recently upgraded from 10.04 to 12.04. My Logitech USB headset always worked fine. Now in 12.04 it is not working. In sound settings, it shows up under 'Hardware' but it does not show up under 'Output' or 'Input'. In 10.04 it showed up in all three tabs, allowing me to switch from internal speakers/mic to the USB headset in the input/output tabs. As far as I remember I never had to install any driver but I'm not 100% sure.

---

### Post by ShadowVegan on 2012-09-28
I figured it out. For anyone with similar issues, I temporarily had my built in speakers disabled then when I tried to re-enable them it didn't work. So I realized it's not an issue with my headset, and did some further looking. I found [this]("http://ubuntuguide.net/sounds-both-from-headphones-and-speakers-ubuntu-12-04") and entered
```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```After restarting my computer, speakers and headset work.

---

### Post by ShadowVegan on 2012-09-29
My headset stopped working again, and my regular speakers don't work either. I tried entering the same code as last time and it's not helping this time. Any ideas? I miss 10.04, nothing ever went wrong. :/

Edit: Restarted computer, unplugged headset and now it's working again. I'd still like to find out why it sometimes doesn't work, if anyone has any ideas. It seems to be software related rather than hardware.

---

