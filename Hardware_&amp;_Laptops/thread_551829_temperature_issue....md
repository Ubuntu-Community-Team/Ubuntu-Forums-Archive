---
title: "temperature issue..."
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by threefcata on 2007-09-15
i'm using ubuntu on a thinkpad x31. recently i noticed that the temperature at the buttom of the laptop is too hot. acpi -V gives me this:

     Battery 1: charging, 83%, 00:25:36 until charged
     Thermal 1: ok, 50.0 degrees C
  AC Adapter 1: on-line

this is /proc/acpi/ibm/fan:

status:         enabled
speed:          0
commands:       enable, disable
commands:       speed <speed> (<speed> is 0-65535)

and it seems the temperature always stays at 50 and the fan never spins up. then i run burn cpu script and this pull the cpu usage to 100%, and i noticed that the fan starts to spin only at 62 degrees C and it can reach all the way up to 75 degrees C... which is terrifying..when i was running windows it's not like this..

i tried tp-fancontrol from thinkwiki.org but i'm not sure if it's working...
is this a bug of ubuntu?

anyway i just want it to be cooler.
anyone?

thx in advance

---

### Post by phen on 2007-12-05
bump, have the same issue with my x31. would like to change the configuration, so that the fan is activated sooner, it seems that the fan control is working, but not setup correctly. 

thanks for any help!

---

### Post by Yellow Pasque on 2007-12-05
I guess you don't have fan control settings in your BIOS, eh?

Out of curiosity, is your CPU downclocking/undervolting when idle? What kind of CPU is in this model?

---

### Post by phen on 2007-12-06
I think that it should downclock when idle, since its an intel pentium centrino thing..

I happened to search the bios for settings yesterday, but as you said, didnt found anything temperature/fan related.



```
kai@schlepptop:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 600.000
cache size      : 1024 KB

```

---

### Post by Yellow Pasque on 2007-12-06
Perhaps you can control the fan through software then. Get lm-sensors and run sensors-detect. Answer 'yes' to the questions it asks you. When that's done, run pwmconfig to configure the fan.

```
sudo apt-get install lm-sensors
sudo sensors-detect
sudo pwmconfig
```

---

### Post by phen on 2007-12-07
hello! thanks for your help! is it possible to remove and undo everything I install and change with lm-sensors? I want to be sure that I cannot make things worse, since I really like my  laptop uncooked :-)

I appreciate your help!

---

### Post by oodledoodle on 2007-12-07
if you are using ati cards try 

```
DISPLAY=:0 aticonfig --set-powerstate=1

```

in a terminal. worked for me. try with or without the display parameter if it doesnt work. it really chilled my card down to the point i can actually touch the bottom on my laptop without getting burned.

---

### Post by phen on 2007-12-07
using ati device but no fglrx, because my adapter is an old radeon7k....


thanks for the info though

> :~$ DISPLAY=:0 aticonfig --set-powerstate=1
The program 'aticonfig' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: aticonfig: command not found


---

### Post by oodledoodle on 2007-12-07
that'll more than likely be the problem anyway. you need to find out how to stop it running on full throttle all the time. good luck anyway, fried hardware is never happy hardware :)

---

### Post by phen on 2007-12-07
hello!

if somebody has the same problem, I can now share my success story :-)

oodledoodle pointed me to the graphics adapter: a little bit of research brought me to the radeon driver manual.
```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	...
        ...
 	Option "DynamicClocks" "on"
EndSection
```

DynamicClocks enables throttling of our good old vintage radeons.

i hope to get a little bit of battery life from it. it didnt slow down anything as mentioned in the manual, but it didn't cool anything down, either.

next I tried the tp-fancontrol script, that can be found here:
You should read the pages carefully, since you'll going to experiment with your laptops heatmanagement.
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Automated_control_scripts]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Automated_control_scripts")

For my X31, success was reported (see Supported Models at bottom of page), so I downloaded tp-fancontrol.

as ubuntu uses a new kernel, your module is called thinkpad-acpi, since you reload your module with
```
modprobe thinkpad-acpi experimental=1 fan_control=1
```
see [URL="http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts"]http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts
[/URL]

