---
title: "Thinkpad fan control with thinkpad_acpi"
date: 2008-06-22
forum: Hardware
---

### Post by chazchaz101 on 2008-06-22
I have followed the istructions at [http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed) for setting up manual fan control, including adding the lines
options thinkpad_acpi fan_control=1
options thinkpad_acpi experimental=1
to /proc/acpi/ibm and rebooting, but when I try to change the fan speed, nothing happens.

For example:
```

root@Laptop:/proc/acpi/ibm# cat /proc/acpi/ibm/fan
status:		enabled
speed:		3140
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
root@Laptop:/proc/acpi/ibm# echo level 7 > /proc/acpi/ibm/fan
root@Laptop:/proc/acpi/ibm# cat /proc/acpi/ibm/fan
status:		enabled
speed:		3080
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
root@Laptop:/proc/acpi/ibm# 

```

I am running Hardy x64 on a ThinkPad t61p

---

### Post by sandoz on 2009-06-20
In Hardy you have to add these lines to

/etc/modprobe.d/options

From Jaunty on you should add it to something like

/etc/modprobe.d/thinkpad_acpi.conf

(After the changes reload the module with
sudo modprobe -r thinkpad_acpi && sudo modprobe thinkpad_acpi
)

The line:
```

options thinkpad_acpi fan_control=1

```
should be enough.

sandoz

---

### Post by nineowls on 2009-08-09
> **sandoz said:**
> In Hardy you have to add these lines to

/etc/modprobe.d/options

From Jaunty on you should add it to something like

/etc/modprobe.d/thinkpad_acpi.conf

(After the changes reload the module with
sudo modprobe -r thinkpad_acpi && sudo modprobe thinkpad_acpi
)

The line:
```

options thinkpad_acpi fan_control=1

```
should be enough.

sandoz
Just a note of thanks. 
I have spent a week getting to a solution for my Thinkpad A31
that with a fresh install of Jaunty was going into critical shutdown 95C
The above is a working solution that saves time.....
I tried it five times and after a complete re-re-install it works.
```
uname -r
``` 
2.6.28-14-generic
**```
sudo -i
```**
```
gedit /etc/modprobe.d/thinkpad_acpi.conf
```
add the line as indicated above
save
do the modprobe as above
```
echo level 7 > /proc/acpi/ibm/fan
```
**in regular terminal** (non root)
 ```
cat /proc/acpi/ibm/fan
```
it works...
but 7 is not highest speed
```

jj@jj-a31l6u904:~$ cat /proc/acpi/ibm/fan
status:		enabled
speed:		3746
level:		7
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
USER@a31l6u904:~$ echo level disengaged > /proc/acpi/ibm/fan
bash: /proc/acpi/ibm/fan: Permission denied
USER@a31l6u904:~$ cat /proc/acpi/ibm/fan
status:		enabled
speed:		4459
level:		disengaged
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
USER@a31l6u904:~$ 


```
so now I just have to figure out how to award beans or something :confused:

---

### Post by richard.e.morton on 2009-08-30
I am running kubuntu 910 Koala Alpha 4 on a T60 - the only difference is the use of kate as the text editor instead of gedit

so the above worked for me.

sudo kate /etc/modprobe.d/thinkpad_acpi.conf
added the line: "options thinkpad_acpi fan_control=1"
restarted module with 
sudo modprobe -r thinkpad_acpi && sudo modprobe thinkpad_acpi

but the next bit failed:
richard@T60:/etc/modprobe.d$ sudo echo level 7 > /proc/acpi/ibm/fan                            
bash: /proc/acpi/ibm/fan: Permission denied                                                    

until I became root
richard@T60:/etc/modprobe.d$ sudo -i

root@T60:~# echo level 7 > /proc/acpi/ibm/fan

to see the fan speed:
root@T60:~# cat /proc/acpi/ibm/fan           
status:         enabled                      
speed:          3860                         
level:          7                            
commands:       level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:       enable, disable                                             
commands:       watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))  

and can even set the fan very fast using:

root@T60:~# echo level full-speed > /proc/acpi/ibm/fan
which gives a blistering fan speed after it slowly spins up and resamples the rpm of the fan:

root@T60:~# cat /proc/acpi/ibm/fan
status:         enabled
speed:          5735
level:          disengaged
commands:       level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:       enable, disable
commands:       watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

---

### Post by nineowls on 2010-04-06
same problem - same solution
with 2.6.31-20-generic
clean install

---

### Post by RayJohns on 2010-09-18
This thread was very helpful to me, as far as being able to control the fan on my ThinkPad.  I wanted to relate my own experiences on Ubuntu 10.04, in case it might help someone else down the line.  I'm using a ThinkPad R51 with linux 2.6.32-24-generic.  I was having some over heating problems on my laptop and wanted to be able to control the fan and keep it running full time (and at a higher speed).

First, in order to monitor the speed of the fan and the temperatures of the CPU, GPU, etc., I installed a program called "Computer Temperature Monitor 0.9.6.1" via the software center.  This program allows you to add a temp icon to the panel bar in Ubuntu.  After installation, just right click on the bar and select "Add to Panel".  

I then installed a program called XSensors (which installs under Applications -> System Tools).  When run, XSensors allows you to monitor the different sensor temps and also allows you to keep tabs on how fast the fan is spinning.

In order to control the fan itself, I had to first create the following file (as root):

**/etc/modprobe.d/thinkpad_acpi.conf**

in that file, I then placed this line:

**options thinkpad_acpi fan_control=1**

Then (again as root), I ran the two following commands:

[b]/sbin/modprobe -r thinkpad_acpi
/sbin/modprobe thinkpad_acpi[/b]

At this point, using the following command, you can see what options are available as far as controlling the fan goes:

**more /proc/acpi/ibm/fan**

output should look something like this:
[i]
status:		enabled
speed:		3599
level:		7
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
[/i]

In order to control the fan, you can simply echo commands to /proc/acpi/ibm/fan.  In my case, since I wanted the fan to always run at a faster speed, I added the following line to the **/etc/rc.local ** file.  This causes the fan to constantly run at around 3600 RPM's when the machine boots into Ubuntu.

**echo level 7 > /proc/acpi/ibm/fan**

You can also use "level full-speed" or "level disengaged", which will allow the fan to run even faster.  However, in my testing, running the fan at level 7 produced the same temperature readings as the full speed mode, but without the more noticeable fan noise.

Anyway, hope this helps.

Ray

---

### Post by richard.e.morton on 2010-09-18
I have just bought a second T60 also for Ubuntu. This one is better built and doesnt overheat. So now I have two different models of T60 and they couldnt behave more differently.

The key difference is that the original unit uses an ATI grpahics chip and this unit is a pure intel centrino duo unit.

2007-CTO - ATI unit that overheats with just a web-browser and burns your leg when using the unit; even with no desktop effects in GNOME. KDE was unusable as it shut down in no time at all.

1951-4TG - a unit that stays cool(warm to touch on base) even with a lot of applications open and using all the desktop effects

my advice is to avoid ATI!

R

---

