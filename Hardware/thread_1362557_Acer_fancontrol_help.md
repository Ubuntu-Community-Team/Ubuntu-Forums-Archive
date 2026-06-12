---
title: "Acer_fancontrol help"
date: 2009-12-23
forum: Hardware
---

### Post by JoeFriday49 on 2009-12-23
I am really coming to like this Ubuntu stuff!...  I've installed 9.10 on an Acer Aspire 5315 and have a couple of questions on the Acer_fancontrol described in [THIS]("http://ubuntuforums.org/showpost.php?p=4925392&postcount=117") post...  
The author has several settings for memory locations based on PC model and the amount of installed memory, but unfortunately there is not a selection for my hardware.  I have updated my memory to 2GB from the factory 512 meg the system comes with.  The only model he has with 2 GB ram is an Aspire 5720...  I don't know whether to point the patch into the 512 meg location at x1F6BCEAF or move it to the x7F6BCEAF address for the 5720 model with 2GB of ram...  I would really hate to scatterbrain my laptop even if it is just a cheapie Wallyworld model...

I have already installed the "coretemp" script and it seems to be working fine.  The longer it's on, the hotter the processor gets.

---

### Post by JoeFriday49 on 2009-12-24
Merry Christmas BUMP

---

### Post by JoeFriday49 on 2009-12-24
Note to self, terminal output when ran acer_fancontrol set up as 5315 W/512 Mb...


/usr/bin/acer_fancontrol: 149: cannot create /proc/acpi/thermal_zone/TZ01/polling_frequency: Permission denied
open() failed: Permission denied
Failed to open /dev/mem mode flags 2, error 13
mempat: Read or write from a location in a file accessed via mmap().
Copyright (c) E2 Systems Limited 2008
Options
-f filename, input for write input or output for read output
-h output this string
-l length to read (implies -r)
-r (default) read
-n add a NUL to the input string
-s write input is string (implies -w)
-w write
-x write input is hexadecimal string (implies -w)
Arguments: Provide the target offset, and the name of a target file
If neither -f, -x or -s is provided, input comes from stdin (-w) or output
goes to stdout (-r, default). If arguments conflict, the last to appear prevail.
Clutch down
open() failed: Permission denied
Failed to open /dev/mem mode flags 2, error 13
mempat: Read or write from a location in a file accessed via mmap().
Copyright (c) E2 Systems Limited 2008
Options
-f filename, input for write input or output for read output
-h output this string
-l length to read (implies -r)
-r (default) read
-n add a NUL to the input string
-s write input is string (implies -w)
-w write
-x write input is hexadecimal string (implies -w)
Arguments: Provide the target offset, and the name of a target file
If neither -f, -x or -s is provided, input comes from stdin (-w) or output
goes to stdout (-r, default). If arguments conflict, the last to appear prevail.
1st gear

---

### Post by JoeFriday49 on 2009-12-24
The next run was as a 5720 with 2 GB Ram...

That's the way I ran it...  I'm not good with the directory structure in Linux, so I ran it from the little "run" box that pop's up with ALT F2...  I lead the instructions off with sudo then selected the path through the file browser to acer_fancontrol...  It did make me enter my password...  I had copied it into /usr/bin and ran it from there in Terminal mode...  It's cooled off again, so I'm gonna' make another run with it set to model 5720 with 2 gig's of ram...

Wishing I could just force the fan on and let it run...  I even looked at the motherboard hoping there was a transistor driving the fan that I could jump out, but it looks as if it runs straight out of the processor...  

Edit to add the script...  I think it's trying to access that directory and read the coretemp:

