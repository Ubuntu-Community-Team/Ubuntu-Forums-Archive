---
title: "Acer Aspire 5749 screen brightness"
date: 2011-10-29
forum: Hardware
---

### Post by qutorial on 2011-10-29
Hello, everyone!
Just became a member of community, installing Ubuntu 11.10 on my laptop Acer Aspire 5749 instead of MeeGo.
Currently I have one issue: brightness buttons. When I press them, the indicator shows up and progress-bar-like widget shows the changes in brightness. But the brightness itself stays the same and does not change.
Please, help!
Computer is like this:[URL="https://www.amazon.de/Acer-Aspire-5749-2334G50Mikk-Notebook-Intel/dp/B005IES4K6/ref=sr_1_sc_1?ie=UTF8&qid=1319883073&sr=8-1-spell"]
https://www.amazon.de/Acer-Aspire-5749-2334G50Mikk-Notebook-Intel/dp/B005IES4K6/ref=sr_1_sc_1?ie=UTF8&qid=1319883073&sr=8-1-spell[/URL]
Newly installed Ubuntu

---

### Post by timvanderwart on 2011-10-29
Hi everyone!

Like qutorial I have exactly the same issue. I have an 14inch Acer Aspire TimelineX 4830TG - 2434G, i5 intel core etc. running on 11.10. (dual boot with Windows7)

Almost everything works out of the box except for the brightness of the screen! My guess is that this is one of the main reasons why my laptop can be active for only 4 hours on it's battery: it should do 8 (if I believe what Acer promises that is...)

I tried fixing it by switching the graphics to integrated in BIOS but to no avail. Also I tried installing powertop but this froze the system in such a way that I had to reinstall Ubuntu completely!

Is there anyone who knows how to fix this, or anyone who knows how I could otherwise improve the battery life?

Tim (Netherlands)

---

### Post by timvanderwart on 2011-10-29
And on another note: is there a way to make the Acer power-manager button work under 11.10?

---

### Post by qutorial on 2011-10-29
The video card is Intel HD 3000. I found an [advice]("http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10") to create and change xorg.conf file to contain this: 

Section “Device”
Identifier	“Default Device”
Option	 “NoLogo”	 “True”
**Option “RegistryDwords”	“EnableBrightnessControl=1&#8243;**
EndSection

But the version of Ubuntu is different, plus it, they say, may lead to weird results.
Help needed :)

---

### Post by timvanderwart on 2011-10-30
I tried this also but it made my whole system freeze up. I had to reinstall everything.

I found out that in GRUB I can change the brightness, just not when Ubuntu runs...

---

### Post by qutorial on 2011-10-30
this forum looks like dead

---

### Post by qutorial on 2011-11-03
Still need an idea.

---

### Post by T0NYisME on 2011-11-03
hi guys, I too had some brightness issues and found this command helped 'xgamma -gamma .75' without quotes. Try adjusting the .75 with .95 as the max and .20 as the minimum, find what works best then add the command to the startup menu. Hope this helps ;-)

---

### Post by Toz on 2011-11-03
Open a terminal and run the following command:
```
lspci | grep VGA
```
You should get a reply something like:
> 01:00.0 VGA compatible controller: ......
Note the numeric device number (in this case, 01:00.0)

Now try in the terminal window:
```
sudo setpci -s <device> F4.B=<value>
```
...where <device> is the device number from the previous step and <value> is a hexidecimal value between 00 and FF. 

Examples:
```

sudo setpci -s 01:00.0 F4.B=00
sudo setpci -s 01:00.0 F4.B=7f
sudo setpci -s 01:00.0 F4.B=ff
```

Does this change the brightness?

---

### Post by qutorial on 2011-11-04
No, this does not change the brightness.

---

### Post by qutorial on 2011-11-04
I guess, gamma option is not what I need. The brightness of the backlight is under the question.

---

### Post by qutorial on 2011-11-04
lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

sudo setpci -s 00:02.0 F4.B=with different hex values here
doesn't work

---

### Post by Toz on 2011-11-05
What directories do you have under **/sys/class/backlight**? 
> $ ls /sys/class/backlight/
acpi_video0


