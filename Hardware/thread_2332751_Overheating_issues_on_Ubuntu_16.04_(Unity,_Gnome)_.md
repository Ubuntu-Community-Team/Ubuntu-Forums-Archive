---
title: "Overheating issues on Ubuntu 16.04 (Unity, Gnome) and LinuxMint"
date: 2016-08-03
forum: Hardware
---

### Post by dlalonde2 on 2016-08-03
Hello

My laptop suffers overheating issues on Ubuntu 16.04, on both Unity and Gnome as well as on LinuxMint when the lid is closed and it's completely idle. I've tried tlp, laptop-mode, no luck. The top command doesn't show me anything particular either.

The graphic card is an Intel and the problem occurs with both the default and the proprietary driver. My fans are clean and the problem doesn't occur on Windows.

So I'm wondering what I can do. I've found intel_pstate but it's from a 2014 article so is it still relevant? Otherwise what could I do? I wouldn't want my computer damaged. 

I've seen things that allow me to monitor the temperature but given the overheating only occurs on idle, that's not really useful.

Thanks!

---

### Post by yoshii on 2016-08-03
Overheating is usually indicative of a hardware failure, not operating system, nor standard programs.  
Laptops in general are usually prone to overheating because of their many inherent design flaws related to dissipating heat effectively.  
Some manufacturers are better than others at preventing overheating and cooling accessories are available such as fan pads that the laptop sits on to be cooled, but even those can't help a whole lot after the temp gets too hot internally.  

Some HP computers were specifically built for resistance to heat, vibrations, and moisture.  That's the only brand I trust anymore outside of brands marketed to hard hat construction workers.  I've had a lot of laptops overheat and die completely, so I looked into this.  Since I changed to the right HP models, I haven't had any issues, even with aan older used computer.  

Dell's in particular I don't trust because I took an old Dell apart after it died and I discovered that it's internal cooling system was really weak and primitive and destined to fail.  
Since I have some electronics repair experience and training, I could see what was wrong with it.  

The other thing is, life is hot!  A lot of places are just too hot for computers... being in the sun, hot apartments, being inside of hot cars, and their cooling systems are usually easily blocked unless the computer is elevated enough and on a hard flat surface and away from walls or pillows.  

Also if you have pets or smoke or live in a place that is dusty, there's a lot of that stuff that builds up inside the computer and blocks the fans and their paths and makes the CPU's overheat.  This is true for desktops also.  But desktops are much easier to take apart and clean out.

---

### Post by gordintoronto on 2016-08-04
Have you installed lm-sensors and run sensors-detect? What do you consider an overheating issue? Have you installed any temperature monitoring software in Windows?

---

### Post by dlalonde2 on 2016-08-04
> **yoshii said:**
> Overheating is usually indicative of a hardware failure, not operating system, nor standard programs.  
Laptops in general are usually prone to overheating because of their many inherent design flaws related to dissipating heat effectively.  
Some manufacturers are better than others at preventing overheating and cooling accessories are available such as fan pads that the laptop sits on to be cooled, but even those can't help a whole lot after the temp gets too hot internally.  

Some HP computers were specifically built for resistance to heat, vibrations, and moisture.  That's the only brand I trust anymore outside of brands marketed to hard hat construction workers.  I've had a lot of laptops overheat and die completely, so I looked into this.  Since I changed to the right HP models, I haven't had any issues, even with aan older used computer.  

Dell's in particular I don't trust because I took an old Dell apart after it died and I discovered that it's internal cooling system was really weak and primitive and destined to fail.  
Since I have some electronics repair experience and training, I could see what was wrong with it.  

The other thing is, life is hot!  A lot of places are just too hot for computers... being in the sun, hot apartments, being inside of hot cars, and their cooling systems are usually easily blocked unless the computer is elevated enough and on a hard flat surface and away from walls or pillows.  

Also if you have pets or smoke or live in a place that is dusty, there's a lot of that stuff that builds up inside the computer and blocks the fans and their paths and makes the CPU's overheat.  This is true for desktops also.  But desktops are much easier to take apart and clean out.

No I've checked for my fans like I said. And this only happens when on Linux. My Windows doesn't overheat.

> **gordintoronto said:**
> Have you installed lm-sensors and run sensors-detect? What do you consider an overheating issue? Have you installed any temperature monitoring software in Windows?

I haven't put lm-sensors because I don't want to know the temperature of my computer but rather why it's hot. Will those tell me? Also I haven't put anything of the sort on Windows because it doesn't overheat. What I consider an overheating issue is that, when I open my laptop lid, my keyboard and computer is hot whereas on Windows it's cool.

---

### Post by QIII on 2016-08-04
Hello!

What is the model of your machine?  Is the fan running when the machine is hot?

Using sensors will give you an objective measure of temperature.  Otherwise how do you know it's hot beyond your subjective experience?  What tool are you using to tell if the machine is at idle?

