---
title: "asus 1015pem"
date: 2010-09-15
forum: Hardware
---

### Post by charlesthump on 2010-09-15
hey there.  firstly, my apologies if the hardware in question has already been discussed, but i was unable to find the exact model number via search, and as these things get pretty particular i'm forced to ask explicitly.  if i've overlooked this discussion elsewhere, then shame on me.

that said, the new asus 1015pem, with the atom n550, looks pretty enticing as a linux netbook.  i'm returning to linux after about 15 years, so the last time i ran it was on a 386 or 486.  i know enough to understand that issues with drivers and other hardware concerns can make or break an install, but not enough to infer $400ish worth of netbook selection from chatter on teh intarweb.

i'm planning on running debian lenny, so my assumption (perhaps foolish) is that if ubuntu is running smoothly on one of these things, then it'll probably be fine with lenny.  has anyone had any experience with this new model already, or has enough insight into the critical architectures (atom n550, gma 3150, usb 3.0, etc.) to say with confidence that there shouldn't be any problems?

any and all feedback is appreciated.

---

### Post by charlesthump on 2010-09-16
bump

---

### Post by matthiasak on 2010-10-02
I just received my 1015pem yesterday and just booted into -- via USB -- ubuntu 10,10 beta x64. 

EVERYTHING WORKS :)

it's very smooth, and buttery, and it makes ne feel all tingly inside :)

best of luck!

matt

---

### Post by castlefox on 2010-10-06
When you say everything does hibernate work ?

What kind of battery life are you getting?

---

### Post by guimaster on 2010-11-11
> **castlefox said:**
> When you say everything does hibernate work ?

What kind of battery life are you getting?

 I will bump this as I am interested in an answer also...

---

### Post by vaerer on 2010-12-08
Bump also, I'm thinking of getting the this for uni.

---

### Post by LocarionStorm on 2010-12-18
I purchased one of these netbooks earlier this week and have loaded Ubuntu 10.10 Netbook Edition on to it.

In regard to hibernation, I have tested and going into and coming out of hibernation worked. However, the system seemed to take longer than it should have to do both.

I will try and get a better timing of battery life this weekend and report back if people are still interested. Based on my usage thus far, I have been able to get at least 8 hours with regular usage.

The wireless works smoothly following the installation of an additional driver and the sound works perfectly as well.

If there are any other questions regarding the 1015PEM, then let me know.

---

### Post by Knef on 2010-12-22
> **LocarionStorm said:**
> I purchased one of these netbooks earlier this week and have loaded Ubuntu 10.10 Netbook Edition on to it.

In regard to hibernation, I have tested and going into and coming out of hibernation worked. However, the system seemed to take longer than it should have to do both.

I will try and get a better timing of battery life this weekend and report back if people are still interested. Based on my usage thus far, I have been able to get at least 8 hours with regular usage.

The wireless works smoothly following the installation of an additional driver and the sound works perfectly as well.

If there are any other questions regarding the 1015PEM, then let me know.
LocarionStorm, did you tweak any settings to get such a long battery life? What does your normal usage consist of?

---

### Post by ALLurGroceries on 2010-12-22
I just got this machine in my hands -- there's another thread over at NBR here [http://forum.notebookreview.com/linux-compatibility-software/532036-asus-1015pem-ubuntu.html]("http://forum.notebookreview.com/linux-compatibility-software/532036-asus-1015pem-ubuntu.html")

I'll update [my post there]("http://forum.notebookreview.com/linux-compatibility-software/532036-asus-1015pem-ubuntu.html#post6990928") after I've worked through the installation, I'm just backing up the recovery partition at the moment.

The approximate battery life is ~5hrs out of the box estimated, although I've yet to go through a full cycle.

The wireless on my particular machine (PU17) is BCM4313 which the brcm80211 staging driver works for, so I'm going to use that instead of the atrocious Broadcom STA (wl) driver.

---

### Post by Heithy on 2010-12-24
Hey i've installed ubuntu 10.10 desktop edition on my 1015PEM and was wondering if anybody has the problem of some of the fn keys not working, and hopefully a solution. the keys are fn-f2, fn-f3 and fn-f7.

also the enable/disable wireless button isn't working for me either. (and the power saving mode switch button next to it, but i don't care about that, although keymapping it for something else would be handy.)

i post this from my 1015pem, contented with my purchase :D

i initially installed ubuntu 10.10 netbook edition with unity. what a joke that is.

