---
title: "How to enable Fn keys on Eee PC 1005HA and 10.04 Lucid Lynx?"
date: 2010-04-30
forum: Hardware
---

### Post by Lazy-legs on 2010-04-30
Hello,

I've just installed Ubuntu 10.04 Lucid Lynx on my Eee PC 1005HA, and everything seems to work except the Fn keys. The only Fn keys that work out of the box are Brightness Up/Down.

I'm mostly interested in making the Volume Mute/Up/Down keys work, and I'd be grateful for any advice and pointers.

Thank you!

---

### Post by kevinp93 on 2010-04-30
[I][B][I]Hi!
[/I][/B][FONT=Arial]
Try these steps.[/FONT]
1)  Open terminal and type  [/I]```
**sudo gedit /etc/default/grub
```[I]
2)  enter password
3) add [/I]```
acpi_osi=Linux
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT
```,  so that it will look like: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"
```
4) save file
5) open terminal again, and type ```
sudo update-grub
```
6) restart the machine
7) use hotkeys  :)

I  followed those steps on my EEE1005HA, and everything worked. Just have  to find a way to ensure dialog boxes come up stating what has been done  (e.g. Volume muted).

---

### Post by kevinp93 on 2010-04-30
And I have kind of found a way to enable the messages. So when I click 'FN' & 'Space' it tells me what mode I am using (it's just a bit slow in changing the status). I followed the steps from [here]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/"), just go to the bit with the title "**Super Hybrid Engine, Installing an eeePC tray utility, and  getting all hotkeys to work". **Also you don't need to install "eeepc-laptop-dkms" according to some  other threads which I went through (even if you tried, you'll get some  error message).And there's no need to go into the "**Finishing off: Final hotkeys" **part. 

SO yeah, that is basically it. It isn't flawless, but it still works:)

---

### Post by Lazy-legs on 2010-05-02
Adding *acpi_osi=Linux* did the trick. Thank you so much, kevinp93!

---

### Post by shihkster1015 on 2010-05-03
How's the battery consumption compared to karmic koala??

---

### Post by marvelty on 2010-05-03
> **kevinp93 said:**
> And I have kind of found a way to enable the messages. So when I click 'FN' & 'Space' it tells me what mode I am using (it's just a bit slow in changing the status). I followed the steps from [here]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/"), just go to the bit with the title "**Super Hybrid Engine, Installing an eeePC tray utility, and  getting all hotkeys to work". **Also you don't need to install "eeepc-laptop-dkms" according to some  other threads which I went through (even if you tried, you'll get some  error message).And there's no need to go into the "**Finishing off: Final hotkeys" **part. 

SO yeah, that is basically it. It isn't flawless, but it still works:)


That how-to recommends installing eeepc-tray which is no longer supported or updated. (the project has become "Jupiter" and is available only through sourceforge/download or eeebuntu repositories) It is a great utility but it tends to crap out after key packages are updated - and without updates itself it won't start working again.

---

### Post by kuurozaki on 2010-05-06
> **kevinp93 said:**
> [I][B][I]Hi!
[/I][/B][FONT=Arial]
Try these steps.[/FONT]
1)  Open terminal and type  [/I]```
sudo gedit /etc/default/grub
```[I]
2)  enter password
3) add [/I]```
acpi_osi=Linux
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT
```,  so that it will look like: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"
```4) save file
5) open terminal again, and type ```
sudo update-grub
```6) restart the machine
7) use hotkeys  :)

I  followed those steps on my EEE1005HA, and everything worked. Just have  to find a way to ensure dialog boxes come up stating what has been done  (e.g. Volume muted).

it works perfectly! Thanks kevin93.... :p

---

### Post by mb36 on 2010-05-17
For EeePC 1001HA the instructions under #2 worked even better than expected. This means I got WiFi (Fn+F2), keypad enable/disable (Fn+F3), Monitor toggle (Fn+F'8') and all three volume hotkeys (Fn+F10-12). The notifications for volume change work. As a bonus the silver touchpad enable, to the left, works which is even better than under Karmic!

Thanks!

---

### Post by Jikul on 2010-05-19
I did this on my 1000HE and everything is working great, except the volume keys. Any ideas?

