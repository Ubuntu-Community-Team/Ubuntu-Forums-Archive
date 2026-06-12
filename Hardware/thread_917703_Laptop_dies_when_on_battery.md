---
title: "Laptop dies when on battery"
date: 2008-09-12
forum: Hardware
---

### Post by zukker on 2008-09-12
Hi

I have a problem which i don't really know why its happening. I recently removed win XP and installed ubuntu on my laptop. But i got this annoying problem.
When i try to run on the laptop battery ubuntu just crashes, i don't know how fix it. Is it that my battery is dead or some setting in ubuntu?

Using a Asus F5V and ubuntu Hardy.. 

any help appreciated.

---

### Post by sdennie on 2008-09-12
Does it completely crash or does it try to shutdown?  One thing you could try would be to go to System->Preferences->Power Management and, in the "On Battery" tab, set all the settings so that no ACPI events cause the machine to turn off (So, set everything to "Do nothing" and "Never").

---

### Post by zukker on 2008-09-12
The screen dims then everything just stops..then all i can do is reboot with the power plugged in.

Tried your what you said and it didn't improve the situation.

---

### Post by IntuitiveNipple on 2008-09-12
> **zukker said:**
> The screen dims then everything just stops..
Does it lose all power, go cold?

Or does it *lock-up* but power remains (LEDs remain lit, hard-disk whirring/vibrating, etc.) ?

---

### Post by zukker on 2008-09-12
Power remains, the fan(s) still operates. But the screen lock-up.

---

### Post by IntuitiveNipple on 2008-09-12
Get some information from the ACPI sub-system. Install the tool:
```

sudo apt-get install acpitool

```
Check the AC adapter and battery:
```

acpitool -aB

```
Try running a log monitor before switching off the AC and see what ACPI messages are processed:
```

tail -f /var/log/acpid

```
It might be best to do this from a text console rather than the GUI. Use Ctrl+Alt+F1 to switch, log-in, then run the command. If the PC locks copy down or photograph the lines you can see. You can test whether it has locked up after removing AC power by pressing Ctrl+Alt+F2 to switch to one of the other consoles. 
If the consoles work then you might have a problem with X. Try switching back to the GUI with Ctrl+Alt+F7.

---

### Post by zukker on 2008-09-13
acpitool -aB results in: Ac-Adapter 1: on-line

tail -f /var/log/acpid

```

client connected 5200 [111:123]
1 client rule loaded
client connected from 5370 [0:0]
1 client rule loaded
starting up
74 rules created
client connected from 5234 [111:123]
1 client rule loaded
client connecteed from 5401 [0:0]
1 client rule loaded

```

ac-power removed and this:

```

exiting
starting up
74 rules loaded
client connected from 5200 [111:123]
1 client rule loaded
client connected from 5370 [0:0]
1 client rule loaded
recieved event ac_adapter AC0 00000080 00000000
notifying client 5200 [111:123]
notifying client 5370 [0:0]
client has disconnected
executing action /etc/acpi/power.sh
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
action exited with status 0
completed event ac_adapter AC0 00000080 00000000
recieved event hotkey ATKD 00000057 00000000
notifying client 5200 [111:123]
completed event
recieved event processor CPU1 00000081 00000000
notifying client 5200 [111:123]
completed event processor CPU1 00000081 00000000

```

and i was unable to switch to the GUI and another console.

---

### Post by IntuitiveNipple on 2008-09-13
> **zukker said:**
> acpitool -aB results in: Ac-Adapter 1: on-line

This would appear to indicate part of the problem. The output you should expect to see would include the battery details, like this:
```

$ acpitool -aB
  Battery #1     : present
    Remaining capacity : 9350 mWh, 16.71%
    Design capacity    : 57720 mWh
    Last full capacity : 55970 mWh, 96.97% of design capacity
    Capacity loss      : 3.032%
    Present rate       : unknown
    Charging state     : charging
    Battery type       : rechargeable, LiOn
  AC adapter     : on-line

```
Let's check what Linux finds s it starts up. Attach a (compressed) copy of /var/log/dmesg created like this:
```

cat /var/log/dmesg | gzip >dmesg.log.gz

```
It is possible there's some kind of ACPI (Advanced Configuration and Power Interface) problem that leads to the battery being incompletely recognised.

---

### Post by zukker on 2008-09-13
Okay

here it is

thanks for the help btw :)

---

