---
title: "Toshiba_acpi fan control (file permissions)"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by roncrump on 2006-02-20
Hi,

I've been having trouble with the fan on my
Toshiba Satellite Pro TE2100. Since I've installed
Ubuntu, it doesn't seem to have come on at all. 
A bit of a worry really.

Anyway, [http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver")
lead me to believe that I should have some magical
Toshiba-related goodies already on my PC, and indeed
I do.

The above-mentioned web site says the following about the file /proc/acpi/toshiba/fan:

fan - The fan state is shown with the read-only field running. A read-write field, force_on, allows you to enable the fan manually. Valid values are [0, 1]. (NOTE: If the general ACPI fan driver should one day improve to support the same functionality, this interface will be removed.)

If I 
```
sudo gedit /proc/acpi/toshiba/fan
```
to edit the force_on value to 1, or
```
sudo echo "running: 0;force_on: 1" > /proc/acpi/toshiba/fan
```
to try and get the same effect, I cannot write to the file.

```
ls -l /proc/acpi/toshiba/fan
``` gives -rw-r--r-- 1 root root (blah blah). With sudo, I thought I could write to this. No? Why not? Root (therefore me?) is the owner.

This looks to me like the right thing to be doing, especially as echoing
parameters to the files in /proc/acpi/toshiba is a recommended way of 
using toshiba_acpi on the web site listed above.

Any suggestions appreciated.

Cheers,
Ron.

---

### Post by bgoody on 2006-02-20
Hi.  I think you have to cd to the directory before you issue the command.
Brian

[QUOTE=roncrump]Hi,

I've been having trouble with the fan on my
Toshiba Satellite Pro TE2100. Since I've installed
Ubuntu, it doesn't seem to have come on at all. 
A bit of a worry really.

Anyway, [http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver")
lead me to believe that I should have some magical
Toshiba-related goodies already on my PC, and indeed
I do.

The above-mentioned web site says the following about the file /proc/acpi/toshiba/fan:

fan - The fan state is shown with the read-only field running. A read-write field, force_on, allows you to enable the fan manually. Valid values are [0, 1]. (NOTE: If the general ACPI fan driver should one day improve to support the same functionality, this interface will be removed.)

If I 
```
sudo gedit /proc/acpi/toshiba/fan
```
to edit the force_on value to 1, or
```
sudo echo "running: 0;force_on: 1" > /proc/acpi/toshiba/fan
```
to try and get the same effect, I cannot write to the file.

```
ls -l /proc/acpi/toshiba/fan
``` gives -rw-r--r-- 1 root root (blah blah). With sudo, I thought I could write to this. No? Why not? Root (therefore me?) is the owner.

This looks to me like the right thing to be doing, especially as echoing
parameters to the files in /proc/acpi/toshiba is a recommended way of 
using toshiba_acpi on the web site listed above.

Any suggestions appreciated.

Cheers,
Ron.[/QUOTE]

---

### Post by roncrump on 2006-03-02
[QUOTE=bgoody]Hi.  I think you have to cd to the directory before you issue the command.
Brian[/QUOTE]

Tried without any joy - still won't let me write to the file.

---

### Post by mpvano on 2006-03-03
The bash syntax you used redirects the output of the command BEFORE it changes the effective account running the command to root. Since writing the file requires root access, the redirection fails.

That is  to say, the "sudo" is the part whose output is redirected. What you want is instead to redirect the echo command's output as root.

Bash escape syntax can get pretty arcane, so in cases like this one, the easiest way to guarantee that you're giving the command properly is to start a root shell by using

sudo su

type the echo command from the resulting root shell, and then exit.

Mario

---

### Post by DavidTangye on 2006-03-04
Try this

sudo bash -c 'echo "running: 0;force_on: 1" > /proc/acpi/toshiba/fan '

---

### Post by Commuto on 2006-03-08
[QUOTE=DavidTangye]Try this

sudo bash -c 'echo "running: 0;force_on: 1" > /proc/acpi/toshiba/fan '[/QUOTE]
Thank you for your input!
I had to slightly adapt your command line, but with :
```
 sudo bash -c 'echo "force_on: 1" > /proc/acpi/toshiba/fan '
```The fan stays on!
And *cat /proc/acpi/toshiba/fan* now gives:
```
me@Host:/$ cat /proc/acpi/toshiba/fan
running:                 1
force_on:                1
me@Host:/$
``` Got my CPU permanently 20°C cooler thanks to this. Great! :o

---

### Post by DavidTangye on 2006-03-10
Commuto
The temperature here is about 25 to 30 C, and my laptop was running at about 40 to 50 with force off. Now with force on it seems much the same so far.

What temperature does yours run at?

ps Here is the script I now run to check it and set it.
> #!/bin/bash
vProg=`basename $0`
vStatO=`awk -F : '/force_on/ {print $2}' /proc/acpi/toshiba/fan`
if [ $vStatO -eq 1 ] ; then
    vDo=Off
    vDoN=0
else
    vDo=On
    vDoN=1
fi

echo "$vProg : `cat /proc/acpi/thermal_zone/THRM/temperature`"
read -p "Set the fan force to $vDo\? (y) " vAns
if [ "$vAns" == "y" ] ; then
        if [ $vDo == On ] ; then
                sudo bash -c 'echo "Setting fan On" ; echo "force_on: 1" > /proc/acpi/toshiba/fan'
        else
                sudo bash -c 'echo "Setting fan Off" ; echo "force_on: 0" > /proc/acpi/toshiba/fan'
        fi
fi


---

### Post by patrickfromspain on 2006-03-11
well... I don't think 50º are too much for a mobile cpu. In fact, my toshiba L10 is now running between 50 and 57º, and I think at 60º the fan goes on. It doesn't bother me.

---

### Post by DavidTangye on 2006-03-11
From the following I think my temperature is far enough below 'critical' that I hope this laptop does not burn out for a good while. :-)

> # /proc/acpi/thermal_zone/THRM/temperature
temperature:             48 C
# /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           74 C
passive:                 83 C: tc1=9 tc2=2 tsp=1800 devices=0xd6aca740
active[0]:               83 C: devices=0xd6fd43a0
active[1]:               83 C: devices=0xd6fd43a0

---

### Post by Commuto on 2006-03-13
My laptop is a Toshiba 5105-S501. P4M-1.7Ghz. Always running @1.3 cuz I don't notice any usage difference other than higher temperatures.

Well I guess I'll scary you with some of my figures. First let's say this a laptop I have used ~10hours a day, e-ve-ry day for 3 and a half year.
Due to dust accumulating, I was permanently running @80°C IDLE. Up to 93°C easily as soon as I was using CPU (archiving files, playing video, damn Flash animations...). I was even "able" to have the computer auto-off once while Webcaming through MSN. I guess the trigger temp for that is 94°C.

Overall the Fan was always running very noisingly, so I did not have to use this command line anymore :roll:.
I can actually give precise figures of fan RPM triggers, I have then well in my mind:
Fan has 3 speeds+Idle:
Idle : up to 69°C
Speed1 : 70°C up to 79°C
Speed2 : 80°C up to 85°C (slight difference in noise than speed1)
Speed3 : 86°C and above (Very noisy. Unberrable)

Then downhill, cuz the thermal regulation runs on a hysteresis scheme:
Speed3->Speed2 @80°C
Speed2->Speed1 @70°C
Speed1->Idle @60°C


What happened next? I opened my laptop up to the *inside* of the CPU fan. Had everything removed thanks to a [web page](http://irisvista.com/tech/laptops/Toshiba5105/satellite_5105_vga_remove_1.htm) that explained how to dissassemble it.
I was eventually able to remove the dust accumulating for more than 3 years inside the fan case :o.

And now? Well I've a brand new laptop!\\:D/
My 80°C+ temperatures are history. My laptop runs between 60 and 70°C withOUT the force switch, and goes down to... 36°C idle with the force switch. 40->44°C on classical use. Room temp is 21°C.

Anyway... just wanted to share this experience with you if it could be of any interested.
Use this switch... and consider cleaning your laptop fan as well! :D

---

