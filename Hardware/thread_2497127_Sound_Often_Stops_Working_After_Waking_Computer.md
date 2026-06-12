---
title: "Sound Often Stops Working After Waking Computer"
date: 2024-04-24
forum: Hardware
---

### Post by geeky-1 on 2024-04-24
My sound output often stops working after waking my computer. The mother board is an ASUS TUF Gaming X570-Plus WiFi with Realtek S1200A Codec. When I open the sound settings, the only output device is the HDMI/DisplayPort and the "Digital Output (S/PDIF) -Starship/Matisse HD Audio Controller" sound device is not shown. I'm on Ubuntu 22.04.4 LTS. The only solution I've found is to reboot.

---

### Post by lukyluke on 2024-07-22
I experience the same problem, in my case just issuing in the console, pulseaudio --start solves the issue. You might want to kill it before in case it does not with pulseaudio -k

Hope this saves you fom rebooting everytime

---

