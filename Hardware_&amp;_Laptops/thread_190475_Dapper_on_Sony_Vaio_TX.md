---
title: "Dapper on Sony Vaio TX"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by Mausoleum on 2006-06-06
I would like to get a thread going similar to the "Breezy on Sony Vaio TX650P".  I just upgraded my TX 650 to Dapper and am now having issues with suspend-to-ram and suspend-to-disk.

Suspend to ram never used to work (or engage).  It now engages when I echo "ram" > /sys/power/state  as root.  However, it does not wake up any more

More severely though, Suspend-to-disk has stopped working.  Before, I could use the keyboard Fn+F12 to initiate Suspend-to-disk.  This no longer works.  Manually echoing "disk" > /sys/power/state  seems to freeze up the system, but it does seem to suspend.  However, X dies!  Resuming to the console seems to work (but wrong colors).

I've played with some of the options in /etc/default/acpi-support, but to no avail.  Anyone with more success?

Thanks,
  Martin

---

### Post by Mausoleum on 2006-06-06
Ha, so what don't you learn.  Echoing stuff in /sys/power/state  is apparently no good, since it bypasses all the nice Ubuntu-fixes-crappy-hardware stuff.

So using  /etc/acpi/hibernate.sh  works to put the laptop into suspend-to-disk mode.  Hitting the power button didn't do anything, since it was calling  hibernatebtn.sh, which was just generating fake keys.  I guess if I was using gnome, that would be the right thing, since I am using fvwm, I just changed the   /etc/acpi/events/sony-hibernate  to call  hibernate.sh instead of hibernatebtn.sh    If someone knows a "more correct" way of doing it, let me know.  Now the Fn-F12 button works again.  Hooray!

However, suspend-to-ram is still no go.  I set it up to reset the hard disk and to disable/reenable dma, still no go.

---

### Post by Mausoleum on 2006-06-06
Hmm.. so I changed the sleep mode from mem to standby... it now goes into standby, but resumes immediately.  No crash, but doesn't really help much easier.  I guesse I'll have to wait some more until sleep-mode works (as nice as it would be....)

MST

---

