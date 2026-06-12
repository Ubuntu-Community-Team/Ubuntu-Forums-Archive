---
title: "Touch Screen Won't Work"
date: 2011-01-07
forum: Hardware
---

### Post by Buckoman on 2011-01-07
I have a Toshiba M700-S7004 Tablet PC and was sick of Vista, cause, well, it sucks. I installed Jolicloud (Which is ubuntu, no?) and I heard that it included touchscreen support. I booted up and, surprisingly, the touchscreen didn't work... I couldn't find any similar problems with my model series, butin short - I need a simple way to get my touchscreen working and ditch the touchpad and keyboard, and just have it working as a tablet. I have basic knowledge of terminal and are very familiar with most commands. Please help, I don't want to keep Vista only... :D

_____________________________________-
Toshiba Portege M700-S7004
1.20Ghz
Tablet Pc with Pen
Centrino vPro
Jolicloud Ubuntu 1.1

---

### Post by Favux on 2011-01-07
Hi Buckoman,

Actually I'm not sure.  I don't know how far Jolicloud 1.1 has gone towards a Chrome like cloud device.  What kernel and Xorg does it have?  Does it have Synaptic Package Manager?  In Synaptic do you see xserver-xorg-input-wacom installed?

---

### Post by Buckoman on 2011-01-08
It said that it was already installed, i am re-installing it now. I'll keep you posted...

---

### Post by Buckoman on 2011-01-08
Sorry to be such a noob xD how to i find the xorg and kernel versions? It's not traditional ubuntu so i don't know how to get there... :/

---

### Post by Favux on 2011-01-08
Not a problem.  In a terminal enter:
```
Xorg -version
and
uname -r
```

---

### Post by Buckoman on 2011-01-09
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux jolicloud 2.6.35.8-1-jolicloud #53 SMP Fri Dec 3 08:02:10 MST 2010 i686
Kernel command line: mem=2000MB BOOT_IMAGE=/boot/vmlinuz-2.6.35.8-1-jolicloud root=/dev/sda2 loop=/jolicloud/disks/root.disk ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4

2.6.35.8-1-jolicloud

Hope this helps! :D

---

### Post by Favux on 2011-01-09
OK, that's basically Maverick.

With xserver-xorg-input-wacom already installed I'm surprised that your stylus didn't work out of the box.

Let's define our terms.  The Toshiba M700 has a Wacom digitizer.  That should give you your stylus/pen, eraser, and two stylus buttons.  Does it also have touch, using your finger?  Or maybe even multi-touch (two fingers)?

Enter in a terminal:
```
xinput --list
```
and post the output.  Let's see what's going on.

---

### Post by Buckoman on 2011-01-09
It is a finger touch and stylus touch, though the stylus only has one finger button on the side of it. Here's the output:


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=15	[slave  keyboard (3)]

---

### Post by Favux on 2011-01-09
That's a little mysterious.  Your serial Wacom digitizer isn't showing up in xinput at all.

Lets look and see if it is a problem in the 50-wacom.conf.  That should be located at /usr/share/X11/xorg.conf.d/.  You should be able to open it from the command line with:
```
gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
Post what's in there.

---

### Post by Buckoman on 2011-01-09
gedit /usr/share/X11/xorg.conf.d/50-wacom.conf gave me a blank rich text with nothing typed in it.

---

### Post by Favux on 2011-01-09
We may be narrowing in on the problem.  Look in that directory, /usr/share/X11/xorg.conf.d/, and see if you see any file called wacom.conf.  There should be other ones like evdev.conf etc.

---

### Post by Buckoman on 2011-01-09
X11 is a far as it goes.

---

### Post by Favux on 2011-01-09
Are they in /usr/lib/X11/xorg.conf.d/?

Or is Jolicloud 1.1 still using .fdi files?  Check in /usr/share/hal/fdi/policy/ and see if there is a 20thirdparty (and a couple of other directories) with a 10-linuxwacom.fdi.

---

### Post by Buckoman on 2011-01-10
/usr/lib/X11/xorg.conf.d/ there is a 10-wacom.conf, though no 10-linuxwacom.conf or 10-wacomlinux.conf. Does the file need to be named with linux in the file name?

---

### Post by Buckoman on 2011-01-10
> **Buckoman said:**
> /usr/lib/X11/xorg.conf.d/ there is a 10-wacom.conf, though no 10-linuxwacom.conf or 10-wacomlinux.conf. Does the file need to be named with linux in the file name?

Text in file 10-wacom.conf: Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

---

### Post by Favux on 2011-01-10
> Originally Posted by Buckoman
/usr/lib/X11/xorg.conf.d/ there is a 10-wacom.conf, though no 10-linuxwacom.conf or 10-wacomlinux.conf. Does the file need to be named with linux in the file name?
No they just renamed it going from Lucid to Maverick.

Try adding this serial snippet in to the 10-wacom.conf and reboot:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
EndSection
```
Let's see if using the "WACf" MatchProduct picks up your serial digitizer.  You can check 'xinput --list' to see if it has appeared.  Use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
to edit it.

