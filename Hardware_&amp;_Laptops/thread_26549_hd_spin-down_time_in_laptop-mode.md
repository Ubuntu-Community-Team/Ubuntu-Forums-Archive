---
title: "hd spin-down time in laptop-mode"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by would on 2005-04-13
hi,

i'm using ubuntu now for 1 week. and i'm really impressed. i used to work with suse 9.2 until now.

but one thing is a littlebit confusing.
when my notebook (ibm t41p) is on battery mode (laptop-mode) the harddisk spins down after a max. time of 10 seconds. but i would like ubuntu to spin it down for example after 5 minutes.
i tried to edit the /etc/acpi/power.sh script as follows: 

# original script:
sleep 5;
grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 0 ]
        then
        xset dpms 0 0 120
        $LAPTOP_MODE start
        $HDPARM -S 12 /dev/hda
        $HDPARM -B 1 /dev/hda
        su $user -c "xscreensaver-command -throttle" &

#edited script:
sleep 5;
grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 0 ]
        then
        xset dpms 0 0 120
        $LAPTOP_MODE start
        $HDPARM -S 80 /dev/hda
        $HDPARM -B 1 /dev/hda
        su $user -c "xscreensaver-command -throttle" &

nothing changed!!!!!!

#then i also tried this:

sleep 5;
grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 0 ]
        then
        xset dpms 0 0 120
        $LAPTOP_MODE start
        $HDPARM -S 0 /dev/hda
        $HDPARM -B 255 /dev/hda
        su $user -c "xscreensaver-command -throttle" &

max. performance for the hd and NO spin-down.
nothing changes.

Maybe somebody can help me.
By the way: The laptop-mode help .txt says there should be a battery.sh script aswell - but there isn't one! maybe in debian?

thanks,

---

### Post by mohaham on 2005-04-16
I'm facing the same problem...can someone help!!!!!

---

