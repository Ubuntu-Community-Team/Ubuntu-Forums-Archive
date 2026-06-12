---
title: "HOWTO:  Better battery life for laptops with intel wireless [ipw2200 &amp; ipw3945]"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ntetreau on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80980](https://bugs.launchpad.net/ubuntu/+bug/80980) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
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
sudo apt-get install linux-restricted-modules-generic wireless-tools
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

### Post by Rinzwind on 2007-04-23
Looks like it's 'false' cuz of this:

/etc/default/acpi-support:
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines

If anyone has 'odd hangs' I'd love to see it posted here :)


edit: after a shutdown and restart I can confirm that this is working for me
Dell Inspiron 9300.

---

### Post by andrew01 on 2007-04-23
Hi,

Is there any chance it will be working with IPW2100 ?

Andrew

---

### Post by Rinzwind on 2007-04-23
Dunno.
1st try this script as is (with IPW2200 in it)
If it works leave it as is
Otherwise try it with IPW2100 :) 

You can't do alot wrong here :)

---

### Post by andrew01 on 2007-04-23
hi again,

i have changed a little bit scripts and they are working great :)

on AC: Power Management off

on Bat: Power Management on
              Level 5 - highest power save level

I added to intelWifiPwr.sh:

I2100_DRIVERNAME=ipw2100

SET_I2100_AC_PARMS_1="power off"
SET_I2100_BAT_PARMS_1="power on"
SET_I2100_AC_PARMS_2="set_power 0"
SET_I2100_BAT_PARMS_2="set_power 5"

function intel2100_BatPwrSave {
    setWifiPwrSave "$I2100_DRIVERNAME" "$IWCONFIG" "$SET_I2100_BAT_PARMS_1"
    setWifiPwrSave "$I2100_DRIVERNAME" "$IWPRIV" "$SET_I2100_BAT_PARMS_2"
}

function intel2100_AcPwrSave {
    setWifiPwrSave "$I2100_DRIVERNAME" "$IWCONFIG" "$SET_I2100_AC_PARMS_1"
}

added to 20-wireless-battery.sh:

intel2100_BatPwrSave

added to 20-wireless-ac.sh:

intel2100_AcPwrSave

Thanks a lot
Andrew

---

### Post by ntetreau on 2007-04-23
Good to see it's working for you, might want to confirm the bug report so that it gets fixed!

---

### Post by schmolch on 2007-04-23
Works great, thx alot!

---

### Post by andrew01 on 2007-04-24
Hello everyone,

I think that changing Tx-Power would increase the battery life too, 
but unfortunately  I have no idea how to do it. I mean I know the command line
which is :

sudo iwconfig eth1 txpower x

where x is power in  dBm

but it doesn't work, I alway have 16 dBm

I have also strange message with sudo iwlist eth1 txpower:

eth1      unknown transmit-power information.

          Current Tx-Power:16 dBm       (39 mW)

Any ideas what I am doing wrong??

---

### Post by ntetreau on 2007-04-25
Sorry but I have no idea.  Let us know if you end up figuring it out!

Nic

---

### Post by outphase on 2007-04-26
This causes my wireless to cut in and out without any increase in battery life :/

---

### Post by ntetreau on 2007-04-26
You could try different power levels, what is your wifi card?

Nic

---

### Post by outphase on 2007-04-27
I'm using a 2200 in a Dell Inspiron 700m. I originally thought the problem was with my battery itself, but these battery threads popped up.

---

### Post by outphase on 2007-05-08
Looks like my problem was with the battery. I'm sure these scripts fixed the OS's hand in the problem, though. Thanks

---

### Post by alchimera on 2007-05-09
Just a *thanks guys!*, it really has made a difference - about 20% - but mainly because i had no idea that laptop-mode was disabled by default ( i assumed that it was working already!)  and  didn't know that ipw2200 had power management...

Up to now i have been booting into a much-tweaked Zenwalk4.4 when on battery and even though it still has the edge, the gain over U7.04 is now marginal.

---

### Post by ntetreau on 2007-05-09
Good to hear it' s working well for you, if you know of the other "tweaks" in Zenwalk, let us know!

Nic

PS:  To be helpful, you might want to confirm the bug report, I still have no idea why this doesn't get fixed!

---

### Post by Bart Samwel on 2007-05-28
I'm afraid the way these scripts are set up is not how they're supposed to be, and they will cause things to be set up incorrectly on switches from battery to AC mode. The problem is, the scripts in the batt-start and batt-stop directories are supposed to be *init scripts*, taking "start" and "stop" arguments. This means that when entering battery mode, all of the scripts in the batt-stop directory are called with the "stop" argument, and all scripts in the batt-start directory are called with the "start" argument. If you put a script in both directories, you will get unpredicatble results. The correct way is to put *one* script in the directory batt-start, which enables your settings when parameter 1 is "start", and which disables them when parameter 1 is "stop".

---

### Post by ntetreau on 2007-05-28
So far so good for me but i understand your point.  You seem to know more about it than i do, would you care about fixing the scripts then?

Nic

---

### Post by FrancoNero on 2007-05-28
all those fixes that are being suggested here, why aren't they being worked into some sort of bugfix release to be blown out there by auto software update? that would be sweet. i always feel bad hacking and texting around with configuration files, i feel like the programming work is being outsourced to the end user :-)

---

### Post by kilou on 2007-05-29
I have a laptop with iw2200 BG card. I've followed the procedure on post#1 and thought everything was fine (I couldn't test it though). However I recently restarted X with Ctrl+Alt+Backspace and when doing that I get the following errors:

Error with wireless request "set power management" (8B2C)
SET failed on device eth1: input/output error

