---
title: "Synaptic Touchpad showing up as a PS/2 Device."
date: 2010-10-20
forum: Hardware
---

### Post by Aitaix on 2010-10-20
DELL Latitude E6510
Ubuntu 10.10


I **REALLY **want to be able to configure my touchpad settings but I cannot because my computer isn't showing my mouse as a Synaptic Touchpad. It's listing it as a PS/2 Generic Device

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse0 event11 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

How can I make it show up as a Synaptic Touchpad so I can turn off this bloody tap to click!

---

### Post by girishadat on 2010-10-23
I am also facing the same problem with my Toshiba Portege M900. It has got a multitouch synaptic touchpad. But not detected in Ubuntu as such.

```
girish@girish-laptop:~$ tpconfig
Could not open PS/2 Port [/dev/psaux]
```

Also /proc/bus/input/devices showing touchpad as,
```
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="**ImPS/2 Generic Wheel Mouse**"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

```

Also,
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=173319&stc=1&d=1287873293[/IMG]

---

### Post by Superfish on 2010-10-27
Same problem for me... Dell Inspiron 1420 with Nvidia GeForce 8400M. This has been broken since 9.04 (I think) and I've been waiting, hoping Maverick would fix this. I've upgrade my Ubuntus (rather than reinstalling) since 7.04, if that makes a difference (want to keep my LinDVD that came installed with the machine!)

Symptoms:
* No "touchpad" tab in the mouse configuration
* syndaemon says "Unable to find a synaptics device"
* "modprobe psmouse proto=imps" has no effect
* From lshal:
```

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'PS/2 Generic Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'PS/2 Generic Mouse'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input12/event4'  (string)

```

Any help would be very much appreciated!

---

### Post by Superfish on 2010-10-27
> **girishadat said:**
> 
```
girish@girish-laptop:~$ tpconfig
Could not open PS/2 Port [/dev/psaux]
```


Try running tpconfig as sudo. This is my output:
```

sudo tpconfig 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

```

(Sorry for the double post!)

---

### Post by solnyshok on 2010-10-28
for toshiba m900 you may try to disable mouse emulation in Bios. I have toshiba r630 and have such setting, maybe you have too.

---

### Post by waydaws on 2010-11-01
Same thing here.  
No horizontal or vertical scroll, etc.  Using a Lenovo g550. 
Lucid(10.04.1 LTS)

cat /proc/bus/input/devices reveals
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse1 event11 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

The lenovo g550 transitioned to ALPS

---

### Post by nrune on 2010-11-02
I think that your issues may be related to this bug. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/527890](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/527890)

[https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660)

If I am right no fix yet.

---

### Post by crisco552 on 2010-11-02
I sure hope there is a fix, I'm having pretty much the exact same problem, however it didn't appear until my touchpad was switched out earlier today.

---

