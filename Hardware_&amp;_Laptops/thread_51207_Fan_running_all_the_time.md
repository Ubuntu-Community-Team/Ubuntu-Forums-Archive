---
title: "Fan running all the time"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by raghav_p on 2005-07-22
Hi,

I have a Gateway M405 laptop and have been running Ubuntu for a month or so. It is centrino based and thus allows for cpu scaling.

I notice that my fan is running all the time. I hardly run any CPU intensive programs, (usually firefox, gaim, thunderbird, openoffice) and usually only have firefox and gaim running at a time.

Using the same programs in Windows XP doesn't have the fan running.

I am afraid that I might damage my laptop. Am I just paranoid or is there anything else I should be aware of?

---

### Post by motoperpetuo on 2008-01-27
I'm currently running Linux Mint 4.0, but from what I understand it's very similar to Gutsy. What's more, my laptop is a Gateway (Solo 1450, to be precise), although I have the impression that this would probably work on any kind of laptop.

Anyway, when I installed Mint, the fan was always on, which was very, very annoying. Same thing when I would boot into Puppy Linux. In Windows, the fan would switch off and on normally (as it did under Feisty, if I remember correctly, the last Linux OS I had on this computer).

Here's what seems to have fixed this situation (based this on advice from [http://www.speakeasy.org/~lbijlsma/gateway_1450/):](http://www.speakeasy.org/~lbijlsma/gateway_1450/):)

1)Opening gedit as root, I saved a new, empty text file called gateway-fan to /usr/local/bin.

2)I added the following contents to the file and saved it:

#/bin/bash



# check temperature

temp=`cat /proc/acpi/thermal_zone/THRM/temperature | awk {'print $2'}`

echo "Current temperature: $temp"



# turn fan on when too warm

if [[ "$temp" -ge "50" ]];

then

echo -n 0 >/proc/acpi/fan/FAN0/state

fi



# turn fan on when too warm

if [[ "$temp" -le "42" ]];

then

echo -n 3 >/proc/acpi/fan/FAN0/state

fi

3)Ran “chmod a+x gateway-fan” to make the file executable.

4)Navigated to /etc and opened the configuration file crontab as root.

5)Added the following line to crontab:

05 * 	* * * 	root 	/usr/local/bin/gateway-fan

6)Saved crontab. This SHOULD cause the system to run gateway-fan every five minutes and turn the fan on or off based on the system temperature.

7)Note that I haven't verified that step 6 actually works (I only did this like fifteen minutes ago), but gateway-fan does work when I execute it manually. It tells me the CPU temperature and switches the fan off if it's cooler than 42.

Anyway, I'm still pretty new to Linux and I'm not sure whether or not this would be considered a solid solution, but that damn fan is off now, so I'm happy. If any more experienced users see this post, please comment.

---

### Post by AndyC_772 on 2008-01-27
I'd check a lot more often than 5 minutes, especially on a notebook where the CPU cooler is physically small and has a low heat capacity of its own. If I ask my PC to do something processor intensive, the CPU fan comes on straight away and the air coming out is hot within moments. 5 minutes of intensive activity with no fan would cook the poor CPU.

Personally I'd be checking every 5 seconds.

[edit]: it is actually the CPU temperature you're checking there, isn't it - not just some remote sensor elsewhere on the motherboard? 50 degrees for the CPU itself is pretty cool. On a notebook you'd also have to consider the GPU temperature as they're often cooled by the same fan.

In short: please don't turn the fan off unless you're sure you know ALL the reasons to turn it back on again!

---

### Post by motoperpetuo on 2008-01-27
what if i were to check once a minute? do you think that would be sufficient? (i'm not sure if you can run things from crontab more often.) in any case, the line i added to crontab:

	05 * 	* * * 	root 	/usr/local/bin/gateway-fan

didn't work. i can turn the fan on an off manually, but i can't get the system to check automatically. 

i'm going to try:

	01 * 	* * * 	root 	gateway-fan

now. i notice that there's what looks like a PATH variable in crontab, and that it includes the location of my executable gateway-fan, /usr/local/bin, so i figured that maybe including that path to the executable was causing it not to run?

i don't want to fry my CPU, but the fan being on all the time is pretty maddening.

---

### Post by AndyC_772 on 2008-01-27
My concern is that even a minute is a long time to be dissipating the kind of power a CPU can draw in such a small space. I'd be worried that serious damage could happen in that time, or , at the very least your CPU will slow right down to preserve itself.

Consider this: a laptop CPU can draw about 30W or so, which is about the same as a good soldering iron. Although it's a rather crude approximation, think how hot a soldering iron tip would be 1 minute after switching on, and what effect that might have on any component it's touching. The CPU always has a passive heatsink, of course, but I wouldn't want to rely on it for too long unassisted.

If you have a way to read the CPU (and, don't forget, GPU) temperature directly, try an experiment: read the CPU temp, turn the fan off, start a processor-intensive task, then poll the CPU temp to see what happens to it. You'll want the command to turn the fan back on typed-in and ready!

Rather than running a cron job to check the temp just once, could you write a script that runs continuously in the background, checking it every few seconds?

---

### Post by motoperpetuo on 2008-01-27
> **AndyC_772 said:**
> 

Rather than running a cron job to check the temp just once, could you write a script that runs continuously in the background, checking it every few seconds?

now that sounds like an even better idea. problem is, i'm still at what i would call "advanced noob" stage with linux, so i wouldn't know where to begin. i'm only capable of writing the simplest of shell scripts. still, i may look into that.

anyway, i've finally got it working with the cron job. my laptop is a six-year-old gateway solo 1450, with a 1.2ghz P3 CPU and 512mb of RAM and i don't normally do anything more intensive with it than watching youtube videos. by monkeying around with the shell script i copied from another forum and tweaked to get this working i've also figured out how to turn my fan on and off from the command line...i guess i could just turn it on manually before doing anything really intensive.

basically, i'm hoping to replace this laptop in a few months. if i can get by this way for a while, i probably will.

also, thanks very much your replies. i can't see being able to slog through learning linux without all the great people on this forum.

---

