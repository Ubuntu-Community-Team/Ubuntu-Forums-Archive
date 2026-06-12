---
title: "New trip point changes being reset during session. Why?"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by adrianj on 2007-03-08
I use this command to change my trip points:

 echo -n "110:0:0:100:88:76:68:60:50" > /proc/acpi/thermal_zone/TZ2/trip_points

when I check the trip points immediately after I change them, they are as above, but just a couple of minutes later they are reset to their original levels. This is during the same session. What is overriding my manual settings?

I am running FF H5 on an HP nx9420.

Any help would be much appreciated!

---

### Post by Nenron on 2007-03-13
Hi adrainj,
I believe I found a workaround to this problem, it's quite simple too.
Maybe you'd like to try it and see if it works for you.

But first...
DISCLAIMER: I am not a Linux expert. I'm a total n00b... Installed Ubuntu Edgy just 2 days ago... The solution I found seems to work on my machine but it might not be the right one. I am posting this solution so it can hopefully be reviewed by someone who knows what s/he's doing.

Now that we have that out of the way...

I'll start with my solution:
Being new to Linux, I know how important it is to write coherent guides with step by step instructions so I'll try to make this as simple as I can.

If you like you may read the man pages for acpid, it's not necessary but it will help you understand what we are doing. Simply enter this at a terminal (press 'q' to quit):

```
man acpid
```

We are going to add an event handler to acpid, we do this by adding a file to the acipd default events directory. Enter the following in an open terminal (Application -> Accessories -> Terminal):

```
gksudo gedit /etc/acpi/events/set-trip-points
```

You will be prompted for your root password.

Now we edit the file that defines what event we are responding to and what action is taken.
Copy and paste the following into the editor:

```

# /etc/acpi/events/set-trip-points
# Called when a thermal_zone event occurs.
# 

event=thermal_zone
action=/etc/acpi/set-trip-points.sh

```

Save the file and close the editor.

Now we need to create the action file (the script that acpid runs whenever an event is signaled):

```
gksudo gedit /etc/acpi/set-trip-points.sh
```

You should paste the following code into the editor:

```

#!/bin/bash
# Overwrite default trip points.

echo -n "enter your string of values here" > /proc/acpi/thermal_zone/*/trip_points

```

This is the script that runs when a thermal_zone event occurs.
You should place your own values where it says **"enter your string of values here"** (the quotes are not necessary) and the asterisk (*****) with the thermal zone you wish to change.

One may find information about [trip points at the Linux ACPI-HOWTO]("http://www.columbia.edu/~ariel/acpi/acpi_howto.html#trip_points") which also contains a lot of useful information about the Linux ACPI.

Once you've entered your values you may save the changes and leave the editor.

The last command for today is:

```
sudo chmod 755 /etc/acpi/set-trip-points.sh
```

Which gives the script executable permissions.

Next time you boot, acpid will load the event file (/etc/acpi/events/set-trip-points) and launch the script every time the trip points are reseted to their original (BIOS? or is it DSDT?) values.

Another way is to simply reset acpid (no reboot necessary) by entering the following in a terminal:

```
sudo kill -SIGHUP "pid of acpid"
```

Where you should replace **"pid of acipd"** with the process ID of the acipd process (without quotes). The ID can be found through the System Monitor (System -> Administration -> System Monitor, make sure you set "All Processes" under view.)
I know there is an easier way to find the ID but I don't know what it is...
told you... 
noob.


