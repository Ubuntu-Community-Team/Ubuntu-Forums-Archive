---
title: "NVIDIA FX5200 VGA card driver problem .."
date: 2008-10-20
forum: General Help
---

### Post by amr_essam on 2008-10-20
Dear there,

i have a problem that's really annoying me
first of all , i have ubuntu 8.04 desktop version and i installed it inside windows.
but when i logged into it , the VGA driver wasn't recognized and the system told me that it has a driver for it :

- before i install this driver , the resolution was 800x600 , and i wasn't able to activate the high visual effects

-after i installed it , the resolution was reduced to 640x480 and the option of 800x600 disappeared but i can activate visual effects

please if anyone can tell me what i have to do , note that it's my first time on ubuntu

Thanks in advance

---

### Post by Hangwire on 2008-10-20
In the Terminal, type

```
sudo apt-get install nvidia-settings
```

Then go to System > Administration > NVIDIA X Server Settings.

It should look a lot like this (depending on your visual theme)
Click on X Server Display Configuration.

[IMG]http://i257.photobucket.com/albums/hh205/sturm31/Screenshot-NVIDIAXServerSettings.png[/IMG]

If the resolution you need is not listed in the Resolution part - Click Advanced, and you will see a small field opening up. Type the resolution you need there, click Apply and it should work. 

Then click Save to X Configuration File.


Good Luck! :)

---

