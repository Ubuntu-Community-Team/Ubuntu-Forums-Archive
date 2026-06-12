---
title: "Closing lid on laptop -&gt; poweroff"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by caspian on 2005-04-26
I'm using a Toshiba Tecra M2. Whenever I close the lid on my laptop, it powers off. Is there a way I can change this? I'd like to get it to suspend when I close the lid... but if it just did nothing, that would be better than powering off.

I just started using Ubuntu... so I'm pretty much a newbie. I've been using Linux for several months... but I'm still learning :).

Thanks to anyone who can assist me!

---

### Post by dave9191 on 2005-04-27
Hey, I dont know why it powers off when you close the screen, you screen should be blanking instead. Maybe its a hardware bios feature/setting. So take a peak in your bios if there is anything about that. If not then feel free to modify (always backup first) the acpi scripts. They should be the ones controlling what happens when you close the lid, press the power button etc..

They are in /etc/acpi. Take a look at the lid.sh one in perticular. 

Hope it helps, 
Dave

---

### Post by caspian on 2005-04-27
Ok, I looked at /ect/acpi/lid.sh and found that it says to blank the screen when the lid is closed.

So, I tried closing the lid to see what happens again... and the screen just turned off. Ha! I've got no clue what its problem was before, but it works now.

Thanks!

 :grin:  :grin:

---

### Post by dave9191 on 2005-04-27
Glad it sorted :)

---

### Post by punkinside on 2005-05-01
hey all, I have a toshiba A70 laptop with the same problem, however I do not know how to change the setting so it just does nothing for when I change the lid: this is my lid.sh:

```
#!/bin/sh

. /usr/share/acpi-support/power-funcs

getXuser;

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        . /usr/share/acpi-support/screenblank
        echo `fgconsole` > $LIDSTATE
        chvt 12
else
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
                su - $user -c "xscreensaver-command -unthrottle"
        fi
        chvt `cat $LIDSTATE`
        su - $user -c "xscreensaver-command -deactivate"
fi

[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

where do I change the setting?! I dont know whats going on there...

---

### Post by dave9191 on 2005-05-01
If you want nothing to happen when you close the lid, just comment everything out in the lid.sh. (put a # at the start of every line).

---

### Post by punkinside on 2005-05-01
hey thanx worked like a charm! still does anyone know what was happening before? id really like to understand what was going on hope its not too much trouble  :)

---

### Post by dave9191 on 2005-05-01
Im sorry but I cant explain what was happening b4. I dont have that problem. But both of you have toshiba laptops, so maybe there is some bios power mangment thing happening there. Or just a miss detection / bad config for toshiba laptops. There are spesific scripts for toshibas around the ubuntu distro, and from the looks of things special acpi thingies for toshibas. Maybe theres is a problem in there somewhere. 

Maybe you would want to file a bug report on that.

---

### Post by punkinside on 2005-05-01
yeah there are a number of issues with Hoary mostly specific to toshiba laptops, like sound, things like suspend/hibernate and the alps touch pad. hope the guys working on breezy take care of this. However for the most part I havent had any problems that didnt get solved (so far) and my machine is working fine :)

---

### Post by dave9191 on 2005-05-01
Runs brilliantly on my sony laptop :D apart from the odd lock up when shutting down or hibernating. Rare but annoying.

---

