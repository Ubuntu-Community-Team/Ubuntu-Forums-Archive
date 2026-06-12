---
title: "laptop-mode help"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by landwomble on 2006-07-19
Hi All,
Now got everything working on my X31 in Ubuntu - but to extend battery life I was looking at the laptop-mode tools.
I can run this using "sudo laptop-mode start" fine, but how do I set it to run this automatically every time the laptop is on battery power?  Ideally I'd like it to automatically switch to laptop mode whenever the mains isn't connected.

Any tips?
Ric

---

### Post by mpvano on 2006-07-19
One normally doesn't directly interact with laptop-mode in Dapper or Breezy. It's handled by the acpi and suspend/resume scripting. However, it's initially disabled because it can be dangerous for a couple of reasons.

1. Make sure everything else is stable and that you're never seeing any unusual freezes or other crashes before enabling it, so that you can tell if it's introducing problems of that sort itself.

2. Be aware, that crashes and freezes are slightly more likely to cause losses of information because laptop mode delays disk writes for a much longer time than is normal in linux. If you crash with unwritten data that's important to a a program, you may lose a database or corrupt a config file in such a way that things can become unusable.

Having said all that, it works great for me, and I have enabled it for several weeks now.

Using sudo, edit the last line of /etc/default/acpi-support to uncomment the following (and make sure it says "true" after the equal sign). Then reboot. Laptop mode should be automatically enabled when running on battery power and disabled when you go back to AC operation.

ENABLE_LAPTOP_MODE=true


The way I work, it adds about 20 minutes to my T30 run time on batteries. It can add a lot more time depending on how busy you normally keep the CPU and file system while running on batteries.

Good luck with it...

Mario

---

### Post by landwomble on 2006-07-19
this isn't filling me with confidence!  if it's buggy, i'd rather avoid, i guess.  does dapper (i'm on 6.06) do someform of power saving of it's own?  acpi is working, i guess, as suspend works fine on fresh install...

---

### Post by eurgain on 2006-07-19
This is just U being conservative.  It is not buggy - it just does not work well for some folk. The whole thing is that laptop mode *inherrently* increases risk of data loss because it saves power by increasing write-back times.  If your system is stable, this will probably not be a problem (and enabling laptop mode will not make any difference). OTOH, if you have crashes, laptop mode will cause you problems, because more cached data will be lost.

A

---

### Post by mpvano on 2006-07-19
I agree with eurgain.

I didn't mean to frighten you off of using it. I was just suggesting you shouldn't consider using it until your system is running stably FIRST.

THEN try it. If you experience system lockups on resumes after enabling it (most people don't), then I'd stop using it!

Mario

---

### Post by a-nubi-s on 2006-07-20
I prefer the way my laptop runs with laptop-mode enabled - cooler, quieter. Can I have it on all the time, even when plugged in?

---

### Post by stimpsonjcat on 2006-07-20
> **a-nubi-s said:**
> I prefer the way my laptop runs with laptop-mode enabled - cooler, quieter. Can I have it on all the time, even when plugged in?
sure. edit /etc/laptop-mode/laptop-mode.conf to include ENABLE_LAPTOP_MODE_ON_AC=1

---

### Post by a-nubi-s on 2006-07-20
Thanks :)

---

### Post by landwomble on 2006-07-22
> **mpvano said:**
> 
Using sudo, edit the last line of /etc/default/acpi-support to uncomment the following (and make sure it says "true" after the equal sign). Then reboot. Laptop mode should be automatically enabled when running on battery power and disabled when you go back to AC operation.

ENABLE_LAPTOP_MODE=true



OK, tried this.  it's disabled my wireless card, or at least at exactly the same time it's stopped working.  putting the line above back to the default "false" hasn't restored it either...aaaargh, any suggestions?

---

### Post by mpvano on 2006-07-23
I'm guessing it's coincidence, but anything's possible.

Putting it back would completely undo any effect it has after the next reboot.

You do realize that changing that line only has an effect when you restart, however. After you put it back did you reboot?

Did you change ANYTHING ELSE at the same time? (Note that I did not suggest enabling it on AC - that was someone else - I have no experience with the change he suggested).

Before too much time goes by, I suggest taking a look at the entries in the system and daemon logs. /var/log/messages, /var/log/syslog, and /var/log/daemon.log. There's a lot of information there to sort through, and some of the things that look like error messages you see there are not a problem, but see if you find anything relevant.

Otherwise, assume it's coincidence and go back to standard wireless troubleshooting:

- tell us your exact hardware and exact wireless card
- tell us your exact OS version
- tell us what kind of router you are trying to connect to
- tell us what security method your router uses.
- tell us what you are trying to use for a "network manager"
- show us what the following commands display

cat /etc/iftab
cat /etc/network/interfaces
sudo iwconfig
sudo ifconfig
sudo iwlist scan


You might be able to troubleshoot the network problem yourself by starting a terminal, running the command "tail -f /var/log/messages" and watching what happens when you try to connect to your wireless network. If nothing interesting shows up there, try "tail -f /var/log/daemon.log" or better yet, watch both at the same time in two different terminal windows....

Mario

---

