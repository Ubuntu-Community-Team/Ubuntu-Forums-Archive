---
title: "Howto: Power management with ipw3945"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by ntetreau on 2007-01-15
Hi everyone,
this is a simple Howto for owners of laptops with Intel 2200 or 3945 wifi cards.  Using these commands will use laptop-mode automatically at bootup to improve your battery life.  Additionnaly, there are two scripts to be added to laptop-mode so that it manages the power saving modes on the intel wifi cards.  This howto assumes you already have a working wireless setup, there are other threads on getting you wifi working, please keep this thread about power management.

**To use laptop-mode by default**:

```
sudo gedit /etc/default/acpi-support
```

Scroll down change laptop-mode to true:

```
ENABLE_LAPTOP_MODE=true
```

For some reason, laptop-mode is only started when the AC is unplugged.  This might seem fine unless you bootup the laptop on the battery, in which case laptop-mode never gets started.  Thus, to enable laptop-mode at boot (taken from a lost thread):

```
sudo update-rc.d laptop-mode multiuser
```

Now that laptop-mode is started automatically, we can make sure it manages the power saving on the intel wireless cards (ipw3945 & iwp2200) this way.

To use the power management, you will need to install the wireless tools:

```
sudo apt-get wireless-tools
```

**For both intel 3945 (ipw3945 driver) and 2200 (ipw2200 driver) cards**:

First, create the helper function file (taken from largecat's post on page 2 of this thread):

```
sudo gedit /etc/acpi/intelWifiPwr.sh
```

copy & paste this code in the editor, save and exit.

```
#!/bin/bash
# Power saving setting for the Intel 3945 and 2200 wireless adaptor
#
# This script relies upon the name of the driver.

I3945_DRIVERNAME=ipw3945
I2200_DRIVERNAME=ipw2200

IWPRIV=/sbin/iwpriv
IWCONFIG=/sbin/iwconfig

SET_I3945_AC_PARMS="set_power 6"
SET_I3945_BAT_PARMS="set_power 7"

SET_I2200_AC_PARMS="power off"
SET_I2200_BAT_PARMS="power on"

#
# Find all the wireless devices using the supplied driver names.
# Place the interface names on the list WIFI_IFNAMES.
#
function findWifiIfsByDriver {
    local DEVICE;
    local LINK_TARGET;
    WIFI_IFNAMES=""

    for DEVICE in /sys/class/net/*; do
	if [ -d $DEVICE/wireless ]; then
# See if the driver for $DEVICE matches the supplied one by checking the link to
# the driver.
	    if [ -h $DEVICE/device/driver ]; then
		LINK_TARGET=`readlink $DEVICE/device/driver | sed 's/.*\///'`

		if [ $LINK_TARGET == $1 ]; then

# add the interface name to the list
		    WIFI_IFNAMES=$WIFI_IFNAMES" "`echo -n $DEVICE | sed 's/.*\///'`
		fi
	    fi
	fi
    done
}


#
# Set all the adaptors using the supplied driver into the supplied
# power saving mode
#
# $1 - driver name
# $2 - power command
# $3 - power command arguments
#
function setWifiPwrSave {
    local DEVICE;
    findWifiIfsByDriver $1;

    for DEVICE in $WIFI_IFNAMES; do
#	echo "Would execute $2 $DEVICE $3"
	$2 $DEVICE $3
    done
}

function intel3945_BatPwrSave {
    setWifiPwrSave "$I3945_DRIVERNAME" "$IWPRIV" "$SET_I3945_BAT_PARMS"
}

function intel3945_AcPwrSave {
    setWifiPwrSave "$I3945_DRIVERNAME" "$IWPRIV" "$SET_I3945_AC_PARMS"
}

function intel2200_BatPwrSave {
    setWifiPwrSave "$I2200_DRIVERNAME" "$IWCONFIG" "$SET_I2200_BAT_PARMS"
}

function intel2200_AcPwrSave {
    setWifiPwrSave "$I2200_DRIVERNAME" "$IWCONFIG" "$SET_I2200_AC_PARMS"
}
```


Then we will create 2 scripts.  The first will run when the laptop is unplugged, the later when it runs on AC.

On battery:

```
sudo gedit /etc/laptop-mode/batt-start/20-wireless-battery.sh
```

Then copy and paste this code into the editor, save and exit:

```
#!/bin/bash

# source the helper script
. /etc/acpi/intelWifiPwr.sh

# set Battery power saving
intel3945_BatPwrSave
intel2200_BatPwrSave
```

Make it executable:

```
sudo chmod +x /etc/laptop-mode/batt-start/20-wireless-battery.sh
```

On AC:

```
sudo gedit /etc/laptop-mode/batt-stop/20-wireless-ac.sh
```

Then copy and paste this code into the editor, save and exit:

```
#!/bin/bash

# source the helper script
. /etc/acpi/intelWifiPwr.sh

# set Battery power saving
intel3945_AcPwrSave
intel2200_AcPwrSave
```

Make it executable:

```
sudo chmod +x /etc/laptop-mode/batt-stop/20-wireless-ac.sh
```

That's it, you can give it a try by plugging and unplugging the AC and running iwconfig to verify that the Power management: on/off changes (this can take up to 15 seconds to change)

Nic

---

### Post by thewillyway on 2007-01-15
I'm a bit new to this... but any idea how to get the impriv utility? Do I have to install the ipw driver from scratch, or is this in any repository?

---

### Post by andreas64 on 2007-01-16
AFAIK the driver is part of the linux-restricted-modules. Install them for your kernel through synaptic.

Andreas

---

### Post by ntetreau on 2007-01-16
Hi,
as per Andreas, the driver is part of the linux-restricted-modules package while the impriv command is part of the wireless-tools package.  Both can be installed with this command:

```
sudo apt-get install linux-restricted-modules-generic wireless-tools
```

or you can search for them in Synaptics

Let us know if you have problems.

Nic

---

### Post by thewillyway on 2007-01-17
Thank you guys! I'll check this out and report back.

---

### Post by eclesh on 2007-01-17
Note that the top two lines should be 'iwpriv' not 'impriv'.  I was going nuts searching for impriv all over.

The battery script should also be set_power 7 instead of set_power 0.

---

### Post by hardyn on 2007-01-17
can this be automated in some fasion? set defaults somewhere AC connect default, and AC disconnected default... sometimes i like not to think ;)

---

### Post by ntetreau on 2007-01-17
eclesh:  Thanks for pointing this out, what a stupid mistake!

hardyn:  It is automated, just read the first post.

Nic

---

### Post by ntetreau on 2007-01-22
Hi everyone, I updated the howto to make it more general in terms of enabling laptop-mode at boot and turn power management on for ipw3945 and ipw2200 wifi cards.  Let me know if you find mistakes.

Nic

---

### Post by Sevmpe on 2007-01-22
Thanks for the Howto. It is working nicely in my Dell 640m. :D

---

### Post by largecat on 2007-01-22
Some helper functions if your 3945 card is not eth1 or you have more then one card:

```
#!/bin/bash
# Power saving setting for the Intel 3945 wireless adaptor

VENDOR_ID=0x8086
DEVICE_ID=0x4222
IWPRIV=/sbin/iwpriv

#
# Find all the Intel 3945 adaptors based on the vendor and device ids
#
function findIntel3945s {
    INTEL3945_IFNAMES=""

    for DEVICE in /sys/class/net/*; do
	if [ -d $DEVICE/wireless ]; then
# See if $DEVICE is an Intel 3945abg
	    if [ -f $DEVICE/device/vendor ] &&
		[ -f $DEVICE/device/device ]; then
		if [ `cat $DEVICE/device/vendor` == $VENDOR_ID ] &&
		    [ `cat $DEVICE/device/device` == $DEVICE_ID ]; then
# Strip off the leading path to get the interface name
		    IFACE_NAME=`echo -n $DEVICE | sed 's/.*\///'`
# and add it to the list of interfaces
		    INTEL3945_IFNAMES=$INTEL3945_IFNAMES" "$IFACE_NAME
		fi
	    fi
	fi
    done
}


#
# Set all the adaptors into battery power saving mode
#
function setIntel3945s_battery {
    findIntel3945s;

    for DEVICE in $INTEL3945_IFNAMES; do
	$IWPRIV $DEVICE set_power 7
    done
}

#
# Set all the adaptors into ac power saving mode (none)
#
function setIntel3945s_ac {
    findIntel3945s;

    for DEVICE in $INTEL3945_IFNAMES; do
	$IWPRIV $DEVICE set_power 6
    done
}

```

Save the above as something like */etc/acpi/intel3945_pwr.sh* and you can then use it from scripts as follows:

```
#!/bin/bash

# source the helper functions
. /etc/acpi/intel3945_pwr.sh

# Set all Intel 3945 wireless adaptors to battery power saving
setIntel3945s_battery;

```

---

### Post by ntetreau on 2007-01-22
Thanks largecat, your script works much better and his more general, I will find the device id for the intel 2200 and post it here.  If you don't mind you could adapt the script to check for which device is connected and use the right command?

Nic

P.S.:  Hoping to have this taken care of by the developer and in light of the great progress done with this issue, I have [open a bug report #80980]("https://bugs.launchpad.net/ubuntu/+bug/80980")

---

### Post by largecat on 2007-01-22
Having looked at the 3945 and 2200 driver source, using the PCI vendor and device id was not such a good idea as there are a number of pairs that match compatible cards (the values I used were from my setup).
Here is a new script that uses the driver name instead (leaves it up to the driver to determine if the card is compatible). Added support for the ipw2200 too.

```
#!/bin/bash
# Power saving setting for the Intel 3945 and 2200 wireless adaptor
#
# This script relies upon the name of the driver.

I3945_DRIVERNAME=ipw3945
I2200_DRIVERNAME=ipw2200

IWPRIV=/sbin/iwpriv
IWCONFIG=/sbin/iwconfig

SET_I3945_AC_PARMS="set_power 6"
SET_I3945_BAT_PARMS="set_power 7"

SET_I2200_AC_PARMS="power off"
SET_I2200_BAT_PARMS="power on"

#
# Find all the wireless devices using the supplied driver names.
# Place the interface names on the list WIFI_IFNAMES.
#
function findWifiIfsByDriver {
    local DEVICE;
    local LINK_TARGET;
    WIFI_IFNAMES=""

    for DEVICE in /sys/class/net/*; do
	if [ -d $DEVICE/wireless ]; then
# See if the driver for $DEVICE matches the supplied one by checking the link to
# the driver.
	    if [ -h $DEVICE/device/driver ]; then
		LINK_TARGET=`readlink $DEVICE/device/driver | sed 's/.*\///'`

		if [ $LINK_TARGET == $1 ]; then

# add the interface name to the list
		    WIFI_IFNAMES=$WIFI_IFNAMES" "`echo -n $DEVICE | sed 's/.*\///'`
		fi
	    fi
	fi
    done
}


#
# Set all the adaptors using the supplied driver into the supplied
# power saving mode
#
# $1 - driver name
# $2 - power command
# $3 - power command arguments
#
function setWifiPwrSave {
    local DEVICE;
    findWifiIfsByDriver $1;

    for DEVICE in $WIFI_IFNAMES; do
#	echo "Would execute $2 $DEVICE $3"
	$2 $DEVICE $3
    done
}

function intel3945_BatPwrSave {
    setWifiPwrSave "$I3945_DRIVERNAME" "$IWPRIV" "$SET_I3945_BAT_PARMS"
}

function intel3945_AcPwrSave {
    setWifiPwrSave "$I3945_DRIVERNAME" "$IWPRIV" "$SET_I3945_AC_PARMS"
}

function intel2200_BatPwrSave {
    setWifiPwrSave "$I2200_DRIVERNAME" "$IWCONFIG" "$SET_I2200_BAT_PARMS"
}

function intel2200_AcPwrSave {
    setWifiPwrSave "$I2200_DRIVERNAME" "$IWCONFIG" "$SET_I2200_AC_PARMS"
}

```

Save the above as */etc/acpi/intelWifiPwr.sh* or similar.
An example of how to set battery power saving state for all 3945 and 2200 devices on your system:

```
#!/bin/bash

# source the helper script
. /etc/acpi/intelWifiPwr.sh

# set Battery power saving
intel3945_BatPwrSave
intel2200_BatPwrSave

```

---

### Post by ntetreau on 2007-01-22
Thanks largecat, the new script is perfect i guess, works very well on my machine.  I will attach it to the bug report and re-edit the howto if you don't mind.

Nic

---

### Post by reader4 on 2007-01-22
Brilliant!  Working nicely on my Gateway 200ARC.  Thanks.

---

### Post by brettr on 2007-01-24
Amazing, Worked like a charm Thanks!! Anybody have any ideas on how much battery power this can save?

---

### Post by Sugar on 2007-02-10
Thx for an excellent post, works like a charm on my X60s :) Great post