### Post by IntuitiveNipple on 2008-09-13
First the good news. ACPI initially recognises the battery information in the ACPI DSDT (Differentiated System Description Table) and reports the battery is found, too:
```

[   36.944585] ACPI: Battery Slot [BAT0] (battery present)
[   36.953687] ACPI: AC Adapter [AC0] (on-line)

```
Now the wobbly bit. I noticed that when ACPI starts the EC (Embedded Controller) it doesn't manage to switch to interrupt mode (the expected and preferred) but instead falls back to polling mode:
```

[   22.504046] ACPI: EC: Look up EC in DSDT
[   22.591464] ACPI: Interpreter enabled
[   22.591468] ACPI: (supports S0 S1 S3 S4 S5)
[   22.591486] ACPI: Using IOAPIC for interrupt routing
[   22.597644] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   22.597646] ACPI: EC: driver started in poll mode

```
I'd expect to see something similar to this:
```

[   12.349551] ACPI: EC: Look up EC in DSDT
[   12.357214] ACPI: Interpreter enabled
[   12.357217] ACPI: (supports S0 S3 S4 S5)
[   12.357231] ACPI: Using IOAPIC for interrupt routing
[   12.357390] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   12.386435] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   12.386437] ACPI: EC: driver started in interrupt mode

```
I'm not sure if this is related to the problem you're experiencing but it is suspicious, especially as 'acpitool -aB' didn't report finding a battery (can you double-check that just in case there was a mistake using the command the first time?).

I'll need to think some more on this to figure out what diagnostics would help here.

---

### Post by zukker on 2008-09-13
Alright

if i type: acpi -aB i get what i wrote before 
however if i type:
acpi -ab i get this: 
Battery 1: Charged 100%
Ac Adapter 1: On-line

---

### Post by IntuitiveNipple on 2008-09-13
That is really weird! Give me some time to think about it :)

If anyone else has seen this behaviour or has some ideas on it, please dive in!

---

### Post by IntuitiveNipple on 2008-09-13
Please try removing and re-inserting the battery (with the system on AC power) whilst capturing the udev events and then report the results here:
```

sudo udevmonitor --environment

```

---

### Post by zukker on 2008-09-13
here goes

```

UDEV [1221315904.772133] remove /devices/LNXSYSTM:00/device:00/PNP0A03:00/PVP0C0A:00/power_supply/BAT0 (power_supply)
UDEV_LOG =3
ACTION = remove
DEVPATH = /devies/LNXSYSTM:00/device:00/PNP0A03:00/PVP0C0A:00/power_supply/BAT0 (power_supply)
SUBSYSTEM = power supply
POWER_SUPPLY_NAME = BAT0
POWER_SUPPLY_TYPE = Battery
POWER_SUPPLY_PRESENT = 0
SEQNUM = 2802
UDEVD_EVENT =1

```

---

### Post by IntuitiveNipple on 2008-09-13
When the battery was re-inserted did udev not report events?

---

### Post by zukker on 2008-09-13
hmm i've must have forgotten to copy that.

here comes the part when the battery is inserted again

```

UEVENT[1221337910.305380] add      /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
ACTION=add
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
SEQNUM=2757

UDEV  [1221337910.306584] add      /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
SEQNUM=2757
UDEVD_EVENT=1

UEVENT[1221337910.308566] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2758

UEVENT[1221337910.308653] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2759

UEVENT[1221337910.311502] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2760

UDEV  [1221337910.311696] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2758
UDEVD_EVENT=1

UDEV  [1221337910.327114] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2759
UDEVD_EVENT=1

UDEV  [1221337910.328235] change   /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0
SUBSYSTEM=power_supply
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12510000
POWER_SUPPLY_CURRENT_NOW=693000
POWER_SUPPLY_ENERGY_FULL_DESIGN=46200000
POWER_SUPPLY_ENERGY_FULL=43142000
POWER_SUPPLY_ENERGY_NOW=43142000
POWER_SUPPLY_MODEL_NAME=F5---22
POWER_SUPPLY_MANUFACTURER=ASUSTEK
SEQNUM=2760
UDEVD_EVENT=1

```

---

### Post by IntuitiveNipple on 2008-09-13
Well, all that makes it look as if the battery itself is fine, and talking to the OS.

Let's put the battery mis-report of acpitool to one side for now in case it is a red-herring. I'll do some thinking and digging on what other diagnostics will be useful and come back to you.

---

### Post by IntuitiveNipple on 2008-09-14
Still thinking :)

---

### Post by zukker on 2008-09-22
anyone got any idea? :)

---

### Post by IntuitiveNipple on 2008-09-22
Find out if this is an X or Gnome issue by starting the PC afresh and not logging in to the GUI. Switch to a console with Ctrl+Alt+F1. Log-in, stop X:
```

sudo /etc/init.d/gdm stop

```
Now start an application to monitor the system that is always updating its display:
```

top

```
Finally, remove the AC adapter and see if the PC locks up.

If the top display continues updating that looks good on the face of it, but now quit top (press **Q**) and try doing some actions at the command-line. Maybe check the ACPI daemon log:
```

tail /var/log/acpid

```

Re-insert the AC Adapter.

What you're going to have to do, unless you want to make wild guesses, is slowly reduce the set of circumstances where the lock-up occurs to a small enough set that you can identify the applications or kernel interactions that are responsible.

