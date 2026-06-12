---
title: "ubuntu Temperature shutdown"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by mcfly2309 on 2007-05-26
hola, i want to know if anyone has had this problem and what does it mean: i downloaded the text installation ubuntu 7.04 for amd64 because i have an athlon64 3000+ cpu and when the installation started, i got an error message about a critical temperature shutdown (85°C) i couldn't read the whole thing because it was too fast and then i didn't try to install it again... :( i worry about this problem because i wonder if it could have damaged the hardware and i bought this pc only 1 month ago. is it possible that linux makes hardware burn or cause any other hardware problems for disk drives and such? or do linux disributions only change how the "software" works?

---

### Post by bunny rabbit on 2007-06-01
Hi I have the same thing. I'm running Dapper. It happens fast. In my case what I could read was: "critical temperature" and a temperature of -10 Celsius. Surely there is no way that that's correct.
When I look in KSystemlog it says:
------------------------
01-06-07 09:58:13	localhost	none	-- MARK --

01-06-07 10:00:22	localhost	init	Switching to runlevel: 0

01-06-07 10:00:22	localhost	kernel	[17257889.616000] Critical temperature reached (98 C), shutting down.

01-06-07 10:00:22	localhost	sensord	Sensor alarm: Chip it8712-isa-0290: -12V: -3.06 V (min = -12.63 V, max = -11.41 V) [ALARM]

01-06-07 10:00:22	localhost	sensord	Sensor alarm: Chip it8712-isa-0290: +3.3V: +6.56 V (min = +3.14 V, max = +3.46 V) [ALARM]

01-06-07 10:00:22	localhost	sensord	Sensor alarm: Chip it8712-isa-0290: -5V: -2.83 V (min = -5.26 V, max = -4.77 V) [ALARM]

01-06-07 10:00:22	localhost	sensord	Sensor alarm: Chip it8712-isa-0290: VCore 1: +1.34 V (min = +1.42 V, max = +1.57 V) [ALARM]

01-06-07 10:00:22	localhost	sensord	Sensor alarm: Chip it8712-isa-0290: VCore 2: +1.22 V (min = +2.40 V, max = +2.61 V) [ALARM]

01-06-07 10:00:22	localhost	shutdown[15370]	shutting down for system halt

01-06-07 10:00:24	localhost	gconfd (ruben-5529)	Gestopt

01-06-07 10:00:24	localhost	gconfd (ruben-5529)	Signaal 15 ontvangen, normale afsluiting

01-06-07 10:00:26	localhost	sensord	sensord stopped

01-06-07 10:00:28	localhost	kernel	[17257895.636000] Critical temperature reached (-10 C), shutting down.
---------------------------------

I guess there is something wrong with the configuration but for the rest I have no clue because I'm very new to the linux and all.
Allso, I'm running boinc all the time which means that my CPU's allways are at about 94% nice load. According to what I see when I run sensors in terminal their temperature really is about 35 C. (big heatsink)
But then, in 'sensors'  those voltages don't seem okay to me. 
Maybe I should uninstall sensord in the synaptic. Sensord seems to be messing things up.
):P

---

### Post by mcfly2309 on 2007-06-07
well, isn't there an answer then?

---

### Post by 444 on 2007-06-07
I guess bunny rabbit can remove sensord as a quick and dirty fix... Or you can adjust sensors.conf to the proper values... the problem is that it's reading the wrong sensors and using outdated values for the vcore (1.5v is for the old Athlons, 1.35v is for the new ones). There is no way your system would even be running with wacked-out 12/3.3/5 values like that, it's reading them wrong.

mcfly2309, I'm pretty sure nothing happened to your hardware, it's probably misreading them as well. Dunno how exactly to solve the problem if you didn't even get to install yet though...

---

### Post by allcazar2 on 2007-06-08
Have the same problem, AMD64 on laptop.
Solved it to put under the computer a cooling-cell from the freezer. 
A bit stupid to install Ubuntu like that, but at least it keeps the temperature down. 

If it works.  It works.

Jurgen

---

### Post by jcankrom on 2007-06-22
I just had this problem occur on my HP Pavilion ze4315 laptop during startup. 
"Critical temperature reached (120 C)"
it was a cold startup, so i know its not really 120C. it must be misreading the temperature sensors. i had this problem once before, right after installing feisty in early May. its worked fine since (a little hotter than windows, but it hasn't shut down for that reason)
i discharged the battery almost completely when i was last using it, now i'm starting it on AC power, could this issue be related to charging?

um, setting the laptop on an icepack really isn't a fix.
Jeff

---

### Post by jcankrom on 2007-06-27
just an update: reinstalling (or rather using the "fix a broken system" option from the text install cd) fixes this issue for me. no idea why, since most people have this issue when installing...

---

### Post by mcfly2309 on 2007-07-30
i solved it by going into the bios -> power management and turning ioapic (or something like that) off. good luck :)

---

### Post by henriquemaia on 2007-07-30
I’m having the same problem here on a Presario 2500 where I’m installing Ubuntu. The temperature readings are not correct at all, since the computer shuts down while reporting temperature critical reached but being very cool underneath. Is there a way to solve this?

---

### Post by henriquemaia on 2007-08-02
> **henriquemaia said:**
> I’m having the same problem here on a Presario 2500 where I’m installing Ubuntu. The temperature readings are not correct at all, since the computer shuts down while reporting temperature critical reached but being very cool underneath. Is there a way to solve this?

Solved it by installing PCLinuxOS on the laptop. It is running fine with it. This is an Ubuntu’s kernel specific bug and a very annoying one.

---