/Sugar

---

### Post by cowlip on 2007-02-14
Thanks for posting this, I hope your bug report gets some love soon!

---

### Post by hardyn on 2007-02-14
> **largecat said:**
> 
```
#!/bin/bash

# source the helper script
. /etc/acpi/intelWifiPwr.sh

# set Battery power saving
intel3945_BatPwrSave
intel2200_BatPwrSave

```

typo: . /etc/acpi/intel/WifiPwr.sh

---

### Post by hardyn on 2007-02-14
questions about above:

sudo update-rc.d laptop-mode multiuser -- what is the actuly doing? how would one undo it?

20-wireless-battery.sh -- why 20, why not 42?

thanks.

---

### Post by ntetreau on 2007-02-20
Hi hardyn,
as for the typo, sorry i'm not seeing it, you might want to check again.  For the number 20, i think the number decides of of the order to run the scripts, 20- before 42-.  In this case, any number would have worked as this is the only script i have in this directory.  For the update-rc.d line, i think it add laptop-mode to the runlevel for all users, hence it runs when the scripts in the runlevel are run at bootup.

Nic

---

### Post by clem-vangelis on 2007-05-11
hi all , i wanted to know if i can do that for my card ( intel 3945abg )?

iwpriv eth1 set_power 7
iwconfig eth1 txpower 11

setting txpower after iwpriv isn't a problem ?

---

### Post by ntetreau on 2007-05-11
I certainly don't see any problem on my machine when I change the txpower.  However, I am not too familiar with that flag, are you?  If so, perhaps you could explain a bit what it does and how to use it?

Nic

---

### Post by clem-vangelis on 2007-05-11
I'm not really familiar with that too , but i think this is the transmission ( sending ) power of the wifi card . thanks for your answer

you were speaking about iwpriv or txpower ?

for iwpriv , it use the specific hardware possibilities ,for example set_power is accessible via module ipw3945

---

### Post by ntetreau on 2007-05-11
Sorry about the confusion, I was referring to txpower.  After reading your post, I tried it and I couldn't find any problems, although I was unsure if there was benefits.

Nic

---

### Post by pvincent on 2007-11-21
thank you for the tip.
it fixes up the wireless on my amilo si1520 with kubuntu7.10

---

### Post by schmolch on 2007-11-25
Does this script re-set the power-management settings after a suspend-resume cycle?

---