thanks in advance for any solutions and advice

---

### Post by khamami on 2010-12-24
1. edit /etc/default/grub as root, and locate the line starting with GRUB_CMDLINE_LINUX_DEFAULT:

change to
GRUB_CMDLINE_LINUX_DEFAULT="something acpi_osi=Linux"

update-grub

2. install jupiter..[http://www.webupd8.org/2010/12/jupiter-0046-released-with-sata-link.html](http://www.webupd8.org/2010/12/jupiter-0046-released-with-sata-link.html).

---

### Post by ALLurGroceries on 2010-12-25
Forcing acpi_osi=Linux on this machine reduces the maximum brightness.

I've noticed those hotkeys don't work either -- they work without eeepc_wmi but then the volume hotkeys don't work.

I haven't tried Jupiter yet, I'm going to get on that when I have time and also look at the Eee module source.

Edit: Jupiter is cute... nice interface... unfortunately it does nothing for hotkeys.

Change L67 of drivers/platform/x86/eeepci-wmi.c from this:
```
	{ KE_KEY, 0x5d, { KEY_WLAN } },
```
To this:
```
	{ KE_KEY, 0x88, { KEY_WLAN } },
```
Takes care of Fn+F2.

I'm also seeing WMI hotkeys on Fn+1, Fn+2, Fn+e, Fn+s, Fn+d and Fn+f, but I'm too lazy to bind them right now. Maybe I'll make them into media controls.

The other missing Fn keys don't show up in syslog so I have nothing for those yet.

Edit 2: Jupiter actually breaks the touchpad upon reboot, so I'm not using it anymore. I bound all the other hotkeys in the keyboard shortcuts app under System->Preferences, so there's no need for it unless you like menus.

I made a 1-line script to disable the LCD witn Fn+F7 and bound it in keyboard shortcuts, since I'm really lazy:
```
#!/bin/sh
sleep 1; xset dpms force suspend
```

Edit 3: New script for disabling the LCD:
```
#!/bin/bash

if [ `sudo setpci -s 02.0 f4.b`  != "00" ]; then
    sudo setpci -s 02.0 f4.b=00
else
    sudo setpci -s 02.0 f4.b=ff
fi
```

There's a handy script to toggle resolution ( [ganked from here]("http://www.cnpbagwell.com/linux/fedora-13-and-asus-eee-pc-1005peb")) that I bound to Fn+F4:
```
#!/bin/bash

find_res=`/usr/bin/xrandr | grep "1024x768"`

if [ $? == "0" ]; then
  xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.00
else
  xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.28
fi
```

For Fn+F3, you have to change /etc/acpi/asus-touchpad.sh line 16 to:
```
XINPUTNUM=`xinput list | grep -i 'touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`
```

Then add a keyboard shortcut as **sudo /etc/acpi/asus-touchpad.sh**

For Fn+F9, I'm going to write a script to cycle through the values 0-2 for **/sys/devices/platform/eeepc-wmi/cpufv** but I haven't gotten to it yet. This controls SHE (super hybrid engine), the doc is in **Documentation/ABI/testing/sysfs-platform-eeepc-wmi** in the kernel:
> 		There are three available clock configuration:
		    * 0 -> Super Performance Mode
		    * 1 -> High Performance Mode
		    * 2 -> Power Saving Mode
So to set super performance mode:
```
echo 0 > /sys/devices/platform/eepc-wmi/cpufv
```
etc...

Finally, I bound the other wmi hotkeys I found, Fn+1,2,e,s,d,f to random stuff. This makes the esdf inverted-T the same as the arrow keys on other asus laptops, controlling the media functions. I bound Fn+1 to the home folder and Fn+2 to the web browser. Here's the relevant section in eeepc-wmi.c:
```
static const struct key_entry eeepc_wmi_keymap[] = {
	/* Sleep already handled via generic ACPI code */
	{ KE_KEY, 0x5d, { KEY_WLAN } },
	{ KE_KEY, 0x88, { KEY_WLAN } },
	{ KE_KEY, 0x32, { KEY_MUTE } },
	{ KE_KEY, 0x31, { KEY_VOLUMEDOWN } },
	{ KE_KEY, 0x30, { KEY_VOLUMEUP } },
	{ KE_IGNORE, NOTIFY_BRNDOWN_MIN, { KEY_BRIGHTNESSDOWN } },
	{ KE_IGNORE, NOTIFY_BRNUP_MIN, { KEY_BRIGHTNESSUP } },
	{ KE_KEY, 0xcc, { KEY_SWITCHVIDEOMODE } },
	{ KE_KEY, 0x6b, { KEY_F13 } }, /* Disable Touchpad */
	{ KE_KEY, 0xe1, { KEY_F14 } },
       	{ KE_KEY, 0xe9, { KEY_DISPLAY_OFF } },
	{ KE_KEY, 0xe0, { KEY_PROG1 } },
	{ KE_KEY, 0x5c, { KEY_F15 } },
	{ KE_KEY, 0xef, { KEY_NEXTSONG } }, /* f */
	{ KE_KEY, 0xed, { KEY_PLAYPAUSE } }, /* d */
	{ KE_KEY, 0xee, { KEY_PREVIOUSSONG } }, /* s */
	{ KE_KEY, 0xec, { KEY_STOPCD } }, /* e */
	{ KE_KEY, 0x83, { KEY_HOMEPAGE } }, /* 1 */
	{ KE_KEY, 0xeb, { KEY_WWW } }, /* 2 */
	{ KE_END, 0},
};
```


Edit 4: My 2GB stick finally came. :) It makes a huge difference, it's not choking at all anymore. The one I got is a Kingston KVR1333D3S9/2GETR 2GB PC3-10600 CL9. It was $25 shipped (in the USA). I posted this swap tweak on page 4 but I'll repeat it here again, since it still seems to help even with 2GB.

To make it swap out to disk less, I changed vm.swappiness to 10 (from 60) and it helps, until it gets over ~850MB of memory usage, and then it starts crawling again. You can test this for yourself with
```
sudo sysctl vm.swappiness=10
```

If it seems better, you can make it permanent with:
```
gksudo gedit /etc/sysctl.conf
```
and add the line
```
vm.swappiness=10
```

Also I forgot to post my resume script for brcm80211. There isn't really resume support for this driver yet, so I made a script in /etc/pm/sleep.d/99-brcm80211
```
#!/bin/sh

case "${1}" in
	hibernate|suspend)
	;;
	resume|thaw)
		sleep 3;

		modprobe -r brcm80211;

		sleep 1;

		modprobe brcm80211;
	;;