### Post by KukMan on 2010-11-04
Me too. I have Acer Aspire 1551. Kernel module psmouse recognize my touchpad as PS/2 Generic Mouse :(

---

### Post by KukMan on 2010-11-04
I loaded from USB drive with Ubuntu 10.04, and it recognized my touchpad as 

```

I: Bus=0011 Vendor=0002 Product=0008 Version=7326
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```

There are also Touchpad tab in Mouse properties. So, it seems problem is in new kernel.

---

### Post by KukMan on 2010-11-09
bump

---

### Post by Superfish on 2010-11-15
Did anyone else here upgrade from earlier versions of Ubuntu, or were these all clean installs? Anyone else try running it off a LiveCD?

---

### Post by KukMan on 2010-12-02
2.6.36 kernel recognizes touchpad same as 2.6.35 =(

---

### Post by Joliea on 2010-12-20
Doesn't work at all :(

---

### Post by Orion13622 on 2010-12-30
Used to be all you had to do was edit the xorg.conf file, however this file no longer exists in 10.04.  All you had to do to change it was just add 2 letters to PS/2 (IMPS/2) which usually enabled the scroll part of the trackpads.  (Used to do it all the time in VMWare), however with 10.04, this is no longer the case.  Anyone have a suggestion?  Developers??

---

### Post by pi/roman on 2010-12-30
On 10.10 I created a seperate touchpad configuration using xorg.conf which nullified the original configuration so that may work. Orion you can create an xorg.conf file by using this command:
```
sudo X :1 -configure
```If you get an error that X server is already active just change ":1" to a different number like ":2" or ":3".
This will create xorg.conf.new in your personal folder.  Then to edit it:
```
sudo gedit ~/xorg.conf.new
```or from alt/f2 run application prompt
```
gksudo gedit xorg.conf.new
```To the "ServerLayout" section add this line:
```
InputDevice    "Touchpad" "CorePointer"
```Then create another "InputDevice" section. Make sure in this section that the identifier is the same as the input device in the "ServerLayout" section, ie if 'Touchpad' had a capital T there it must have a capital T here.
```
Section "InputDevice"
    Driver        "synaptics"
    Identifier    "Touchpad"
EndSection
```Save this as xorg.conf and move it to the folder /etc/X11 then reboot or restart X.
If it register's your touchpad it should assign the synaptics driver to it, allowing you to use the synaptics configurations.

---

### Post by Yeti can't ski on 2011-01-08
Finally a good soul came up with a patch for the problem (at least on my Dell V13): 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/380126](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/380126)

See the posts of Marcin and Lars Fehrs. 

It is a little bit tricky - it requires compiling the kernel - but it worked fine for me.

---

### Post by pi/roman on 2011-01-08
Check to see if your touchpad is detected as such.  If so then one of these commands should give the output of ID_INPUT_TOUCHPAD=1.
```
udevadm info -q all -n input/mouse0 | grep ID_INPUT
udevadm info -q all -n input/mouse1 | grep ID_INPUT
udevadm info -q all -n input/mouse2 | grep ID_INPUT
```If you check all your input devices and none of them are detected as touchpads then try my fix here:
[[COLOR=Blue]http://ubuntuforums.org/showpost.php?p=10333651&postcount=43[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10333651&postcount=43")

Please take note that the name of the touchpad used in the example is [COLOR=black]"PS/2 Generic Mouse"[/COLOR]. If your touchpad has a different name then you should use it instead.

Please let me know the results, good or bad.

---

### Post by quik_lives on 2011-02-06
pi/roman, I tried the solution you linked to and it took away all recognition of the device. I undid the changes and got it back...I see you said it may need to be tweaked, and it may just be that I'm not adept enough to follow directions or tweak it.

Also, re: compiling the kernel/fix from the bug report, I'm apparently not smart enough to make it work, I will have to wait for an easier fix.

---

### Post by Aitaix on 2011-02-09
found this[ link]("https://confluence.nau.edu/confluence/display/%7Ecmg238@nau.edu/Recognize+ALPS+Touchpad+on+Dell+E6510+in+Ubuntu")

but i have no idea how to 

[LIST=1]
[*]Patch src/drivers/input/mouse/alps.c
[/LIST]

---

### Post by sbraz on 2011-08-23
pardon my all-caps-rage but...

IT TOOK 9 MONTHS BUT FINALLY I CAN SCROLL WITH MY TOUCHPAD

it's Alps's fault, their policy is so closed source that kernel.org had to reject this patch from the official tree as Alps doesn't want to disclose any detail about their touchpads, no matter what. (source: arch linux forums, i lost the link)

> **Aitaix said:**
> found this[ link]("https://confluence.nau.edu/confluence/display/%7Ecmg238@nau.edu/Recognize+ALPS+Touchpad+on+Dell+E6510+in+Ubuntu")

but i have no idea how to 

[LIST=1]
[*]Patch src/drivers/input/mouse/alps.c
[/LIST]

it involves downloading kernel sources, using the command **patch -p1 < %patchfile%**, compiling a replacement psmouse.ko module and copying it over the current psmouse.ko found under /lib/modules/%kernel-version-number%/kernel/drivers/input/mouse/.

i've tried the link you posted but it didn't work as it should, meaning that it makes the touchpad turn into an actual "alps touchpad" but scrolling didn't work (or i did something wrong when i tried).

in arch linux forums (again, i've lost this link sorry) i've found this link here:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commitdiff;h=bd79df42218fe1db5e683b567791d4bb97b60685](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commitdiff;h=bd79df42218fe1db5e683b567791d4bb97b60685)

i've applied the patch and now it's working... no multitouch (alps's fault again) but scrolling works.

```
root@sbraz-netbook:~# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SideWinder™ X3 Mouse	id=12	[slave  pointer  (2)]
[B]&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=15	[slave  pointer  (2)]
[/B]&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=10	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=11	[slave  keyboard (3)]
    &#8627; 1.3M WebCam                             	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=16	[slave  keyboard (3)]
```

notice that this is a patch from/for dell notebooks so it might not work for you as it did for me. :)

also, [COLOR="Red"]**be careful when carelessly messing with sources and kernel modules, you risk *bricking your box*.**[/COLOR]

---

