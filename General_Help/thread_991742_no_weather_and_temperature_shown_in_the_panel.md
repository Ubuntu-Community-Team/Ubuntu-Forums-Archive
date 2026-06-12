---
title: "no weather and temperature shown in the panel"
date: 2008-11-24
forum: General Help
---

### Post by chunchengch on 2008-11-24
I am using Ubuntu 8.10 and have checked the "show weather" and "show temperature" in the clock preference setting window, but they do not show in the panel, does anyone has this problem? and how can this be fixed?

Thanks for reply.

[ATTACH]93935[/ATTACH]    [ATTACH]93936[/ATTACH]

---

### Post by blazemore on 2008-11-24
I don't know if this is supported. I've always assumed it isn't.
Unless it shows it in the calendar (when you click the time).

You could always get a screenlet or something, or maybe there's a gnome panel applet somewhere to do the trick.
Maybe you should look into writing one, since you want it.

---

### Post by swoody on 2008-11-24
Have you added your location into the "Locations" tab in "Clock Preferences"? It will only display the temp and weather info for the "Locations" you have added. If your exact city isn't listed, just select the closest one.

---

### Post by blazemore on 2008-11-24
You'd think it would use the city you selected during installation.

---

### Post by swoody on 2008-11-24
Well, as far as I know, the city selection in installation is just to get your time zone correct. The weather info is MUCH more accurate, and has MANY more choices for locations. While a person in Miami can select New York in the installation to get the proper time zone, the weather is not even close ;)

---

### Post by chunchengch on 2008-11-24
> **woody86 said:**
> Have you added your location into the "Locations" tab in "Clock Preferences"? It will only display the temp and weather info for the "Locations" you have added. If your exact city isn't listed, just select the closest one.

Yes, I do add the the location in "Clock Preferences" as I did in 8.04 and 7.10, but I only got this problem in 8.10, it is really weird.

---

### Post by swoody on 2008-11-24
Have you tried adding other locations nearby? Is it just your specific location that won't show the info, or will it not show the info for any location?

---

### Post by swoody on 2008-11-24
Try adding the weather-report applet to your panel. Right-click on it, and select "Update" (strange, but it may make the clock weather work :))

If that doesn't get your weather working in the clock, enter this in a terminal: 
```
sudo dpkg-reconfigure tzdata
```
and make sure the timezone is set to your city. Then reboot.

---

### Post by Hated On Mostly on 2008-12-20
> **woody86 said:**
> Try adding the weather-report applet to your panel. Right-click on it, and select "Update" (strange, but it may make the clock weather work :))

If that doesn't get your weather working in the clock, enter this in a terminal: 
```
sudo dpkg-reconfigure tzdata
```
and make sure the timezone is set to your city. Then reboot.


Thanks, that command fixed the "weather not being displayed" bug for me in 8.10 (Intrepid Ibex). Even though my settings were correct, it wouldn't display until I ran that command.


No need to reboot.

Just refresh the gnome panels after running the command woody86 posted:

```
killall gnome-panel
```

---