esac
```
The reason to wait 1 second is that sometimes reinserting the module will fail without a delay, I'm not exactly sure why, but it's broken until a reboot when it happens. Adding 1 second of wait time fixes it and I've not had that problem since.

---

### Post by PALKOVNIK on 2010-12-28
> **ALLurGroceries said:**
> Forcing acpi_osi=Linux on this machine reduces the maximum brightness.
[/code]


mmm, Hey)
i've just removed broadcom-sta driver (because i've got machine with BCM4313, which also works with bcmwl) and brightness-reduce problem has disappeared
i am happy, wish you also would be)

PS. your method is classic Unix-way, but we use Ubuntu here :) (i think about installing Debian Sqwueeze, because i've got it on my lap-top)

---

### Post by ALLurGroceries on 2010-12-28
@PALKOVNIK I've been using brcm80211 instead of STA, thanks though. I still have the reduced backlight if I force ACPI_OSI, no reason to do that for me though.

---

### Post by PALKOVNIK on 2010-12-28
> **ALLurGroceries said:**
> @PALKOVNIK I've been using brcm80211 instead of STA, thanks though. I still have the reduced backlight if I force ACPI_OSI, no reason to do that for me though.

i forgot to tell, that i've also installed packages "acpi" and "jupiter"

---

### Post by drum4zirrus on 2010-12-31
> **ALLurGroceries said:**
> 

Change L67 of drivers/platform/x86/eeepci-wmi.c from this:
```
    { KE_KEY, 0x5d, { KEY_WLAN } },
```To this
```
    { KE_KEY, 0x88, { KEY_WLAN } },
```Takes care of Fn+F2.



Hi, I'm new to Linux/Ubuntu

How am I able to change this? In my folder i can't find a file named "eeepc-wmi.c"
Where can I change those keys?  

Thank You

---

### Post by ALLurGroceries on 2011-01-04
@ drum4zirrus

It's the source code to the eeepc-wmi kernel module, found in your kernel source tree. You need to rebuild this module after modifying the source. If you want detailed instructions let me know and I can try to write them up when I get some time.

---

### Post by fuduntu on 2011-01-06
> **ALLurGroceries said:**
> Forcing acpi_osi=Linux on this machine reduces the maximum brightness.


It also instructs the BIOS to send ASUS specific key presses (fn-f1, fn-f2, fn-space, etc) to the OS, and fixes a problem with RFKill not toggling the WIFI and Bluetooth radios.  The hotkeys will never work right without it.

> **ALLurGroceries said:**
> 
Edit: Jupiter is cute... nice interface... unfortunately it does nothing for hotkeys.


Sure it does, install jupiter-support-eee.

```