---

### Post by chapman.s87 on 2010-05-21
Hey thanks the the poster who showed how to get the function key working. Could someone explain what exactly happens when you add this to the grub code??

---

### Post by dsfitzpat on 2010-05-21
The issue is explained pretty well in the bug report (bug #505452: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452))
Basically the eeePC bios is programmed to determine the operating system being used at boot - and adding this line lets it know.
As a bonus fix, they explain how to keep notifications working for the brightness hotkeys - see post #44.

---

### Post by sabutuga on 2010-05-25
Thank you kevinp93. your instructions it worked great for me excepet for the Fn space!
Have you got any idea how to fix this and/or where do I change the clock speed on a eeepc 1005 with Ubuntu NBR installed?

thank you

---

### Post by applesauceyeah on 2010-05-29
_Thank you, _[kevinp93]("http://ubuntuforums.org/member.php?u=1063380")!

The solution also works on 1000HE.

---

### Post by henriquemaia on 2010-06-07
This solution works on my 1000HE, I get the fn keys working, but there's a strange side-effect: 

when a sound occurs (like a telepathy contact online notification), the computer screen dims and the battery is activated (just for a brief moment). If, for instance, I remove the battery and a sound starts, the computer shuts down immediately (due to the lack of power).

In order to stop this odd behavior, I just have to remove the **acpi_osi=Linux** and things go back to normal... but I have no fn keys.

Does anyone have an idea how to solve this?

---

### Post by barrieluv on 2010-06-07
I haven't done any of the fixes suggested but after a recent kernel update my volume keys are now working as well as brightness/suspend/wifi on-off.

---

### Post by henriquemaia on 2010-06-07
> **barrieluv said:**
> I haven't done any of the fixes suggested but after a recent kernel update my volume keys are now working as well as brightness/suspend/wifi on-off.


With the latest kernel on mine, some fn keys work, some do not (volume keys, for instance).

---

### Post by lloydm on 2010-06-12
got eeebuntu 3.0 live cd and i noticed that all function keys were working so i copied the eeepc-acpi.local from the live cd and used that on my 1005ha running nbr 10.04 and now all Fn keys work!!

#
# Configuration file for EeePC ACPI utilities
# Andrew Wyatt
# Generic ACPI utilities for the EeePC line of netbooks.
#

# NOTE: Copy this file to eeepc-acpi.local and edit the copy,
#       this will save your settings between upgrades.
#
# If you choose to edit this file instead when you upgrade, it will
# be automatically copied to eeepc-acpi.local and overwritten.
#
# When editing the .local version, be sure to clear out keys that you don't
# need rather than commenting.  This will prevent conflicts.
#
# Example: If you are disabling WIFI and using FN-F2 for Bluetooth, add the
# following without the #s:
#
# KEY_WIFI=""
# KEY_BT="00000010"
#
# This will remove the default configuration from KEY_WIFI and assign that key
# to KEY_BT.

# This is the path to the ACPI utilities.

EEEPC_PATH=/etc/acpi/eeepc
EEEPC_VAR=/var/eeepc

# If you are using a WIFI driver that is non-standard for the Eee, or otherwise
# detected incorrectly, set it here.
#
# Example: WIFI_DRIVER="ndiswrapper" or WIFI_DRIVER="ath5k"
#
# WIFI_DRIVER=""

# Eee PC function keys; If a key doesn't do its intended function, uncomment
# KEY_SHOW, save, then press that key to get its ID.  Replace the key ID with
# the ID shown on your screen, and then re-comment KEY_SHOW.
# Example:
# if KEY_VGAOFF is 00000016, but using KEY_SHOW you see that it is really 00000017 then
# set KEY_VGAOFF to "00000017".

# KEY_SHOW="1"

# To disable an option, put a # in front of it, and to enable an option, remove the #.
# Be cautious not to hook two functions to one key, or weird things could happen
# (Touchpad disable could also open firefox if both are enabled, and vice versa)

# This is the trigger key to turn the active display on and off.
KEY_VGAOFF="00000016"

# This is the trigger key to enable or cycle through connected displays.
KEY_VGAOUTA="00000030"
KEY_VGAOUTB="00000031"
KEY_VGAOUTC="00000032"

# This is the trigger key to start Performance Monitor
KEY_PERFMON="00000012"
KEY_PERFMON_COMMAND="/usr/bin/gnome-system-monitor"
KEY_PERFMON_NAME="System Monitor"
KEY_PERFMON_ICON="gnome-monitor"

# This is the trigger key to toggle WIFI on and off.
KEY_WIFI="00000010"

# These trigger keys toggle volume up and down and mute.
KEY_VOLU="00000015"
KEY_VOLD="00000014"
KEY_MUTE="00000013"

# This is the trigger key to toggle the touchpad on and off.
KEY_TOUCHPAD="0000001a"

# This is the trigger key to cycle through available resolutions.
KEY_RESOLUTION="0000001b"

# This is the trigger key to toggle USB power on and off.
# KEY_USB="0000001c"

# This is the trigger key to toggle Bluetooth off and on.
KEY_BT="0000001c"

# This is the trigger key to toggle Webcam off and on.
KEY_CAM="0000001d"

# This is the trigger key to cycle through screen rotation.
# KEY_ROTATE="0000001c"

# This is the trigger key to cycle through CPU states (Performance, Ondemand, and Powersave)
# KEY_FSB="0000001d"

# To enable custom commands, comment out the keys above that match the trigger key
# Ex: 0000001a matches the Touchpad toggle and Firefox.
#
# Next uncomment the custom key you would like enabled, and all of the associated options.
#
# The format of the custom keys are as follows:
#
# KEY_CUSTOM is the trigger key.
# ""_COMMAND is the program to execute.
# ""_NAME is the display name to show in the notification.
# ""_ICON is the icon to display in the notification.

# KEY_CUSTOMA="0000001a"
# KEY_CUSTOMA_COMMAND="/usr/bin/firefox"
# KEY_CUSTOMA_NAME="Firefox"
# KEY_CUSTOMA_ICON="firefox-3.0"

# KEY_CUSTOMB="0000001b"
# KEY_CUSTOMB_COMMAND="/usr/bin/pidgin"
# KEY_CUSTOMB_NAME="Pidgin"
# KEY_CUSTOMB_ICON="pidgin"

# KEY_CUSTOMC="0000001c"
# KEY_CUSTOMC_COMMAND="/usr/bin/gcalctool"
# KEY_CUSTOMC_NAME="Calculator"
# KEY_CUSTOMC_ICON="accessories-calculator"

# KEY_CUSTOMD="0000001d"
# KEY_CUSTOMD_COMMAND="/usr/bin/evolution --component=mail"
# KEY_CUSTOMD_NAME="Evolution"
# KEY_CUSTOMD_ICON="evolution"

# Disable touchpad when typing
# The TOUCHPAD_KEY_DISABLE option enables / disable stopping the touchpad while typing (1=on and 0=off)
TOUCHPAD_KEY_DISABLE="1"

# TOUCHPAD_DELAY is the delay in seconds before re-enabling the touchpad after typing
TOUCHPAD_DELAY="0.5"

# Volume control
# 
# Options:
# Set to "AUTO" and the tool will adjust all playback devices.
# Set to "FAKE" to the tool will send ACPI fake keypresses to adjust volume and display desktop OSD
# Set to "LineOut" or your specific device for fine control.
#
# Change increment of volume increase / decrease by adjusting VOL_ADJ (Default "2dB")

VOL_DEV="AUTO"
VOL_ADJ="1dB"

# Settings for CPU on Battery vs AC.  These are triggers initiated by plug and unplug events.
# There is normally no need to change them unless your Eee PC is not changing power options
# when plugged in and then unplugged.

POWER_AC="00000050"
POWER_BAT="00000051"

# Mode settings for Eee PC when plugged in or on battery.
# MODE_AC = Plugged in
# MODE_BAT = Unplugged

MODE_AC="performance"
MODE_BAT="ondemand"

# Enable following to implement all of the powersave controls with one exception.  It will
# use the "ondemand" scaler rather than "powersave" which will increase performance of your
# Eee at the cost of some battery life.
#
# If you aren't taxing the CPU the power savings difference is minimal.  This will however let
# you watch a movie in Power Saver mode.
#
# FASTER_POWERSAVE="1"

# Stop these services if running when going to ondemand or powersave modes.  Start them if
# they aren't running when entering performance mode.
#
# Comment with a # to disable this feature, add or remove services at will, just keep a space
# between them.
#
# Check to make sure you are already running some of these before blanket enabling because
# it doesn't check the runlevel, it just starts and stops them.
#

# PAUSE_SERVICES="anacron crond atd sshd"

# The following option will turn off power to all USB devices that support suspending power.
# This doesn't seem to work for USB connected lights.  Use with caution, it does a sync
# before powering off but if you have drives mounted they will not be cleanly unmounted!
#
# If you are booting from a USB device such as your card reader, or thumb drive, this will
# probably crash your computer.
#
# Set to 1 to enable and 0 to disable
#
# USB_SUSPEND=1

# Set these to override assumed states, useful to force overclocking of FSB or to support devices
# not properly detected.  If you experience lockups, etc; boot single and look at /proc/eee/fsb to get
# new default settings.
#
# The Eee PC FSB format is typically "100 24 1" or "30 15 1".  These break down to the following:
#
# FSB: 100
# MULTIPLIER: 24
#
# Voltage is managed automatically and is not yet a parameter.  If you are using a system that supports
# an FSB overclock of 110, but this tool defaults you to 100 then change OVERRIDE_FSB to "110".

# OVERRIDE_FSB=""
# OVERRIDE_MULTIPLIER=""

# This option will allow you to apply a custom scale.  Only use this option if instructed by the maintainer.
# FSB_SCALE=""
#
# This option will eliminate FSB scaling; for example it will allow shifting from performance to ondemand
# but it will not alter the FSB settings.  If this is enabled, all FSB changes are ignored including overrides.

# DONOT_SCALE_FSB="1"

# Set this to "managed" or "auto".  When set to "managed" the utilities provided in this package will manage
# your fan for you and you will be able to set thresholds by altering the TEMP values below.  When set to
# "auto" the fan will be managed by your BIOS.
FAN_MODE="managed"

# Eee PC temperature control settings (only applies if fan is managed). These values are in Celcius, and when
# the temperature rises above the defined value, the fan management utility will increase fan speed until the
# temperature is reduced back below the threshold.

TEMP_NORMAL=55
TEMP_WARN=60
TEMP_CRIT=70

# The following parameters define what to restore on startup.  When changing state 1=on and 0=off.
# When you boot your machine and log in, anything set to 1 will restore setting back to previously set
# value, otherwise previous settings will be ignored.
#

# Restore USB state (powered on or off)
# BOOT_USB=1

# Restore Bluetooth
BOOT_BLUETOOTH=1

# Restore Camera
BOOT_CAMERA=1

# Number of seconds to delay before changing CPU speed.  This allows the system more time to complete startup
# before switching to a slower mode.
BOOT_CPU_DELAY=45

# Set screen resolution on startup
BOOT_RESOLUTION=1

# Restore LVDS panel on / off
BOOT_LVDSOFF=1 

# Restore Screen Rotation
BOOT_ROTATION=1

# Restore touchpad
BOOT_TOUCHPAD=1

# Restore external monitor
BOOT_VGA=1

# Restore WIFI
BOOT_WIFI=1

---

### Post by ginobe on 2010-06-12
i know this if prob not the right place but i'm a total noob and need major help with my sony vgn-fs980. i installed ubuntu 10.04 and everything seems to work except of course the fn key. i found another thread which provided a like to install a fsfn .deb package but its not working for me and no one has replay from that thread so was wondering if anyone can be so kind to lend me a hand please. thanks in advance.  :)

---

### Post by l0b0 on 2010-06-21
Worked on 1005HAB as well, thanks! BTW, does anyone know of a BIOS setting that could take care of this instead?

---

### Post by teaker1s on 2010-07-04
Hi, grub entry worked for me.
With great expectations I tried [http://auroraos.org/](http://auroraos.org/) and found it extremely disappointing on my 1001ha.(plus they are currently running part their own version and part standard Debian repositories (it will break)

But it did offer jupiter [http://auroraos.org/project/jupiter](http://auroraos.org/project/jupiter) which works nicely on lucid if you install the deb and eeepc deb from sourceforge

function space bar changes power mode

---

### Post by Mike8913 on 2010-07-07
i started to do what post #2 says but I found that my grub folder must be located elsewhere as the terminal command opened up and empty file...


any idea, running lucid

---

### Post by mabtifro2 on 2010-07-09
mine too was empty!!! can someone please upload their grub file, or paste the complete file code?

i have other problems with my upgrade, most notably, the multi-touch/ two-finger scrolling stopped working too. did any of you experience that? i followed instructions on enabling the multi-touch for my 1005ha on 9.10 a few months agho, but its all been lost with this 10.04 update

---

### Post by leekb on 2010-07-11
I have also wiped out Windows XP from my Eee PC 1000H and installed Ubuntu 10.04 Netbook Edition on it. Everything works fine including audio, video, touchpad, wifi, lan, sd card reader, etc. The grub entries fixed most of the Fn keys and custom hard keys are working. Thanks.:KS
[U][B]
Asus Eee PC 1000H[/B][/U]
Fn+F1 = Suspend. Works even before the grub fix.
Fn+F2 = Wireless/Bluetooth Toggle. Works even before the grub fix. However, it seems to toggle WiFi only. In XP it toggles Bluetooth as well. That's not a problem though. No on-screen notification. 
Fn+F5 = Decrease Brightness. Works even before the grub fix. Before grub fix, on-screen notification was available. After the grub fix, on-screen notification stopped working.
Fn+F6 = Increase Brightness. Works even before the grub fix. Before grub fix, on-screen notification was available. After the grub  fix, on-screen notification stopped working.
Fn+F8 = Toggle monitor. Works after applying the grub fix. No on-screen notification.
Fn+F9 = ? combo key. Works after applying the grub fix. I remapped this key combo to launch an application.
Fn+F10 = Mute. Works after applying the grub fix. On-screen notification works fine too.
Fn+F11 = Decrease Volume. Works after applying the grub fix. On-screen notification works fine too.
Fn+F12 = Increase Volume. Works after applying the grub fix. On-screen notification works fine too.

Custom Hard Key #1 = Activate Screen Saver. Works after applying the grub fix.
Custom Hard Key #2 = No response before and after the grub fix.
Custom Hard Key #3 = User Hard Key. Works after applying the grub fix. Key remapped to launch app.
Custom Hard Key #4 = User Hard Key. Works after applying the grub fix. Key remapped to launch app.

---

### Post by mabtifro2 on 2010-07-12
> **Mike8913 said:**
> i started to do what post #2 says but I found that my grub folder must be located elsewhere as the terminal command opened up and empty file...


any idea, running lucid

hey mike, i had the same problem. i started a new thread and was able to solve the problem. basically you have to edit the /boot/grub/menu.lst file by adding "acpi_osi=Linux" to the line "# defoptions=quiet splash" so that it becomes:

"# defoptions=quiet splash acpi_osi=Linux"

then run "sudo update-grub"

if a prompt pops up asking you what to do (like in my attachment), choose the first option (install the package maintainer's version). then restart and it should work. refer to my thread for more detail:

[http://ubuntuforums.org/showthread.php?t=1529767](http://ubuntuforums.org/showthread.php?t=1529767)

---

### Post by Gatemaze on 2010-07-18
Nice one guys... All seem to work, except from the Fn+F7 = blank monitor, which used to work before the acpi additions... any ideas on this?

Cheers

---

### Post by warpasylum on 2010-07-24
hey guys, i've got a 1005pe n' i've got the same issue after upgrading to lucid just now. all was fine in karmic.

---

### Post by warpasylum on 2010-07-24
Changed grub line in /etc/default/grub from GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash acpi_osi=Linux acpi_backlight=vendor" according to the instructions at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505452). Works great on my 1005PE.

---

### Post by verminform on 2010-07-24
Asus ePC 1015PE - Lucid


Thank you very much.

---

### Post by MarkieB on 2010-10-06
no longer participating in ubuntuforums.org

---

### Post by introspectif on 2010-12-03
This worked on my Eee PC 901. Thanks!

---

### Post by Navyblue on 2011-03-19
> **leekb said:**
> 
Fn+F1 = Suspend. Works even before the grub fix.
Fn+F2 = Wireless/Bluetooth Toggle. Works even before the grub fix. However, it seems to toggle WiFi only. In XP it toggles Bluetooth as well. That's not a problem though. No on-screen notification. 
Fn+F5 = Decrease Brightness. Works even before the grub fix. Before grub fix, on-screen notification was available. After the grub fix, on-screen notification stopped working.
Fn+F6 = Increase Brightness. Works even before the grub fix. Before grub fix, on-screen notification watills available. After the grub  fix, on-screen notification stopped working.
Fn+F8 = Toggle monitor. Works after applying the grub fix. No on-screen notification.
Fn+F9 = ? combo key. Works after applying the grub fix. I remapped this key combo to launch an application.
Fn+F10 = Mute. Works after applying the grub fix. On-screen notification works fine too.
Fn+F11 = Decrease Volume. Works after applying the grub fix. On-screen notifitchcation works fine too.
Fn+F12 = Increase Volume. Works after applying the grub fix. On-screen notification works fine too.

I am Eee PC 1015 PEM, Everything is as described. Except that there is a bug for brighness OSD. At maximum brightness, the OSD isn't at maximum (at about 2/3), however it still take the same 5 notches from minimum to maximum.

On top of that, after adjusting brightness, there will be a drop in brightness when a key is pressed (brightness OSD would appear too). However after adjusting the brightness and another function key is toggled (such as volume), the brightness will drop but will instantly revert (brightness OSD would still briefly appear).

So it's either the volume control or the brightness control.

---

### Post by mhpathfinder on 2011-06-13
Yet nother vote of thanks to KevinP93.  Fixed my EEE PC 1000HEB Fn issue.
MH

In Re:
Re: How to enable Fn keys on Eee PC 1005HA and 10.04 Lucid Lynx?
Hi!

Try these steps.
1) Open terminal and type
Code:

sudo gedit /etc/default/grub


2) enter password
3) add
Code:

acpi_osi=Linux

to
Code:

GRUB_CMDLINE_LINUX_DEFAULT

, so that it will look like:
Code:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"

4) save file
5) open terminal again, and type
Code:

