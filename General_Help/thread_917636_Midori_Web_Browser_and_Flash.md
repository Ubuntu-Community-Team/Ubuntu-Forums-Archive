---
title: "Midori Web Browser and Flash"
date: 2008-09-12
forum: General Help
---

### Post by lviggiani on 2008-09-12
Hi guys,
I've installed Midori web browser but I can get Flash contents working.
Following the wiki from the midori web site ([http://wiki.xfce.org/midori_faq](http://wiki.xfce.org/midori_faq))
I run it though a terminal by typing:

```
$ export MOZ_PLUGIN_PATH="/usr/lib/mozilla/plugins:/opt/mozilla/lib/plugins"
$ midori
```

but still no flash contents!
Where I do wrong?
Thanks!

---

### Post by fragos on 2008-09-12
Firefox, Epiphany and Midori apparently share the same flashplugin. I had installed "flashplugin-nonfree" to work with Epiphany. After installing "Midori" and doing nothing else flash worked in Midori.

---

### Post by elliah on 2008-10-30
i have flashplugin-nonfree installed but flash still doesnt work in midori..any help?

---

### Post by bojo42 on 2009-02-01
I had the same problem with Midori & Webkit from the Webkit Team's PPA on a minimal installation of Ubuntu. But on my desktop machine with Ubuntu 8.10 flash did work in Midori.

But after running ```
sudo update-alternatives --config mozilla-flashplugin
``` (even when it's useless when you only have flashplugin-nonfree) and ```
export MOZ_PLUGIN_PATH="/usr/lib/flashplugin-nonfree" && midori

``` it somehow worked. Seems that under some conditions Midori doesn't get the correct location of libflashplayer.so in Ubuntu 8.10.

---

### Post by fragos on 2009-02-01
On my system one install of flash worked with Firefox, Epiphany and Midori.

---

### Post by mehanika on 2009-06-04
I have flash working on midori, here's the solution: you have to download the lastest version of flash, untar the file libflashplayer.so on  ~/.mozilla/plugins (if there's no plugins' folder, create it) and use the same code but changin' the path to ~/.mozilla/plugins. That worked for me

---

### Post by cyb3rkn19ht on 2009-11-20
I have Ubuntu 9.10 with Midori repositories. I added the repositories by following [this tutorial]("http://ubuntuforums.org/showthread.php?t=1199960"). I did NOT install flashplugin-nonfree, I already had adobe-flashplugin.
```
export MOZ_PLUGIN_PATH="/usr/lib/mozilla/plugins:/opt/mozilla/lib/plugins"
```
Worked for me.

---

### Post by soulchainer on 2009-11-28
Ohmmm... the same problem here just a moments ago...
On my case the solution was a little... stupid xD
Open the ~/.config/midori/config and edit the line (you need to edit it with Midori closed)

```
enable-plugins=false
```
to
```
enable-plugins=true
```

Only copy libflashplayer.so and this.

Yes, is a stupid solution, but you need to figure out it xD The option isn't in any Midori menu. And for other options, like ask for destination folder for downloads, also needs to edit here.

Hope to it helps to anybody.

---

