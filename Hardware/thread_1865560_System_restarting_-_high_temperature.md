---
title: "System restarting - high temperature?"
date: 2011-10-20
forum: Hardware
---

### Post by orrymr on 2011-10-20
Hi all,

My computer has been restarting of its own volition today, and I'm not quite sure why. I'm running an Core 2 duo system with 2 gigs of ram. When I checked out the BIOS after a reboot, my cpu die/package temp was 68.6c. I've been looking around the net, and can't find a definitive answer about whether or not this is within the acceptable range of temperatures.

Could this be the reason why my system is rebooting?

---

### Post by northd_tech on 2011-10-20
If you are running the GNOME desktop, I would definitely install the Gnome Sensors Applet- mine is 'front & center' on my Panel at the top of my screen between the menus and the battery icon/clock.  I watch mine often.  I also have the CPU Frequency Scaling Monitor right next to that so I can watch how hard my CPU's are 'grunting.'

[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

I believe that you will need the lm-sensors package installed before the Gnome Sensors Applet is installed to get it to work.

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

I find it easiest to just install "lm-sensors" and "sensors-applet" packages in Synaptic Package Manager to obtain these.

Depending upon how your BIOS settings are configured, I would think that excessive temperature could definitely get an Operating System to quit (but I would expect a Shutdown in that case, not a Restart- hmmm....) :confused:

---

### Post by orrymr on 2011-10-20
Looks like both my cores are in the mid to high forties (celcius), and my gpu is steady at about 42.

I guess temperature isn't the problem. (I did open up my case and put a fan in front of it, and it's still restarting).

---

### Post by diasf on 2011-10-20
The whole "put a fan in front of it" doesn't necessarily help.

Monitor the temperatures and check if the system fans are working. Up to 70C is fine, maybe even a bit more if gaming. (80C is too much usually).

Other than that you prolly wanna check the /var/log/syslog and dmesg, tho I'm fairly certain you need to check the directory (/var/log) to get a version that isn't limited to the last boot. (aka after the problem happened)

---

### Post by northd_tech on 2011-10-20
I also forgot to mention that many people are quite fond of Conky for monitoring.  As I understand, with the right scripts and configuration you can get Conky to do just about anything short of washing your dishes and socks for you. ;)

[IMG]http://conky.sourceforge.net/conky.png[/IMG]

[http://conky.sourceforge.net/aboutconky.html](http://conky.sourceforge.net/aboutconky.html)

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Edit:  Just as a guess- are you sure that your power supply isn't the one getting hot (and maybe dropping your bus voltage too low, forcing a restart like the old "reset" button on the old XT/AT PC's)?  Just a possibility...

---

### Post by orrymr on 2011-10-20
Thanks for all the suggestions guys :smile:

Well, I think the reason the CPU temp could've been quite high is because I was doing some stuff in octave; the temperatures are around 50 deg now.

I've changed my multiplug and it hasn't rebooted yet, so hopefully the problem was as simple as a faulty multiplug. I'm busy using lm-sensors, but I think I'll install conky as well; it looks pretty cool :P

---

### Post by diasf on 2011-10-20
Just keep in mind that the temperature drops quite fast after it reboots itself.... so by the time it boots again, you log in, and check, the temperature could've dropped significantly

---