---

### Post by dlalonde2 on 2016-08-04
> **QIII said:**
> Hello!

What is the model of your machine?  Is the fan running when the machine is hot?

Using sensors will give you an objective measure of temperature.  Otherwise how do you know it's hot beyond your subjective experience?  What tool are you using to tell if the machine is at idle?

It's an HP EliteBook 8440p. The fan doesn't run. But I have no other indication other than feeling and there's a clear increase in Ubuntu vs Windows. 

If I understand correctly, the best thing would be to install sensors that will tell me whether it's too hot or just hotter?

---

### Post by Yellow Pasque on 2016-08-04
> **dlalonde2 said:**
> It's an HP EliteBook 8440p.

If you have the Nvidia GPU, that's the first thing I would suspect. You can find some power management tips here: [https://nouveau.freedesktop.org/wiki/Optimus/](https://nouveau.freedesktop.org/wiki/Optimus/)

---

### Post by dlalonde2 on 2016-08-04
> **Temüjin said:**
> If you have the Nvidia GPU, that's the first thing I would suspect. You can find some power management tips here: [https://nouveau.freedesktop.org/wiki/Optimus/](https://nouveau.freedesktop.org/wiki/Optimus/)

Unfortunately I checked that but I have the Intel Graphic Card. Is there maybe a driver I can get without using the default one or the one in the "Additionnal Drivers" section?

---

### Post by QIII on 2016-08-04
> **dlalonde2 said:**
> The fan doesn't run.

Ding, ding!  We have a winner!  :)

This is what needs to be sorted out, then.  We need to see why that isn't running.  

Some models of computers are actually designed so that the OS (Windows) controls fan speed rather than the motherboard.  That may not be the case here, but there are sometimes reasons why fans don't run with Linux.  I had an older Dell laptop with Fedora on it.  I had to install and configure i8kutils.

Let me do some poking around.

Edit:  I am going to be in and out for a while.  This sort of thing is often solved using lm-sensors and fancontrol.  lm-sensors, of course, provides the sensing.  fancontrol allows you to detect pwm fans that can be controlled and then configure some control.  I have to step away for now, but hopefully someone else will be able to step in.

---

### Post by Yellow Pasque on 2016-08-05
Usually, the fan shuts off when the lid is closed (i.e. laptop is in suspend). As far as I can tell from OP's description, that's the only time it's overheating.

As for fancontrol, it doesn't usually work on laptops in my experience (laptop often uses ACPI to control the system fan).

---

### Post by CatKiller on 2016-08-05
As far as I can tell, we haven't actually established that the laptop does go into suspend when the lid is closed under Linux.

---

### Post by mook765 on 2016-08-05
Found this thread here on the forum
> [https://ubuntuforums.org/showthread.php?t=1313895](https://ubuntuforums.org/showthread.php?t=1313895)


---

### Post by dlalonde2 on 2016-08-05
> **QIII said:**
> Ding, ding!  We have a winner!  :)

This is what needs to be sorted out, then.  We need to see why that isn't running.  

Some models of computers are actually designed so that the OS (Windows) controls fan speed rather than the motherboard.  That may not be the case here, but there are sometimes reasons why fans don't run with Linux.  I had an older Dell laptop with Fedora on it.  I had to install and configure i8kutils.

Let me do some poking around.

Edit:  I am going to be in and out for a while.  This sort of thing is often solved using lm-sensors and fancontrol.  lm-sensors, of course, provides the sensing.  fancontrol allows you to detect pwm fans that can be controlled and then configure some control.  I have to step away for now, but hopefully someone else will be able to step in.

Well that's quite possible given as I've noticed yesterday that, on Windows, my fans runs on and off (while I'm using it mind you).

> **Temüjin said:**
> Usually, the fan shuts off when the lid is closed (i.e. laptop is in suspend). As far as I can tell from OP's description, that's the only time it's overheating.

As for fancontrol, it doesn't usually work on laptops in my experience (laptop often uses ACPI to control the system fan).

I selected to do nothing when the lid is closed and it's on AC so there's only the screen that shuts off. 

> **CatKiller said:**
> As far as I can tell, we haven't actually established that the laptop does go into suspend when the lid is closed under Linux.

Indeed it doesn't ;)

> **mook765 said:**
> Found this thread here on the forum

I'll try that as well then, thanks! :)

I'll keep you posted, thanks for your help!

---

### Post by dlalonde2 on 2016-08-07
Alright thanks everyone! I've added both this ([https://ubuntuforums.org/showthread.php?t=1313895&p=8646540#post8646540](https://ubuntuforums.org/showthread.php?t=1313895&p=8646540#post8646540)) and I've ran lm-sensors and it seems to have solved the problem. It's been running for two day with the lid down and it's not as hot. 

Thanks guys! :)

---