---

### Post by Buckoman on 2011-01-11
Successfully edited, but it didn't work. This is weird...

---

### Post by Favux on 2011-01-11
To rule out a hardware failure do we know that the Wacom digitizer works in Vista?

---

### Post by Buckoman on 2011-01-11
Most definately. Does Wacom offer drivers for Linux?

---

### Post by Favux on 2011-01-11
Yes, in the sense they support one of the LWP developers.

Let's try modifying the snippet like so:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection
```
or
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	MatchDevicePath "/dev//ttyS*"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection
```
Remember to back up your current working 10-wacom.conf and be prepared to restore it from the command line if we break X.

You still have the default xf86-input-wacom (the package xserver-xorg-input-wacom) correct?  What version is Synaptic Package Manager saying you have?

---

### Post by Buckoman on 2011-01-11
How to check Synaptic version?

---

### Post by Favux on 2011-01-11
Don't know where it is in Joli or if you have it.  If you do open it an use Search/Find for Wacom.

---

### Post by Buckoman on 2011-01-12
Searched wacom in Synaptic:

xserver-xorg-input-wacom

-Installed and Reinstalled, No Dice...

searched wacom in my pc:

xorg-wacom-pc:

sdkdir=/usr/include/xorg

Name: xorg-wacom
Description: X.Org Wacom Tablet driver.
Version: 0.10.5
Cflags: -I${sdkdir}

and source_xserver-xorg-input-wacom.py:

#!/usr/bin/python

'''Xorg Apport interface

Copyright (C) 2007, 2008 Canonical Ltd.
Author: Bryce Harrington <bryce.harrington@ubuntu.com>

This program is free software; you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 2 of the License, or (at your
option) any later version.  See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for
the full text of the license.
'''

import os.path
import glob
import subprocess
from apport.hookutils import *

def installed_version(pkg):
    script = subprocess.Popen(['apt-cache', 'policy', pkg], stdout=subprocess.PIPE)
    output = script.communicate()[0]
    return output.split('\n')[1].replace("Installed: ", "")

def nonfree_graphics_module(module_list = '/proc/modules'):
    '''
    Check loaded modules to see if a proprietary graphics driver is loaded.
    Return the first such driver found.
    '''
    try:
        mods = [l.split()[0] for l in open(module_list)]
    except IOError:
        return None

    for m in mods:
        if m == "nvidia" or m == "fglrx":
            return m