Error with wireless request "set power management" (8B2C)
SET failed on device eth1: input/output error

Error with wireless request "set power management" (8B2C)
SET failed on device eth1: input/output error

Error with wireless request "set power management" (8B2C)
SET failed on device eth1: device or resource busy

I disconnected the wireless (eth1) connection and then did another Ctrl+Alt+Backspace but it did the same. So I guess the powermanagement scripts do not work on my system???? Should I remove the references to ipw3945 in the scripts??

---

### Post by ntetreau on 2007-05-31
Hi kilou, what happens if you set the power mode manually:

```
sudo iwconfig eth1 power on
```

then 

```
iwconfig eth1
```

---

### Post by kilou on 2007-05-31
This seems to work:

```
kilou@kilou-laptop:~$ iwconfig eth1
eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kilou@kilou-laptop:~$ sudo iwconfig eth1 power on

kilou@kilou-laptop:~$ iwconfig eth1
eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:on[/COLOR]
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by strabes on 2007-08-06
Works for me, thanks!

---

### Post by strabes on 2007-08-07
Actually, I think this procedure is messing with my suspending when I shut my laptop lid. I use kpowersave. Before I did this, it suspended perfectly when I shut the lid but now it doesn't do anything. Suspending works perfectly if I use the log out menu. Any ideas?

---

### Post by ntetreau on 2007-08-07
No idea how it could mess up your suspend.  Perhaps you could take a look at the syslog?  If it works when you suspend manually, it would seem as if the lid button wasn't properly recognized.  Can you remove the scripts and check it out again?

---

### Post by strabes on 2007-08-07
When I removed all the scripts it suspends and resumes perfectly when my laptop lid is shut. Also, I never recall a problem with suspending and resuming before creating these scripts either. This is crazy.

---

### Post by ntetreau on 2007-08-08
When the scripts are there, does it matter if you suspend while plugged or unplugged?  Since you can suspend manually, it really looks as if the lid button wasn't properly recognized when the script are there, but I can't see why.  

There are numerous good thread on the issue the of lid button not being properly mapped.  If you'd really want to, you could leave the script in, and then debug the lid button.

Nic

---

### Post by strabes on 2007-08-09
> **ntetreau said:**
> When the scripts are there, does it matter if you suspend while plugged or unplugged?  Since you can suspend manually, it really looks as if the lid button wasn't properly recognized when the script are there, but I can't see why.  

There are numerous good thread on the issue the of lid button not being properly mapped.  If you'd really want to, you could leave the script in, and then debug the lid button.

Nic

After having removed the scripts, I've figured out that my laptop **doesn't** suspend from a lid close while it's on **battery power** but when it's plugged in it does perfectly.

Fn+Esc is my laptop's default keyboard combination for "Stand By" (suspend) and it works perfectly when plugged in and on battery power. Same when I use KDE's logout menu.

I'm going to search for someone with a similar problem (different lid behavior while on AC and battery. I'll let you know how it turns out.

---

### Post by strabes on 2007-08-09
UPDATE: I have figured out some more important information. If I boot up on AC power, unplug it, and then try to suspend by closing the lid, it doesn't work. But, if I boot up on battery power, closing the lid suspends it perfectly.

So apparently something is wrong with it applying the settings on bootup or something. Is anyone else experiencing this???

---

### Post by cb474 on 2007-08-12
I followed the instructions here to get laptop mode enable when booting from the battery. It used to work in me with Edgy. But now that I'm in Feisty it doesn't work. Any suggestions?

---

### Post by sunami88 on 2007-08-18
This is actually a really great fix, but now my little wifi light winces at me every now and again. Is this bad for my wifi card in any way? I would go in and change the power save mode its in, but it seems to be on a scale of 1 to 10. 

> 
SET_I3945_AC_PARMS="set_power 6"
SET_I3945_BAT_PARMS="set_power 7"


So does 10(example) mean a higher power saving mode, or is 10 using more power?

---

### Post by ntetreau on 2007-08-19
Here's the full explanation copied from the ipw3945 README file:

3.9. Power Management
-----------------------------------------------
The Intel PRO/Wireless 3945ABG Network Connection driver for Linux 
supports the configuration of the Power Save Protocol through a private 
wireless extension interface. The driver supports the following 
different modes:

	0       AC - Always ON
	1-5	Different levels of power management.  The higher the 
		Number, the greater the power savings, but with an impact to 
		packet latencies. 
	6	AC - Always ON
	7	BATTERY - Default setting for battery mode
	>7      AC - Always ON

Power management works by powering down the radio after a certain 
interval of time has passed where no packets are passed through the 
radio.  Once powered down, the radio remains in that state for a given 
period of time.  For higher power savings, the interval between last 
packet processed to sleep is shorter and the sleep period is longer.

When the radio is asleep, the access point sending data to the station 
must buffer packets at the AP until the station wakes up and requests 
any buffered packets.  If you have an AP that does not correctly support 
the PSP protocol you may experience packet loss or very poor performance 
while power management is enabled.  If this is the case, you will need 
to try to find a firmware update for your AP, or disable power 
management (via `iwconfig eth1 power off`)

To configure the power level on the Intel PRO/Wireless 3945ABG Network
Connection driver for Linux, you must use the iwpriv set_power command:

Setting the power management on and off via 'iwconfig power' is not
currently supported by the driver.

	iwpriv set_power 1-5  Set the power level as specified.
	iwpriv set_power 7    Set power level to default BATTERY level.

Setting the power level to any other value (0, 6, >7) will result in setting
the device into AC mode with Power Management disabled.  

If you explicitly set AC mode, the radio will always be on, however because
you have set a specific mode, it will still show as 'Power Management: on'
via wireless tools.

---