If you view the contents of that directory, there should be files like brightness and max_brightness. 
> $ ls /sys/class/backlight/acpi_video0
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power	   device      power	       type


View contents of max_brightness to get maximum value:
> $ cat /sys/class/backlight/acpi_video0/max_brightness 
10


View contents of current brightness value:
> $ cat /sys/class/backlight/acpi_video0/actual_brightness 
10


Try to change value of brightness file to adjust brightness:
> $ echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness 


Does this work for you? If not, post back the contents of **/var/log/Xorg.0.log** and the results of:
```
lsmod
```
...and
```
cat /proc/cmdline
```

---

### Post by qutorial on 2011-11-05
I have this:

$ ls /sys/class/backlight/
acpi_video0  intel_backlight

Then

ls -al /sys/class/backlight/intel_backlight/
total 0
drwxr-xr-x 3 root root    0 2011-11-05 12:02 .
drwxr-xr-x 4 root root    0 2011-11-05 12:02 ..
-r--r--r-- 1 root root 4096 2011-11-05 18:24 actual_brightness
-rw-r--r-- 1 root root 4096 2011-11-05 18:24 bl_power
-rw-r--r-- 1 root root 4096 2011-11-05 18:24 brightness
lrwxrwxrwx 1 root root    0 2011-11-05 18:24 device -> ../../card0-LVDS-1
-r--r--r-- 1 root root 4096 2011-11-05 18:24 max_brightness
drwxr-xr-x 2 root root    0 2011-11-05 18:24 power
lrwxrwxrwx 1 root root    0 2011-11-05 12:02 subsystem -> ../../../../../../../class/backlight
-r--r--r-- 1 root root 4096 2011-11-05 18:24 type
-rw-r--r-- 1 root root 4096 2011-11-05 12:02 uevent

max is 976
when I write to the brightness, it changes!
Thank you!

But how to attach this to the Unity normal work?

Thank you!

---

### Post by qutorial on 2011-11-05
And little off-top, I have also Ubuntu on Samsung X11 (cv03) with NVidia graphics. No reaction at all on Fn-Up/Down. /sys/class/backlight is empty.

---

### Post by Toz on 2011-11-06
> **qutorial said:**
> I have this:

$ ls /sys/class/backlight/
acpi_video0  intel_backlight

Then

ls -al /sys/class/backlight/intel_backlight/
total 0
drwxr-xr-x 3 root root    0 2011-11-05 12:02 .
drwxr-xr-x 4 root root    0 2011-11-05 12:02 ..
-r--r--r-- 1 root root 4096 2011-11-05 18:24 actual_brightness
-rw-r--r-- 1 root root 4096 2011-11-05 18:24 bl_power
-rw-r--r-- 1 root root 4096 2011-11-05 18:24 brightness
lrwxrwxrwx 1 root root    0 2011-11-05 18:24 device -> ../../card0-LVDS-1
-r--r--r-- 1 root root 4096 2011-11-05 18:24 max_brightness
drwxr-xr-x 2 root root    0 2011-11-05 18:24 power
lrwxrwxrwx 1 root root    0 2011-11-05 12:02 subsystem -> ../../../../../../../class/backlight
-r--r--r-- 1 root root 4096 2011-11-05 18:24 type
-rw-r--r-- 1 root root 4096 2011-11-05 12:02 uevent

max is 976
when I write to the brightness, it changes!
Thank you!

But how to attach this to the Unity normal work?

Thank you!

What do you currently use on the kernel parameter line? This will show you:
```
cat /proc/cmdline
```