$ cat /etc/acpi/actions/eeepc-actions.sh 
#!/bin/bash
#
# EeePC Actions
# Andrew Wyatt
# Generic script to take actions on keypress
#

JUPITER_VAR="/var/jupiter"
JUPITER_PATH="/usr/lib/jupiter/scripts"

KERNEL_REV=$(uname -r | sed -s -e "s#-.*##" -e "s#2.6.##" -e "s#\W.*\$##")

. /usr/lib/jupiter/scripts/notify
. /etc/default/jupiter-support-eee


EEE_USER=$(who | sed -n '/ (:0[\.0]*)$\| :0 /{s/ .*//p;q}')

SELECTION=$3

if [ "$KEY_SHOW" = "1" ]; then
      notify "$SELECTION" "/usr/share/pixmaps/jupiter/jupiter.png"
fi

### Define Kernel specific actions here..
if (( "$KERNEL_REV" < "31" )); then
  KEY_WIFI="00000010"
fi
###

case $SELECTION in
  "")
    exit 0
  ;;
  $KEY_RESOLUTION)
     su $EEE_USER -l -c "DISPLAY=:0 $JUPITER_PATH/resolutions" &
  ;;
  $KEY_ROTATE)
     su $EEE_USER -l -c "DISPLAY=:0 $JUPITER_PATH/rotate" &
  ;;
  $KEY_FSB)
     $JUPITER_PATH/cpu-control &
  ;;
  $KEY_VGAOUTA)
     $JUPITER_PATH/vga-out clone &
  ;;
  $KEY_VGAOUTB)
     $JUPITER_PATH/vga-out vga &
  ;;
  $KEY_VGAOUTC)
     $JUPITER_PATH/vga-out lvds &
  ;;
  $KEY_WIFI)
     $JUPITER_PATH/wifi &
  ;;
  $KEY_PERFMON)
    notify "$KEY_PERFMON_NAME" "$KEY_PERFMON_ICON"
    su $EEE_USER -l -c "DISPLAY=:0 $KEY_PERFMON_COMMAND $KEY_PERFMON_ICON" &
  ;;
  $KEY_TOUCHPAD)
    su $EEE_USER -l -c "DISPLAY=:0 $JUPITER_PATH/touchpad" &
  ;;
  $KEY_BT)
     $JUPITER_PATH/bluetooth &
  ;;
  $KEY_CAM)
     $JUPITER_PATH/camera &
  ;;
  $KEY_CUSTOMA)
    notify "$KEY_CUSTOMA_NAME" "$KEY_CUSTOMA_ICON"
    su $EEE_USER -l -c "DISPLAY=:0 $KEY_CUSTOMA_COMMAND" &
  ;;
  $KEY_CUSTOMB)
    notify "$KEY_CUSTOMB_NAME" "$KEY_CUSTOMB_ICON"
    su $EEE_USER -l -c "DISPLAY=:0 $KEY_CUSTOMB_COMMAND" &
  ;;
  $KEY_CUSTOMC)
    notify "$KEY_CUSTOMC_NAME" "$KEY_CUSTOMC_ICON"
    su $EEE_USER -l -c "DISPLAY=:0 $KEY_CUSTOMC_COMMAND" &
  ;;
  $KEY_CUSTOMD)
    notify "$KEY_CUSTOMD_NAME" "$KEY_CUSTOMD_ICON"
    su $EEE_USER -l -c "DISPLAY=:0 $KEY_CUSTOMD_COMMAND" &
  ;;
esac

