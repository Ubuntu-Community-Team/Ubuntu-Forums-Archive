---
title: "HD spinning down too soon on battery..."
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by otherside on 2005-05-15
When running on battery i can hear my hard drive spin down after about 10 seconds.  I check hdparm -C /dev/hda and it reports "standby".  So, i give the command 
hdparm -S 180 /dev/hda
and it reports back to me that i have set the spin down time to 15 minutes.  But then i hear the drive spin down again after 10 seconds.  Does anyone know if there is anything else that may be superceding hdparm in Hoary on a laptop???

Nate

---

### Post by Osmodia on 2005-05-21
I've got the same problem.

Does somebody has a solution?

---

### Post by Arthemys on 2005-05-22
Your BIOS settings may be taking priority over what linux is telling it. Are you loading APM or ACPI on start up?

---

### Post by mohaham on 2005-05-22
i'm having the same problem..
i tried using hdparm -S  too but it doesnt seem to work.

---

### Post by otherside on 2005-05-23
I am loading ACPI....

Nate

---

### Post by otherside on 2005-05-25
Ok...This is how I fixed the problem for those of you that are having the same issue.  I found the "laptop-mode" conf file in /etc/default and changed the value from "enable_laptop_mode=yes" to no.  I then went to /etc/acpi and opened a text editor to edit the script "power.sh".  I changed these lines...so that they would look like the ones below...

xset dpms 0 0 120 # changed to 600
        $LAPTOP_MODE start #changed to stop
        $HDPARM -S 12 /dev/hda #changed to 0 TO DISABLE SPIN DOWN
        $HDPARM -B 255 /dev/hda #changed to 255...can't remember the initial value
        su $user -c "xscreensaver-command -throttle" &


That should do it!  My drive now continues to spin when in battery mode.  Plus it's really not good for a drive to spin up and down so much...it greatly reduces the drive's lifetime.

Nate

---

### Post by mlord on 2005-05-26
[QUOTE=otherside]When running on battery i can hear my hard drive spin down after about 10 seconds.  I check hdparm -C /dev/hda and it reports "standby".  So, i give the command 
hdparm -S 180 /dev/hda
and it reports back to me that i have set the spin down time to 15 minutes.  But then i hear the drive spin down again after 10 seconds.  Does anyone know if there is anything else that may be superceding hdparm in Hoary on a laptop???

Nate[/QUOTE]
 The problem seems to be the '-B xxx' flag --> enables built-in powersaving parameters of the drive, causing it to ignore the '-S xxx' flag completely.

Cheers

---

### Post by mohaham on 2005-06-05
[QUOTE=otherside]Ok...This is how I fixed the problem for those of you that are having the same issue.  I found the "laptop-mode" conf file in /etc/default and changed the value from "enable_laptop_mode=yes" to no.  I then went to /etc/acpi and opened a text editor to edit the script "power.sh".  I changed these lines...so that they would look like the ones below...

xset dpms 0 0 120 # changed to 600
        $LAPTOP_MODE start #changed to stop
        $HDPARM -S 12 /dev/hda #changed to 0 TO DISABLE SPIN DOWN
        $HDPARM -B 255 /dev/hda #changed to 255...can't remember the initial value
        su $user -c "xscreensaver-command -throttle" &


That should do it!  My drive now continues to spin when in battery mode.  Plus it's really not good for a drive to spin up and down so much...it greatly reduces the drive's lifetime.

Nate[/QUOTE]

Excellent.. Thanks.
changing..
$HDPARM -B 1 /dev/hda to $HDPARM -B 255 /dev/hda 
alone resolved the spin down issue...
now ..
$HDPARM -S 12 /dev/hda can be set appropriately for a decent spin down interval in LAPTOP-MODE..
Thanks to you..

[EDIT] It appears that without disabling LAPTOP-MODE its not possible to fix this spin-down issue

---

