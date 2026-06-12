---
title: "Compaq D500 case fan speed sticks high."
date: 2008-07-15
forum: Hardware
---

### Post by SmokinJuan on 2008-07-15
My case fan usually regulates properly by speeding up when the machine is under load and slowing down when it's idle. 

Since I installed 8.04 it doesn't always regulate properly (two previous Ubuntu versions didn't have this problem).  If the machine is put under load causing the case fan speed to increase, often it will stay at medium speed even after the CPU settles and cools.
If the machine is put under load again while the fan is stuck at medium it will speed up but then returns to the medium speed after the load is removed.
The only way I've found to correct the problem is to reboot.  The fan speed settles back down when the POST screen is displayed.

I've tried lm-sensors (which includes pwmconfig and fancontrol) but it only detects hard drive, cpu and main board temperatures - no fans.  pwmconfig detects no fans.  CPU and mainboard temperatures return to normal 40-45ish while the fan continues at medium speed.  I had to run /usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus to make lm-sensors detect anything.

The BIOS has no settings relating to the fans, temperatures, etc. other than the readouts.

I've found nothing under the /dev or /proc/acpi directories to control the fans, but there's a lot of entries in there and I may have missed one.

A proper fix would be great, but I'd be happy with a setting in one of those directories where I or a cron entry could manually reset the fan speed.  So far I've not been able to find anything of the sort.

Please help!

---

### Post by SmokinJuan on 2008-07-16
This problem just became more more fun!  

Now when my machine is rebooted cron may or may not start until about 8 hours after reboot.  Slightly separate problem, but somewhat related.

---

### Post by SmokinJuan on 2008-07-16
No ideas? Guesses? Words of encouragement?  No one else to bump this?  Can't even get a flame for writing too much|little for such a simple|complex problem?

Well, to put your mind at ease, my fan is currently running at normal speed... but just so you don't get too comfortable: I'm sure it'll be whirring by the end of the night.

---

### Post by SmokinJuan on 2008-07-17
My last post was wrong.  The fan didn't hang up last night. It hung up this morning instead.  What's interesting is that this afternoon when I came home and started browsing I watched a video that spun the fan up a bit more and it actually managed to settle back down to a nice quiet idle speed.

The problem is not solved so feel free to post an answer, idea or direction.

---

### Post by SmokinJuan on 2008-07-20
Don't everyone jump up at once!  

Since this is a community forum I guess that people would like to get to know me before helping.  

Hi, my name is SmokinJuan and I use Ubuntu on my Intel desktop and AMD server.  I've been doing so since 7.04 I believe.  I'd tried an earlier version, maybe 5.# or 6.#, but there were a few proprietary applications in Windows I thought were necessary. Before the switch to Ubuntu I used the AMD as the desktop and Intel as the server.  I decided to swap the two and put the AMD in the basement *because the fans on that box are unregulated and forever loud.*  When I swapped the two I decided to make the jump to Ubuntu.  

Oh, the irony!

---

### Post by SmokinJuan on 2008-07-23
:popcorn:

---

### Post by Dark_Stang on 2008-07-23
Have you tried to update the bios?  <-my only idea at this point

---

### Post by SmokinJuan on 2008-07-24
Thanks for the response Dark_Stang.  

I considered upgrading the BIOS earlier but was leery bricking my box.  Looking through the list of changes for the BIOS reveals nothing related to power management. Also, considering that two prior versions of Ubuntu worked correctly I assume the problem lies in software rather than firmware.  

I hoped to use measured troubleshooting steps rather than the shotgun "try this and that" approach since the problem is intermittent. It may be hard to determine if the fix works or the box is just intermittently working. 

All that aside, options are running thin so I'll try the upgraded BIOS later today and post results. 

Thanks again.

---

