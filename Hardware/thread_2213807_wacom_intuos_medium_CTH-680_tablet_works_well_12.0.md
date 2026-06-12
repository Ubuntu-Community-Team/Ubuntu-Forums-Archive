---
title: "wacom intuos medium CTH-680 tablet works well 12.04"
date: 2014-03-28
forum: Hardware
---

### Post by pdc on 2014-03-28
One gets some posts about the wacom tablets; I thought to record that with our 12.04 LTS ubuntu; 3.2.0-23-generic that all that was needed to get the wacom tablet working fine was to install the latest [COLOR="#008000"]input-wacom[/COLOR] package

to do that, go here

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

click on [COLOR="#A52A2A"]Get the Drivers[/COLOR] then click on the [COLOR="#A52A2A"]input-wacom button[/COLOR] .....that takes you to the instruction page first of all with a link to download the needed package

I used[COLOR="#008000"] input-wacom-0.20.0.tar.gz
[/COLOR]
...........so if one downloads and saves, the commands from the instructions are

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf input-wacom-0.20.0.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd input-wacom-0.20.0[/COLOR]

> [COLOR="#FF0000"]./configure[/COLOR]

..........if one reads at the end of the install, there is an instruction: if you have a USB tablet, copy what they tell you.......and add sudo in front and paste into the terminal; now that it has finished the configure process

the structure of the command is [COLOR="#DDA0DD"]sudo cp ./<kernel version>/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet[/COLOR] and the script that runs will give you [COLOR="#EE82EE"]<kernel version>[/COLOR] and [COLOR="#EE82EE"]`uname -r`[/COLOR] already entered for you to copy and paste

***_after doing that crucial copy and paste_***, the next and final command is:

> [COLOR="#FF0000"]sudo depmod -a[/COLOR]

when that is finished, reboot ..........how does one know the tablet is working...............well, when plugged into a usb port, it controls the mouse on your desktop..........thence you can open gimp

---

### Post by kurja on 2014-03-29
I just recently got a pen & touch and it worked out of the box in 12.04 (x86), and gimp.

Only the wacom gui under system settings isn't capable of configuring the buttons for some reason, so that needs to be scripted.

---

