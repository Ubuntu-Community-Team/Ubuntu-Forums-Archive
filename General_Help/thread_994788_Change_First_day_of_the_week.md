---
title: "Change First day of the week"
date: 2008-11-27
forum: General Help
---

### Post by gamx on 2008-11-27
I guess this must be an easy one... The thing is that I have my system set up in English and in the clock applet in Gnome the first day of the week is a Sunday (as it should be). I would like that Monday were the first day, so I changed the LC_TIME locale from en_US to es_ES which does the trick but now the clock applet (and all it has to do with the time) appears in Spanish. Is there a way (or a locale I guess) to have a week starting on Monday and still being able to have everything in English.
Thanks

---

### Post by mixmaster on 2008-11-27
Changing the locale will affect a lot of things ... you may also find that the numeric format goes from 1,000,000.000 to 1.000.000,000 which can be rather confusing.

I use Xfce which has a "first day of week" setting associated with the calendar preferences.  You might look somewhere like that.

---

### Post by Keyper7 on 2008-11-27
I think the gnome clock applet obeys the Evolution preferences.

Open Evolution and go to Edit > Preferences > Calendar and Tasks > General.

See if changing the settings there work (refresh the applet to be sure).

PS: it might take an entire day to check your reply to this, but I will

---

### Post by spiderbatdad on 2008-11-27
See which locale is running:
```
locale
```

In my  case it is en_us
Edit the file:
```
gksu gedit /usr/share/i18n/locales/en_US
``` At this section:```
week    7;19971130;7
first_weekday	**1**
first_workday	2
```I would change the first weekday to 2 to make it Monday.

EDIT: run```
sudo locale-gen
```to generate the new locale setting. Finally:```
killall gnome-panel
```to reload gnome-panel.
Credits to google and ubuntuforums archives:[http://ubuntuforums.org/archive/index.php/t-26409.html](http://ubuntuforums.org/archive/index.php/t-26409.html)

---

### Post by gamx on 2008-11-27
Thanks Spiderbatdad. Your suggestion did the trick!

Following another message in this thread, I wonder why the option to change the first day of the week in evolution is not tied to the clock panel too. After all both applications are intended to be integrated...

Gamx

---

### Post by Keyper7 on 2008-11-28
I wonder that too...

Lucky for you that someone appeared to correct my wrong suggestion... ;-)

---

### Post by javinovich on 2011-09-05
That suggestion of spiderbatdad did the trick.

I always blamed the clock applet about not managing locales properly but now that I edit the local file in my case en_AU (for Australia) I realize that the first day is incorrectly set to Sunday (the american way) instead of Monday as we use it here.

On the other hand I wonder why there is no easy way to tweak all those parameters from within the Ubuntu menus, hopefully Gnome 3 will fix that.

I am a little bit happier Natty user now.

Thanks,
Jav

---

