---
title: "How do I set up external monitor for laptop?"
date: 2011-02-14
forum: Hardware
---

### Post by pagunston on 2011-02-14
I have Ubuntu installed on my Asus F3sg Laptop although I want to plug in my Benq Fp92W LCD monitor to use as an alternative display. What is the best way to set this up? I managed to do this with the Nvidia X server settings although after a reboot, I need to reconfigure the settings. I am fairly new to Linux therefore reconfiguring every time I reboot is not an option because it usually takes me at least ten minutes just to get everything right. Basically, I want to be able to use my monitor as the primary display however I would also like to be able to unplug the monitor and automatically use the laptop LCD whenever I need to move the laptop.

---

### Post by jerrrys on 2011-02-16
sounds like you need to save your settings

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=save+edited+Nvidia+X+server+settings&as_qdr=all&sa=Google+Search&lang=en#1049](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=save+edited+Nvidia+X+server+settings&as_qdr=all&sa=Google+Search&lang=en#1049)

---

### Post by pagunston on 2011-02-16
> **jerrrys said:**
> sounds like you need to save your settings

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=save+edited+Nvidia+X+server+settings&as_qdr=all&sa=Google+Search&lang=en#1049](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=save+edited+Nvidia+X+server+settings&as_qdr=all&sa=Google+Search&lang=en#1049)

I clicked the save settings button and this appeared: Failed to parse existing X config file '/etc/X11/xorg.conf'!

---

### Post by jerrrys on 2011-02-16
have you tried this ?

[ATTACH]183670[/ATTACH]

found that here

[http://www.google.com/search?client=ubuntu&channel=fs&q=Failed+to+parse+existing+X+config+file+%27%2Fetc%2FX11%2Fxorg.conf%27&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Failed+to+parse+existing+X+config+file+%27%2Fetc%2FX11%2Fxorg.conf%27&ie=utf-8&oe=utf-8)

---

### Post by pagunston on 2011-02-16
So I managed to save the settings and now when I boot up, the monitor automatically detects the display. There is another issue though. My desktop seems to be bugged. There is two layers for the wallpaper as you can see in the attached image. How do I fix this? 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=183674&d=1297907436

---

### Post by jerrrys on 2011-02-16
check screen resolution

---

### Post by pagunston on 2011-02-16
Resolution is Auto. I tried all the other possibilities though this didn't change the overlapping wallpaper.

---

### Post by jerrrys on 2011-02-16
are you using compiz / if so, turn it off and see

---

### Post by pagunston on 2011-02-16
How do I turn off Compiz? Sorry.

---

### Post by jerrrys on 2011-02-16
system>preference>appearance>visual effect>none

---

### Post by pagunston on 2011-02-16
Did that but it made no difference.

---

### Post by pagunston on 2011-02-16
Ok, I fixed it by turning on only the External monitor and disabling the Laptop monitor. All settings have also saved successfully for rebooting. 

Thanks.

---

### Post by jerrrys on 2011-02-16
glad to hear that and future background reference

[ATTACH]183676[/ATTACH]

---