If the PC doesn't lock-up when running just the command line, the next thing to try is with X and Gnome running but *without logging in*:
```

sudo /etc/init.d/gdm start

```
Now switch back to the text console (Ctrl+Alt+F1) and go through the procedure of running top, removing the AC adapter, etc. If the text console seems to be okay switch to the GDM log-in screen (Ctrl+Alt+F7) and check if it is still responding (but don't log-in). Re-insert the AC adapter.

If that works, continue to log-in. As soon as it is logged-in switch back to the text console (Ctrl+Alt+F1) and do the 'top' test again.

If the text console continues to work switch to the GUI (Ctrl+Alt+F7) and test whether it has locked up or is still interactive.

If it has locked up that could indicate a problem with the user profile.

Switch back to the text console (Ctrl+Alt+F1) or, if that won't respond, try using the magic sys-request sequence to kill all processes on the GUI console.

First ensure the system thinks it is on the GUI console, regardless of what is displayed on the (frozen) screen by pressing Ctrl+AltF7, then press Ctrl+Alt+SysRq+K.

If you're lucky that will kill X and Gnome and they will restart, leaving you at the GUI log-in prompt.

If the magic sys request fails, restart the PC.

Now you need to determine if something in that user profile is responsible. Start the PC, log-in, and then use System > Administration > Users and Groups to create another user.

Restart the PC so no settings from the current user are inherited and then log-in to the GUI with the new user credentials.

Do the AC adapter removal and see if the system still locks-up.

If so, this sequence of tests has told you:

1. The fault doesn't occur without X and Gnome running
2. The fault doesn't occur if Gnome is running without a user logged in
3. It affects a clean user profile as well as a well-used one

Hopefully you can see that by figuring out the permutations of your actual results it is possible to define more narrowly the circumstances when the lock-up happens, and thus focus investigations.

---

### Post by zukker on 2008-09-22
> Finally, remove the AC adapter and see if the PC locks up.

it does lock-up here

> Do the AC adapter removal and see if the system still locks-up.

and here =(

---

### Post by IntuitiveNipple on 2008-09-22
In some ways that is good news, because it means the problem exists without all the complications of X and Gnome power management.

Another test to try and further reduce the problem scope. Restart the system and use the GrUB boot menu to start in Recovery mode.

Once started do the test again.

If it happens then you've managed to reduce the scope to a manageable and understandable size.

---

### Post by zukker on 2008-09-22
alright :)

top keeps updating when in recovery mode even when its on battery.

> tail /var/log/acpid 

```

completed event "video LCDD 00000086 00000000"
recieved event "video LCDD 00000086 00000000"
notyfying client 5241[111:123]
notifying client 5408[0:0]
executing action "/etc/acpi/video_brightnessup.sh"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
action exited with status 0
completed event "video LCDD 00000086 00000000"
exiting

```

> sudo /etc/init.d/gdm start

black screen

---

### Post by IntuitiveNipple on 2008-09-22
```

executing action "/etc/acpi/video_brightnessup.sh"

```
Hmmm... what's the chances that scripts being executed by the acpi daemon are causing a problem?

First, check what scripts are being executed when the AC adapter is removed. Empty the log-file:
```

sudo mv /var/log/acpid /var/log/acpid.old
sudo touch /var/log/acpid
sudo chown root:adm /var/log/acpid
sudo chmod  640 /var/log/acpid

```
Now remove the AC adapter. The log-file should contain only the reports from that event.
Now check what scripts were executed:
```

egrep 'executing action' /var/log/acpid

```
Then consider disabling those listed by removing their executable status:
```

sudo chmod a-x /etc/acpi/${SCRIPTNAME}

```
Obviously replace ${SCRIPTNAME} with each script's name.

You could disable them all to begin with, test, and then selectively re-enable them one at a time until you can reproduce the fault. Alternatively, selectively disable them one at a time until the fault stops occurring.

---

### Post by zukker on 2008-09-22
still the same issue :S

---

### Post by IntuitiveNipple on 2008-09-22
> **zukker said:**
> still the same issue :S
What script actions are executed?

Did you disable them all?

Did you check (by monitoring the acpid log) that when the AC adapter is removed the scripts fail to execute?

It might be a better idea to move the executed scripts to a temporary directory so they can't accidentally be executed.

---

### Post by zukker on 2008-09-22
> What script actions are executed?

Did you disable them all?

Did you check (by monitoring the acpid log) that when the AC adapter is removed the scripts fail to execute?

It might be a better idea to move the executed scripts to a temporary directory so they can't accidentally be executed.

hmm, okay now the log is empty...and removing/reinstering the AC-adapter doesn't add anything in /var/log/acpid

---

### Post by IntuitiveNipple on 2008-09-22
> **zukker said:**
> hmm, okay now the log is empty...and removing/reinstering the AC-adapter doesn't add anything in /var/log/acpid
Hmmm, it might need acpid restarting too:
```

sudo /etc/init.d/acpid restart

```

---

### Post by zukker on 2008-09-22
Okay.

When going from AC power -> battery power there's only one script running at this moment.

```
/etc/acpi/power.sh
```

however i got this when removing the battery aswell don't know if it important, might aswell post it.

```
 Stopping anca(h)ronistic cron anacron
```

---

### Post by dvirusslayer on 2008-11-07
hi my battery seems fine on my vista when I dual partition but on Ubuntu, when I try to run on my battery the computer just simply goes cold so I really don't understand this I run a compaq f750 US
thanks in advance

---

