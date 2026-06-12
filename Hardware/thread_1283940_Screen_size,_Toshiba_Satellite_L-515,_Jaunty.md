---
title: "Screen size, Toshiba Satellite L-515, Jaunty"
date: 2009-10-06
forum: Hardware
---

### Post by angellika on 2009-10-06
Hi There,
 
every time I switch on my laptop I have to change screen resolution from 800 x 600 to desired (1360 x 760). It is quite annoying and totally time wasting:7 I have Jaunty and it 
does not detect my Monitor. It looks that I am missing the driver. this i got from terminal *lshw*:
 
PHP Code:

[LEFT][COLOR=#000000][COLOR=#007700]*-[/COLOR][COLOR=#0000bb]display[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]1 UNCLAIMED[/COLOR][/COLOR][/LEFT]
[COLOR=#000000]
[LEFT][COLOR=#0000bb]description[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]Display controller[/COLOR]
[COLOR=#0000bb]product[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]Mobile 4 Series Chipset Integrated Graphics Controller[/COLOR]
[COLOR=#0000bb]vendor[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]Intel Corporation[/COLOR]
[COLOR=#0000bb]physical id[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]2.1[/COLOR]
[COLOR=#0000bb]bus info[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]pci[/COLOR][COLOR=#007700]@[/COLOR][COLOR=#0000bb]0000[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]00[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]02.1[/COLOR]
[COLOR=#0000bb]version[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]07[/COLOR]
[COLOR=#0000bb]width[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]64 bits[/COLOR]
[COLOR=#0000bb]clock[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]33MHz[/COLOR]
[COLOR=#0000bb]capabilities[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]bus_master cap_list[/COLOR]
[COLOR=#0000bb]configuration[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]latency[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0 [/COLOR][/LEFT]
[/COLOR]
 
The other problem is that the icons in upper panel are totally changed as you see in the picture ([http://imagebin.ca/view/3g9Lls.html](http://imagebin.ca/view/3g9Lls.html)). I mean the Application is on the right side and I want to be where it was by default. It was changed by this resolution problem. Also the icons in the desktop are every times changed. How can i changed the position of Application, Places and System?
 
[IMG]http://imagebin.ca/view/3g9Lls.html[/IMG][IMG]http://imagebin.ca/view/3g9Lls.html[/IMG]
 
can anyone please try to help me? thanks, jaro

---

### Post by pratt92000 on 2009-10-17
well you are doing better then i . i cant get any bigger then 800x600. ubuntu in an ald toshiba TE2000. i have tried to add new resolution with out any luck.

---

### Post by angellika on 2009-10-19
> **pratt92000 said:**
> well you are doing better then i . i cant get any bigger then 800x600. ubuntu in an ald toshiba TE2000. i have tried to add new resolution with out any luck.

it really sucks. nobody cares about this thread. I am sending it second time. I hope it will be working with Koala:)  800 x 600 must be really ****.

Try this in terminal 

xrandr --output LVDS --mode 1360x768

it should change your resolution, but u will have to use it every time you switch off and switch on your machine.

have a look here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) if it is not working.

good luck

---

### Post by felipe51 on 2009-10-20
One of the reason related to your display resolution problem could be current max display resolution.
please try: 1366 x 768
instead of: 1370 x 768

rembember to backup your xorg.conf


add the following subSection inside your section "Screen"

```
SubSection "Display"
 Depth 24
 Modes "1366x768"
EndSubSection
```

if it doesn't work, attaching the content of your "xorg.conf" to this thread would be of great help.

best regards
Felipe

---

### Post by felipe51 on 2009-10-20
Also consider figuring out your **HorizSync** and **VertRefresh**, you could figure thos values, executing on a console the following command 

```
sudo ddcprobe
```


if you need to install it enter:

```
sudo apt-get install xresprobe
```


check the output of the command:

```
sudo ddcprobe
```

at the end of the output it should say **monitorrange:**
*example:* **monitorrange: 28-72, 43-60**

**28-72** correspond to your monitor **HorizSync**
**43-60** correspond to your monitor **VertRefresh**

please backup your **xorg.conf** and edit xorg.conf adding the lines below to the section "Monitor" with your corresponding values of **HorizSync** and **VertRefresh**

```
Section "Monitor"
 Identifier "Configured Monitor"
 **HorizSync** **28-72**
 **VertRefresh** **43-60**
EndSection
```

Best regards,
Felipe

---

### Post by BitJunkie on 2009-10-20
Maybe this thread will be of some help.

[http://ubuntuforums.org/showthread.php?t=1256607](http://ubuntuforums.org/showthread.php?t=1256607)

---

### Post by angellika on 2009-10-20
Dear Felipe,

I did what you suggested and it is working now. Honestly thanks a lot
because I was having this problem for last two months. 

My xorg.conf now looks like:
  
[php]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

SubSection "Display"
 Depth 24
 Modes "1366x768"
EndSubSection[/php]

This is not important since everything works but when I used *sudo ddcprobe* I did not get information about monitorrange. This is what I got:

[php]vbe: VESA 3.0 detected.
oem: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Cantiga Graphics Controller Hardware Version 0.0
memory: 131008kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 3441
eisa: SEC3441
serial: 00000000
manufacture: 0 2008
input: analog signal.
screensize: 30 17
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1366x768@59
monitorid: SAMSUNG
monitorid: 140AT04-T01[/php]


Thank you very much :)

Jaro

---

### Post by angellika on 2009-10-21
> **angellika said:**
> Dear Felipe,

I did what you suggested and it is working now. Honestly thanks a lot
because I was having this problem for last two months. 

My xorg.conf now looks like:
  
[php]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

SubSection "Display"
 Depth 24
 Modes "1366x768"
EndSubSection[/php]This is not important since everything works but when I used *sudo ddcprobe* I did not get information about monitorrange. This is what I got:

[php]vbe: VESA 3.0 detected.
oem: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Cantiga Graphics Controller Hardware Version 0.0
memory: 131008kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 3441
eisa: SEC3441
serial: 00000000
manufacture: 0 2008
input: analog signal.
screensize: 30 17
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1366x768@59
monitorid: SAMSUNG
monitorid: 140AT04-T01[/php]Thank you very much :)

Jaro


Unfortunately it was not working on the second day:( , but BitJunkie thread made it works. 

[http://ubuntuforums.org/showthread.php?t=1256607](http://ubuntuforums.org/showthread.php?t=1256607)

I switched off and switched on computer two times, just make sure:) and it is still working so far. 

Now I have these lines in xorg.conf

[php]Section "Device"
    Identifier    "Configured Video Device"
        Option          "Monitor-LVDS"     "Laptop LCD"
        Option          "Monitor-TV"       "TV"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "Laptop LCD"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Monitor"
    Identifier    "TV"
    Option        "Ignore" "True"    
EndSection

Section "Screen"
    Identifier    "Default Screen"
     Monitor        "Laptop LCD"
    Device        "Configured Video Device"
EndSection
[/php]I hope it will work tomorrow :)

Thanks to everyone,

Jaro

---

### Post by BitJunkie on 2009-10-21
> **angellika said:**
> I hope it will work tomorrow :)

I made this change 6 or 7 weeks ago and my L505 has been working ever since. So hopefully, yours will be OK tomorrow too. :)

---

### Post by angellika on 2009-10-23
> **BitJunkie said:**
> I made this change 6 or 7 weeks ago and my L505 has been working ever since. So hopefully, yours will be OK tomorrow too. :)

It is still working. So, this thread is solved and I have now more free time to waste :) 

Thank you very much,

Jaro

---

