---
title: "[SOLVED] LCD backlight brightness (8.04)"
date: 2008-09-17
forum: Hardware
---

### Post by rekado on 2008-09-17
ALOHA!

I've been reading every single entry on LCD backlight issues I could find and since nothing helped solving the problem I would like to ask for help again.

Using the brightness hotkeys of my Haier A61 notebook (rebranded Clevo I guess) the on-screen-display appears and changes. The brightness however stays the same.

I can change the brightness before booting Ubuntu. When I setup the brightness to be at maximum and boot Linux, only the hotkey for lowering the brightness is recognized. When I try the key combination for increasing brightness the OSD does not show up.

The opposite is the case when setting the brightness to the lowest setting before booting. Adjusting the brightness to a medium level before boot allows me to use both hotkeys, and both will make the OSD appear. The brightness never changes, though.

I set up the power management thingy to dim the display after some time - that also doesn't work. The screen goes dark but the backlight is still on.

I already checked out the content of the brightness file somewhere in /proc/acpi/... and the only one not containing something along the lines of "not supported" is located in .../video/IGD/... if I remember correctly (not at my notebook at the moment).
The brightness values are: 7 3 0 1 2 3 4 5 6 7. Writing directly to the brightness file will change it's value but not affect the screen's brightness.

The brightness slider applet for the GNOME panel won't work either.

I'm stuck. Could someone point me to the right direction, please...?


I'm using Ubuntu 8.04 and the graphics chip is Intel's i915. The problem seems to be new in Hardy. I remember adjusting the brightness without any problems in earlier versions (not sure when it started).

---

### Post by rekado on 2008-09-18
What information can I provide to help you help me?
Does anyone else face this problem?

---

### Post by rekado on 2008-09-23
BUMP.

It seems that this is nothing to do with Fn-keys after all, but with some other kind of problem. When directly writing a brightness value to the file, there is no change in the display's brightness, even though the value is accepted.

It works till GRUB, when booting Linux it fails. Could someone point me to the right direction, please?

---

### Post by rekado on 2008-09-28
Ok, I've collected lots of information that I hope someone can find useful. These are all "brightness" files on my system:

**/sys/class/backlight/acpi_video0/brightness**
contains only "7"; could be that i created it myself...

**/sys/class/backlight/acpi_video0/actual_brightness**
contains "7" as well, which is both the lowest and the highest value (see below)

**/sys/class/backlight/acpi_video0/max_brightness**
also contains a "7".

I set the screen to lowest brightness before booting Linux.

**/sys/module/video/parameters/brightness_switch_enabled**
contains a single "Y".

**/proc/acpi/video/IGD/LCD/brightness**
delivers this information when writing its content to stdout using cat:
[I]levels:  7 3 0 1 2 3 4 5 6 7
current: 7
[/I]

[B]/proc/acpi/video/IGD/TV/brightness
/proc/acpi/video/IGD/CRT/brightness
/proc/acpi/video/VGA/DVIA/brightness
/proc/acpi/video/VGA/DVI/brightness
/proc/acpi/video/VGA/LCD/brightness
/proc/acpi/video/VGA/CRT/brightness[/B]

returns only:
*<not supported>*

The following dbus command outputs a value between 0 to 100 dependent on the position of the bar in the OSD:
> 
dbus-send --type=method_call --print-reply --dest=org.freedesktop.PowerManagement --session /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.GetBrightness

The output is:

> method return sender=:1.23 -> dest=:1.65 reply_serial=2
uint32 0


...where the last zero is shown before I touched the hotkeys. After trying to increase the brightness (OSD changes) the value approaches 100. The brightness hotkey for reducing the backlight won't work when the actual perceivable brightness is already the lowest possible. Likewise, the hotkey combo for increasing the brightness will not cause a change in the OSD when the screen's brightness has been increased to full power before booting linux.

Thus, I assume that the real visible brightness is being queried somewhere before the OSD appears. Even though the on-screen-display indicates that the brightness is very high, i still cannot lower it, because the real brightness is on the lowest level already. The OSD is stuck then.

