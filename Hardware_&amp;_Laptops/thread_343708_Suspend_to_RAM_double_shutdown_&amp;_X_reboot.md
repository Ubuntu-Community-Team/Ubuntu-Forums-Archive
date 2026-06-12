---
title: "Suspend to RAM: double shutdown &amp; X reboot"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by phillywize on 2007-01-21
Weird issue:  after much hacking and messing around under the hood, I have gotten suspend-to-ram to work, sort of, on my laptop.  The issue is this:  first, when I come back from suspend, I momentarily get my session back (locked screen prompting for a password), and then my machine -- without prompting from me -- goes straight back into suspend.  I hit the power button, and it comes back.

Here endeth my first issue (which I hope I can correct), and begineth my second (which I REALLY hope I can correct).  After I come back from the second (unwanted) suspend, xorg restarts itself, as if I'd ctrl-alt-backspaced, run sudo /etc/init.d/gdm restart, or done something similar.

While issue #1 is annoying and buggy, issue #2 means I lose my session after a suspend.  Any ideas on where to start?  I am wondering if it could be a scripting issue, although I have not touched my acpi event scripts.  Any thoughts on where to go with this?

I am running Edgy on a Dell Inspiron 8200 with an nVidia GeForce Go 220 video card, 1 gig of ram, and a P4 1.7...  I am running the proprietary nvidia driver -- a recent, if not the most recent, stable release.

Thanks,
Bob

---

### Post by phillywize on 2007-01-28
A bump and a prayer...

---

### Post by r0dzilla on 2007-11-18
I am having a similar problem with my desktop.

When I press the power button on my desktop, it comes back up, I either get a text screen filled with USB messages, or the password prompt.  Either way, the computer suspends again.

Sometimes it seems things get ran twice and my x-session is slow so I just reboot.

---

### Post by mardawi on 2007-11-18
My friend has Dell Inspiron 8200 but daul booting openSuSE 10.3 and ubuntu 7.10, suspend just works out-side-the-box! probably it's worth it to upgrade.

Anyway, I think this script would help in your xorg problem, i found it somewhere on the net, on my laptop i get my session back but without a harddrive :confused:

but maybe it would work for you, give it a try!

```

#!/bin/sh

# discover video card's ID
ID=`lspci | grep VGA | awk '{ print $1 }' | sed -e 's@0000:@@' -e 's@:@/@'`

# securely create a temporary file
TMP_FILE=`mktemp /var/tmp/video_state.XXXXXX`
trap 'rm -f $TMP_FILE' 0 1 15

# switch to virtual terminal 1 to avoid graphics
# corruption in X
chvt 1

# write all unwritten data (just in case)
sync

# dump current data from the video card to the
# temporary file
cat /proc/bus/pci/$ID > $TMP_FILE

# suspend
echo -n mem > /sys/power/state

# restore video card data from the temporary file
# on resume
cat $TMP_FILE > /proc/bus/pci/$ID

# switch back to virtual terminal 7 (running X)
chvt 7

# remove temporary file
rm -f $TMP_FILE

```

just save it in a file, make it executable and execute with sudo.... Good luck!

---