def add_info(report, ui):
    tags = []

    # Build System Environment
    codename = command_output(['lsb_release','-sc'])
    tags.append(codename)

    report['system']  = "distro:             Ubuntu\n"
    report['system'] += "codename:           " + codename + "\n"
    report['system'] += "architecture:       " + command_output(['uname','-m']) + "\n"
    report['system'] += "kernel:             " + command_output(['uname','-r']) + "\n"

    attach_related_packages(report, [
            "xserver-xorg",
            "libgl1-mesa-glx",
            "libdrm2",
            "xserver-xorg-video-intel",
            "xserver-xorg-video-ati",
            "xserver-xorg-video-nouveau"
            ])

    # Verify the bug is valid to be filed
    version_signature = report.get('ProcVersionSignature', '')
    if not version_signature.startswith('Ubuntu '):
        report['UnreportableReason'] = _('The running kernel is not an Ubuntu kernel')
        return

    bios = report.get('dmi.bios.version', '')
    if bios.startswith('VirtualBox '):
        report['SourcePackage'] = "virtualbox-ose"
        return

    product_name = report.get('dmi.product.name', '')
    if product_name.startswith('VMware '):
        report['UnreportableReason'] = _('VMware is installed.  If you upgraded recently be sure to upgrade vmware to a compatible version.')
        return

    if report['ProblemType'] == 'Crash' and 'Traceback' not in report:
        nonfree_driver = nonfree_graphics_module()
        if (nonfree_driver == "fglrx"):
            report['SourcePackage'] = "fglrx-installer"

        elif (nonfree_driver == "nvidia"):
            report['SourcePackage'] = "nvidia-graphics-drivers"

    attach_file_if_exists(report, '/etc/X11/xorg.conf', 'XorgConf')
    attach_file(report, '/var/log/Xorg.0.log', 'XorgLog')
    attach_file_if_exists(report, '/var/log/Xorg.0.log.old', 'XorgLogOld')

- at this point i'm really surprised it hasn't started working... There are plenty of other files including "wacom" on my computer... most .conf files... Any suggestions?

---

### Post by Favux on 2011-01-12
As long as you don't have a duplicate wacom.conf somewhere and don't have wacom entries in xorg.conf (/etc/X11) you should be good on the configuration file with the 10-wacom.conf, barring any needed adjustments.

Since you have the Lucid default xf86-input-wacom, which is version 0.10.5, the only thing I can suggest is to try updating it.  Right now it's at 0.10.10+.  You can clone the git repository for it by following the instructions in part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Buckoman on 2011-01-12
I'm sorry, I appreciate all of your work and all the commands you've given to me, but it still isn't working. Do you have any ideas?

---

### Post by Favux on 2011-01-12
Let's try restarting X and see if it works then.

Do you know how?  You can re-enable the old key combination by going to System > Preferences > Keyboard > click 'Layouts' tab > click 'Layout Options' button > select "Keys sequence to kill the X server' > check the check box.

---

### Post by Buckoman on 2011-01-12
Just did... No Dice... :/

---

### Post by Favux on 2011-01-12
Shoot.

Well I know we had a problem with the M700's in the old xorg.conf/setserial days.  Had to add a serial line in a non-standard place I think.  I wouldn't think that would apply anymore.

One thought.  If you did update xf86-input-wacom you shouldn't be using the ISD4 line anymore in the wacom.conf serial snippets.  It was deprecated.  Not sure that would make any functional difference though.

---

### Post by Buckoman on 2011-01-12
Could you give me instructions on how to add that certain line? Im sure it wouldn't hurt...

---

### Post by Favux on 2011-01-12
Not sure about that.  Unfortunately the Ubuntu M700 wiki we keep referring to was taken down by Ubuntu about a year ago with their wiki rewriting.  As far as I know they haven't replaced any of the laptop wikis.

Here's what we did:
> /bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
X-Kent reports success on post #78 and I summarize on post #79:  [http://ubuntuforums.org/showthread.php?t=1055845&page=8](http://ubuntuforums.org/showthread.php?t=1055845&page=8)  FC1032 reporting success on an M750 (same line I think we got from the M700 wiki) on [post #91]("http://ubuntuforums.org/showthread.php?t=1055845&page=10").

Check /bin/ and see if you see the setserial executable in it.  If you do there probably isn't any harm in using it.

An openSUSE wiki:  [https://docs.google.com/Doc?id=dg8nknth_3hs868qhh](https://docs.google.com/Doc?id=dg8nknth_3hs868qhh)

---

### Post by GotDiesel on 2011-01-21
I don't know if you guys have got this issue solved yet but I found this and I am currently working to get my T900 working to it's fullest.  If you have any luck with it let me know.  Actually you may have already seen this link but here it is anyway:

[http://thelackthereof.org/Fujitsu_Lifebook_T730](http://thelackthereof.org/Fujitsu_Lifebook_T730)

---