You should try with the value **acpi_backlight=vendor**. You can try it temporarily via [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

---

### Post by Toz on 2011-11-06
> **qutorial said:**
> And little off-top, I have also Ubuntu on Samsung X11 (cv03) with NVidia graphics. No reaction at all on Fn-Up/Down. /sys/class/backlight is empty.

Are you using the proprietary drivers? If so, try by adding **EnableBrightnessControl=1** in /etc/X11/xorg.conf. 

```
sudo gedit /etc/X11/xorg.conf
```
...and add in the DEVICE section, the following:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...save the file and log out and back in again.

---

### Post by qutorial on 2011-11-13
Any ideas?

---

### Post by Toz on 2011-11-13
> **qutorial said:**
> Any ideas?
Yeah, my last two posts. Any results?

---

### Post by jayarbie on 2012-01-17
Hi folks,

I have a new Acer Aspire 5749 and have the same problem now. Since the last post in this thread is now 2 months old, do you have any news? Did any of the suggestions here really help? Did anybody report the bug on launchpad?

Thanks a lot!
jb

---

### Post by Toz on 2012-01-17
As a first suggestion, try booting with the kernel parameters: **acpi_osi=Linux acpi_backlight=vendor**

If no luck, post back the results of the following commands:
```
sudo lspci -vnn | grep -A10 VGA
dmesg
ls /sys/class/backlight
```

...and the contents of /var/log/Xorg.0.log

---

### Post by jayarbie on 2012-01-18
[B]acpi_osi=Linux acpi_backlight=vendor  

[/B]works, thank you very much!

---

### Post by jayarbie on 2012-01-18
Hi,

unfortunately I celebrated to soon. The options solve the issue with the screen bightness but bring up another one: when they're set and you close the notebook lid the screen turns black (it's not in standby) and stays like this when you open the lid again: there's no chance to activate the screen afterwards (needs hard turn-off then). Could it help to try only one of the two options?

