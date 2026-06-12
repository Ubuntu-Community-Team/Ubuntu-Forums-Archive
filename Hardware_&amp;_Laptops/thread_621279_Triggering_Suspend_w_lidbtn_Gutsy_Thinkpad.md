---
title: "Triggering Suspend w/ lidbtn Gutsy Thinkpad"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by catfishk on 2007-11-23
my Thinkpad T60 is currently running Xubuntu (Gutsy v 7.10) and a modified 2.6.22 kernel including SLAB to hibernate/suspend using uswsusp (s2both)

 below is my /etc/acpi/lid.sh script, telling the machine to invoke s2both when the lid switch is triggered, though only when unplugged and running on batteries.  in addition it runs a few DPMS and xscreensaver routines.  (i think i obtained this script from a Gentoo wiki board and many thanks to the unknown author).  it works great!

 however, i'd like to have the laptop wake up IMMEDIATELY upon opening the lid, without the need to depress the power button as i do now.  somehow, someway, this worked in Ubuntu Feisty on this laptop.  i don't know if another ACPI event is triggered when the lid is opened (and the switch thereby 'let go')?

 any assistance would be extremely appreciated!  thanks in advance!

 /etc/acpi/lid.sh
>  #!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"           
            . /usr/share/acpi-support/screenblank
        fi
    done
else
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            grep -q off-line /proc/acpi/ac_adapter/*/state
            if [ $? = 1 ]
                then
                if pidof xscreensaver > /dev/null; then 
                    su $user -c "xscreensaver-command -unthrottle"
                fi
            fi
            if [ x$RADEON_LIGHT = xtrue ]; then
                [ -x /usr/sbin/radeontool ] && radeontool light on
            fi
            if [ `pidof xscreensaver` ]; then
                su $user -c "xscreensaver-command -deactivate"
            fi
            su $user -c "xset dpms force on"
        fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

#!/bin/bash

if [ "`sed -e "s/.[^ ]* *//" /proc/acpi/ac_adapter/AC/state`" = "on-line" ]
        then
                logger "ACPI: AC adapter is on-line, not hibernating..."
        else
                logger "ACPI: AC adapter is off-line, hibernating..."
                /sbin/s2both
fi


  /etc/acpi/events/lidbtn
>  # /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
#action=/etc/acpi/sleep.sh
#action=/sbin/s2both


---

### Post by catfishk on 2007-11-28
come on, don't be shy!  there HAS to be an ACPI expert out there somewhere right?! :)

---

