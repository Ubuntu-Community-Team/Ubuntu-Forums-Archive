---
title: "Need help with script running on bootup."
date: 2009-07-05
forum: Hardware
---

### Post by Hep! on 2009-07-05
I am running Xubuntu 9.04
I put all variants as the prefix because this does not apply to Xubuntu specficially, and the method to do this in Ubuntu and Xubuntu will be [s]pretty much[/s] the same.

I wrote 3 scripts to help with power optimizations.
The first two scripts are called 16-optimizations.sh and are placed in /etc/acpi/ac.d/ and /etc/acpi/battery.d/. These scripts work fine in that they apply the settings I want when I plug in/unplug AC. The problem is, if I boot up on AC or on battery, the settings don't apply unless I make a power source change.

To handle this, I made a third script.
```
#! /bin/bash

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	. /etc/acpi/ac.d/16-optimizations.sh
else
	. /etc/acpi/battery.d/16-optimizations.sh
fi
```

Looks good, right? Well, if I run that script in bash [sudo bash /etc/power-optimizations.sh] it works fine, and applies the right power scheme without actually changing the power source.
I had originally placed this script in /etc/acpi/start.d/ as I figured this was run on every start (and I had named it 99-optimizations.sh at that time). I've now tried a ton of things to get this script to run on startup, but I can't get any of them to work (nor do I know which is the "right" way to do it anyway!

I have already "sudo chmod +x power-optimizations.sh" to make the script executable.

-As mentioned, tried /etc/acpi/start.d/ as well as /etc/acpi/resume.d/
-Tried editing rc.local, both to make a call to the script and I tried pasting the code of the script directly into rc.local. Tried creating a folder /etc/rc.boot/ and put the script in there. I also tried out [this guide]("https://help.ubuntu.com/community/RcLocalHowto") on making an rc.local (I guess the /etc/rc.local file does nothing?
-Tried placing the script in /etc/init.d/ and run "sudo update-rc.d power-optimizations.sh defaults". This gives me a missing LSA header or something message, but still creates links to the script in rcN.d, where N is a runlevel.
-Finally tried going to Applications > Settings > Session and Startup > Application Autostart and adding an entry called "Power Optimizations" that calls "/etc/power-optimizations.sh"
Still no beans.

I've been checking if the script is active 3 ways:
- Current powertop draw - default settings are ~20W, battery script is ~10W.
- "cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor" should return "conservative" if the script has executed; returns "ondemand" if it has not executed.
- "ifconfig" should not show eth0 when in battery mode.

I have literally poured about 8 dedicated hours into this, and I really can't stand doing any more. Please, PLEASE, PLEASE... help me. Someone shed some light on what I am doing wrong.

Please and thank you to ANYONE who tries to help me here. Hopefully it's a simple mistake I've made along the way... permissions? Script needs to be executed as super user or something? I'm a total newb, and I'm at a loss here.

-Hep!

---

### Post by pytheas22 on 2009-07-05
Could you try adding this line to the script:
```

#! /bin/bash

**touch /root/script-ran**

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	. /etc/acpi/ac.d/16-optimizations.sh
else
	. /etc/acpi/battery.d/16-optimizations.sh
fi
```

Then reboot.  After the reboot, see if the file '/root/script-ran' exists.  This will let you know whether the script is running at all.  I know you think it's not, but it's possible that the system is trying to run it, but for some reason it either doesn't finish it, or there's a problem with the conditional statements or something.

Please let me know the results of this test, and we can take it from there.

---

### Post by Hep! on 2009-07-05
I thought I had found the solution here:
[http://ubuntuforums.org/showpost.php?p=7537950&postcount=55](http://ubuntuforums.org/showpost.php?p=7537950&postcount=55)
but putting the script in /etc/pm/power.d/ still doesn't work.

I created a file called /etc/init.d/local and made it executable and set to boot.

This is all I put in it:
```
#!/bin/sh

touch /root/script-ran
```

I rebooted, and that file now exists. So you're right, the script is running, but my code isn't executing properly, or the settings are being over-written by something else later on.


EDIT:
Okay, my script is now placed in /etc/pm/power.d/ as suggested above. I changed the code to look like this:
```
#! /bin/bash

touch /root/script-ran

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	. /etc/acpi/ac.d/16-optimizations.sh
else
	. /etc/acpi/battery.d/16-optimizations.sh
fi

touch /root/script-completed
```

Both files exist after a reboot. So confused, I guess something else is overwriting my settings. How can I make this the last thing run on boot?

---

### Post by pytheas22 on 2009-07-05
What are the actual contents of . /etc/acpi/ac.d/16-optimizations.sh and /etc/acpi/battery.d/16-optimizations.sh?  It's looking like something in those scripts is going awry, since the master script which launches them seems to be completing alright.

You might also want to use the same method as above to try to figure out what the condition statement is testing to.  In other words, change your master script to look like:


```
#! /bin/bash

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	**touch /root/"etc_acpi_ac.d_16-optimizations.sh is running"**
else[B]
	touch /root/"etc_acpi_battery.d_16-optimizations.sh is running"[/B]
fi
```

---

### Post by Hep! on 2009-07-05
/etc/acpi/ac.d/16-optimizations.sh
```
#! /bin/bash

# This script is for performance optimizations when on AC


# Sets CPU speedstep to be performance on demand
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
# Increases dirty page writeback frequency
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
#Disables laptop mode
echo 0 > /proc/sys/vm/laptop_mode
# Enables wake on LAN and turns on the Ethernet port
ethtool -s eth0 wol g
ifconfig eth0 up
```

/etc/acpi/battery.d/16-optimizations.sh
```
#! /bin/bash

# This script is for battery life optimizations


# Sets CPU speedstep to be conservative
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
# Decreases dirty page writeback frequency
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
# Enables laptop mode
echo 5 > /proc/sys/vm/laptop_mode
# Disables wake on LAN and turns off the Ethernet port
ethtool -s eth0 wol d
ifconfig eth0 down
```


The weird thing is, these scripts are working properly when I plug in/unplug the laptop. Even power-optimizations.sh works when I manually run it. I will add the check in to the code to test if the if statement is working properly then report back.
Thank you.


EDIT:
Changed the code to look like this:
/etc/pm/power.d/16-optimizations.sh
```
#! /bin/bash

touch /root/script-ran

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	touch /root/ac-ran
	. /etc/acpi/ac.d/16-optimizations.sh
	touch /root/ac-com
else
	touch /root/bat-ran
	. /etc/acpi/battery.d/16-optimizations.sh
	touch /root/bat-com
fi

touch /root/script-completed
```

After two reboots, one on AC, one on battery, my /root folder now contains:
ac-com, ac-ran, bat-com, bat-ran, script-completed, script-ran.

---

### Post by pytheas22 on 2009-07-05
hmmm, this does seem a bit puzzling.  I guess the last check to run would be to put a "touch ..." line at the end of both /etc/acpi/ac.d/16-optimizations.sh and /etc/acpi/battery.d/16-optimizations.sh to make for absolute certain that they're both finishing correctly.

If they are, then the only thing that makes sense to me is that something else is running after these scripts complete to undo the changes they made.  To see if this is the case, you could try adding some commands to the end of the script that would check the power state immediately after the script finishes and redirect the information into a file; in other words, add lines like these to the end of the scripts:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor > /some/file
ifconfig > /some/file
```

Then you should be able to confirm that the scripts are indeed running completely and applying the desired changes, but that something else is preventing them from sticking.

---

### Post by Hep! on 2009-07-05
Added touch /root/ac-ran, ac-completed, battery-ran, battery-completed to their respective scripts. I was very careful not to change the power state while the laptop was turned on.
After the two reboots, one on AC, one on battery, all four files were in /root/.

But uh. Here's the weirdest part. *Now it's working.* I didn't change anything else.

EDIT: No, it's not working. What the heck? When I FIRST started the computer, I ran cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor to check it out, then ifconfig. Both were as they should be on battery. Ran ifconfig like 10 more times to be sure. Then ran cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor again, and now it's back to ondemand. What could be changing this on me?

EDIT2: I found this: [https://answers.launchpad.net/ubuntu/+question/12145](https://answers.launchpad.net/ubuntu/+question/12145), which sounds a lot like my problem. It's not appearing that my scaling_governor is the only thing not sticking at this point. I checked laptop-mode.conf, but I don't see any mention of "ondemand" or "governor" at all, so I don't know what needs to be changed. Because I am in Xubuntu, not Ubuntu, I do not have gnome-power-manager installed (considering installing it though to check it out...)
EDIT3: Got curious and sudo apt-get install gnome-power-manager, and it says I have it. But... I can't find it. I am just even more lost now.
EDIT4: And I just found out that the updated laptops-mode.conf does not have the cpu scaling controls anymore, those are now located in /etc/laptop-mode/conf.d/cpufreq.conf... I changed the settings to reflect what I want, and guess what? Something is STILL changing my governor, and I don't know what.

---

### Post by pytheas22 on 2009-07-05
Well, at least you're a bit closer to understanding this.

You could try launching gnome-power-manager from the command line if you can't find it in the menu.  Does this help?

---

### Post by Hep! on 2009-07-05
I've certainly learned a lot about troubleshooting scripts, thank you so much for your help.
I was bashing my head into the wall for hours last night, thinking my startup scripts were not running (I was testing by throwing "xterm" in at the beginning, and when xterm didn't come up, I assumed it wasn't running). Now with the touch /root/blahblah, I've got a more useful tool at my disposal. I opened gnome-power-manager from command line and it opened the generic power management control panel (same with gnome-power-preferences, but this throws some errors first before opening). What I need are its configuration files, so I can tell it to stop touching my CPU scaling.

------------

Really, the difference in power savings between conservative and ondemand are fairly small compared to the other tweaks. I'd really like to figure out what is causing this, and fix it. I installed cpufrequtils and tried using that in my script to set the governor, but it too gets reset. I am glad that my other tweaks are now working on startup, which is most important. I just wish I could figure out what's causing this one... my scaling_governor gets reset after about 6-10 seconds after my initial startup. It does not get modified again after this (until a reboot)if I change it to conservative manually.

I've now learned that rc.local DOES function in 9.04, no need for the /etc/init.d/local workaround. I tried putting a "echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
" in my rc.local, which doesn't fix it. I've renamed my scripts to be 99-optimizations in hope that they'd execute after whatever has been overwriting them, I've removed cpufrequtils, in paranoia that it might inadvertently cause another problem.
Still stuck on this, but at least I know a lot more now than I did when I started this topic.

---

### Post by pytheas22 on 2009-07-06
I don't know much about how Linux manages CPU frequency, but you might check out [this thread]("http://ubuntuforums.org/archive/index.php/t-1111609.html"), which explains some possible ways to prevent the kernel (assuming that's the culprit) from overriding your script's settings.

It may also help to disable apmd by typing:
```

sudo /etc/init.d/apmd stop
```

I'm not sure if that's affecting things for you, but it's possible.  Read apmd's man page for more options.

---

### Post by Hep! on 2009-07-09
I took a break from that issue and played with getting the video working optimally for a few days. Now that I've taken care of that, I'm coming back to this one.

I tried your suggestion to no avail. I also tried telling laptop-mode-tools not to touch my CPU frequency, which didn't work, as well as entirely disabling laptop-mode-tools (also didn't work).
Man, this drives me nuts! Wish I could figure out what kept resetting it.
And it definitely gets reset a few seconds of startup, but is part of something that runs on startup... if I change it back once it gets changed, it won't change again until a reboot.

---

### Post by pytheas22 on 2009-07-09
> And it definitely gets reset a few seconds of startup, but is part of something that runs on startup... if I change it back once it gets changed, it won't change again until a reboot.

Oh, I didn't realize that--I thought it always kept changing back.  I wonder if you could put something like this in rc.local:
```

sleep 120 && /etc/acpi/ac.d/16-optimizations.sh &
```

That should effectively delay your command by 120 seconds, but not delay the boot process; hopefully by that point, whatever is causing the problem will already have run, so your script can run and its changes will be permanent.

I guess this is more of a workaround than a solution, but I think it would work.

---

### Post by Hep! on 2009-07-10
Workaround, solution, all the same thing :)

I will give that a try, and see how it goes. Thanks again for the suggestion.

Will report back on if it works.

EDIT: That worked!!
What I actually did was edit my /etc/pm/power.d/99-optimizations.sh to look like this:

```
#! /bin/bash

# This script checks if on AC or battery and sets the appropriate mode.


if on_ac_power; then
	sleep 120 && /etc/acpi/ac.d/99-optimizations.sh &
else
	sleep 120 && /etc/acpi/battery.d/99-optimizations.sh &
fi
```

Could I ask what the trailing ampersand does? I had considered doing this sans the ampersands, but it didn't seem to work and the boot seemed to take longer. I know && is a deliminator that says "do this && then do this"

I am really happy that I've got a solution, thank you so much for your help.

---

### Post by pytheas22 on 2009-07-11
Glad to hear that finally worked!

The ampersand tells the system to start executing that line in the background, then go on immediately to the next line without waiting for the first one to finish.  So without the ampersand, the system would hold up the boot process for 120 seconds, then run your command, then resume booting.  But with the ampersand, the rest of the system has time to finish booting before "sleep" finishes and the second command is run. (This may not be the clearest explanation, and I'm sure there's a much more formal definition of what the ampersand does, but I hope this will allow you to get the point.)

---

### Post by Hep! on 2009-07-11
No, that's a very good explanation. Thank you again for your help.

---

