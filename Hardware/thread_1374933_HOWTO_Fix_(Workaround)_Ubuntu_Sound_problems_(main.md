---
title: "HOWTO: Fix (Workaround) Ubuntu Sound problems (mainly on HDA Intel)"
date: 2010-01-07
forum: Hardware
---

### Post by proxess on 2010-01-07
First add this to add model auto to your alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
```
options snd-hda-intel power_save=10 power_save_controller=N **[COLOR="Red"]model=auto[/COLOR]**
```
Find the corresponding line and add the model text.

Create a script that will restart pulse and alsa:
```
gksu gedit /home/<USERNAME>/.fix_sound
```
```
#!/bin/bash
killall pulseaudio
alsa force-reload
sleep 2
killall pulseaudio
```

Make it executable:
```
chmod +x /home/<USERNAME>/.fix_sound
```

Make it so that ubuntu doesn't ask for your password when you run the script on startup:
```
sudo visudo
```
```
%<USERNAME> ALL=NOPASSWD: /home/<USERNAME>/.fix_sound
```

and then add the script as this to Startup Applications as such:
```
gksu /home/<USERNAME>/.fix_sound
```

Your sound will be muted when you start up.

---

