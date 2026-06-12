---
title: "Using Asus Led's status"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by AndreAPL on 2005-09-11
Hi there.I wonder if i can use my Asus M2000N status leds, in windows i can use it for new mail notification and wireless on/off. already know that can manually control them,but how to use with a email program, and the other when the wireless is working.

Thanks

---

### Post by easterndodo on 2005-12-05
Well, for mail you might use a mail program that allows you to run a program chosen by yourself when new mail arrives: maybe you create a script containing:
   echo 1 > /proc/acpi/asus/mled

to light on the "new mail" led.

For the wireless, I might propose you the script i created :cool: to turn on and off the wireless by pressing Fn+F2 (like in windows):

[FONT="Courier New"]#!/bin/bash
# Find and enable/disable wireless devices

state=`cat /sys/bus/pci/drivers/ipw2200/0000:01:05.0/rf_kill`

if [ $state = 0 ] 
then
	echo 1 > /sys/bus/pci/drivers/ipw2200/0000:01:05.0/rf_kill
	echo 0 > /proc/acpi/asus/wled
else
      	echo 0 > /sys/bus/pci/drivers/ipw2200/0000:01:05.0/rf_kill
	echo 1 > /proc/acpi/asus/wled
fi[/FONT]

Probably you'll have to adapt the line with "ipw2200/0000:01:05.0" with the bus id of your laptop. I have an intel pro/2200BG wireless card integrated in the laptop, so basically you do an [FONT="Courier New"]lspci[/FONT]
and find the bus ID for the card; on my laptop the output of lspci contains the line:
 [FONT="Courier New"]0000:01:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)[/FONT]

If you have another network wireless card the procedure should be similar.

On Intel ones, echoing 1 on the file rf_kill shuts down the card, and echoing 0 turns it on (like the Fn+F2 in windows).

My script turns on and off alternatively the card and lights the "wireless" led on asus laptops. To get it associated to the Fn+F2 hotkey you have to create  a file like this and put it into /etc/acpi/events:

[FONT="Courier New"]
# /etc/acpi/events/asus-wireless
# This is called when the user presses the wireless button and calls
# /etc/acpi/wireless.sh for further processing.

event=hotkey ATKD 0000005d
action=/etc/acpi/asus-wireless.sh[/FONT]

The key ID could be different, to find it kill the [FONT="Courier New"]acpid[/FONT] daemon and do a [FONT="Courier New"]cat /proc/acpi/event[/FONT], then press Fn+F2 and on the screen the key id will be printed.

So place the script in /etc/acpi (on my computer i named it "asus-wireless.sh") and the other file in /etc/acpi/events (I named it "asus-wireless"). Restart the acpid daemon (sudo /etc/init.d/acpid restart) and you should be ok!

---

### Post by AndreAPL on 2006-04-16
thanks. nice work
now using thunderbird with asus mail-led plugin :D

---

### Post by songochain on 2006-04-17
Any idea to disable/enable touchpad using asus-a4k buttons?? They 're near power button.
I've found this script:
```

#!/bin/sh

# get the current state of the touchpad
TPSTATUS=`synclient -l | grep TouchpadOff | awk '{print $3}'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   synclient TouchpadOff=1
else
   synclient TouchpadOff=0
fi

```

I've installed synclient but when i want to know if it runs ok, this happens:
```
synclient -h
Can't access shared memory area. SHMConfig disabled?

```

Any idea??
Thanks

---

### Post by unixlike on 2007-10-17
Hi!
I have resolved the same problem with your script.

Only problem is that when I stop the acpid daemon and I run cat... the hotkeys fn+F2 is not recognized.
The other hotkeys are recognised succesfully.

What can I do?

Thanks.

---

