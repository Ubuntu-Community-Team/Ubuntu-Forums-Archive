---
title: "No Birghtness control on DELL Inspiron N4010"
date: 2013-06-30
forum: Hardware
---

### Post by Gfurst on 2013-06-30
Hello folks, I've installed Ubuntu 13.04 on my machine, Dell Inspiron N4010, a couple of days ago, after setting most things i cannot get brightness control.
The bright function keys do work, the slider even shows on right upper corner, but it does not change. Even the System Settings >> Birghtness and Lock, i can move the slider but no change.
This is a known issue with Inspiron, lost of post around and there's even a work around it:
```
echo X | sudo tee /sys/class/backlight/intel_backllight/brightness
```
Where X is the bright value from 1 to 4500 something. This works but is not functional.

Now, what i would like help with, is how to set up a functional work around, maybe as a starting script might work, but i won't be able to easily change brightness.
The /sys/class/backlight folder has two items, the intel_backlight and the dell_backlight one. Is there a way to choose between the two? I would prefer Dell.
Another user reported a 0video driver instead of the intel, and it works, any way to install and use this one instead?

Or finally if nothing works, a startup script to set brightness a bit low( it always turn on too strong), or a script to bind to the brightness keys?
Thanks, any help or suggestion is welcome.

---

### Post by Toz on 2013-06-30
Can you post back the results of the following commands for more information to see if a workaround can be drafted up:
1. Your current kernel command line:
```
cat /proc/cmdline
```
2. Info on your video cards:
```
sudo lspci -vnn | grep -A12 VGA
```
3. Your backlight interfaces and current values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
4. Acpi codes for your brightness function keys. First, open a terminal window and enter the following command:
```
acpi_listen
```
...the press once the function+brightness up combination and once the function+brightness down key combination. Then, post back what codes are dispalyed in the terminal window.

Hopefully we can try to replicate something like [this]("http://ubuntuforums.org/showthread.php?t=2156192&p=12702299&viewfull=1#post12702299") for your laptop.

---

### Post by Gfurst on 2013-07-01
Hey Toz thanks for the thoughtful reply, in order:

1. My current system command line
```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=665bde14-86b6-4d47-a4c6-59abb57daee3 ro quiet splash vt.handoff=7
```

2. Video info
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
```

3.Brightness stuff
```
/sys/class/backlight/dell_backlight
15
15
/sys/class/backlight/intel_backlight
4882
4882
```

4.Brightness keys
```
video DD02 00000087 00000000
video DD02 00000086 00000000
```

So as i thought, two different backlight drivers, brightness keys do work though, Unity's pop up for brightness shows up as expected but no changes occur.
Saw the link, its certainly a type of solution, i went looking for something filed as a bug that would fit, and came up with: [http://ubuntuforums.org/showthread.php?t=2148814](http://ubuntuforums.org/showthread.php?t=2148814)
LoL, gonna try the acpi_backlight=vendor, as i know the acpi_osi=!windows_2012 did not work for me.

---

### Post by Toz on 2013-07-01
Okay. I would try the following kernel parameters (one set at a time, remember to run "sudo update-grub" and reboot afterwards):
```
acpi_osi=
```
```
acpi_osi=Linux acpi_backlight=vendor
```

Note: the acpi_osi=\"!Windows 2012\" is a tricky one. The 2 important lines in your /etc/default/grub file should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by Gfurst on 2013-07-01
Hey the following didn't yield any results
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

Just to be clear, the first two parameters are supposed to go "LINUX_DEFAULT=" or the  "LINUX=" line in grub's config?
Or it just doesn't make much of difference?

---

### Post by Toz on 2013-07-01
It doesn't really matter which line, but its cleaner if you leave the defaults in the GRUB_CMDLINE_LINUX_DEFAULT line and put any additional parameters that you want to add in GRUB_CMDLINE_LINUX. You can check to see if they are applied by seeing if they show up when running the following command:
```
cat /proc/cmdline
```

I have a feeling these won't work for you, but give it a try anyways. You may have to fill in a bug report to get it properly dealt with. We can always create a workaround to get you access to the brightness controls.

EDIT: I think this might be the relevant bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1105604]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1105604")

---

### Post by Gfurst on 2013-07-01
Hey Toz, thanks, i was searching for that bug report without success.
I'll try the grub options tomorrow, sorry for taking too long, but took some time installing Win7 straight out of the recovery partition, then the bastard wiped out my system's partition, luckily it was easy to reinstall.
Now both working :)

I too think those will not work, let's see tomorrow. See ya

---

### Post by Gfurst on 2013-07-03
Hey back here, tested all of the boot parameters, none worked:
```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=a70a4762-30a7-429a-8250-08ee55791a8d ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7

