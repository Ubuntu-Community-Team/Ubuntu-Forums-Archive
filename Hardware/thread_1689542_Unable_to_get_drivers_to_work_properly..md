---
title: "Unable to get drivers to work properly."
date: 2011-02-16
forum: Hardware
---

### Post by CoNFUS3D on 2011-02-16
Hi, I have just installed Ubuntu 10.1. The drivers that have come with ubuntu, they are all glitchy etc. It skips and what not. I have tried installing the drivers for my c-media cmi8738 sound card, to no avail. Just wondering if anyone could please help me to figure out why it hasn't worked.

thanks :)

---

### Post by lidex on 2011-02-16
The alsa subsystem of the ubuntu kernel supplies the audio drivers. What exactly is skipping? Streaming audio? Mp3s? What programs?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by CoNFUS3D on 2011-02-16
sorry, mp3s skip, have not tried streaming yet... in all programs, have tried amarok, audacious and rhythmbox. Just tried videos, does the same thing. Tried vlc and movie player

here is the link to the alsa thing... [http://www.alsa-project.org/db/?f=17bacee770497ca30316ac3e9df1e69cf119f1f4](http://www.alsa-project.org/db/?f=17bacee770497ca30316ac3e9df1e69cf119f1f4)

---

### Post by lidex on 2011-02-17
Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html](http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html)

---

### Post by CoNFUS3D on 2011-02-17
I tried that, there is no load-module module-hal in the file.. 

EDIT:

ok, so I have done the first part, I have tried the usermod thing, says that group does not exist...

---

### Post by CoNFUS3D on 2011-02-17
*bump*


anyone?

---

### Post by CoNFUS3D on 2011-02-17
ok, so here is how it is, I have done all that... when I do the pulseaudio -k ; pulseaudio -D, it tells me that no such process exists, then says daemon startup failed....

---

### Post by lidex on 2011-02-18
How is the audio?

---

### Post by CoNFUS3D on 2011-02-18
I have still had no luck, I tried uninstalling pulseaudio, that didn't do anything, I tried all that stuff on that site, but it is still lagging :(, any ideas?

---