```

---

### Post by ALLurGroceries on 2011-01-06
> **fuduntu said:**
> It also instructs the BIOS to send ASUS specific key presses (fn-f1, fn-f2, fn-space, etc) to the OS, and fixes a problem with RFKill not toggling the WIFI and Bluetooth radios.  The hotkeys will never work right without it.

If you want to get those hotkeys working with eeepc-wmi instead of eeepc-acpi you can use my modifications above to the kernel module. That way you don't get reduced brightness and everything works this way (except for cycling through SHE settings with Fn+F9, I haven't gotten to that yet). I was using the eee script for Jupiter but it broke my touchpad, and some of the hotkeys still didn't work. Cheers. :)

---

### Post by fuduntu on 2011-01-06
> **ALLurGroceries said:**
> If you want to get those hotkeys working with eeepc-wmi instead of eeepc-acpi you can use my modifications above to the kernel module. That way you don't get reduced brightness and everything works this way (except for cycling through SHE settings with Fn+F9, I haven't gotten to that yet). I was using the eee script for Jupiter but it broke my touchpad, and some of the hotkeys still didn't work. Cheers. :)

Do you mean that it disabled your touchpad (fn-f3, or jupiter -> Devices -> Enable Touchpad)?  It can't possibly break it.

I haven't used eeepc-wmi, I'll take a look but I'm not a fan of recompiling kernel modules to make things work (hard coded key codes in the kernel makes my skin crawl).

Interesting blurb about the brightness, the Eee PC sets it to 133 decimal by default probably to increase the life of the backlight.

You can "overdrive" it by tweaking a PCI configuration register:

[http://forum.eeebuntu.org/viewtopic.php?p=17759#p17759](http://forum.eeebuntu.org/viewtopic.php?p=17759#p17759)

---

### Post by ALLurGroceries on 2011-01-06
@fuduntu I didn't have it disabled, I had to re-enable it manually at startup, I'm on debian though. I didn't bother to find out why it was doing that, because I found a different solution. :p Nice tip about the brightness. About hardcoded stuff, you might want to look at the eeepc-acpi module and asus-laptop modules, they also hardcode things... it takes about 3 seconds to compile anyway. Not a huge deal if you're used to building modules, a pain though if you run a stock one and don't mess around with the kernel.

Edit: The latest BIOS (0904 released Jan 5) seems to have changed the maximum brightness level with or without acpi_osi=linux, at the highest setting it's at the maximum backlight brightness. It took 10+ minutes to flash, which was weird, but it did that the last time.

---

### Post by PALKOVNIK on 2011-01-09
> **ALLurGroceries said:**
> 
Edit: The latest BIOS (0904 released Jan 5) seems to have changed the maximum brightness level with or without acpi_osi=linux, at the highest setting it's at the maximum backlight brightness. It took 10+ minutes to flash, which was weird, but it did that the last time.

offtop, anyway, how can i check my BIOS version on my 1015?? asking, because can't find it myself

edit: also, could you write here md5sum of your new bios-file (0904)??

---

### Post by ALLurGroceries on 2011-01-09
@PALKOVNIK, there are a few ways to tell what BIOS you are on. The POST screen should tell you, if you have quiet boot enabled you have to hit Esc at the asus logo when you first turn the computer on. If you can't catch it fast enough, you can just press F2 to get into the BIOS setup utility and that will show you.

If you don't want to reboot, you can install the hwinfo package and run:
```
sudo hwinfo --bios | grep -i version
```

The first "Version:" number should be your BIOS revision.

The MD5 for the .ROM itself that I flashed is: 668330820583c817b1e16dd0c653eb87

---

### Post by PALKOVNIK on 2011-01-09
1 more question:
i use network manager to manage wi-fi connections and when i turn on wireless it (nm) refreshes the networks-list very slow, but iwlist shows networks immediately
everybody has got same problem?? or does anybody know how to fix it??
to manage wireless by iwlist and iwconfig is not and option because i use lots off different networks

---

### Post by fuduntu on 2011-01-10
> **ALLurGroceries said:**
> @PALKOVNIK, there are a few ways to tell what BIOS you are on. The POST screen should tell you, if you have quiet boot enabled you have to hit Esc at the asus logo when you first turn the computer on. If you can't catch it fast enough, you can just press F2 to get into the BIOS setup utility and that will show you.

If you don't want to reboot, you can install the hwinfo package and run:
```
sudo hwinfo --bios | grep -i version
```

The first "Version:" number should be your BIOS revision.

The MD5 for the .ROM itself that I flashed is: 668330820583c817b1e16dd0c653eb87

You can also 'sudo dmidecode -s bios-version'

---

### Post by ALLurGroceries on 2011-01-10
@PALKOVNIK I don't have any problems with brcm80211, but I did always have issues with broadcom sta/wl.

@fuduntu thanks that's the right way to do it, I forgot about dmidecode. :)

---

### Post by PALKOVNIK on 2011-01-11
[QUOTE=ALLurGroceries;10341049]@PALKOVNIK I don't have any problems with brcm80211, but I did always have issues with broadcom sta/wl.
QUOTE]

how did you build it??
i'm using this guide [http://ohioloco.ubuntuforums.org/showthread.php?t=1617380](http://ohioloco.ubuntuforums.org/showthread.php?t=1617380)
with driver from [http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz](http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz)

and it's not working, it builds, but not working (however, iwlist and network manager are showing networks, but can't connect to any of them)

---

### Post by ALLurGroceries on 2011-01-11
@PALKOVNIK did you install the firmware? There's a guide here: [http://ubuntuforums.org/showthread.php?t=1617380]("http://ubuntuforums.org/showthread.php?t=1617380")

edit: oops you linked that guide... :p

---

### Post by PALKOVNIK on 2011-01-12
ummm, question about brcm80211 again
does it work in ad-hoc mode??
i've alredy installed debian and still got nothing

---

### Post by ALLurGroceries on 2011-01-13
@PALKOVNIK, I just tried ad-hoc and it doesn't seem to work, I'm not sure if it's supposed to be working yet (it's a staging driver). In syslog I get this:
```
Jan 13 15:24:55 1015pem wpa_supplicant[1769]: Failed to set operating mode
Jan 13 15:24:55 1015pem NetworkManager[1752]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 13 15:24:55 1015pem NetworkManager[1752]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 13 15:24:55 1015pem NetworkManager[1752]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 13 15:25:01 1015pem NetworkManager[1752]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 13 15:25:01 1015pem NetworkManager[1752]: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Jan 13 15:25:01 1015pem NetworkManager[1752]: <warn> Activation (wlan0) failed for access point (test)

