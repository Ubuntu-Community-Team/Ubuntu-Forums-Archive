---
title: "CPU Temp high!!"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2005-05-07
I've got a Sony Viao PCG-FXA35/D

AMD 1GH CPU.
Hoary 

The system fan is running and blowing out Hot air.

I did a search and came up this this command;
[COLOR=Red]mike1@mikesubuntu:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             53 C[/COLOR]

It's been as high as 62.  The CPU is running at like 10-19% (accourding to gkrellm)

Is there anyway I can check the fan in the terminal?  Or a command to start the fan?

---

### Post by dave9191 on 2005-05-07
Try having a look in /proc/acpi/fan to see if you have any info about your fan there.

---

### Post by Arthemys on 2005-05-08
One of the things I've noticed at least with my past experiences with laptops is that they run much warmer than logically you'd imagine they would. Granted the last time I've used a laptop was about a year ago, Compaq Presario 910us.

The fan would come on more often than I'd like if it was any form of cloth surface. pants, bedding, etc... With such a small space for so much heat, I would assume it would run pretty hot at the core. I don't have readings to back this up with but maybe Kel can chime in.

When he had his IBM ThinkPad T30, I noticed the fan being on almost constantly; not really blowing hot air just in general.

Though ~55c should be fine for any CPU. Correct me if I'm wrong though.

---

### Post by WildTangent on 2005-05-08
70 degrees C is generally considered the CPU "Death Zone" 62, or even 55 for an extended period of time is toeing the line for sure

-Wild

---

### Post by Arthemys on 2005-05-08
[QUOTE=WildTangent]70 degrees C is generally considered the CPU "Death Zone" 62, or even 55 for an extended period of time is toeing the line for sure[/QUOTE]

I'm just taking into consideration the actual area inside the laptop for cooling. But who am I to say, I'm no engineer. :P

---

### Post by dave9191 on 2005-05-08
A cpu at full load can happily survive 55C. If it starts crossing the 60 mark you should start getting concerned. If it hits 70C you should shutdown and let it cool. Once it hits around 90C it will fry. 

Idle temp should be prefably around 40C or less (ie browsing, emails and so on). 

My laptop on a table surface when browsing or emailing hangs around 35. Under heavy load sitting on a soft material like my bed sheets it can hit 65C. But then I dont play tux racer on my bed sheets for too long :) 

greenwom, type 'top' into the termainal and see if there are any applications using a lot of cpu. When you arent doing anything your cpu shouldnt be 10-20% in use.

Also you need to make sure that laptop loads properly during boot without failoures. 

Dave

---

### Post by Gandalf on 2005-05-09
[QUOTE=WildTangent]70 degrees C is generally considered the CPU "Death Zone" 62, or even 55 for an extended period of time is toeing the line for sure

-Wild[/QUOTE]
 well i'm beyond it now :o
wael@nasreddine:/proc/sys$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             72 C

---

### Post by pau on 2005-05-09
I win!

andromina| cat /proc/acpi/thermal_zone/THRM/temperature                                                                  
temperature:             75 C


But the funny thing is that the fan is not working and the laptop is really cool (temperature, I mean  ;-)  )

No process shows more than 2% so I don't think these 75C are right...

---

### Post by Gandalf on 2005-05-09
[QUOTE=pau]I win!

andromina| cat /proc/acpi/thermal_zone/THRM/temperature                                                                  
temperature:             75 C


But the funny thing is that the fan is not working and the laptop is really cool (temperature, I mean  ;-)  )

No process shows more than 2% so I don't think these 75C are right...[/QUOTE]
 well i think that too :D

---

### Post by chemgoat on 2005-05-15
I have an Averatec 3200 series laptop. I've been using linux on it for about a month and a half and can't get the temperature to read correctly. Any suggestions? It just says it is at 0 deg C all the time. There is nothing listed when I do 'ls' in /proc/acpi/fan, so I can't find anything about it there, and in /proc/acpi/thermal_zone/THRM/ it says the temperature is 0C, 
"polling_frequency" is disabled, in 
"cooling_mode" it says: <setting not supported>
                                    cooling mode:   passive
"state" says:  state:   ok

I don't know what to do or where to look. By placing a thermometer under my computer one day, it was about 120 deg F. I am currently using gkrellm to monitor cpu, processes, hda, and other such things. I would really like to know whether my computer is running hotter than it should, by looking at something on the computer, rather than measuring external temperature. 
Thanks!

---

### Post by wildcard on 2005-05-28
I had problems with my Dell 700m running what seemed to be hot (50-55 degrees C) when idling, and going closer to 60C when running stuff . This temp was derived from both gkrellm and emifreq-applet.

Using the rcconf tool, I found that both the acpid and apmd power management daemons were running. This is probably by design to ensure compatibility.

Disabling acpid and rebooting didn't make an impact on temperature (though it did disable battery detection)

Disabling apmd and rebooting made a LOT of difference - I now run at 45-50C when doing 'light' activity (IM, email, web-surfing), depending on how my processor speed is cycled at the time. My fans are also coming on a lot more consistently as well.

I'd recommend downloading rcconf via synaptic and using the tool to disable whichever power management daemon you're not using (most likely apmd) and seeing if that helps with temp issues.

---

### Post by eyequeue on 2005-05-28
> **greenwom]
I did a search and came up this this command said:**
> mike1@mikesubuntu:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             53 C[/color]

The CPU is running at like 10-19% (accourding to gkrellm)

Is there anyway I can check the fan in the terminal?  Or a command to start the fan?

Since you have gkrellm installed already, go to the Configuration
Builtins > Sensors

---

### Post by pestypest on 2006-03-21
[QUOTE=wildcard]I had problems with my Dell 700m running what seemed to be hot (50-55 degrees C) when idling, and going closer to 60C when running stuff . This temp was derived from both gkrellm and emifreq-applet.

Using the rcconf tool, I found that both the acpid and apmd power management daemons were running. This is probably by design to ensure compatibility.

Disabling acpid and rebooting didn't make an impact on temperature (though it did disable battery detection)

Disabling apmd and rebooting made a LOT of difference - I now run at 45-50C when doing 'light' activity (IM, email, web-surfing), depending on how my processor speed is cycled at the time. My fans are also coming on a lot more consistently as well.

I'd recommend downloading rcconf via synaptic and using the tool to disable whichever power management daemon you're not using (most likely apmd) and seeing if that helps with temp issues.[/QUOTE]
Ok i installed rccconf tool and im not sure how to use it or start it. maybe u can give me a small how-to? would be great :D

---

### Post by rado_london on 2006-05-15
```
rado@ubuntu:/proc/acpi/fan$ cat /proc/acpi/thermal_zone/THR1/temperature
temperature:             40 C

```
Thats on my laptop and it is still very hot. But when I touch my laptop the hottest place is the RAM section. Is that normal or not?

---

### Post by StephUb on 2007-12-07
I have exactly the same issue and i posted here few minutes ago.

[http://ubuntuforums.org/showthread.php?p=3909393#post3909393](http://ubuntuforums.org/showthread.php?p=3909393#post3909393)

---

