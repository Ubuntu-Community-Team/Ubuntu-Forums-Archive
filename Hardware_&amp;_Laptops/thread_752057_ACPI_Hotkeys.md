---
title: "ACPI Hotkeys"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by Burillo on 2008-04-11
I was wandering why my hotkeys don't work with Gutsy for a long time (they did with Feisty) and, instead of whining about that i sit down and write these scripts. Hope this helps someone.

NOTE: you should have acpi, acpid and acpi-support installed.

i didn't have the will to find out why it fails under certain circumstances so i just hard coded some values. awfully LAME i know but i'm lazy!

you need to adjust these scripts if you want to use them on the other laptops.

1. Where are the scripts?

 the scripts that are triggered by the acpi basically reside in /etc/acpi. The naming of the scripts depends on your system.

2. What do i need to know?

first, you should know where is your acpi-backlight process.
```
more /usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux
```
look through this text file and find out where your baclkight process is located. Lookup for your laptop manufacturer's name and you will find a filename beginning with /proc/acpi. For example, my laptop's manufacturer is ASUS, so i look for "asus" in that file:
```
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "asus" ]; then
        # cat /proc/acpi/asus/brn
        #  5
        value="`cat $HAL_PROP_LINUX_ACPI_PATH`"
```
That is, my backlight process is located in /proc/acpi/asus/brn.

Next, you may need to know what values does it accept. To find out the maximum brightness value you need to first input some higher number into the process:
```
echo 999 > /proc/acpi/asus/brn (change the path with one you need)
```
and then check what is the maximum value:
```
cat /proc/acpi/asus/brn (change the path with one you need
```
mine returned 15, so i figured out that was maximum LCD brightness value. The lowest should obviously be 0, but you better check this too.

3. The scripts

this is for turning brightness UP
```
#!/bin/bash
FILENAME='/proc/acpi/asus/brn'
read line < $FILENAME
elif [ "$line" -eq 9 ]; then
echo 10 > /proc/acpi/asus/brn
else
line=$(expr $line + 1)
echo $line > $FILENAME
fi

```

this one is to turn brightness DOWN
```
#!/bin/bash
FILENAME='/proc/acpi/asus/brn'
read line < $FILENAME
#              if [ "$line" -eq VALUE ]; then
#              echo VALUE > $FILENAME           OPTIONAL - ONLY IF MINIMAL VALUE IS NOT 0
elif [ "$line" -eq 10 ]; then
echo 9 > $FILENAME
else
line=$(expr $line - 1)
echo $line > $FILENAME
fi

```

I ain't that cool in bash scripting, so the reason why i have to hard-code 9 and 10 breakup remains unknown for me. Feel free to suggest the universal solution.

4. Assigning scripts to buttons

To find out which script is used by certain key you have to press the key (i. e. Fn+F6 for brightness up in my case) and then type```
tail /var/log/acpid
```in the console. The output should be something like this:
```
[Fri Apr 11 13:55:00 2008] received event "video LCDD 00000086 00000000"
[Fri Apr 11 13:55:00 2008] notifying client 5206[103:116]
[Fri Apr 11 13:55:00 2008] notifying client 5791[0:0]
[Fri Apr 11 13:55:00 2008] executing action "/etc/acpi/video_brightnessup.sh"
[Fri Apr 11 13:55:00 2008] BEGIN HANDLER MESSAGES
[Fri Apr 11 13:55:00 2008] END HANDLER MESSAGES
[Fri Apr 11 13:55:00 2008] action exited with status 0
[Fri Apr 11 13:55:00 2008] completed event "video LCDD 00000086 00000000
```
it may be different, but the key is the NAME - in this case it's "/etc/acpi/video_brightnessup.sh" (remember i told you all scripts reside in /etc/acpi?). This is the file you need to replace (create backups, just in case!) to get this working.

5. P. S.

No OSD or graphical stuff will be shown - only the actual brightness change.

---

