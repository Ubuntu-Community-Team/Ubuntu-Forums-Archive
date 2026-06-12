---
title: "dell inspiron 710m, wrong lid state in /proc/acpi/button/lid/LID0/state"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by su99 on 2007-04-10
Recently I installed Ubuntu 7.04beta on my dell 710m. Everything works perfectly (after some settings of course) except one thing:

1. Boot up the system, login and wait for the desktop to fully load.

2. Close the laptop lid, the laptop doesn't suspend, which is not expected. (screen backlight is off, but hd and fan keep spinning, apps keep running)

Note: i'm using default theme and gdm, the tray panel has gnome-power-manager applet on it, and I've set the policy to be "suspend" when lid closes in gpm's preferences dialog.

3. Since the laptop didn't suspend in step 2, opening the lid immediately turns backlight on. And I can see all apps are still running without interruption.

4. WEIRD THINGS HAPPENS FROM THIS STEP: if I close the lid again, the laptop correctly suspends!

5. And opening the lid correctly resumes the laptop.

6. HOWEVER, if I close the lid again, it fails to suspend, just like step 2-3. If I do that one more time, it succeeds, like 4-5.

So, the pattern is, after boot, the 1st, 3rd, 5th, 7th ... time I close the lid, the laptop won't suspend; but it does suspend correctly when I close lid for the 2nd, 4th, 6th, 8th ... time.

By looking into this deeper, I'm pretty sure the reason is: before the 1st/3rd/5th lid-close, the state value in /proc/acpi/button/lid/LID0/state is "closed", which is wrong. So gpm thinks the lid-close is actually a lid-open event, and no suspend operation is carried out. However, after 1st/3rd/5th lid close and open, the value becomes correct -- "open", so the 2nd/4th/6th lid close is correctly handled. And when the laptop resumes correctly from 2nd/4th/6th lid close, the value is wrong again, so the next time it fails to suspend. It's always that success and failure follow each other in an interleaved way.

By lshal --monitor, i can see the same pattern. For example, when I boot up the machine and run lshal --monitor:

```

Start monitoring devicelist:
-------------------------------------------------

```

Very clean. And run "lshal" without parameter and find LID0, I can see the button.state.value=true (means lid closed), which is wrong already.

Now I close the lid (it's the 1st time after a clean boot), the laptop fails to suspend, as I described above. Then open the lid, and it shows:

```

Start monitoring devicelist:
-------------------------------------------------
acpi_BAT0 property battery.remaining_time = 12600 (0x3138)
acpi_BAT0 property battery.charge_level.current = 45584 (0xb210)
acpi_BAT0 property battery.reporting.current = 3080 (0xc08)
acpi_LID0 condition ButtonPressed = lid
[COLOR="Blue"]acpi_LID0 property button.state.value = false[/COLOR]
acpi_LID0 condition ButtonPressed = lid

```

2nd line from bottom (marked blue) showed that the LID0 state is false (open) now, which is correct. Then I close the lid again (this counts as the 2nd time), it suspends correctly. Opening the lid correctly resumes too, and I observed the following new output from lshal --monitor:

```

acpi_BAT0 property battery.charge_level.percentage = 68 (0x44)
acpi_BAT0 property battery.remaining_time = 12419 (0x3083)
acpi_BAT0 property battery.charge_level.current = 44932 (0xaf84)
acpi_BAT0 property battery.reporting.current = 3036 (0xbdc)
[COLOR="Blue"]acpi_LID0 property button.state.value = true[/COLOR]
acpi_LID0 condition ButtonPressed = lid
net_00_16_ce_07_ee_65 removed
net_00_14_22_8a_64_78 removed
usb_device_46d_c002_noserial_if0_logicaldev_input removed
usb_device_46d_c002_noserial_if0 removed
usb_device_46d_c002_noserial_usbraw removed
usb_device_46d_c002_noserial removed
usb_device_46d_c002_noserial added
usb_device_46d_c002_noserial_if0 added
net_00_16_ce_07_ee_65 added
net_00_14_22_8a_64_78 added
usb_device_46d_c002_noserial_usbraw added
usb_device_46d_c002_noserial_if0_logicaldev_input added
computer_logicaldev_input_0 removed
computer_logicaldev_input_1 removed
computer_logicaldev_input_2 removed
computer_logicaldev_input_0 added
computer_logicaldev_input_1 added
computer_logicaldev_input_2 added

```

Most info is irrelevant. The blue line is the key: it correctly detected the pressing down of the lid button. However, there is no releasing of the lid button. And LID0 state remains true (closed) after resuming. This caused the next lid-close to fail.

Looks like resuming from a correct suspend doesn't update the lid-open (equivalent with lid-button-release) state.

I'm not sure if I described the problem clearly. Hope someone can give me some hint on how to solve this issue. For example, is there a way to force a "rescan" of LID0 state? Or even manually use something like hal-set-property to change it to "false"? If so, how can I guarantee it's executed only after resuming?

Thanks in advance.

---

### Post by su99 on 2007-04-11
i might have found a quick (and possibly dirty, depending on how you look at it) solution. seems to work well on my laptop so far: every time i close/open the lid, suspend/resume is always correctly done.

the solution is easy. open /etc/acpi/power.sh, before the line "getState;", add the following code:

```
(
	echo DELAYING force lid open...
	sleep 5
	hal-set-property --udi /org/freedesktop/Hal/devices/acpi_LID0 --key button.state.value --bool false
	echo FORCED lid open = $?
)&
```

that's it. power.sh gets executed every time the laptop resumes. this piece of code forces to set the lid button state to open (LID0's button.state.value=false). "sleep 5" and background execution ("&" at the end) are necessary here, otherwise this hal-set-property call gets executed too early, and later tasks in power.sh seem to "restore" the lid state value to the wrong one.