sudo update-grub

6) restart the machine
7) use hotkeys

---

### Post by theDaveTheRave on 2012-05-24
I may have found a solution for others who can't get thier various function keys to work.

Open a terminal and run 
```
xev
```
now any key you press (or mouse movement0 will send the information into the terminal. If it is a hotkey that is allready set up may get a 'Notify Event' message.

When I did this I found my F3 key with a Fn combo became an XF86TouchpadToggle event.
The next job was to write a custom shell script to turn the touchpad on and off, then use the XF86TouchpadToggle as the property for a new custom shortcut, and set it to see my shell script.


----Extra info just in case the above doesn't work----
It is possible to determine what the key codes for all the key press combinations, you need to skip into a 'proper terminal' (use Ctrl Alt Fn [n=1 to 12 ~]  ie a function key)

Login into this 'session' and run the following command

```
dumpkeys
```
this command produces a lot of output, so I recomend sending it to a file for easier reading, like the following...
```
dumpkeys >keyInfo.txt
```

Now if that file doesn't get you anywhere, you may need this command...
```
getKeyCodes
```
again you may want to redirect to a file.

then you can look for the key combo you are interested in.

Alternatively you can run
```
showkey -a
```
or
```
showkey -s
```

then when you press your key combo you will get the ASCII return codes for them. 

References...

I found the xev stuff on the web, but I can't find the link now!
showkey stuff comes from [http://rick.vanrein.org/linux/funkey/]("http://rick.vanrein.org/linux/funkey/")
and to be able to run dumpkeys and getKeyCodes without errors I figured out from a reply on [LinuxQuestions]("http://www.linuxquestions.org/questions/linux-general-1/error-with-dumpkeys-and-setkeycodes-362836/").

David.

I've become a bit of a rarity on these forums over the last year or so, so if you want more info you may find I respond quicker to a pm, but remember to post here also, to help others.

---