Here is what I think is going on:
I noted that the trip point reset coincides with an event that is being routed through apcid. (Please excuse me if I'm not using the correct terminology). When I printed out the logs at /var/log/acpid I saw something like this:
```

received event "thermal_zone TZ1 00000081 00000000"
notifying client aaaa[b:c]
notifying client xxxx[y:z]
completed event "thermal_zone TZ1 00000081 00000000"

```
This usually happens when the temperature value is at (or close to) the value it had at an original trip point, for example: if before setting the new trip point one had a trip point at 60 C, than, when the temperature reaches that value an event will be fired.

I think the BIOS is telling the OS to synchronize with its values. This is supported by another find at a Microsoft site: [ACPI Notify Codes for ACPI Source Language]("http://www.microsoft.com/whdc/system/pnppwr/powermgmt/ACPInotify.mspx"). One can see that 0x81 is the notify code for thermal trip point change! (If the trip point changed, the OS must update it.)

So basically the short answer is that Linux is doing what it's supposed to.

A few last notes:
1. It might not be correct to handle all thermal_zone events this way, maybe we need to limit the event to 00000081 type events, on second thought, I don't really think it's a problem.

2. The script will only run when a thermal_zone event is fired, this might not happen immediately (may not happen at all). If you want to set the trip points at startup you should add an entry in one of the /etc/rc*.d/ directories, I'm not sure which one though (rc2.d, I think) or how exactly to do this. Maybe someone can help out with this one?

Another option is to edit the rc.local and add the command, I'm not sure this is the right way.

3. Another related issue is that although you can change the trip points during a session by editing the /etc/acpi/set-trip-points.sh file, these changes will only be applied, once more, when a thermal_zone event is fired.

I apologize if this post has been too long and confusing with all the technical details. I guess I'm just eager to make a good first impression :).

I hope this is helpful.

---

### Post by adrianj on 2007-03-15
Thanks Nenron for your descriptive reply. I'm wondering now if you're a newbie what am I? 

I' am also wondering if my trigger points are even valid and being used. These is the output of the following: cat /proc/acpi/thermal_zone/*/*

<setting not supported>
cooling mode:   active
<polling disabled>
state:                   ok
temperature:             29 C
critical (S5):           256 C
active[0]:               91 C: devices=0xdf80f84c 
active[1]:               85 C: devices=0xdf80f7e8 
active[2]:               79 C: devices=0xdf80f798 
active[3]:               68 C: devices=0xdf80ffcc 
active[4]:               58 C: devices=0xdf80ff7c 
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             40 C
critical (S5):           102 C
passive:                 97 C: tc1=1 tc2=2 tsp=300 devices=0xdf800310 0xdf80089c 
<setting not supported>
cooling mode:   active
<polling disabled>
state:                   ok
temperature:             48 C
critical (S5):           110 C
active[0]:               100 C: devices=0xdf80fd9c 
active[1]:               88 C: devices=0xdf80ff2c 
active[2]:               76 C: devices=0xdf80fedc 
active[3]:               68 C: devices=0xdf80fe8c 
active[4]:               60 C: devices=0xdf80fe3c 
active[5]:               55 C: devices=0xdf80fdec 
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             39 C
critical (S5):           105 C
passive:                 95 C: tc1=1 tc2=2 tsp=300 devices=0xdf800310 0xdf80089c 
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             28 C
critical (S5):           102 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=0xdf800310 0xdf80089c 
<setting not supported>
cooling mode:   critical
<polling disabled>
state:                   ok
temperature:             20 C
critical (S5):           110 C

The "setting not supported" worries me. I have also noticed that my fan starts at 20% regardless of any of these points. As I am writing this post  the GPU temp is 48 c but the fan is still on, although the first trigger point is 55 c. Can the fan be controlled by the CPU states C1, C2 etc instead?  As you can see from above all my temps are low but the fan still spins at 20%.

Adrian

---

### Post by Nenron on 2007-03-15
> **adrianj said:**
> Thanks Nenron for your descriptive reply. I'm wondering now if you're a newbie what am I? 

Heh... I only said I was a *Linux* newbie. Just so no one gets the wrong idea about me and later blame me for frying his chip (shouldn't happen in any case, BTW).

I'm familiar with the technical terms since I'm doing something similar in WinXP (actually, it's MUCH easier in Linux). Also, I'm kind of in between jobs right now  ;), so I have a bit of spare time to try and figure these things out.

> 
The "setting not supported" worries me. I have also noticed that my fan starts at 20% regardless of any of these points. As I am writing this post  the GPU temp is 48 c but the fan is still on, although the first trigger point is 55 c. Can the fan be controlled by the CPU states C1, C2 etc instead?  As you can see from above all my temps are low but the fan still spins at 20%.

Adrian

"setting not supported" means the cooling mode can't be set directly. In my TZ2 I have the same thing for the cooling mode but am still able to affect the fans using the trip points.

I'm not sure what the problem is... I do have a few suggestions:

Did you try your /proc/acpi/fan directoy? You can find instructions at [URL="http://www.columbia.edu/~ariel/acpi/acpi_howto.html#proc_fan"]
http://www.columbia.edu/~ariel/acpi/acpi_howto.html#proc_fan[/URL]

I'd expect there would be 9 of them, one for each active state. Remember to read back the value to see it has actually changed.


ADDED:
After playing around with my settings a bit I think I know what's going on. Fan states are only changed when a trip point is passed, I think that if you raise the temperature and then lower it, on the way down the fans should shut down (if you pass a trip point). If you want to shut down all your fans at startup you can place the following command in /etc/rc.local:

WARNING!!! THIS MIGHT NOT BE A GOOD IDEA, THE FANS WILL BE OFF NO MATTER WHAT THE TEMPERATURE IS AT STARTUP AND THEIR STATE WILL REMAIN OFF UNTIL A TRIP POINT IS PASSED.

```
echo 3 > /proc/acpi/fan/*/*
```

Still, I doubt a processor could be fried and I think the worst that can happen is a system shutdown.
END ADDED.

I'm not sure the C-States are relevant, I didn't really play around with those yet. I believe they aren't directly related to the fans but rather change some internal state in the processor. You can find information about them at the same link (section 7.2).

Finally, are you sure this is a Linux issue? Is the behavior different under windows?
There might be a fan that the BIOS won't let Linux control. If you can set all the fans in the fan directory to "off" but still hear a fan working then that just might be the case.
Maybe then, playing around with the BIOS setup, could make a difference.

Regarding my former post:
I think I've discovered why there is an event sent from the BIOS to reset the trip points. I believe it's done for hysteresis, that is, once the temperature passes a trip point and a fan is activated, the BIOS lowers the value of the trip point so the fan will stops working at a lower temperature than the one it started in, thus avoiding rapid activation and deactivation of the fan.

This means that the action "script" I posted before isn't so good since we loose hysteresis, I wouldn't consider it a critical issue, but still, it would be nice to have it. I'll post a new improved script if I manage to get one working.

Again, sorry about all the techno-babble, I hope at least some of it is making sense.

---

### Post by phoxx on 2007-04-06
Good post Nenron, I was having trouble understanding why the changes made by my startup script to /proc/acpi/thermal_zone/*/trip_points were being overwritten at some point between startup and opening a terminal after login, and (after running the script manually) when coming back from suspend mode. Seems to me like the high load for extended periods caused by both loading X + logging in and returning from suspend mode simply caused the CPU temp to fluctuate enough that the thermal_zone event was sent.

> **Nenron said:**
> 
Regarding my former post:
I think I've discovered why there is an event sent from the BIOS to reset the trip points. I believe it's done for hysteresis, that is, once the temperature passes a trip point and a fan is activated, the BIOS lowers the value of the trip point so the fan will stops working at a lower temperature than the one it started in, thus avoiding rapid activation and deactivation of the fan.

This means that the action "script" I posted before isn't so good since we loose hysteresis, I wouldn't consider it a critical issue, but still, it would be nice to have it. I'll post a new improved script if I manage to get one working.


As to the problem of removing hysteresis using your solution, I suggest simply setting polling_frequency to 20-30 seconds. This should give enough time for the temperature to drop well below the specified threshold before another check is made.

---

### Post by trippinnik on 2007-06-03
aack, why can't i set the trip points? 
sudo echo 80:70:35:60:55:50:45 > /proc/acpi/thermal_zone/THM0/trip_points 
bash: /proc/acpi/thermal_zone/THM0/trip_points: Permission denied

the defaults are way to high for my processor and it's been overheating.  I followed the instructions for the script but it seemed to work for a little while and then stopped.  I'll try changing the polling frequency as suggested too, but I am not sure how.

---

### Post by trippinnik on 2007-06-03
got it, changed the permissions and the polling freq.  everything seems good.  Way better than having to underclock often... even if it can't run full speed for very long.  Anyone know where i can confirm that the p3 mobile isn't supposed to go above 60 C?

---

### Post by trippinnik on 2007-06-03
The intel site says 100 C! I thought my laptop had been locking up from overheating.  I guess I'll just be sure to keep it under 70 C?

---

### Post by merike on 2008-01-01
Is one supposed to have so little information in those trip_points files?
I only have:
```
merike@MARY-JO:/proc/acpi/thermal_zone/THM0$ cat trip_points
critical (S5):           127 C
merike@MARY-JO:/proc/acpi/thermal_zone/THM1$ cat trip_points
critical (S5):           97 C
passive:                 93 C: tc1=5 tc2=4 tsp=600 devices=CPU0 CPU1
```

---

