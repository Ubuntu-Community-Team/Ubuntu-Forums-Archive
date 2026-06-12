---
title: "RE: CPU Fan does not work on an HP ProBook 4320s"
date: 2015-06-20
forum: Hardware
---

### Post by timothyhobbs on 2015-06-20
Dear moderators, please move this post to the CLOSED post ["RE: CPU Fan does not work on an HP ProBook 4320s"]("http://ubuntuforums.org/showthread.php?t=2217658&page=6").

Hello,

Thank's for the usefull script. I'm using an HP Elitebook 2540p which has the same problem. Fan runs in BIOS but turns off when an operating system starts. The information which you shared was very helpfull.

On my 2540p you can set the fan speed with:

```

$ echo "\_SB.PCI0.LPCB.EC0.KFCL 0x99 0x00" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```

With the seccond argument being the speed and the first argument being some unknown.

You can get the fan speed with:

```

$ echo "\_SB.PCI0.LPCB.EC0.MFAC" > /proc/acpi/call && echo $(cat /proc/acpi/call) 
0x10alled

```

I don't know bash very well, and it seems that the output of the MFAC function is different than the PWM0 command in the previosly posted script. Anyways, I wasn't able to get that script to work. I simplified things a bit and I now have a script that works.

 Here is my script for the HP Elitebook 2540p:

Put this in /usr/sbin/eb_fan and run:

```

# chmod +x /usr/sbin/eb_fan

```

```

#!/bin/bash
# 
# HP EliteBook 2540p Fan Control Script
# V 0.1.0
# ACPI SFSD/GFSD Methods
# ASSUMING DUAL CORE CPU
# For single core CPU check comments below


INTERV=5 # Polling interval, seconds
FANOFFTIME=30

# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}

set_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.KFCL 0x99 0x$1"
    echo "$(acpi_call $CMD)"
}

while true; do
    # Get CPU temperature
    SENSE="$(sensors)"
    CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
    # FOR SINGLE CORE CPU
    # Comment from here
    CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
    SUM="`expr $CORE0 + $CORE2`"
    TEMP=`expr $SUM / 2`
    #UNTIL HERE and uncomment the line below
    #TEMP=$CORE0

    echo $TEMP
    if [ $TEMP -gt 85 ]; then
      set_speed "64" > /dev/null
    elif [ $TEMP -gt 65 ]; then
      set_speed "30" > /dev/null
    elif [ $TEMP -gt 55 ]; then
      set_speed "10" > /dev/null
    else
      set_speed "0" > /dev/null
      sleep $FANOFFTIME
    fi
    sleep $INTERV

done


```

If you are using systemd you can use the following service file to launch the script:

Place in /etc/systemd/system/eb-fan.service

```

[Unit]
Description=Automatic Elitebook 2470p Fan control

[Service]
TimeoutStartSec=0
ExecStart=/usr/sbin/eb_fan

[Install]
WantedBy=multi-user.target

```

And run

```

# systemctl enable eb-fan.service

# systemctl enable eb-fan.service

```

You will also need to add the acpi_call module to /etc/modules.

Thanks again for the hard work! I bought this laptop from the bazar for $500 which seemed pretty insane given that it's really got very good specs and seems brand new. I'm pretty sure that the previous owner sold it because it was overheating massively under windows. If so, I really feel sorry for the fellow/gall.

Tim

---

### Post by timothyhobbs on 2015-06-22
Unfortunately, this fix does not work when the laptop is running on battery power. I will be returning the laptop.

---

