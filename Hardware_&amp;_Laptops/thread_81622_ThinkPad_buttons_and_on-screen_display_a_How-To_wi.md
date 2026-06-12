---
title: "ThinkPad buttons and on-screen display: a How-To with questions"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-10-24
**A how-to for visual feedback for the ThinkPad buttons**

This is an *almost* complete guide to getting on-screen display for the ThinkPad buttons. One last problem is baffling to me, and I hope an expert can help.

**1.** Install **tbp** from the universe repository; no either do one one of two things (or both, if you want):

Either (slightly dangerous if you mess things up) edit the file /etc/modules by adding the string "nvram" (no quotation marks) to a line at the end of the file, or (less dangerously), using the System | Preferences menu, use Sessions, go to the Startup Programs tab and add the line:

```
tpb -d
```

and assign any order; the default of 50 is fine.

Then go to a terminal and enter:
```
sudo adduser yourusername nvram
```
Log in and log out. Most of the ThinkPad buttons will now appear with visual feedback near the bottom of the screen. (It's possible you may need to reboot, but logging in and out should be enough).

**2.** On ThinkPads with 802.11g and Bluetooth, the Fn+F5 button seems to turn off both 802.11g and Bluetooth. Let's add a feature that uses Fn+F6 to toggle Bluetooth only, complete with visual feedback on screen (in addition to the Bluetooth LED).

Download and install **xosd-bin**. Then create three scripts (based on scripts made for Hoary by J. Kraemer and others). Here are the scripts with their names and contents:

**/etc/acpi/ibm-bluetooth-osd.sh**

```
#!/bin/sh
#/etc/acpi/ibm-bluetooth-osd.sh

. /etc/acpi/osd

cat /proc/acpi/ibm/bluetooth|grep status|grep -q enabled
if [ $? == 0 ]; then
#	echo "disabling bluetooth"
	echo disabled > /proc/acpi/ibm/bluetooth;
	osd_print 'Bluetooth off'
else
#	echo "enabling bluetooth"
	echo enabled > /proc/acpi/ibm/bluetooth;
	osd_print 'Bluetooth on'
fi

```

**/etc/acpi/events/ibm-bluetooth**

```
# /etc/acpi/events/ibm-bluetooth
# This is called when the user presses Fn-F6 button and calls
# /etc/acpi/ibm-bluetooth-osd.sh for further processing.

event=ibm/hotkey HKEY 00000080 00001006
action=/etc/acpi/ibm-bluetooth-osd.sh

```

**/etc/acpi/osd**

```
#!/bin/bash

# /etc/acpi/osd
# written by J Kraemer, output and location modified by EM for Breezy

osd_print() {
  echo $1 | osd_cat -d 3 -p bottom -A left -O 1 -s 2 -S black -i 25 -o -21 -c blue &
}

```

In a terminal enter

```
sudo chmod +x /etc/acpi/osd
sudo chmod +x /etc/acpi/ibm-bluetooth-osd.sh

```

Edit the file /etc/crontab and add this line at the end:

```
@reboot root sleep 20; echo 0xffff > /proc/acpi/ibm/hotkey
```

Reboot. Press Fn+F6 and watch the Bluetooth light toggle on or off.

Now, **here's the question**. As you'll notice, the on-screen display doesn't work with Fn+F6. You can make it work for the current session by opening a terminal and entering:

```
sudo /etc/init.d/acpid restart
```

but there must be a way around this. I've tried adding nvram to /etc/modules, but that doesn't help either. Can anyone help sort this one out? If so, it's easy to add visual feedback to the Fn+F5 button also, using the same technique as described above and modifying the existing ibm-wireless.sh script.

---

### Post by emendelson on 2005-10-25
I've now edited the first post, because it turns out that in Breezy there's no need to run tpb -d as a startup program in a session; you can instead add "nvram" (no quotes) at the end of /etc/modules, and the effect is the same (after a reboot). All that's needed for visual display of the ThinkPad buttons is to use the adduser command to add yourself to nvram. If anyone can help with the question at the end of the first post, I'd be very grateful - that's still the big puzzler in this procedure.

---

### Post by thinkpadg41 on 2005-10-27
Ubuntu Breezy Badger 5.10 and thinkpad G41, installed the tpb :

apt-get install tpb

the Brightness is working with OSD, but the Volume buttons only showing the OSD with no effect of sound, min or max still the same. The wireless network light should be on with Fn+F5, but does not work at all.

---

### Post by emendelson on 2005-10-27
Possibly a difference in the way the G series works?

---

### Post by sonytony18 on 2005-12-20
I have a thinkpad R32 and have got almost all the special button and Fn+<> combinations working using the info given in this great article giving good details on how to customize the thinkpad buttons, [http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html")
(Note: the article is for T42 but works equally well for older models)

I have the same problem with volume buttons, the OSD shows up fine but the volume does not change. 

I looked into the /etc/tpbrc and found from the comments that controlling the mixer via the buttons is disabled by default and should be enabled only if your model does not have a hardware mixer. It says you need to enable write access to the nvram device to turn it on, but i havent tried it yet. Also I use ALSA as my sound input/output and the comments mention only OSS so I am not sure whether it will work if I enable it.

---