#!/bin/sh
# acer5720_fancontrol.sh - control the CPU fan on an Acer 5720 with a 64 bit
# Linux.
# ***************************************************************************
# Copyright (c) E2 Systems Limited 2008. This is Free Software (as in Beer),
# but please respect the copyright.
# ***************************************************************************
# Principle of Operation
# ***************************************************************************
# On the Acer 5720, the ACPI Embedded Controller controls the CPU fan.
#
# Communication between the Operating System and the ACPI Embedded Controller is
# documented in the the Differentiated System Description Table (DSDT).
#
# The DSDT is provided as part of of the BIOS. It is written in ACPI Source
# Language (ASL) and compiled to ACPI Machine language (AML), intructions for a
# bytecode interpreter that is part of the Operating System.
#
# The DSDT is accessible on Linux as /proc/acpi/dsdt; 'cat' it somewhere to
# look at it.
#
# The Intel ASL compiler (iasl) compiles ASL to AML, and decompiles AML (eg. as
# saved from /proc/acpi/dsdt) back to ASL.
#
# Which I did.
#
# As a result, I can see:
# -   There is no _TZP. Which means that the OS is supposed to poll; there
#     is no provision for asynchronous notification of temperature changes.
#     (Support for asynchronous notifications would be signalled by having
#     a _TZP that returned 0)
# -   The _TMP method checks that the Embedded Controller is running, and that
#     Temperature Sensing is enabled, and if so it reads a pair of values from
#     a region of memory defined in the DSDT as 'NVST', picks the higher value,
#     and writes it to the Embedded Controller, 'SKTA' in 'ERAM' (ie. SKTA is
#     the command, and the value is its argument), before it returns this
#     value to be used in the /proc/acpi/thermal_zone/TZ01/temperature string. 
#
# Having deduced that DTS1 and DTS2 are supposed to be the CPU temperatures,
# I found that after enabling polling, and writing temperature values into these
# memory locations, the fan behaves as it should.
#
# I think it likely that if you commanded the Embedded Controller directly,
# you would achieve the same effect. The 'thinkpad_acpi' kernel module provides
# a facility to do this from user space through the /proc file system, but
# although the intrinsic capability is independent of the 'thinkpad-ness' of
# the laptop, the module unsportingly refuses to load on my Acer. 
#
# The root cause of the problem appears to be the fact that under 64 bit Linux,
# DTS1 and DTS2 don't get updated. It must be the Embedded Controller or SMM
# BIOS code that is supposed to update them, since they aren't written anywhere
# in the DSDT, and how could the Operating System possibly know that the
# temperatures are meant to go at these locations, in single bytes, in degrees
# Celsius. What I do not know is whether 64 bit Linux stops the Embedded
# Controller writing values to DTS1 and DTS2, or whether it somehow prevents
# the controller reading the source values from the CPU's in the first place, or
# the updates are supposed to be done by BIOS SMM code, and the 64 bit Linux has
# disabled SMI's, or whether the Embedded Controller sends directions to the OS
# to update these locations which the OS ignores. The fact that setting
# ec_intr=0 makes a difference perhaps lends support to this last analysis.
#
# If you boot with acpi_osi=Linux, a command is issued to the BIOS via the
# SMI_CMD port that isn't executed for any other operating system (see the
# OSMI(0x70) method call in the _OSI method in the DSDT).
#
# ec_intr=0 and acpi_osi=Linux together sort of work. 
#
# Anyway, those are the reasons for the existence of this script.
# ***************************************************************************
# This script does not check that it is actually running on an appropriate
# target machine, and writes direct to main memory. Use at your own risk!
# ***************************************************************************
# Things you might think of varying or need to vary
# set -x
# The Patch Addresses. Select the one appropriate for your machine.
# Acer Aspire 5315 with 512 MB of RAM
PATCH_ADDRESS=x1F6BCEAF
# Acer Aspire 5720 with 1 GB of RAM
#PATCH_ADDRESS=x3F6BCEAF
# Acer Aspire 5720 with 2 GB of RAM
#PATCH_ADDRESS=x7F6BCEAF
# ***************************************************************************
# The fan-on and fan-off temperatures (in degrees Centigrade).
# ***************************************************************************
# The fan adopts different speeds, depending on the values written into DTS1
# and DTS2. By experiment, setting the temperature and listening for a change
# in the noisiness of the fan, I think the following are the break points, as
# the temperature rises.
#
# - 0x32 - First speed
# - 0x42 - Second speed
# - 0x4a - Third speed
# - 0x52 - Fourth speed
#
# As the temperature falls, the switch-off values are about 5 C lower. However,
# I find the fan varying its speed annoying, so I only make the fan run faster
# ***************************************************************************
FAN_ON=55
FAN_OFF=50
# -  The sleep between temperature checks
FAN_POLL=10
# -  The thermal_zone polling_frequency.
THERM_POLL=1
# The mempat binary applies the patches, so needs to be in the PATH.
# **************************************************************************
# Function to read the thermal_zone temperature
read_tz_temp() {
    set -- `cat /proc/acpi/thermal_zone/TZ01/temperature`
    tz_tmp=$2
    export tz_tmp
}
# ***************************************************************************
# Function to read the Core 2 Duo temperature
read_core_temp() {
    core_tmp=`
    cat /sys/devices/platform/coretemp.*/temp1_input |
    {
        core_tmp=0
        while read x
        do
            if [ "$x" -gt "$core_tmp" ]
            then
                core_tmp=$x
            fi
        done
        expr $core_tmp / 1000
    }
    `
    export core_tmp
}
# ***********************************************************************
# Load the coretemp module.
modprobe coretemp || {
    echo "You must have module coretemp to monitor the CPU temperature"
    exit 1
}
# ****************************************************************************
# Loop, checking the temperature periodically.
# -   Exit if it appears that the Embedded Controller is controlling the
#     temperature without further assistance from this script; not any more.
# -   Turn the fan up if the temperature exceeds a threshold, and the fan
#     is on
# -   Turn the fan on if the temperature exceeds the threshold, and the fan
#     is not on
# -   Turn the fan off if the temperature is low, and the fan is not off
# ****************************************************************************
# You need to poll the temperature. This is controlled by setting the
# thermal_zone polling_frequency, thus
echo -n $THERM_POLL > /proc/acpi/thermal_zone/TZ01/polling_frequency
# Get the initial temperature, as recorded via the thermal_zone.
read_tz_temp
last_tmp=$tz_tmp
while :
do
    read_tz_temp