The following dbus message to set the brightness (value 0 to 100) is also uneffective:

> dbus-send --type=method_call --print-reply --dest=org.freedesktop.PowerManagement --session /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:0


The output is:
> method return sender=:1.23 -> dest=:1.66 reply_serial=2

xbacklight -set ... does not work. It however changes the current brightness value in the brightness file. Also using the hotkeys does this. The actual brightness, however, does not change.

I really don't know what else I could do. I remember that long time ago, several kernels before it worked.

I think the error could be fixed (but I don't know where):

No matter if I write to the brightness files or use xbacklight or use the hotkeys - they all do change the value in the respective files and change the OSD indication but have no effect on the actual brightness whatsoever. But when booting with lowest brightness settings, somehow the system ignores the hotkey for lowering the brightness --> it seems to know the actual brightness value when evaluating if a hotkey command should be processed or ignored.
Likewise in an inverted setting.

Where is the decision made if a hotkey should bring up the brightness indicator bar (OSD)? Is this implemented in software?


EDIT: looks similar to the bug 150086 in lauchpad. Could be related though there are differences.

---

### Post by xubcel on 2008-09-29
Hello.  I am no expert (like you, I am waiting for an answer to my post) but a brightness scale with two 7's and 3's sounds wrong.  Besides uninstalling and reinstalling apcid, you might view this link that mentions how to check brightness scale and a related problem.

[http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/](http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/)

---

### Post by rekado on 2008-09-29
Hi Xubcel, thanks for your comment on this. I was afraid I would be doing monologues forever... :)

I checked the website and it explains the same fix (but in a script) that didn't work on my machine.
I also thought that the brightness scale really looks weird but I've seen something similar in other posts that stated that the fix works.

Hmm. I will remove and install acpid again, though I'm afraid that this will probably undo all my efforts that I made to adjust the power management... Let's see.

---

I just reinstalled acpid (completely remove, then install). There is no difference at all. One thing I noticed is that the system claims that the LCD is unknown to the BIOS itself:

> cat /proc/acpi/video/IGD/LCD/info 

device_id:    0x0110
type:         UNKNOWN
known by bios: no


This is just weird!

---

### Post by xubcel on 2008-09-29
Maybe the first 7 and 3 are the settings for AC and battery mode, or something like that.

/proc/acpi/video/IGD/LCD/brightness
delivers this information when writing its content to stdout using cat:
levels: 7 3 0 1 2 3 4 5 6 7
current: 7

I did not notice if you checked for enables/disables of LCD in BIOS (although hotkeys work before booting Ubuntu).

Maybe there is a conflict.  What happens if you disable the following by setting to "N"?

/sys/module/video/parameters/brightness_switch_enabled
contains a single "Y".

Or, I am not sure if you tried the hotkeys with acpi's dimmer off, or acpi off, or acpi uninstalled.

You might want to make a chart for all the combinations.

---

### Post by rekado on 2008-10-06
There is no such setting in my BIOS. It is quite crippled, can only change the time and the boot order but not much else...

The brightness_switch_enabled file has no effect on it.
Booting with acpi=off, though, will make the brightness hotkeys work. But I would lose all the advantages of ACPI then. Booting with acpi=ht ... well, it's not finishing the boot process; I'm stuck right before the full desktop appears but the brightness control works.

Yesterday I reinstalled Intrepid Ibex Beta but the problem persists.

---

### Post by rekado on 2008-10-06
I filed a bug now containing all information I could get:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/279163](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/279163)

---

### Post by chinchillart on 2008-10-08
Thanks for the information!
I'm trying to solve a related problem with my LG Flatron (20" Desktop LCD )

After setting up the cpufreqd to work with the Athlon X2 processor, I've lost the automatic LCD standby... The screensaver also stopped to work.

Before the cpufreqd install and config, everything worked fine.
Anyway, I've the same problem with the LCD brightness gnome applet. It doesn't work.

