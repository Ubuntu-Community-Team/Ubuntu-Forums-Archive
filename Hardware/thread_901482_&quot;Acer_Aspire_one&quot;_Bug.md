---
title: "&quot;Acer Aspire one&quot; Bug"
date: 2008-08-26
forum: Hardware
---

### Post by jrev on 2008-08-26
Hi,
If you buy the Acer Aspire one, be careful of your first step :

When you start this Netbook, don't select the language, the password or the geopraphic zone with your keyboard ! 
It will not be registered and you will get the default language i.e US english and default keyboard and the New York time 

Better choose those options with the touchpad or the mouse.

You will thus spare some discussions on the phone with the support service of Acer...
to find out the remedy.

[B]That's a bad bug for the newcomers to a Linux mini laptop 

[/B]

---

### Post by Chokkan on 2008-08-28
Wow! That a pretty big bug there isn't it. So what was the solution, just so others have it with a little less hassle?

---

### Post by jrev on 2008-08-29
The solution is there :

[http://forum.framasoft.org/viewtopic.php?t=29999&highlight=](http://forum.framasoft.org/viewtopic.php?t=29999&highlight=)

Do you need a translation ?

Just suppress the file oobe.log :

cd /usr/share/oobe
then :
rm oobe.log

Reboot your PC and start again to select the first 3 choices with the touchpad or mouse

[COLOR="Blue"]**Not with the keyboard ! **[/COLOR]
otherwise the selection is not registered and you have your PC with the default config which is :

English (eu), New York time etc.

---