# *****************************************************************************
# The test below is commented out, because of reports that the test can return
# true even though the laptop's thermal control isn't working reliably.
#    if [ "$last_tmp" != "$tz_tmp" ]
#    then
#
# The Embedded Controller or SMM BIOS code is maintaining the temperature; we
# are not needed
#
#        exit 0
#    fi
    read_core_temp
#
# If the fan is proving ineffectual, run it faster
#
    if [ "$core_tmp" -gt "$last_tmp" -a "$fan" = on ]
    then 
        if [ "$core_tmp" -ge  82 ]
        then
            mempat -x 5252 $PATCH_ADDRESS /dev/mem
            echo "3rd gear"
            last_tmp=82
        elif [ "$core_tmp" -ge  74 ]
        then
            mempat -x 4a4a $PATCH_ADDRESS /dev/mem
            echo "2nd gear"
            last_tmp=74
        else
            mempat -x 4242 $PATCH_ADDRESS /dev/mem
            echo "1st gear"
            last_tmp=66
        fi
    elif [ "$core_tmp" -ge "$FAN_ON" -a "$fan" != on ]
    then 
#
# Patch the DTS1 and DTS2 in NVST with a value that matches the first fan-on
# threshold (50 C)
#
        mempat -x 3232 $PATCH_ADDRESS /dev/mem
        echo "Clutch down"
        fan=on
        last_tmp=50
    elif [ "$core_tmp" -lt "$FAN_OFF" -a "$fan" != off ]
    then
#
# Patch the DTS1 and DTS2 in NVST with a value that is lower than the lowest
# off threshold (40 C)
#
        mempat -x 2828 $PATCH_ADDRESS /dev/mem
        echo "Ignition Off"
        fan=off
        last_tmp=40
    fi
    sleep "$FAN_POLL"
done

---

### Post by JoeFriday49 on 2009-12-24
Different, but not necessarily better:

Note to self:  set to model 5720 W/2GB ram...  Still not working, terminal reads:


mmap() failed: Operation not permitted
Failed to map length 2 at address 1f6bceaf error 1
Ignition Off
mmap() failed: Operation not permitted
Failed to map length 2 at address 1f6bceaf error 1
Clutch down
mmap() failed: Operation not permitted
Failed to map length 2 at address 1f6bceaf error 1
1st gear

---

### Post by JoeFriday49 on 2009-12-25
Did another test this time with it set for the memory location for 1 gig of ram...  It always seems to give the same mmap error with whatever address I'm pointing to.  I guess I need to figure out what address I can use, but I just don't know enough to do so...   Could it have something to do with the 32 bit vs 64 bit OS?  Here's the terminal output:
 
mmap() failed: Operation not permitted
Failed to map length 2 at address 3f6bceaf error 1
Clutch down
mmap() failed: Operation not permitted
Failed to map length 2 at address 3f6bceaf error 1
1st gear

---

### Post by JoeFriday49 on 2009-12-26
Only 2 more Christmas dinners to cook and I'll be done!...  Whew!

---

### Post by JoeFriday49 on 2009-12-27
There has to be a simple answer to this...  I think I've read every thing ever written on mmap () failed error messages, or at least everything Google can find, but it's so far above a newby like me it may as well be written in greek...  Seems like I just need a good memory location that the program can poke a number into.  Maybe I need to install a 64 bit OS, but I see no advantage to that with a 32 bit processor...  Hmmmm...  May be worth a try anyway...

