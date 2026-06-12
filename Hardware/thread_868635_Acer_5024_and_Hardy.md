---
title: "Acer 5024 and Hardy"
date: 2008-07-24
forum: Hardware
---

### Post by Tha-Fox on 2008-07-24
I've had a hard fight with my Acer laptop so I decided to write down something about my experiences with Hardy. I installed on empty formatted partition using 8.04.1 version.

**Installation:**
I installed Hardy using live-cd. Wi-fi card (Broadcom :evil:) is detected while trying to determine network settings, but it doesn't work yet. Everything else works normally.

**First boot:**
Every essential part of the system works out of the box except wi-fi. This is quite an improvement compared to installations few years ago.

**How to get wi-fi work:**
You need ethernet-connection (or you need Windows-drivers. I haven't tested this method.) You can get a new firmware for your card by going to Restricted Drivers Manager. (Maybe another name, I have Finnish desktop.) There choose Broadcom-card and enable it. (If you can't see the card there, then add more repositories, instructions can be found from this forum.) If it asks you where to get firmware from, choose Internet if you have some other connection (ethernet). You can also choose Windows-drivers from your hard disk, if you already have them.

There are now two ways to activate wi-fi. With Hardy I used acerhk, but with earlier versions I've used acer_acpi and succeeded with both. Open the terminal and copy-paste either of these methods one line at the time. Just to remind you, either acerhk or acer_acpi, **not both!**

**acerhk-way**

```

modprobe acerhk
echo "on" > /proc/driver/acerhk/wirelessled

```

**acer_acpi-way**

```

sudo modprobe acer_acpi
sudo chmod 777 /proc/acpi/acer/wireless
sudo echo 1 > /proc/acpi/acer/wireless

```

After that you should see your wi-fi -led blinking and trying to connect. Now reboot and check whether it still works or not. In other words, is the wi-fi -led on or off. If it´s off, don't worry :) Mine was too. We must add the code we used to activate the led to be executed automagically in the start-up.

First we open up an editor:

```

sudo gedit /etc/rc.local

```

Now you must copy-paste the code you used (acer-hk or acer_acpi-way) between the last comment line (beginning with #) and "exit 0". So if I use for example acerhk, this file should look like this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe acerhk
echo "on" > /proc/driver/acerhk/wirelessled
exit 0

```

Remember to save before exiting editor. Now the card should work after reboot.

**Ati x700**

This works out-of-the-box, but if you need 3D and/or you want desktop-effects, I suggest to install fglrx-driver from Restricted Drivers Manager.

I am currently trying to figure out how to use TV as display while watching movies via either S-Video- or VGA-cable. Instructions are welcomed and needed :) My card reader is physically broken so I can't test it. I'm going to test the infrared-port after I get the TV-issue solved.

I've installed Hardy two times. First time I upgraded from Gutsy but my laptop freezed every now and then. I couldn't find any other solution to that than downgrading back. This time I haven't experienced any freezes (yet), but we'll see...

Any comments about instructions?

---

### Post by Tha-Fox on 2008-07-24
My Acer worked for a week and today it has crashed twice in 15 minutes. Just like [here]("http://ubuntuforums.org/showthread.php?t=836686").

---