```

---

### Post by drum4zirrus on 2011-01-14
> **ALLurGroceries said:**
> @ drum4zirrus

It's the source code to the eeepc-wmi kernel module, found in your kernel source tree. You need to rebuild this module after modifying the source. If you want detailed instructions let me know and I can try to write them up when I get some time.

Hi!

That would be really nice! I have no idea where to start and how to edit the kernel. And rebuilding sounds scarry to me ;). I wouldn't like to break the machine...

Thank you a lot

---

### Post by ALLurGroceries on 2011-01-14
@drum4zirrus you can just update the bios and force acpi_osi=linux from the boot prompt instead. The newest bios doesn't reduce the backlight brightness like the previous versions. If you don't force acpi_osi at boot, it will default to wmi instead of acpi, and that is why I modified the module in the first place.

If you want to use eeepc-wmi for some other reason (like to modify the fn + esdf keys to be media keys as I have) then I will try to write some short instructions.

To update your bios go to [http://support.asus.com/download/](http://support.asus.com/download/) and choose Eee family. You have to unzip and rename the bios image file to 1015PE.ROM and put it on a freshly FAT-formatted USB stick, then boot and press alt+f2. Note that it can take 10+ minutes on the programming stage, I have no idea why it takes so long, but don't interrupt it.

---

### Post by drum4zirrus on 2011-01-14
@ALLurGroceries: OK, i jus't tried it... the message "USB drive not found" is not ending. that's not part of the update, is it? Can I interrupt? 

"You can just update the bios and force acpi_osi=linux from the boot prompt instead." 

How can I do that? OMG I don't even get a bios update working. very poor :-)

Thanks a lot!

---

### Post by ALLurGroceries on 2011-01-14
@drum4zirrus

Yeah as long as it's not gotten to the point where it says 'programming' you aren't in the middle of an upgrade and you can reboot or whatever. Make sure your usb drive is formatted fat16.

To force acpi_osi=Linux, press the E key at the grub menu and go to the line that ends in something like 'quiet splash' (not exactly sure what it looks like for ubuntu) and add acpi_osi=Linux. Then press ctrl+x to boot.

[https://help.ubuntu.com/community/Grub2#Editing Menus During Boot]("https://help.ubuntu.com/community/Grub2#Editing Menus During Boot")

If it works you can then make it permanent by editing the grub configuration file in /etc/default/grub like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux"
```

---

### Post by drum4zirrus on 2011-01-14
OK, now I've got it. It was the wrong partition (FAT32). Since I had no idea how to format in FAT16 in ubuntu, I dit it in Windows. Now, it's flashing, hope I get a positive result in the next 8 minutes :-)