to verify it: after a successful resume, wait until "FORCE lid open = 0" appears in /var/log/acpid, try "lshal | more" and find the button.state.value under LID0, it should be false now. that's why the next suspend can be done correctly. note that the value in /proc/acpi/button/lid/LID0/state is still wrong ("closed"), but it doesn't matter, next suspend will just work well. it looks like gpm uses the value from hal property, not /proc/.../state.

not sure if this mod has any side effect. will keep an eye on it for a few days. in what other cases does power.sh get executed?

power.sh seems to be executed after boot up, so this workaround also fixes the 1st lid-close after boot up. great.

---

### Post by dan171717 on 2007-04-11
sounds buryied deep in the system try an earleir vertion of ubuntu or dig around on google you could try and change power properties to something random then back again???

odd problem:confused: :confused: :confused:

---

### Post by su99 on 2007-04-11
> **dan171717 said:**
> sounds buryied deep in the system try an earleir vertion of ubuntu or dig around on google you could try and change power properties to something random then back again???

odd problem:confused: :confused: :confused:


dan, i've tried every other trivial settings, and spent hours in google. none of them helped.

well, 7.04beta works pretty well except for this one issue, and it isn't a big one even if it can't be solved (just close the lid twice everytime i want to suspend it. not a big deal. i can press that little pin near the lcd hinge once, then close the lid). so i don't really want to bother backing up all my data and trying an older version.