Only ONE more Christmas dinner to cook and life returns to normal!...  Bittersweet...  Yes...  ) :

---

### Post by JoeFriday49 on 2009-12-27
Well you can't install a 64 bit OS in this PC...  Oh well, good thought and the author did mention it several times in the script, but it's only a 32 bit processor...  

Well at least the Christmas dinners are completed and I probably won't eat anything for at least 2 days,  I mean hours...  LOL

---

### Post by JoeFriday49 on 2009-12-29
Well I have tried to contact the fellow that posted the original solution here:
[http://ubuntuforums.org/showthread.php?t=604158&highlight=acer_fancontrol+post+117&page=12](http://ubuntuforums.org/showthread.php?t=604158&highlight=acer_fancontrol+post+117&page=12)

---

### Post by JoeFriday49 on 2009-12-31
Yawl are simply gonna' love this one...  Here's the reply I got back from Acer...  I emailed their help desk just to see if maybe there was an outside chance they had a fix...  Set down yer coffee before you read this one, serious spew alert!...

<snip>
Subject
---------------------------------------------------------------
Fan  Problem


Discussion  Thread
---------------------------------------------------------------
Response  (Aswathy_GWSI664) - 12/31/2009 04:40 AM
Dear Joe Friday,

Thank you  for contacting Acer America. I'll be happy to assist you with this  issue.

I understand from your mail that you are having issue with the  fan.

I have verified your serial number in our database and found that  your unit is out of warranty.

In order to resolve this issue, the unit  can be taken for repair.

Please be informed that you will have to pay $  199 for the service.

If you are interested, confirm your shipping  address, E-mail address and phone number.

For further clarifications  please feel free to visit our web site [http://support.acer.com/](http://support.acer.com/).

Have a  great day!

Respectfully,
Acer America 
Online Technical  Support

---

### Post by garywright on 2010-01-01
You can force the fan to run continuously. When Ubuntu is highlighted in the Grub menu press <e> to edit and add the line <acpi=off>. Then enter the command to boot which is displayed on the bottom of the screen. It will then run with the fan continuously. I have an Acer 5315 with the same problem and this is the only way that I can run Ubuntu. Incidentally, when I now boot into Vista the fan always stops running after waking from sleep ie I can no longer safely sleep in Vista. Sure wish they could fix this fan stuff.

---

### Post by JoeFriday49 on 2010-01-04
> **garywright said:**
> You can force the fan to run continuously. When Ubuntu is highlighted in the Grub menu press <e> to edit and add the line <acpi=off>. Then enter the command to boot which is displayed on the bottom of the screen. It will then run with the fan continuously. I have an Acer 5315 with the same problem and this is the only way that I can run Ubuntu. Incidentally, when I now boot into Vista the fan always stops running after waking from sleep ie I can no longer safely sleep in Vista. Sure wish they could fix this fan stuff.

Is there a way to get to this point without a dual boot setup?  I tried to do as you suggested, but the first thing I see on my screen is Grub loading...  I don't have a selection menu and by the time I get the message it won't stop...

---

### Post by DonNielsen on 2010-01-04
> **JoeFriday49 said:**
> Is there a way to get to this point without a dual boot setup?  I tried to do as you suggested, but the first thing I see on my screen is Grub loading...  I don't have a selection menu and by the time I get the message it won't stop...

If you need to get into the grub menu to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts.
By default you have to press 'ESC' within three seconds.

---

### Post by JoeFriday49 on 2010-01-04
> **DonNielsen said:**
> If you need to get into the grub menu to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts.
By default you have to press 'ESC' within three seconds.

I can't seem to get it to do anything by hitting escape once...  If I hit it multiple times I can make the system hang, but it's on a blank screen and I can't type in anything...

---

### Post by JoeFriday49 on 2010-01-16
I'm gonna' close this thread. my problem is gone!  I have upgraded the BIOS to 1.40 and the fan is now holding the processor temperature between 45 and 50 deg c!

Thanks folks!

---

### Post by joeganda on 2010-01-17
Also my problem with overheating is gone after updating my bios from v1.29 to v 1.43. I kicked of Vista, but could update anyway with an iso described in msg 39 on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
The fan runs every now and then, I hope it will be enough. Strangely it works, despite I turned off acpi in the boot and told grub to use the acpi of Linux.

---