Then I will try it with the grub thing. When I get this to work, my 1015 would be almost perfect. I just did a ram upgrade today, now it's performing even better. Nice device :-)

Thank you so much. I really appreciate your support.

Michael

---

### Post by ALLurGroceries on 2011-01-14
Yeah I'm waiting on my 2GB stick to get here... can't come too soon. Once it starts swapping it slows to a crawl, even on a slim Debian install it seems to go about ~100MB over the limit when I've got a lot of browser tabs open (bad habit I know). :p

To make it swap out to disk less, I changed vm.swappiness to 10 (from 60) and it helps, until it gets over ~850MB of memory usage, and then it starts crawling again. You can test this for yourself with
```
sudo sysctl vm.swappiness=10
```

If it seems better, you can make it permanent with:
```
gksudo gedit /etc/sysctl.conf
```
and add the line
```
vm.swappiness=10
```

---

### Post by drum4zirrus on 2011-01-14
Hmm, with 2GB it works quiet fine now. But I will try your hint anyway, so thank you.

Strange, I did it as you told me (see image). But still, only the brightness and the volume keys work... did I forget something? A packet?



Cheers 

Michael

---

### Post by ALLurGroceries on 2011-01-14
Try a capital on Linux instead of lowercase linux, as in acpi_osi=Linux

I'm not sure if that makes a difference, if it does, my fault. :p

---

### Post by drum4zirrus on 2011-01-14
sure makes a difference :-) I now can disable wifi by pressing Fn+F2 (and with the special button on the top left). But if I press it again, it wont turn back on :icon_frown: Do you have the same problem?

EDIT: It takes some time to turn back on :-) Im such a patient person :-)

---

### Post by ALLurGroceries on 2011-01-14
I don't have that problem, but you can try to figure out what's happening by running
```
sudo tail -f /var/log/syslog
```

The first thing I'd look at is rfkill (sudo apt-get install rfkill if it's not installed):
```
sudo rfkill list
```

If it says soft blocked yes for wireless lan, you can force it back with this, where 49 is the ID of the card
```
sudo rfkill unblock 49
```

If that doesn't do the trick, reloading the module may work.

If you're on the proprietary broadcom STA driver, you can try removing and reinserting the driver module:
```
sudo modprobe -r wl; sudo modprobe wl
```

If you're on brcm80211, the same:
```
sudo modprobe -r brcm80211; sudo modprobe brcm80211
```

If none of that works, take a good look at syslog.

Edit: I updated [my post on page 2]("http://ubuntuforums.org/showthread.php?p=10277446#post10277446") with a resume script for brcm80211. Also my 2GB stick of RAM finally came, it makes a huge difference! :)

---

### Post by TAcadia on 2011-04-23
Hey guys,

Had the same issues as well. But now it's all solved! :)

As advised by you guys, here's what I did:

1) Updated the BIOS to the latest 0904
2) Edited the grub file and updated it
3) Installed Jupiter

Now I can can use the FN buttons :)

Thanks loads! Cheers!

---

### Post by Pocio on 2011-06-18
Hi all...I am trying to upgrade the bios of my eeepc 1015pem but the process is on 

Reading file "1015PE.ROM"

from more than 25 minutes...

May I have to worry about it?

---

### Post by ALLurGroceries on 2011-06-18
It should say something like begin programming...

At the programming stage it takes like 10 minutes. If it does not get to programming you probably need to format your usb stick fat16 instead of fat32.

If the flash goes bad there is bootblock recovery. It just reqiures the rom file on a fat16 usb stick with the file called 1015pe.rom

---

### Post by Pocio on 2011-06-18
Thank you very much for the quick reply :)

It says nothing...I have only a blinking cursor at the end of *reading file "1015pe.rom"*

So you say that it is doing nothing and I may shut down the pc?

What exactley is bootblock recovery?

EDIT: I already had ormatted the usb drive fat 16.

---

### Post by ALLurGroceries on 2011-06-18
Yes unless it gets to programming it is not really flashing so you can reboot.

Bootblock recovery is a built in flashing utility if the bios cannot boot normally because it has become damaged. It is like "self help" for bios in the case of a bad flash.

Double check your formatting is actually fat16. If you did it from windows it will be fat32 unless you do it from the command line. If you are certain it is fat16 then maybe download the file again. Make sure to rename it 1015pe.rom or it will not flash.

---

### Post by Pocio on 2011-06-18
Ok, I rebooted and all is fine...thank you thank you thank you very much again and again :)

