---
title: "Thinkpad Fan Issues"
date: 2010-09-25
forum: Hardware
---

### Post by neogeek on 2010-09-25
I have a Lenovo X60 tablet and I have Ubuntu LL on it. I feel the temperature of the laptop has been pretty ever since I upgraded from Ubuntu HH. I installed the Xsensors and my readings are:

Temp 1: 52 deg C
Temp 2: 55 deg C
Fan Speed: 3278 rpm

I would like to cool the laptop a little more and did some search on the forums. 

I did the following:

1. Create a file called /etc/modprobe.d/thinkpad_acpi.conf with its contents being "options thinkpad_acpi fan_control=1".
2. Download thinkfan from Debian: [http://packages.debian.org/sid/thinkfan](http://packages.debian.org/sid/thinkfan)
3. Install it the usual way.
4. Edit /etc/default/thinkfan so that the 5th line reads: START=yes

Is there a way to control the fan speed from the above method?

From another forum, I did the following:
#more /proc/acpi/ibm/fan

Got this output:

status:		enabled
speed:		3338
level:		3
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

Run this:
#echo level 7 > /proc/acpi/ibm/fan

Output:bash: /proc/acpi/ibm/fan: Permission denied

I tried #sudo echo level 7 > /proc/acpi/ibm/fan but I am still getting the same error.

Would appreciate any help. Thanks!

---

### Post by gmtro on 2010-10-27
I advice you to use only the first option - **thinkfan**. you may play with **/etc/thinkfan.conf** to set up the correct temperature trigger values for your tablet. 
The second option just set up the fan speed to one high value. You may try 
 *echo level 7 > sudo tee /proc/acpi/ibm/fan*
but from your output thinkfan is already working and it will overwrite this command output
;)

---

### Post by tich on 2011-02-17
my computer (gpu specifically) has been really over-heating too. thinkfan seems like it should be a fairly simple little program to set up but i am having some problems figuring it out and i don't want to mess anything up and fry my computer!

i was wondering if someone who uses it could set up a tutorial?

---

### Post by Allmighty_Lulala on 2011-07-03
Hey,

here is a short tutorial [HTML]http://thinkpad-wiki.org/Thinkfan#Einleitung[/HTML]german, but works (not for me though...)

My fan slows down only for a second, then goes back up (and after 10 seconds it again slows down, but immediately up...)
Thinkfan obviously works but then there's something wrong.. sensors? I don't know

EDIT: Got it. Solution: removing thinkpad fan control nd installin laptop-mode-tools (they dont seem necessary, I removed them now, and thinkfan still working)

---