I wish someone could suggest me some in-depht documentation about power saving related issues and configuration in Ubuntu/Debian.

Rob

---

### Post by rekado on 2008-10-10
> **chinchillart said:**
> Thanks for the information!
I'm trying to solve a related problem with my LG Flatron (20" Desktop LCD )

After setting up the cpufreqd to work with the Athlon X2 processor, I've lost the automatic LCD standby... The screensaver also stopped to work.

Before the cpufreqd install and config, everything worked fine.
Anyway, I've the same problem with the LCD brightness gnome applet. It doesn't work.

I wish someone could suggest me some in-depht documentation about power saving related issues and configuration in Ubuntu/Debian.

Rob

This sounds unrelated as my brightness issue is something to do with ACPI, I assume. It didn't work before setting up frequency scaling at all and the brightness controls stop functioning in the very early stages of the boot process, before anything related to frequency scaling is executed.
Guess you should start a new thread then.

---

### Post by rekado on 2008-11-18
Is there anything else I could provide as info? Or a workaround that I haven't mentioned yet? That's the only issue left on my laptop.

---

### Post by rekado on 2008-12-02
Does anyone of you know another way to single down the cause of this problem to a certain source? Or can I obtain the source of the acpi packages somewhere?

---

### Post by rekado on 2008-12-07
"Good news, everyone..."

Playing with the options explained here [http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt) I finally managed to get it done!

I added the boot option *acpi_osi=* to my kernel line in /boot/grub/menu.lst and now it works! By default acpi_osi is used to hand over a string to the BIOS to pretend we are running Windows or any other OS for that matter. Providing an empty string apparently leaves it as it is - so now it works. Truth prevails!

---

### Post by brundles on 2008-12-17
Thanks for that - it works a charm. 

I've been arguing with my laptop (Novatech X70 - also based on a Clevo) for a couple of days now and it was starting to annoy me!

---

### Post by dnova on 2009-07-06
> **rekado said:**
> "Good news, everyone..."

Playing with the options explained here [http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt) I finally managed to get it done!

I added the boot option *acpi_osi=* to my kernel line in /boot/grub/menu.lst and now it works! By default acpi_osi is used to hand over a string to the BIOS to pretend we are running Windows or any other OS for that matter. Providing an empty string apparently leaves it as it is - so now it works. Truth prevails!
Can someone please clarify for me where in the file acpi_osi= needs to go? I'm still new at this, and slightly paranoid. Thanks!

---

### Post by rekado on 2009-07-06
Open the file /boot/grub/menu.lst with your favorite editor. Somewhere in the middle of the file there should be a line that starts with "kernel /boot/"... This is the kernel line that I meant. There might be several kernel lines in your menu.lst file. In order to identify where to add it, have a look at the lines before the kernel line starting with "title". You should see the text that you usually select in GRUB upon booting. If you never select any different kernel in GRUB, then just go with the first.

Add "acpi_osi=" (without the quotes) to the end of that line. Make sure that it is still only one line (and not suddenly two lines as it happens with older versions of "nano").

Then reboot.

Before you do this, though, make sure it works by adding "acpi_osi=" as a boot option during boot. You can do this when the GRUB menu appears. Select the kernel line you want to temporarily modify and press "e" (I guess) to edit the line. When you are done boot this modified line by pressing "b".

If this solves your problem proceed as above by changing the entry in menu.lst.

---

### Post by rpglover64 on 2009-07-20
YES!

I have been looking for a solution to this problem for almost a year (well, not so much looking for a solution as dealing with).

To make it easier for people with a similar problem to find this post:

I have a Dell Inspiron 1420.
Symptoms included that the acpi event fired twice and that it looked like multiple things were controlling brightness.

---

### Post by levis lover on 2010-07-13
**how to add this option in GRUB2 ??**

---

### Post by fishears on 2010-12-06
>sudo gedit /etc/default/grub

and add it to the "GRUB_CMDLINE_LINUX=" parameters

then 
>sudo update-grub

---

