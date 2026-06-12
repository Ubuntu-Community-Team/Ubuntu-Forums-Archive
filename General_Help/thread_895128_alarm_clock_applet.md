---
title: "alarm clock applet"
date: 2008-08-19
forum: General Help
---

### Post by trash on 2008-08-19
I found it extremely hard to find a good SIMPLE alarm clock
Out of the 5-6 i tried AlarmClockapp was the simplest.

[http://www.gnomefiles.org/app.php/AlarmClockApp](http://www.gnomefiles.org/app.php/AlarmClockApp)

I am running Xubuntu/Hardy, I have XfApplet(which allows you to add gnome applets to xfce pannel) installed from universe repo.

The Gutsy deb wasn't available so i did download the source, which installed fine using the install instuctions.

just thought I would let others know about this nice little program:)

---

### Post by adarkmethod on 2008-08-26
[http://www.gnomefiles.org/app.php/Alarm_Clock](http://www.gnomefiles.org/app.php/Alarm_Clock)

works in gutsy gnome atleast

unpack, open terminal, type "cd /path/to/folder", press enter, type "sudo python setup.py install"

---

### Post by trash on 2008-08-26
cool, i'll give it a try soon:)

---

### Post by hotdoog on 2009-07-29
This is a way better program IMO than the default one in the Repos simply named "Alarm Clock"

I was using that one for a while on my travelling netbook because I couldn't remember the name of this one --- it's a pretty generic title, Google under pseudoberries (the makers) to find anything relevent. I had to ask my wife back at home to tell me the exact name of the program so I could install this here. (yes, my ssh isn't working right now)

What I like about this is the interface. Simple. Useful. You can re-use old alarms (the biggest lack in the other "Alarm-Clock" package) is this. Also, it is an easy to "install" applet so you don't need to put it in your list of gnome start up programs, you can hover over the icon to get a quick countdown on your alarms... I'm so glad I finally got this one working tonight. I'm actually using it as a wakeup alarm clock and it now matters to me that the program be fully functional.

Thanks VERY much to the software authors!:KS

---

### Post by larytet on 2009-08-20
or
```

crontab -e 

```

for command line oriented guys

For example, to open [http://ubuntuforums.org/](http://ubuntuforums.org/) 4 times a week at 18:15

```

DISPLAY=:0.0

# m h  dom mon dow   command
# 10 bis 
  15 18 *  *   sun,mon,tue,wed,thu     /usr/bin/firefox http://ubuntuforums.org/

```


Use ```
echo $DISPLAY
``` to figure out your current display settings

---

### Post by luc765 on 2009-11-01
Hello,

You can find the package deb alarmclockapp_0.1.3-1_i386.deb to the following address :

[http://users.skynet.be/linux-rixensart/app61_banque.html#alarmclockapp](http://users.skynet.be/linux-rixensart/app61_banque.html#alarmclockapp)

The package is in English even if the text that accompanies is in French

Regards,


Lucien

---

### Post by tich on 2010-04-12
does anyone know if there is a deb for alarm clock 1.3 for 64bit?

---

