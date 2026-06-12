---
title: "Keyboard repeat rate dddriving me crazzzy"
date: 2008-11-11
forum: Hardware
---

### Post by scooper on 2008-11-11
I'm experiencing the problem described in this [thread]("http://ubuntuforums.org/showthread.php?t=943775").  The keyboard repeat rate and delay is bad for my typing style (delay is much too short) and is unaffected by System Settings and also xset from the command line.

I can make the appropriate change in the System Settings panel, but it has no affect.  I also tried "xset r rate 1000 30" from the command line, again no joy.  In all cases the setting is accepted fine, but has no affect.

The ["solution"]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196") linked by the post does work temporarily.  Adding and then removing Option AutoAddDevices "off" xorg.conf ServerFlags does temporarily get things working, even through an X restart.  But it was lost at the next system reboot.  It must have "rediscovered" my keyboard and messed it up again.

I imagine that I could put that option back and just not rely on automatic discovery.  That would require that I customize the X11 configuration to better understand my specific hardware without discovery.  Suggestions on how to achieve this fall-back position would also be helpful.  I really like the extra keyboard and mouse buttons.

My keyboard is a wireless Logitech S510 that worked perfectly with Gutsy and Hardy.

Thanks!

---

### Post by sisco311 on 2008-11-11
try to set the repeat rate with *kbdrate*:
```
sudo kbdrate -d 500 -r 20
```

if the command works add it to the *rc.local* file:
```
kdesudo kate /etc/rc.local
```
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**kbdrate -d 500 -r 20**
exit 0

---

### Post by scooper on 2008-11-11
> **sisco311 said:**
> try to set the repeat rate with *kbdrate*:
```
sudo kbdrate -d 500 -r 20
```

if the command works add it to the *rc.local* file:
```
kdesudo kate /etc/rc.local
```

Thanks!  I'll give that a try tonight.  Not sure what the difference is between using kbdrate and xset.

---

### Post by Oreo on 2008-11-11
That seems to have worked for me!
Thanks!

---

### Post by scooper on 2008-11-12
Finally got to try it, but kbdrate has no effect whatsoever on my keyboard.  For example, I did the following.

```
$ sudo kbdrate -r 30 -d 750
Typematic Rate set to 30.0 cps (delay = 750 ms)
```

The delay and rate still felt like the original 250 ms and 10 cps.  This is really irritating.

Any other suggestions out there?  I have a hard time believing I'm the only one.

Thanks.

---

### Post by mperry on 2008-11-12
I have the same issue on 2 Thinkpad T43s and a Shuttle Glamor X64 box running 8.10. I tried the kbdrate fix and it works but... When my laptop comes out of suspend it feels like it did before I ran the command. My desktop seems cured; but time will tell.

I think the kbdrate does not "stick" across sessions or something when run in a terminal and just putting it in /etc/rc.local perhaps does not equate with it being the default. I have had to place it back in the laptops each time it comes out of a suspend. I need to go hunting around in /etc/acpi I guess for a place to put the command. AFter I do the command, the change is noticeable.

---

### Post by scooper on 2008-11-12
> **mperry said:**
> I think the kbdrate does not "stick" across sessions or something when run in a terminal

It doesn't work for me at all, not even the millisecond after running it.

---

### Post by sisco311 on 2008-11-12
> **scooper said:**
> Finally got to try it, but kbdrate has no effect whatsoever on my keyboard.  For example, I did the following.

```
$ sudo kbdrate -r 30 -d 750
Typematic Rate set to 30.0 cps (delay = 750 ms)
```

The delay and rate still felt like the original 250 ms and 10 cps.  This is really irritating.

Any other suggestions out there?  I have a hard time believing I'm the only one.

Thanks.

sorry, no idea

> **mperry said:**
> I have the same issue on 2 Thinkpad T43s and a Shuttle Glamor X64 box running 8.10. I tried the kbdrate fix and it works but... When my laptop comes out of suspend it feels like it did before I ran the command. My desktop seems cured; but time will tell.

I think the kbdrate does not "stick" across sessions or something when run in a terminal and just putting it in /etc/rc.local perhaps does not equate with it being the default. I have had to place it back in the laptops each time it comes out of a suspend. I need to go hunting around in /etc/acpi I guess for a place to put the command. AFter I do the command, the change is noticeable.

you can try to write a resume script:
```
gksu gedit /etc/pm/sleep.d/00kbdrate
```
```

#!/bin/bash

case "$1" in
	suspend|hibernate)
		;;

	resume|thaw)
                kbdrate -d 500 -r 20
                ;;
esac
```

save the script and make it executable:
```
sudo chmod +x /etc/pm/sleep.d/00kbdrate
```

---

