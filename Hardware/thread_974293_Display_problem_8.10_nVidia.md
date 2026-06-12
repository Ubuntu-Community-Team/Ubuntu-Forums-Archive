---
title: "Display problem 8.10 nVidia"
date: 2008-11-07
forum: Hardware
---

### Post by dafi on 2008-11-07
Under 8.10 64bit nVidia driver 177.80 Thunderbird tooltips contain random pixels as shown in picture

[[IMG]http://img386.imageshack.us/img386/750/schermatapf9.png[/IMG]](http://imageshack.us)
[[IMG]http://img386.imageshack.us/img386/schermatapf9.png/1/w408.png[/IMG]](http://g.imageshack.us/img386/schermatapf9.png/1/)

---

### Post by garyedwardjohnston on 2008-11-07
I randomly got this for a bit too.  It wasn't with just tooltips though, mostly firefox.  Mine went away after 1/2 a second though.

If yours is staying like that, try taking a look into changing setting for tooltips through compiz first, then metacity.

I need a lot more info about what you're running to be more specific.

---

### Post by dafi on 2008-11-07
> **garyedwardjohnston said:**
> I randomly got this for a bit too.  It wasn't with just tooltips though, mostly firefox.  Mine went away after 1/2 a second though.

If yours is staying like that, try taking a look into changing setting for tooltips through compiz first, then metacity.

I need a lot more info about what you're running to be more specific.

I've Compiz running with "low level" effect.

How can I give you more details (config files or other system settings) ? 

thanks

---

### Post by dafi on 2008-11-09
I've removed the 'New wave' theme (from community-themes package) restoring the default one and now all works fine

---

### Post by rubberglove on 2008-11-14
> **dafi said:**
> I've removed the 'New wave' theme (from community-themes package) restoring the default one and now all works fine

This same problem has been bugging me for a while now, and your post was the hint I needed to fix it!

I replaced the image used to theme the tooltips (/usr/share/themes/NewWave/gtk-2.0/Images/Others/tooltips.png), reloaded the theme, and now the tooltips in thunderbird work.

The original image was a thin grey border, with the rest transparent, so my replacement tooltips.png is simply all transparent. Now tooltips in thunderbird are working properly with compiz + NewWave (my favourite theme).



Actually, it looks like the NewWave theme in the 'community themes' package is just not up to date? 
It seems like they fixed this issue in NewWave -- if you download the theme directly from [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave") everything works!

---