actually, by searching this forum, i believe someone else has met exactly the same problem on edgy, with the same laptop model: [http://ubuntuforums.org/showthread.php?t=296207](http://ubuntuforums.org/showthread.php?t=296207)

---

### Post by technikalKP on 2007-08-30
Thanks for posting this fix!   The 'only suspend every-other-close' thing has been getting on my nerves ever since I installed ubuntu.

---

### Post by julianjm on 2007-11-06
The same thing happens here with my (quite old) HP Compaq nx9030. I have to close the lid twice to actually suspend the computer.

Is there any official fix for this? Can I do anything to help track this issue, as it seems that not everyone can reproduce it.

Julian J. M.

---

### Post by technikalKP on 2007-11-06
Mine has actually reverted back to being problematic after upgrading to Gutsy.  It seems that the udi for my lid switch has changed and is inconsistent.

ex: entering the command

>  hal-get-property --udi /org/freedesktop/Hal/devices/acpi_LID0 --key info.product


Now results in the error message:
> error: libhal_device_get_property_type: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/acpi_LID0

digging around, it now seems that the Lid Switch has the udi of computer_logicaldev_input***x***, where** *x ***varies from 0 - 2.  Each successful sleep/resume cycle triggered by a lid close changes it.  I've tried running dpkg-reconfigure hal, but that hasn't helped.  Starting a suspend cycle by clicking the 'sleep' button does not seem to change the udi.

I've screwed around with this so much I'm sure it's something I introduced, but I can't figure out what the issue is.  I've managed to work around it somewhat by modifying the fix that su99 posted to include a bunch of checks to see if the property I'm trying to modify is actually the Lid button.  it's ugly and I'm sure there are better approaches, but I don't know hal well enough to know of a different way to do it.  This is what I have:

> (
	echo DELAYING force lid open...
	sleep 5
	if  hal-get-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_0 --key info.product == 'Lid Switch'; then	
		hal-set-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_0 --key button.state.value --bool false
	else if  hal-get-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_1 --key info.product == 'Lid Switch'; then	
		hal-set-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_1 --key button.state.value --bool false
	fi
	else if  hal-get-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_2 --key info.product == 'Lid Switch'; then	
		hal-set-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_2 --key button.state.value --bool false
	fi
	else if  hal-get-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_3 --key info.product == 'Lid Switch'; then	
		hal-set-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_3 --key button.state.value --bool false
	fi
	else if  hal-get-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_4 --key info.product == 'Lid Switch'; then	
		hal-set-property --udi /org/freedesktop/Hal/devices/computer_logicaldev_input_4 --key button.state.value --bool false
	fi
fi
	echo FORCED lid open = $?
)&



Another option I've seen posted it to replace the /etc/acpi/lid.sh with sleepbtn.sh.  This resulted in problematic returns from resume for me, though.  To try it, open terminal and enter the following commands

> 
cd /etc/acpi
sudo mv lid.sh lid.sh.old
sudo ln -s sleepbtn.sh lid.sh


Then, under power settings, set actions to 'nothing' for lid close and give it a shot.  If it doesn't work, you can revert to the old state by entering

> 
cd /etc/acpi
sudo rm lid.sh
sudo mv lid.sh.old lid.sh


This is the only real issue I have with Ubuntu on this laptop - and every time I think I have it sussed out, it messes up again.  Any hints would be appreciated.

---

### Post by technikalKP on 2007-11-06
I cleaned up the code to something more workable and readable:

> 
(	UDI=`hal-find-by-property --key info.product --string 'Lid Switch'`
	echo $UDI
	echo DELAYING force lid open...
	sleep 5
	hal-set-property --udi $UDI --key button.state.value --bool false
	echo FORCED lid open = $?
)&


I still don't know why acpi_LID0 is gone, or why there's no consistency in what UDI the switch is assigned to.

---

### Post by technikalKP on 2007-11-12
FWIW - the following work-around has been working ok for me for the last several days.  Not a fix to the root cause, but it does allow the machine to reliably suspend and resume when closing the lid.

First, disable ACPI actions by setting Actions to 'Do Nothing' for 'When Laptop Lid is Closed' for  AC and Battery under System|Preferences|Power Management

Second, remove the lid.sh script and replace it with a symbolic link to sleepbtn.sh.  The effectively causes the system to replicate a press of the 'sleep' button each time the lid is closed:
> 
cd /etc/acpi
sudo mv lid.sh lid.sh.old
sudo ln -s sleepbtn.sh lid.sh


And finally, modify acpi-support script to enable "DOUBLE_CONSOLE_SWITCH=true" option.  This fixes an occasional screen weirdness that occurred when resuming.

> 
cd /etc/acpi
sudo gedit acpi-support

Find the line that says 

> #DOUBLE_CONSOLE_SWITCH=true


Remove the '#' and save.

I do occasionally get spurious 'action forbidden' messages when resuming from suspend.  I believe this is due to multiple 'lid' events coming in at the same time.  There's a policy in place that ignores ACPI events during the first 10 seconds of resume, so it still works - it just annoys you with a warning message.  Otherwise it's been more stable and reliable than any other method I've tried with this laptop.

---