I checked the drive and actually is FAT16...I really don't know. I use gparted.

Thank you again!!!

---

### Post by ALLurGroceries on 2011-06-18
Hehe. Well ur hands are clean then! I only saw this happen to one person who formatted with windoze and it ended up being fat32 so that was why I mentioned it.

Maybe you got a bad download? I'm not sure of any other reason besides it is really picky about the filename being 1015pe.rom

---

### Post by Pocio on 2011-06-18
The file name was 1015PE.ROM with uppercase...right?

I checked gparted again and I can see that my usb drive had a flag "boot"...maybe is was that?

btw sorry for my bad English :)

---

### Post by ALLurGroceries on 2011-06-18
I'm not sure the boot flag would affect it...

Yeah 1015PE.ROM in uppercase, but I don't think it matters on a FAT filesystem.

---

### Post by ursusarctos on 2011-06-23
First, thanks to everyone in the thread so far for some very good info.

I've just installed 11.04 on my new netbook, and can confirm that the default grub configuration now includes the acpi=Linux tweak.  Also that Jupiter is awesome and quite functional, if a little less responsive than I might like.  With the power saving settings enabled, my battery times now rival those under Windows.

However, I'm having problems with hibernating, and wonder if anyone has any suggestions.  Here's what happens.

When I hibernate the computer (either by a configured lid-close, or through the menu in the upper right, I get a blinking cursor.  Eventually the computer goes dark and powers down, and only the power button does anything.  This seems normal so far.

However, when I power the machine back on, GRUB comes up.  Is this right?

If, in GRUB, I select my linux install, most of the screen (the leftmost 4/5) is filled with random-looking noise.  However, I do get a mouse pointer, and if I enter my password, the right 1/5 of the screen displays the retrieved session from before.  But with 4/5 of the screen filled with junk, that's not very useful.

That said, if I then suspend and resume the machine, the session is fully restored and usable.

Any ideas what's going on here?  Or how to deal with the problem?

---

### Post by trickish on 2011-07-24
Hi guys very informative thread about the 1015pem. I really enjoy your technical skills and great information. 
Im having problems with my wireless and have tried various guides I can connect to networks with no security but not to WPA & WPA2protected networks. I was wondering  if one of you could point me in the direction what you did to get the wireless working?

---

### Post by fuduntu on 2011-07-24
> **trickish said:**
> Hi guys very informative thread about the 1015pem. I really enjoy your technical skills and great information. 
Im having problems with my wireless and have tried various guides I can connect to networks with no security but not to WPA & WPA2protected networks. I was wondering  if one of you could point me in the direction what you did to get the wireless working?

If you are using WPA with TKIP, switch it to AES.

---

### Post by trickish on 2011-07-24
> **fuduntu said:**
> If you are using WPA with TKIP, switch it to AES.
Thanks for the reply how do i see if im using TKIP and afterwards switch it to AES? Sorry im a noob with this technical stuff.
Edit i found out that it is something about changing the details on the router which i do not have access to do.

---

### Post by fuduntu on 2011-07-24
> **trickish said:**
> Thanks for the reply how do i see if im using TKIP and afterwards switch it to AES? Sorry im a noob with this technical stuff.
Edit i found out that it is something about changing the details on the router which i do not have access to do.

The change would have to be made on your WIFI router.  Consult your router users guide for guidance.

---

### Post by trickish on 2011-08-03
> **fuduntu said:**
> The change would have to be made on your WIFI router.  Consult your router users guide for guidance.

Thanks for the advice. I do not have access to my router so this will not be possible and i also have the problem in other locations. So i will just continue to look for answers. Again thanks for your feedback. Anyone else with a 1015pem who managed to solve the problem?

---

### Post by StarZtorm on 2011-09-29
This is the greatest thread i have ever seen for this computer. thank you guys so much! <3

I have my 1015PEM running only Ubuntu. erased the whole disc when i got it and installed 10.10 first, and then freshly installed 11.04 when it came out. (I bought the netbook in february 2011) I havent done any updates to bios or the hardware yet, but im planning to do it prior to installing Oneiric Ocelot when it launches 13. October. 

And for the record i love unity.

Alas, i have a question. When i upgrade to Ocelot, and i have the 2GB RAM module installed and bios updated (dunno about the HDD yet. thinking about getting a SSD, but its damn expensive when u want some size). Are there any advantages to the 64bit version of the OS instead of the 32bit?

---