```
The grub part was exactly as you told me, I wonder if the comas could make a difference.

Anyway, one interesting thing, after i reboot from windows, where i can change brightness, i carries over to Ubuntu, even though i can't change it starts dimmed.
Another interesting thing is that changing brightness via command line
```
echo X > /sys/class/backlight/intel_backlight/brightness
```
Will throw permission denied, maybe this could be a cause of user not being able to change.
Another thing i thought about is that i should be using the dell_backlight instead of intel_backlight.
Another user reported working same configuration but with a /backlight/video0, generic perhaps?

I will keep a look at the launchpad bug and also back it up, have to create account first.

---

### Post by Toz on 2013-07-03
> **Gfurst said:**
> Another interesting thing is that changing brightness via command line
```
echo X > /sys/class/backlight/intel_backlight/brightness
```
Will throw permission denied, maybe this could be a cause of user not being able to change.
This is because as a user you don't have access to that location. You need root privledges. Try instead:
```
echo X | sudo tee /sys/class/backlight/intel_backlight/brightness
```
> I will keep a look at the launchpad bug and also back it up, have to create account first.
Your best bet may be to follow that bug report.

As for a workaround, which one of your backlight interfaces responds with brightness changes:
```
echo 7 | sudo tee /sys/class/backlight/dell_backlight/brightness
echo 15 | sudo tee /sys/class/backlight/dell_backlight/brightness
```
...or
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by Gfurst on 2013-07-03
> This is because as a user you don't have access to that location. You need root privledges.
What i meant was that the whole problem's source, could be the user( the acpi keys group or whatever) that is supposed to control that brightness does not have access.
Anyway, I'll let that part people who actually know about it.

For the work around, the drive used is intel_backlight, the sudo tee code( found on another post) i did use it when it was too bright.
In fact just a startup script to set brightness to around 20% might be good enough.
I've guess a scripted solution for the keys could be hard, the permission thing would get in the way.

Thanks Toz

---

### Post by Toz on 2013-07-03
> In fact just a startup script to set brightness to around 20% might be good enough.
To set the default brightness on startup:
1. Edit /etc/rc.local:
```
gksu gedit /etc/rc.local
```
2. Add the following _above_ the *exit 0* command:
```
echo 976 > /sys/class/backlight/intel_backlight/brightness
```
3. Save the file.
*Note1: sudo tee is not required here because this script is run as root.
*Note2: 976 is about 20% of the max 4882. Feel free to adjust this number to suit.


> I've guess a scripted solution for the keys could be hard, the permission thing would get in the way.
Not necessarily. Lets try creating some scripts first to see if it will work. We can automate it later and attach it acpi to make it seamless.

1. Create the script to increase brightness:
```
gksu gedit /etc/acpi/brightup.sh
```
...and copy/paste this code:
```

#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4272 ]; then
   curr=$((curr+610));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
...and save the file.

2. Create the script to decrease brightness:
```
gksu gedit /etc/acpi/brightdown.sh
```
...and copy/paste the following code:
```

#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 610 ]; then
   curr=$((curr-610));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
...and save the file.

3. Make the scripts executable:
```

sudo chmod +x /etc/acpi/brightup.sh
sudo chmod +x /etc/acpi/brightdown.sh
```

4. Test like this:
```
sudo /etc/acpi/brightdown.sh
sudo /etc/acpi/brightdown.sh
sudo /etc/acpi/brightdown.sh
sudo /etc/acpi/brightup.sh
sudo /etc/acpi/brightup.sh
sudo /etc/acpi/brightup.sh
```
...does the brightness change?
*Note: sudo is only needed during testing. When we tie this into acpi, the scripts will run as root.

---

### Post by Gfurst on 2013-07-09
Hey Toz, i didn't forget about this, and finally got around creating those scripts, they work :D

I've made some small adjustments to suit me better:
The I've calculated for 20 steps instead of 8 and changed the min and max accordingly
```
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4638 ]; then
   curr=$((curr+244));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
```
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 246 ]; then
   curr=$((curr-244));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
And still working, now how do i tie these to the acpi keys?

---

### Post by Toz on 2013-07-09
> **Gfurst said:**
> And still working, now how do i tie these to the acpi keys?

Create the following files (as root):
_**/etc/acpi/events/dell-brightness-up**_
```

event=video DD02 00000087 00000000
action=/etc/acpi/brightup.sh
```
_**/etc/acpi/events/dell-brightness-down**_
```
event=video DD02 00000086 00000000
action=/etc/acpi/brightdown.sh
```

Make sure all 4 files are executable:
```

sudo chmod +x /etc/acpi/events/dell-brightness-up
sudo chmod +x /etc/acpi/brightup.sh
sudo chmod +x /etc/acpi/events/dell-brightness-down
sudo chmod +x /etc/acpi/brightdown.sh
```

Then restart acpid:
```
sudo service acpid restart
```

And hopefully all will work.

---

### Post by Gfurst on 2013-07-09
Hey Toz, it did work, with the exception of a small annoying thing: the brightness indicator will be stuck at max while the actual brightness changes.
I thought this could be tied to the dell_backlight variables, even tried adding it to the scripts to it could change accordingly. But it resets with every acpi keypress.

Anyway my problem is solved, I'll mark the thread. Thanks for the help, you're great at this.
If you don't there is another topic I need help with: [http://ubuntuforums.org/showthread.php?t=2159894](http://ubuntuforums.org/showthread.php?t=2159894)

---

