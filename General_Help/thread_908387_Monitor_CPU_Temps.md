---
title: "Monitor CPU Temps"
date: 2008-09-02
forum: General Help
---

### Post by CarlosinFL on 2008-09-02
How can I monitor my CPU temperature in Ubuntu 8.04? I had an issue come up and my machine over heated and I have no way to tell how hot my machine is running unless I am booted into the BIOS.

Anyone have any suggestions to monitor CPU and air temps on my Desktop?

---

### Post by mellowd on 2008-09-02
conky

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)


You can get it like so:

```
sudo aptitude install conky
```

---

### Post by CarlosinFL on 2008-09-02
> **mellowd said:**
> conky

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)


You can get it like so:

```
sudo aptitude install conky
```

I tried for like a week to get the application to work and it never worked for me. Maybe I don't know how to configure the conkyrc file or something. I might try again if no other suggestions come up.

---

### Post by adult swim on 2008-09-02
you can use lm-sensors to detect your temperatures with a terminal
here is a tutorial of how to set it up
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by CarlosinFL on 2008-09-02
> **adult swim said:**
> you can use lm-sensors to detect your temperatures with a terminal
here is a tutorial of how to set it up
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Thanks. Will try and see if works.

---

### Post by Rhubarb on 2008-09-02
A much easier way:


Install lm-sensors, and sensors-applet:
```
sudo aptitude install lm-sensors sensors-applet
```


Let lm-sensors discover any temperature sensors you have in your PC:
```
sudo sensors-detect
```
Answer yes to any prompts there.


Reboot your computer.
Right click on an empty part of your gnome panel where you'd like the temperatures to be, Select "Add to Panel...".
Scroll down to "Hardware Sensors Monitor", click on it, then press the "Add" button.


You now have all the temperatures and fan speeds that lm-sensors has found.
To configure the applet, so you can add / remove more temperatures / fans, right click on it, and select "Preferences".

---

### Post by tuxxy on 2008-09-02
I would recommend both conky and lm-sensors, this way you can post the output of lm-sensors to conky allowing to constantly monitor the temps from your desktop without loading up a terminal.

---

