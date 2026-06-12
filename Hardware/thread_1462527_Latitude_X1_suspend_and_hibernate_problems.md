---
title: "Latitude X1 suspend and hibernate problems"
date: 2010-04-25
forum: Hardware
---

### Post by X1er on 2010-04-25
I'm new to Ubuntu (9.10) and almost gave up due to suspend and hibernate not completing.  I had to hold power button to shut off completely, then restart.  Hibernate and suspend worked if initiated from the login screen before Ubuntu fully loaded, but not after that.  Tried a few simple things with different Power Management settings, but nothing worked until I stumbled upon something about unmounting SD cards.  It worked!  

As long as I unmount the SD card before (don't even need to remove it) sending to suspend or hibernate it works.  Not a perfect solution, since it won't work if I forget to unmount, but it's better than no option for suspend or hibernate.

Thanks to all of those offering different solutions.

-Dell Latitude X1
-Ubuntu 9.10 only (no dual-boot or Windows)

---

### Post by Jope on 2010-05-02
I have a Dell Latitude D430 and had the same problem after I decided to try out Ubuntu 10.04. The machine hung on a black screen on suspend and hibernate, HD running and LEDs on. Removing the SD card allowed the machine to go to sleep. I used to run only Windows on this machine, so I have no idea how it would have worked with previous releases of Ubuntu.

I solved it by writing a small script that unmounts everything from /media and saved it as /etc/pm/sleep.d/umount

Then I configured Nautilus to not pop up new browser windows when media was inserted, because naturally the machine mounts the SD card again on resume. I don't like those popup windows when plugging in a thumbdrive either, so it was a fully acceptable solution to me.

I'm a bit ashamed to even be posting something this trivial here, but perhaps it will help some of the less technical users out there who are hesitant to just whip together something like this.

Oh yes, and this has only been tested on Ubuntu 10.04 and the aforementioned Latitude D430. YMMV.
```

#!/bin/sh

# Action script to umount all media in reaction to pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2010, Ville Jouppi <vjouppi@sci.fi>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, umount everything under /media

case "${1}" in
        suspend|hibernate)
                umount /media/*
                ;;
        resume|thaw)
                # Do nothing
                ;;
esac

```

Oh and if you don't know how:

sudo gedit /etc/pm/sleep.d/umount

<paste the contents in and save>

sudo chmod 755 /etc/pm/sleep.d/umount

should do the trick.

---

