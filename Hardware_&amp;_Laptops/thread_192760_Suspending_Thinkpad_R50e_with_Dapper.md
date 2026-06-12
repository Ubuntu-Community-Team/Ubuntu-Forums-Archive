---
title: "Suspending Thinkpad R50e with Dapper"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by lutzky on 2006-06-09
Back in Breezy, I set up suspending like so: I have a script, /usr/local/bin/thinkpad-sleep, in which the most essential part is this:

```

...
cat /proc/bus/pci/00/02.0 > /var/cache/video.config
...
echo -n mem > /sys/power/state
...
cat /var/cache/video.config > /proc/bus/pci/00/02.0
...

```

It is those two 'cat' lines which finally solved suspending on my R50e (otherwise it would show a blank screen on resume).
Now, dapper comes with its own suspending mechanism, and I'd rather use that. So I changed /etc/default/acpi-support to enable SAVE_VIDEO_PCI_STATE (which, as far as I can tell, does exactly that). But no dice. Video comes up blank (screen completely OFF). Any ideas?

---

### Post by splitsch on 2006-06-09
Hello!
You might want to check this post:
[http://www.ubuntuforums.org/showthread.php?t=187584&highlight=r50e](http://www.ubuntuforums.org/showthread.php?t=187584&highlight=r50e)
and here: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation)
now hibernate and sleep are working:
fisrt: > Open a terminal and enter this command:

  sudo gedit /etc/default/acpi-support

And uncomment "ACPI_SLEEP=true" (by removing the # character in front of it)
And in the same file, uncomment "restore_pci_somethingIforgot"
Then:
>  sudo cp /etc/acpi/sleep.sh /etc/acpi/sleep.sh_backup
  sudo gedit /etc/acpi/sleep.sh

Replace the line "echo -n $ACPI_SLEEP_MODE >/sys/power/state" with 
(take from Problem with display remaining black after resume):
  
  # change to console 1
  FGCONSOLE=`fgconsole`
  chvt 6

  # safe video state
  cat /proc/bus/pci/00/02.0 > /tmp/video_state

  # sync filesystem
  sync

  # sync hardware clock with system time
  hwclock --systohc

  # go to sleep
  echo -n 3 > /proc/acpi/sleep

  # waking up
  # restore system clock
  hwclock --hctosys

  # restore video state
  cat /tmp/video_state > /proc/bus/pci/00/02.0

  # change back to X
  chvt $FGCONSOLE

  # clean up behind us
  rm /tmp/video_state

then, edit your Xorg.conf
> Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option   "VBERestore"  "true"
EndSection

It works fine with my r50e laptop.
I don't use kpowersave, though, but klaptop !
Suspend work from calling the /etc/acpi/sleep script in the console or calling it from right-click on klaptop>suspend.

Bye!

---

### Post by lutzky on 2006-06-11
Thanks, worked very well. However, it seems like too much work... shouldn't this be autodetected and made to 'just work'? I was so impressed with Dapper's usability for new users with laptops.

---

### Post by splitsch on 2006-06-11
I know, it should be detected, but it seems that there is a bug!
Check in launchpad :p
r50e thinkpad aren't supported right away...

bye

---

### Post by jrei on 2006-06-12
thanks, 

> 
Open a terminal and enter this command:

sudo gedit /etc/default/acpi-support

And uncomment "ACPI_SLEEP=true" (by removing the # character in front of it)
And in the same file, uncomment "SAVE_VIDEO_PCI_STATE=true"



Did the job for my IBM Z60m.
The hibernate test and the suspend test worked. 

Greetings, Jörn

---

