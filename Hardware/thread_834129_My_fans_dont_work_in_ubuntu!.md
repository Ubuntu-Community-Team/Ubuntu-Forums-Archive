---
title: "My fans dont work in ubuntu!"
date: 2008-06-19
forum: Hardware
---

### Post by Clockswork on 2008-06-19
I installed Ubuntu last night coz I was so tired of Vista everything worked fine although I did happen to notice how hot my computer got!

I put my hand under the fan and just as I thought there was no air coming out of there. 

So how can I monitor my fans? I have a Dell Xps m1530! Please help!

Edit: And by the way what is a normal temperature for a Dual 2 core processor on 2.10 ghz?

---

### Post by TubaTodd on 2008-06-19
> **Clockswork said:**
> I installed Ubuntu last night coz I was so tired of Vista everything worked fine although I did happen to notice how hot my computer got!

I put my hand under the fan and just as I thought there was no air coming out of there. 

So how can I monitor my fans? I have a Dell Xps m1530! Please help!

Edit: And by the way what is a normal temperature for a Dual 2 core processor on 2.10 ghz?

You probably want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

```


install package: lm-sensors

run: sensors-detect
I answered "yes" to all of their questions

run: pwmconfig
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add
/usr/sbin/fancontrol &
to rc.local
```


I've kept that bookmarked in Firefox for a while. My Sony Vaio desktop runs full speed unless I follow these easy steps. 

BTW, it doesn't say in the instructions, but you MAY need to reboot before you run "pwmconfig"

---

### Post by Clockswork on 2008-06-19
> **TubaTodd said:**
> You probably want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

```


install package: lm-sensors

run: sensors-detect
I answered "yes" to all of their questions

run: pwmconfig
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add
/usr/sbin/fancontrol &
to rc.local
```


I've kept that bookmarked in Firefox for a while. My Sony Vaio desktop runs full speed unless I follow these easy steps. 

BTW, it doesn't say in the instructions, but you MAY need to reboot before you run "pwmconfig"


When I run sensors-detect and answer the questions I get "Sorry, no sensors were detected..."

And when I run pwmconfig I get /usr/sbin/pwmconfig: No sensors found! (Modprobe sensor modules)?

---

### Post by TubaTodd on 2008-06-19
ok...did you try rebooting AFTER installing lm-sensors? I know I had to reboot somewhere in the process because of a "no sensors" error. I just don't remember when.

---

### Post by Clockswork on 2008-06-19
> **TubaTodd said:**
> ok...did you try rebooting AFTER installing lm-sensors? I know I had to reboot somewhere in the process because of a "no sensors" error. I just don't remember when.

Yes I did still no dice

Any more advice I really dont want to go back to windows :(

---

### Post by TubaTodd on 2008-06-19
try...

```
sudo sensors
```

and see if you get any results. Also check out this how-to

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by sdennie on 2008-06-19
A reasonable temperature for an idle Core 2 Duo is probably around 40C depending on the ambient temperature of the room (and whether or not you are obstructing the fans by having the laptop on your lap).  If it's under load or the ambient temperature is very high, it can get much hotter than that.  You should be able to see the current temperature with:

```

acpi -t

```

---

