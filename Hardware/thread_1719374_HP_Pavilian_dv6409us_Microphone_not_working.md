---
title: "HP Pavilian dv6409us Microphone not working"
date: 2011-04-01
forum: Hardware
---

### Post by Techie141 on 2011-04-01
Hi, I have an HP Pavilian dv6409us that was broken two times, and was fixed, but after i upgraded to Ubuntu 10.10,my microphone stopped working, I hope that someone can help me! :D:D:D:D:D:D:D THX

---

### Post by lidex on 2011-04-02
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
No help? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

