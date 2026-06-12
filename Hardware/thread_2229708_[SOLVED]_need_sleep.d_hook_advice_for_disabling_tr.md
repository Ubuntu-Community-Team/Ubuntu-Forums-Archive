---
title: "[SOLVED] need sleep.d hook advice for disabling trackpad"
date: 2014-06-14
forum: Hardware
---

### Post by regnumimbriumx on 2014-06-14
hey all,

my acer c7 chromebook has a thin and flexible chassis which, when bumped on the lid, appears to click the trackpad and resume from suspend, even though this is not the desired behavior. other users have reported the same issue and by running a butterknife under the closed lid and even grazing (not clicking) the trackpad i appear to be able to also trigger a resume from suspend.

deciding that i should just disable the trackpad during suspend, i've added a hook script to /etc/pm/sleep.d/, named "15_trackpad-nap", as follows:
```
#!/bin/bash
. /home/my_user/env
case "$1" in
   suspend|hibernate)
      export DISPLAY=:0.0
      xinput --set-prop "Cypress APA Trackpad (cyapa)" "Device Enabled" 0
   ;;
   resume|thaw)
      export DISPLAY=:0.0
      xinput --set-prop "Cypress APA Trackpad (cyapa)" "Device Enabled" 1
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```

the ". /home/my_user/env" line was based on step 2 of this post ([http://www.rottenrei.be/posts/2013-02-11-synclient-and-pm-utils/](http://www.rottenrei.be/posts/2013-02-11-synclient-and-pm-utils/)), because i was initially having the same two errors as that person. after generating and including my own environment, the sleep.d hook appears to execute just fine. however, running a knife over the "disabled" trackpad or bumping the lid still causes it to resume.

yet /var/log/pm.suspend claims that it executes my hooks without issue:
```
Running hook /etc/pm/sleep.d/00_trackpad-nap suspend suspend:
/etc/pm/sleep.d/00_trackpad-nap suspend suspend: success.
```

and

```
Running hook /etc/pm/sleep.d/00_trackpad-nap resume suspend:
/etc/pm/sleep.d/00_trackpad-nap resume suspend: success.

```


i know that i'm calling the right device, in my script:
xinput list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Cypress APA Trackpad (cyapa)                id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

...and running my script from a terminal definitely disables the trackpad. in fact, if i disable the trackpad manually and close the lid and put the computer to sleep, i can still awaken the laptop with a knife or a bump to the trackpad, but the trackpad is still disabled on resume!

other potential problems: i'm working on an acer c7 chromebook which is using a hacked BIOS to boot ubuntu. also, /etc/modules requires a few entries to get the trackpad and a couple other things working under ubuntu (for reasons i don't understand). these are:
```
i2c_i801
i2c_dev
chromeos_laptop
cyapa
lp
rtc

```
the "cyapa" entry also appears alongside the listed xinput device for the trackpad. again, i don't know if this is at all relevant; i just need to figure out how to prevent the trackpad from waking the machine during sleep! i know that this is possible because i was able to use a command via terminal many months ago as a temporary fix, but i've since then lost the code :\

does anybody have any great ideas? thanks!

**EDIT [SOLVED]**: everything written above was pretty much useless, for me. i went so far as to manually set xinput touchpad and trackpad to off, plus every single synclient value to 0 (except for TouchpadOff, which i set to 1). the trackpad was completely non-functional but, alas, would still readily wake the computer if anything - the monitor, a finger, a piece of metal - touched it.

the way to disable undesired touchpad wakes on these chromebooks is to add the following line to /etc/rc.local, just above the "exit 0" line:
```
echo TPAD>/proc/acpi/wakeup
```

reboot. by issuing the command "cat /proc/acpi/wakeup" in a terminal you can observe that TPAD is now set to disabled and is no longer capable of waking the device.  the first time that i did this, the mouse was extremely unresponsive after its first wake. after rebooting, though, it works perfectly!

to give the touchpad better sensitivity, it has been recommended that these steps be followed:
```
sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf




```After the line MatchDevicePath "/dev/input/event*", append your new values on new lines: 
```
Option "FingerHigh" "10" 
Option "FingerLow" "5" 
Option "RightButtonAreaLeft" "600"
Option "TapButton3" "2"
Option "ClickFinger3" "2"
Option "ClickTime" "5"
Option "SingleTapTimeout" "140"
Option "MaxTapMove" "20"
Option "MaxTapTime" "140"
Option "LockedDrags" "true"
Option "LockedDragTimeout" "100"

```

although this works on initial boot, after waking from suspend, the system will ignore the synclient options that you specified at boot. to address this, i've placed a file in /etc/pm/sleep.d called 15_trackpad-nap (note: this file may require special environmental variables that can be generated with this command, from any terminal: sh -c 'export -p' > env     ...once the 'env' file is created, you should link to it on the second line of the following code:):


```
#!/bin/bash
#. /home/your_user/env
case "$1" in
   suspend|hibernate)
      #Nothing to do!
   ;;
   resume|thaw)
      export DISPLAY=:0.0
      synclient FingerHigh=10
      synclient FingerLow=5
      synclient RightButtonAreaLeft=600
      synclient TapButton3=2
      synclient ClickFinger3=2
      synclient ClickTime=5
      synclient SingleTapTimeout=140
      synclient MaxTapMove=20
      synclient MaxTapTime=140
      synclient LockedDrags=true
      synclient LockedDragTimeout=100 
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```

..
make this new file executable or it won't be run by the system. you may have to change the export DISPLAY values if you use more than one monitor. for other troubleshooting help, see your /var/log/pm.suspend log.


thanks to these three threads, for the help:
[http://ubuntuforums.org/showthread.php?t=2088620](http://ubuntuforums.org/showthread.php?t=2088620)
[http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu)
[https://johnlewis.ie/mediawiki/index.php?title=Ubuntu_Post_Installation](https://johnlewis.ie/mediawiki/index.php?title=Ubuntu_Post_Installation)

---