then start ./tp-fancontrol  (I had to remove the first, blank line in the script, so that #!bin/bash is the very first line) with

```
 sudo ./tp-fancontrol
```

You have to execute both commands each time you start your computer. will try to figure out a way that this is done automatically.

---

### Post by phen on 2007-12-07
update: the bottom of my laptop is still very hot, but cpu and harddisk are WAY cooler now.

---

### Post by oodledoodle on 2007-12-07
good to hear you're getting to the root of the problem!

---

### Post by StephUb on 2007-12-07
The bottom of my laptop is also getting very warm.
I believe it to be the ram because acpi -V give me always 50
and it's hotter at the spot where RAM is...

Why is that hotter that when i use windows.

I am also scared to never ear the fan working on ubuntu and my acpi/fan folder is empty

I am on a sony VIAO FS790B with a Intel centrino 1.73

thanks

---

### Post by phen on 2007-12-08
well, if you are not absolutely sure thats the RAM causing the high temperatures, you could try ooodle... suggestions to cool your graphics card. have you got an ATI Radeon card?

otherwise try to install lm-sensors as stated above,  i think there are allready some things you can try. or search for sony vaio FS790B related posts!

---

### Post by CareyB on 2007-12-08
I really have to find this reference, but I read a post somewhere that expains why:  Apparently the maintainer of the acpi stuff for Ubuntu made the decision about what thermal trip points to use, and set it up so users cannot change them, as they were able to in the past.  You write values to the acpi virtual file system.

If I recall correctly, the point was to make the computer quiter, as they can run much warmer than people generally think.  Now, either he didn't consider laptop users at all, or he never uses his laptop on his lap.

Anyway...  The actual problem is with the acpi thermal trip points.

```
$> cat /proc/acpi/thermal_zone/TZS0/trip_points
...and...
$>  cat /proc/acpi/thermal_zone/TZS1/trip_points

```
...on my laptop shows the trip points for the two sensors.

Apparently you can write values (look it up elsewhere), but they're reset within minutes.

I don't like that some part of Ubuntu is behaving like Microsoft.  Setting the values to an *odd* default is one thing, but 'protecting' us by not letting us set them ourselves is very non-Linux.  The reasoning, I believe, is that they didn't want to be blamed for people damaging their computers, but isn't it every Linux user's right to fry his bits, if he wants?

Anyway...  I'd like my little Acer to run cooler, if noisier, even if the current settings are considered safe, and within the parameters of the chips.  And I'd like to be able to run a noisy fan when I want, too.

---

### Post by Yellow Pasque on 2007-12-08
> **CareyB said:**
> Apparently you can write values (look it up elsewhere), but they're reset within minutes.
If that's the case, I'd run a cron job to write the values every x minutes.

---

### Post by phen on 2007-12-08
I've found these trip points, but no way to change them. didnt know that you could change the file (even if it will be reset)...

well, these trip points are not good for my laptop, I need them lower. tp-fancontrol works quite well, little bit complicated to configure, it would have been easier with these trip points :)

---

### Post by CareyB on 2007-12-08
Yes...  ACPI trip points are the correct solution.

Do a search for 'acpi trip points' and you'll find how.  It's not a file, by the way.  It's more like system variables.  I don't know for sure, but you're probably modifying run-time parameters for some part of a kernel module.

I'll look into tp-fancontrol, but I think it's not compatiable with all hardware.

---

### Post by phen on 2007-12-08
I think you need IBM-acpi module loaded. since you dont use a thinkpad, you should try lm-sensors (see above)

---

### Post by CareyB on 2007-12-08
Here's that info on setting the ACPI:

[http://ubuntuforums.org/showthread.php?t=379729](http://ubuntuforums.org/showthread.php?t=379729)

---

### Post by CareyB on 2007-12-08
This appears to be the authoritative answer:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

And 'oh, crap'!  How do I turn on my fan?

---

### Post by CareyB on 2007-12-12
Check also this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

Reduced the temperature on my Acer a bucket, and the only thing that seems to be getting hot now is the RAM.  I guess that's my next quest ;-)

---

### Post by dwalker109 on 2008-03-02
My X31 was running quite hot initially (no fan spin until 62 degrees, as described by others). I just updated the BIOS and ECP to the latest versions, and it runs a lot cooler now.

I found [Thinkpad Fan Control]("http://www.gambitchess.org/moin.py/ThinkPad_Fan_Control") to be pretty good as well, should I want to go for hotter and quieter.

**Update:** Looks like I spoke too soon. The fan runs constantly if you reboot it when it is hot, but under normal usage is doesn't come on until the temperature gets to over 60 degrees. Back to TP-Fan, then.

---

