---
title: "wrong video resolution toshiba 1400-s151"
date: 2008-05-21
forum: Hardware
---

### Post by john182 on 2008-05-21
I installed ubuntu 8.04 and my video resolution is set to 800x600 and i can´t modify it, and days ago i first installed ubuntu 7.04 and the resolution was ok, 1024x768, i uninstalled it cause a bad installation, i need also windows xp to do some work.

so i donwloaded the new ubuntu version and i´ve found threads on google that helps to solve the problem but doesn´t work on ubuntu 8.04

please if someone can help me find an answer.

the video card installed is: trident video accelerator cyberblade xp ai1 v6.4022-016b.22icdnp

---

### Post by overdrank on 2008-05-21
> **john182 said:**
> I installed ubuntu 8.04 and my video resolution is set to 800x600 and i can´t modify it, and days ago i first installed ubuntu 7.04 and the resolution was ok, 1024x768, i uninstalled it cause a bad installation, i need also windows xp to do some work.

so i donwloaded the new ubuntu version and i´ve found threads on google that helps to solve the problem but doesn´t work on ubuntu 8.04

please if someone can help me find an answer.

the video card installed is: trident video accelerator cyberblade xp ai1 v6.4022-016b.22icdnp

Hi and could you tell us what you have tried to adjust your resolution? Like reconfigure your xorg?

---

### Post by john182 on 2008-05-21
i´m a newbie at linux stuff, i found a thread about using sudo gpedit/etc/11/xorg.cong i think that was it but when i tried that i recieved a message at the terminal that host "name" could not be reached.

i really don´t know how to configure xorg, i can work on linux but it is annoying that i can work at only one little space in my screen

---

### Post by overdrank on 2008-05-21
> **john182 said:**
> i´m a newbie at linux stuff, i found a thread about using sudo gpedit/etc/11/xorg.cong i think that was it but when i tried that i recieved a message at the terminal that host "name" could not be reached.

i really don´t know how to configure xorg, i can work on linux but it is annoying that i can work at only one little space in my screen

Ok I have not used that card but some user's have been able to change the default depth from 24 to 16 and has help. This link has some good info 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by auriza on 2009-06-14
I also have **Trident Cyberblade XPAi1** on my Toshiba Satellite 1800 laptop.
To fix the video resolution to 1024*768, you have to edit **xorg.conf** file manually.

Open the Terminal (Application --> Accessories --> Terminal), and type:
```
sudo gedit /etc/X11/xorg.conf
```This will open up xorg.conf file in text editor. 

Replace the content of the file with the following text:
I got it from: [http://ubuntuforums.org/showpost.php?p=5039883&postcount=12](http://ubuntuforums.org/showpost.php?p=5039883&postcount=12)
```

Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Generic Monitor"
    Device        "Trident Microsystems CyberBlade XPAi1"
    SubSection "Display"
           Depth 8
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 16
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 24
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 32
           Modes "1024x768"
    EndSubSection
EndSection
```Don't forget to add newline (press ENTER) at the end of the file before saving.

I have tested it in Ubuntu 9.04 and it works! Hope this will help.

---

### Post by jagland on 2010-08-29
That also worked with a Toshiba Portege 2000 running Ubuntu Netbook Remix. Simply insert that as /etc/X11/xorg.conf 

:)

---

### Post by whiskers751 on 2012-04-06
Also try on GitHub: Toshiba-Portege-4000-Tools and look in the screen folder!

---

