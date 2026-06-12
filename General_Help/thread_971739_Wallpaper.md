---
title: "Wallpaper"
date: 2008-11-05
forum: General Help
---

### Post by newkie on 2008-11-05
Hi, I'm using Ubuntu 8.10 amd64, and wanted to know whether to use a different wallpaper to each desktop. (use 4)
And i had installed the nvidea-xserver, but when I restart the computer, the resolution changes. How do I do to keep the high resolution?

---

### Post by empty_tank on 2008-11-05
use wallpapoz in order to have different wallpaper for every desktop

---

### Post by beercz on 2008-11-05
wallpapoz?

---

### Post by Simian Man on 2008-11-05
> **beercz said:**
> wallpapoz?

[There's this thing called Google...]("http://www.google.com/search?q=wallpapoz")

---

### Post by beercz on 2008-11-05
> **Simian Man said:**
> [There's this thing called Google...]("http://www.google.com/search?q=wallpapoz")
yeah, I know, I was just being lazy....

I will look at it later.

Thanks anyway :-)

---

### Post by drs305 on 2008-11-05
Here is the link. It isn't being developed any longer but still works very well for what you want:
[http://wallpapoz.akbarhome.com/index.html]("http://wallpapoz.akbarhome.com/index.html")

Click on the 'grab it' link to go to the download page, where you can download the .bz2 file.

You can also register (no cost) and get the .deb from:
[http://www.getdeb.net/app/Wallpapoz]("http://www.getdeb.net/app/Wallpapoz")

---

### Post by beercz on 2008-11-05
> **drs305 said:**
> Here is the link. It isn't being developed any longer but still works very well for what you want:
[http://wallpapoz.akbarhome.com/index.html](http://wallpapoz.akbarhome.com/index.html)

Click on the 'grab it' link to go to the download page, where you can download the .bz2 file.
Thanks drs305

---

### Post by newkie on 2008-11-07
And the problem with the resolution? have to change each time I turn the computer is very annoying. I squeeze (on nvidia x-server settings) "to save x configuration file" but when I restart the changes that I made just vanish.
What do I do?

---

### Post by drs305 on 2008-11-07
> **newkie said:**
> And the problem with the resolution? have to change each time I turn the computer is very annoying. I squeeze (on nvidia x-server settings) "to save x configuration file" but when I restart the changes that I made just vanish.
What do I do?

I am currently running 8.10 on an AMD64 machine, but of course the video card is probably the most important component for this issue. If you go to System, Administration, Hardware Drivers, do you have a proprietary nvidia driver enabled? For my setup, 2 are available (173 & 177) and the 177 has been very stable for me. Again, it depends on your card of course.

---

### Post by newkie on 2008-11-09
im noting having trouble with the driver itself. is the configure wich arent being save when i click save. i got two pvs and the two do the same thinger. (al two use nvidia drivers, and the other pc alredy are 4 years old.) how i change the resolution use the console? i was tinking in try to make something like a script to change the resolution front 1024x786 to 1280x1024 each time i turn my linux on.

---

### Post by fooman on 2008-11-09
you need to run nvidia-settings as root in order to make 'em stick:

```
gksudo nvidia-settings
```

---

### Post by newkie on 2008-11-09
¬¬
	
I tried to use this command, tried to run the command from a konsole as root and still the whole time I log-and log-in of the resolution falls again. I just noted that this problem of not save the setting also extends to the network card. I made a manual ip config on my pc but when I log-off it does not save anything ... Heck, this whole thing of root can, and cant do is starting to piss me off

---

### Post by newkie on 2008-11-09
hey, i try run "sudo nvidia-settings". it ask for password, then open the configure window but when i change the resolution (which work!) and CLICK IN THE 'SAVE DO X CONFIGURATION' the window closes and the console said "segmentation fault"

---