```
sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:0623]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
``````

ls /sys/class/backlight
acpi_video0  intel_backlight

```You can find the dmesg output here: [https://privnote.com/n/hiovsdzwgkivmnfa/#mtojvxtsbvbqpssz](https://privnote.com/n/hiovsdzwgkivmnfa/#mtojvxtsbvbqpssz)

jb

[EDIT: and here is the content of /var/log/Xorg.0.log [https://privnote.com/n/gobiwyrlevmhotzy/#ichmyckrczxbjwlp](https://privnote.com/n/gobiwyrlevmhotzy/#ichmyckrczxbjwlp) ]

---

### Post by Toz on 2012-01-18
Do the brightness buttons allow you to increase the brightness when you open the lid? Can you go to TTY1 (Ctrl+Alt+F1) and get a visible screen? Does returning back to the gui (Ctrl+Alt+F7) return the brightness?

Are you sure the system doesn't go into standby when you close the lid? From your dmesg:
> [ 52.892126] PM: Entering mem sleep
.....
[ 58.498541] PM: Finishing wakeup.
[ 58.498543] Restarting tasks ... done.
[ 58.503826] video LNXVIDEO:00: Restoring backlight state
[ 58.517862] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id


Notice the error message.

Can you post back the contents of /var/log/pm-suspend.log?

How about trying just **acpi_osi=Linux** and just **acpi_backlight=vendor** to see if that helps.

---

### Post by mind_master on 2012-01-19
The same problem with bightness at my Acer 5750G, when I close the lid it goes to the sleep mode and after it the brightness level is set to 0 and I need to increase it manually.

I've found some kind of a fix for Asus P31SD, but it helps only when I send my laptop to the sleep mode manually. 
Here's the fix: 
we have to create file like ```
/etc/pm/sleep.d/20_custom-asus-u31sd
```
and put this code there (don't look at buses stuff):
```
#!/bin/sh
 
BUSES="0000:00:1a.0 0000:00:1d.0"
 
case "${1}" in
    hibernate|suspend)
    # Switch USB buses off
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
    done
    # Saving brightness to /tmp/br
    cat /sys/devices/platform/asus-nb-wmi/backlight/asus-nb-wmi/brightness > /tmp/br
    ;;
    resume|thaw)
    # Switch USB buses back on
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    # Restoring brightness from /tmp/br
    cat /tmp/br > /sys/devices/platform/asus-nb-wmi/backlight/asus-nb-wmi/brightness
    ;;
esac
```

and brightness file for my Acer is not ```
/sys/devices/platform/asus-nb-wmi/backlight/asus-nb-wmi/brightness
``` but ```
/sys/class/backlight/intel_backlight/brightness
```

So any guesses why this doesn't work when I close the lid?

---

### Post by Toz on 2012-01-19
@mind_master, What is the contents (value) of the file /sys/class/backlight/intel_backlight/brightness before you put your system to sleep? 
```
cat /sys/class/backlight/intel_backlight/brightness
```

Are you able to change the brightness by directly manipulating the contents of that file:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where <value> is the brightness value you would like (should be a number between 0 and the contents of /sys/class/backlight/intel_backlight/max_brightness)

If this works, I would suggest that you change the code of /etc/pm/sleep.d/20_custom-asus-u31sd to read:
```

#!/bin/bash

case "${1}" in
    hibernate|suspend)
       # do nothing
       ;;
    resume|thaw)
       echo <value> > /sys/class/backlight/intel_backlight/brightness
       ;;
esac

```
...again, replace <value> with the desired value.

And if that works, you may also want to try this version of the script (that will save the current brightness before sleep and apply it back after sleep)
```

#!/bin/bash

case "${1}" in
    hibernate|suspend)
       cat /sys/class/backlight/intel_backlight/brightness > /tmp/BR
       ;;
    resume|thaw)
       echo `cat /tmp/BR` > /sys/class/backlight/intel_backlight/brightness
       ;;
esac

```

---

### Post by mind_master on 2012-01-19
> **Toz said:**
> @mind_master, What is the contents (value) of the file /sys/class/backlight/intel_backlight/brightness before you put your system to sleep? 
```
cat /sys/class/backlight/intel_backlight/brightness
```

Are you able to change the brightness by directly manipulating the contents of that file:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where <value> is the brightness value you would like (should be a number between 0 and the contents of /sys/class/backlight/intel_backlight/max_brightness)

If this works, I would suggest that you change the code of /etc/pm/sleep.d/20_custom-asus-u31sd to read:
```

#!/bin/bash

case "${1}" in
    hibernate|suspend)
       # do nothing
       ;;
    resume|thaw)
       echo <value> > /sys/class/backlight/intel_backlight/brightness
       ;;
esac

```
...again, replace <value> with the desired value.

And if that works, you may also want to try this version of the script (that will save the current brightness before sleep and apply it back after sleep)
```

#!/bin/bash

case "${1}" in
    hibernate|suspend)
       cat /sys/class/backlight/intel_backlight/brightness > /tmp/BR
       ;;
    resume|thaw)
       echo `cat /tmp/BR` > /sys/class/backlight/intel_backlight/brightness
       ;;
esac

```

It works when I just restore some fixed value but when I try to save and load it, then in /tmp/BR I get 0.

---

### Post by jayarbie on 2012-01-19
Hello Toz.

I tested the whole thing once again: 

**acpi_osi=Linux** neither fixes the screen brightness issue nor causes the screen wake-up issue on closing and opening the lid.
**acpi_backlight=vendor** vice versa, fixes screen brightness function buttons and causes the screen stays black problem

Here ist the content of the /var/log/pm-suspend.log [https://privnote.com/n/lzlrtjxdwjzjhuir/#ncwocynyeblgjtlr](https://privnote.com/n/lzlrtjxdwjzjhuir/#ncwocynyeblgjtlr)

greets & thanks for your support
jb

---

### Post by Toz on 2012-01-19
> **mind_master said:**
> It works when I just restore some fixed value but when I try to save and load it, then in /tmp/BR I get 0.

Hmmm. What is the value in that file prior to initiating suspend?

---

### Post by Toz on 2012-01-19
> **jayarbie said:**
> Hello Toz.

I tested the whole thing once again: 

**acpi_osi=Linux** neither fixes the screen brightness issue nor causes the screen wake-up issue on closing and opening the lid.
**acpi_backlight=vendor** vice versa, fixes screen brightness function buttons and causes the screen stays black problem

Here ist the content of the /var/log/pm-suspend.log [https://privnote.com/n/lzlrtjxdwjzjhuir/#ncwocynyeblgjtlr](https://privnote.com/n/lzlrtjxdwjzjhuir/#ncwocynyeblgjtlr)

greets & thanks for your support
jb

So it looks like when you close the lid, the system suspends - then resumes when you open the lid (according to that log file). 

After you open the lid (using both acpi_osi=Linux & acpi_backlight-vendor), do the function keys allow you to increase brightness (try both up and down brightness keys.

Also, try going to TTY1 (press Ctrl+Alt+F1 and back to TTY7 (press Ctrl+Alt+F7). Does the brightness return?

A couple more things:
Can you manipulate brightness directly by echoing a brightness value to the brightness file? Since you have 2 backlight interfaces, you will have to try this for each  interface. First, determine the current and maximum values. For the current values:
```
cat /sys/class/backlight/intel_backlight/brightness
cat /sys/class/backlight/acpi_video0/brightness
```
For the maximum values:
```
cat /sys/class/backlight/intel_backlight/max_brightness
cat /sys/class/backlight/acpi_video0/max_brightness
```

Then, try to echo a value (pick one between 0 and max_brightness) and see if it changes the brightness:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
echo <value> | sudo tee /sys/class/backlight/acpi_video0/brightness

```
... where <value> is a number between 0 and the contents of max_brightness from above.

Does the brightness change, and if so, for which interface?

---

### Post by mind_master on 2012-01-20
> **Toz said:**
> Hmmm. What is the value in that file prior to initiating suspend?

It doesn't exist but after closing/opening the lid, it has 0 inside.

---

### Post by Toz on 2012-01-20
In post #23, the your response showed that it did exist. Can you try this (before suspend) and post back the results:
```
ls /sys/class/backlight
```
```
for b in `ls /sys/class/backlight`; do echo "$b"; cat /sys/class/backlight/$b/brightness; cat /sys/class/backlight/$b/max_brightness; done
```

---

### Post by jayarbie on 2012-01-20
Hello Toz,

> After you open the lid (using both acpi_osi=Linux & acpi_backlight-vendor), do the function keys allow you to increase brightness (try both up and down brightness keys.Yes I can increase and decrease the brightness with the function keys with both options as well as with only the option acpi_backlight-vendor, acpi_osi=Linux doesn't seem to have an impact.

> Also, try going to TTY1 (press Ctrl+Alt+F1 and back to TTY7 (press Ctrl+Alt+F7). Does the brightness return?Going to TTY1 and returning back to TTY7 brings back the happily shining screen no matter if acpi_osi=Linux & acpi_backlight-vendor are active or not


And last but not least here are my results for echoing the screen brightness directly in the terminal:

First without acpi_osi=Linux & acpi_backlight-vendor

```
~$ cat /sys/class/backlight/intel_backlight/brightness
976
~$ cat /sys/class/backlight/acpi_video0/brightness
0
~$ cat /sys/class/backlight/intel_backlight/max_brightness
976
~$ cat /sys/class/backlight/acpi_video0/max_brightness
9
``````
~$ echo 15 | sudo tee /sys/class/backlight/intel_backlight/brightness
15
```-> the screen brightness changes

```
~$ echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
15
tee: /sys/class/backlight/acpi_video0/brightness: the argument is not valid

```-> the screen brightness doesn't change


Next with active acpi_osi=Linux & acpi_backlight-vendor

```
~$ cat /sys/class/backlight/acpi_video0/brightness
cat: /sys/class/backlight/acpi_video0/brightness: file or folder not found
~$ cat /sys/class/backlight/acpi_video0/max_brightness
cat: /sys/class/backlight/acpi_video0/max_brightness: file or folder not found
``````
~$ echo 15 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` -> the screen brightness changes

```
~$ echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
tee: /sys/class/backlight/acpi_video0/brightness: file or folder not found
```-> the screen brightness doesn't change

I hope this helps a little bit ...
jb

---

### Post by jayarbie on 2012-01-20
P.S.

```
 for b in `ls /sys/class/backlight`; do echo "$b"; cat /sys/class/backlight/$b/brightness; cat /sys/class/backlight/$b/max_brightness; done
acpi_video0
0
9
intel_backlight
976
976
```

---

### Post by Toz on 2012-01-20
> **jayarbie said:**
> P.S.

```
 for b in `ls /sys/class/backlight`; do echo "$b"; cat /sys/class/backlight/$b/brightness; cat /sys/class/backlight/$b/max_brightness; done
acpi_video0
0
9
intel_backlight
976
976
```

Ok, since acpi_osi=Linux doesn't make a difference, then drop it.
 
From what I understand, acpi_backlight=vendor fixes the issue with the brightness keys not working, but introduces a secondary problem where after you close and re-open the lid, the brightness is all the way down.

If this is correct, then you have 2 options:
1. On opening of lid, use the brightness keys to re-adjust the brightness

2. To automate this, create the following file:
```
gksudo gedit /etc/pm/sleed.d/20reset_brghtness
```
...with the following content:
```

#!/bin/bash

case "${1}" in
    hibernate|suspend)
       #do nothing
       ;;
    resume|thaw)
       echo 976 > /sys/class/backlight/intel_backlight/brightness
       ;;
esac

```
...save the file and make it executable:
```

sudo chmod +x /etc/pm/sleed.d/20reset_brghtness
```
...and give it a try.

---

### Post by MFaughn on 2012-01-20
I've got the same problem with the same controller.  My brightness is at 100% all the time no matter what.  Laptop is Acer 7750-6423 running 11.10 freshly installed.  I've tried all the steps in this post and a couple of other things to no avail.  Note that using the brightness keys (Fn <- and Fn -> for me) does show a graphic indicating that the brightness is changed.  Doing this also changes the brightness value in the brightness file mentioned in a couple of places in this thread...but that obviously has no effect.  

> **Toz said:**
> As a first suggestion, try booting with the kernel parameters: **acpi_osi=Linux acpi_backlight=vendor**

If no luck, post back the results of the following commands:
```
sudo lspci -vnn | grep -A10 VGA
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:050e]
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

> **Toz said:**
> ```
dmesg
ls /sys/class/backlight
```

:~$ ls /sys/class/backlight/
acpi_video0  intel_backlight

dmesg is in the attached tarball along with Xorg.0.log

> **Toz said:**
> 
...and the contents of /var/log/Xorg.0.log

thanks for any guidance.  this brightness is killing my eyes.  ouch.  I've got the weekend to resolve the issue or it goes back to the Mart of Wal from whence it came.

---

### Post by jayarbie on 2012-01-21
Hello,

yesterday I received a kernel update to 3.0.0-15-generic x86_64 and at the moment I think using the boot option acpi_backlight-vendor does not cause the problem  anymore (screen stays black when re-opening the lid). I will watch this for a while and test it in various constellations.

Thank you so far!
jb

---

### Post by Toz on 2012-01-21
@MFaughn, try updating your kernel to the newest version (3.0.0-15). Also, try with just the **acpi_backlight=vendor** parameter. After you boot with this parameter, post back the results of:
```
cat /proc/cmdline
```
...and whether it works or not.

---

### Post by Toz on 2012-01-21
> **jayarbie said:**
> Hello,

yesterday I received a kernel update to 3.0.0-15-generic x86_64 and at the moment I think using the boot option acpi_backlight-vendor does not cause the problem  anymore (screen stays black when re-opening the lid). I will watch this for a while and test it in various constellations.

Thank you so far!
jb

Yes. Kernel 3.0.0-15 includes a fix for intel i915 backlight problems as documented here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652"). Hopefully this fixes your issue.

---

### Post by qutorial on 2012-04-01
I confirm, with the new kernel and update to the grub configuration the brightness buttons work.
To use this fix

[LIST=1]
[*]Update your system 

```
sudo apt-get update 
sudo apt-get upgrade
```
[*]Edit the kernel load parameters: 

```
sudo gedit /etc/default/grub 
```There change the line starting as:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ... so on ... "

```adding a space before the closing quote" and a parametter setting 
**acpi_backlight=vendor**
I had this line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 acpi_backlight=vendor"

```Save the file, exit the editor.
[*]Update GRUB
```
sudo update-grub
```
[*]Reset your PC. Should work!
[/LIST]


I thank everyone for help very much!

---

