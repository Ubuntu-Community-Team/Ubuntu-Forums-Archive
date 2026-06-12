---
title: "Asus K52 / Asus A52"
date: 2010-04-23
forum: Hardware
---

### Post by jsevi83 on 2010-04-23
[COLOR=Blue]UPDATE: Ubuntu Precise Pangolin 12.04[/COLOR]

Everything works out of the box except suspend and toggling wireless led. You can install this pacakge to solve them: [http://dl.dropbox.com/u/62752658/asus-k52_1.0_precise.deb](http://dl.dropbox.com/u/62752658/asus-k52_1.0_precise.deb)

Or if you prefer, you can solve things manually:


**- SUSPEND:** you need to create a new file with these commands:

sudo gedit /etc/pm/sleep.d/20_custom-asus-k52
```
#!/bin/sh

case "${1}" in
        hibernate|suspend)
              # Switch USB buses off
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Switch wireless off
              nmcli nm sleep true
              rmmod ath9k
              echo 0 > /sys/devices/platform/asus_laptop/wlan
        ;;
        resume|thaw)
              # Switch USB buses on
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Switch wireless on
              modprobe ath9k
              nmcli nm sleep false
              echo 1 > /sys/devices/platform/asus_laptop/wlan
        ;;
esac
```sudo chmod +x /etc/pm/sleep.d/20_custom-asus-k52



**- WIRELESS LED:** you need to create two new files with these commands:

sudo gedit /etc/acpi/asus-k52-wireless-led.sh

```
#!/bin/sh
# Toggle Wireless LED on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy*/rfkill*/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan

elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
fi
```sudo chmod +x /etc/acpi/asus-k52-wireless-led.sh


sudo gedit /etc/acpi/events/asus-k52-wireless-switch

```
# /etc/acpi/events/asus-k52-wireless-switch
# This is called when the user presses the wireless button (Fn+F2) on the ASUS K52
# and calls /etc/acpi/asus-k52-wireless-led.sh for further processing.

event=hotkey (ATKD|HOTK) 0000005d
action=/etc/acpi/asus-k52-wireless-led.sh

```



If you are using the 64bit version, the webcam will be upside down in 32bit applications (like Skype). To fix that you need to install a new package with this command:

sudo apt-get install libv4l-0:i386

And then run Skype with this command:

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype


*******************************************************************************************************


[COLOR=Blue]Ubuntu Oneiric Ocelot 11.10[/COLOR]

Almost the same issues as in Ubuntu Natty. I created a package to solve them which you can download here:

[http://ubuntuone.com/0q8b4sJUu0geFIgu8x3WOH](http://ubuntuone.com/0q8b4sJUu0geFIgu8x3WOH)

If you prefer to solve things manually, follow the instructions from Ubuntu Natty. Wireless will also be disabled after suspend, you can solve it reading this post:

[http://ubuntuforums.org/showpost.php?p=11312574&postcount=399](http://ubuntuforums.org/showpost.php?p=11312574&postcount=399)

To get the touchpad hotkey working (Fn + F9) you have to open System Settings > Keyboard > Shortcuts and create a custom shortcut pointing to the touchpad script  /etc/acpi/asus-k52-touchpad.sh

There is a bug which doesn't allow the use of three finger tap on the touchpad, hope there is a fix soon. On the other hand, palm detection is finally working.

For now we can solve the three finger tap issue with the instructions here:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

*******************************************************************************************************

[COLOR=Blue]Ubuntu Natty 11.04[/COLOR]

Almost everything is working out of the box. To solve issues with suspend to ram and wireless led check the solutions for Ubuntu Lucid. To use the touchpad key (fn+f9), save the touchpad script in the solutions for Ubuntu Lucid and map it to the key.

I created a package which automatically solves issues with suspend and wireless led. It also contains the touchpad script, you can use gnome-binding-properties to create a new combination which executes  /etc/acpi/asus-k52-touchpad.sh

Package:  [http://ubuntuone.com/p/puF/](http://ubuntuone.com/p/puF/)


For the webcam I didn't have to do anything, it's working ok. The only thing is that I'm using Ubuntu 64bit, and for 32bit applications that use the webcam (example: skype) the image is upside down. To solve it I run it like this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

There is a nice utility in the official repositories called 'guvcview' which lets you configure some settings of the webcam (you can invert or mirror the image, for example). I recommend it.


If wifi slows down after disconnecting AC cable, run this command:

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

*******************************************************************************************************

[COLOR=Blue]Ubuntu Maverick 10.10[/COLOR]

- To solve the problems relative to sound, run this on a terminal:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)


Then reboot your laptop. If still have any problems, check page 34 ( [http://ubuntuforums.org/showthread.php?t=1460790&page=34](http://ubuntuforums.org/showthread.php?t=1460790&page=34) )


- To solve the webcam upside down problem, run this on a terminal:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade


- To solve the suspend and wireless-led problem, check the following solutions for Ubuntu Lucid 10.04.

*******************************************************************************************************

[COLOR=Blue]Ubuntu Lucid 10.04[/COLOR]

I own an Asus A52F, twin brother of the Asus K52F. Here is a list of the problems you might find when installing Ubuntu Lucid, and their respective solutions.

[COLOR=Red]LIST OF PROBLEMS:[/COLOR]

1) SOUND: speakers do not mute when headphones are plugged in. (SOLVED)

2) SOUND: hdmi sound out not working. (SOLVED)

3) SOUND: external microphone not working. (SOLVED)

4) SUSPEND: suspend to ram freezes my laptop. (SOLVED)

5) WEBCAM: image upside down. (SOLVED)

6) Wireless LED: the led doesn't turn off when I press Fn+F2, but wireless is disabled. (SOLVED)

7) Available RESOLUTIONS: I get the maximum resolution for my screen, 1366x768, but I am missing other resolutions available in Windows. (IMPROVED)

8 ) TOUCHPAD: not detected as a touchpad, detected as "ImPS/2 Logitech Wheel Mouse". Touchpad tab missing in System>Preferences>Mouse and syndaemon is not working. The key to disable touchpad Fn+F9 is not working. (SOLVED)

Palm proof technology not working.

9 ) Calculator button (Fn + KP_Enter) not working. (SOLVED)



[COLOR=Green]LIST OF SOLUTIONS:[/COLOR]

1,2,3) SOUND: paste these commands on a terminal.

wget [www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip")
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb

Install the package and reboot. Now speakers should mute when headphones are connected, HDMI and microphones (internal & external) should be working. Open alsamixer and unmute S/PDIF (you can do that pressing "m"). Choose HDMI output from the pulseaudio volume applet (hardware tab) when needed. 

***Note: I am using Alsa 1.0.23 and Linux Kernel 2.6.34.


4) SUSPEND: you need to create a new file with this commands:

sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac
```sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd


5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.


6) Wireless LED: you need to create two files and restart acpi. Follow this commands:

sudo gedit /etc/acpi/events/asus-wireless-switch
```

event=hotkey ATKD 0000005d
action=/etc/acpi/asus-wireless-switch.sh
```sudo gedit /etc/acpi/asus-wireless-switch.sh

```
#!/bin/sh
# Toggle wireless device on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy*/rfkill*/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan    
elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
fi
```sudo chmod +x /etc/acpi/asus-wireless-switch.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart


7) Available RESOLUTIONS: you can get 1024x768 by adding to your repositories ppa:ubuntu-x-swat/x-updates (more stable than ppa xorg-edgers). Do this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade

Then reboot and that's it. THIS IS ONLY FOR INTEL GRAPHIC CARDS > Asus K52F & Asus A52F


8 ) TOUCHPAD: I found a solution to get the Elantech touchpad detected as such (and not ImPS/2 Logitech Wheel Mouse). Follow the instructions on this post:   [http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

EDIT: if you are running 2.6.34-rc7 or later you just need to run this two commands:
echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

Then you can check your settings with "synclient -l" or with xinput list-props "ETPS/2 Elantech Touchpad"
I made a startup script to keep two fingers tap as middle click, and three fingers tap as right click, with this command:
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3

Edit this file to get the touchpad button working:

sudo gedit /etc/acpi/asus-touchpad.sh

```
#!/bin/sh
# Toggle Elantech touchpad device on Asus laptops

[ -f /usr/share/acpi-support/power-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

getXconsole

TPSTATUS=`xinput list-props "ETPS/2 Elantech Touchpad" | grep "Device Enabled" | awk '{ print $4 }'`

test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 1 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 0
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD OFF" "
     Press Fn+F9 to enable"
elif [ $TPSTATUS = 0 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD ON" "
     Press Fn+F9 to disable"
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3
fi
```sudo service acpid restart
sudo /etc/init.d/acpi-support restart

EDIT: when pressing Fn+c (splendid button) this file is called "/etc/acpi/asus-f8sv-touchpad", and acts as Fn+F9. To solve it, uncomment that file or change it's action to something else that asus-touchpad.sh


9 ) Create two files to get the calculator button working: (if using maverick, check posts 183 and 186)

sudo gedit /etc/acpi/events/asus-calculator
```

event=hotkey (ATKD|HOTK) 000000b5
action=/etc/acpi/asus-calculator.sh
```sudo gedit /etc/acpi/asus-calculator.sh

```
#!/bin/sh
# Start calculator on Asus K52 laptops

. /usr/share/acpi-support/power-funcs

getXconsole

gcalctool &
```sudo chmod +x /etc/acpi/asus-calculator.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart

---

### Post by demetrius2009 on 2010-04-23
Hello! I have the same issues as you. Have you found out the solution for SOUND?:(

---

### Post by jsevi83 on 2010-04-23
No, I haven't found a solution for sound, but don't worry, if I find it I will post it here. I've been searching the web without luck, I found in another forum some users that have the same laptop and sound issues. Here is the link:

[http://ubuntuforums.org/showthread.php?p=9156275](http://ubuntuforums.org/showthread.php?p=9156275)

---

### Post by L815 on 2010-04-23
```
xinput set-prop "ImPS/2 Logitech Wheel Mouse" 125 0
```

For disabling the touchpad, this worked for me. 

My headphones work but don't mute the laptop speakers, on 10.04 64bit alsa 1.0.23 with kernel 2.6.34-rc5.

I'm very happy to report that using the latest alsa has gotten rid of the delay in pause/play with flash videos and pulse.

---

### Post by demetrius2009 on 2010-04-24
I hope that ubuntu guys will repair that issue till release... :popcorn:

---

### Post by jsevi83 on 2010-04-24
Hi L815, can you suspend your laptop using kernel 2.6.34-rc5? Or it is still not working?

---

### Post by demetrius2009 on 2010-04-24
My Asus K52JR also freezes when I try to suspend to RAM
Kernel: 2.6.32-21-generic
Ubuntu 10.04 32 bit

---

### Post by jsevi83 on 2010-04-25
I just added ppa:ubuntu-audio-dev/ppa to my repositories, and installed linux-alsa-driver-modules and linux-headers-alsa-driver. After a reboot I get new channels in alsamixer, also new hardware in the pulseaudio volume applet.

That might have solved the problems with hdmi sound, but I cannot test it right now, I will have to wait till tomorrow. What I can confirm is that now I have four input sources, and any of them is working, so my microphone became useless. Also, when I plug my headphones the speakers are still sounding, but now sound is not coming out of my headphones (as it did before).

I don't know if I should start trying again different options in /etc/modprobe.d/alsa-base.conf like "options snd-hda-intel model=xxx"

Does anyone now if it is possible to apply the changes without rebooting?

---

### Post by neoflight on 2010-04-26
> **demetrius2009 said:**
> My Asus K52JR also freezes when I try to suspend to RAM
Kernel: 2.6.32-21-generic
Ubuntu 10.04 32 bit

K52JR-X5 on 10.04 64 here. 
I can confirm this. 
Does not even turn off the screen (faint glow stays) when try to suspend/hibernate. Have to cold boot. 

Battery life is a pain. Win7 gets me ~3:30 hrs on normal use. 
10.04 starts with 2:10 hrs. PowerTop is not of much help either. 
Anyone else?

---

### Post by jsevi83 on 2010-04-26
When I try to suspend I get the same, the screen just gets frozen, but the usb devices do turn off, maybe it's related to the graphic card... But I have an integrated Intel, not an ATI.

When you talk about the battery, do you mean it lasts (in Ubuntu) 2h 10min, or that is the calculation made by gnome-power-manager? The calculations are not perfect, they get better (as I understand) when the laptop has learned from previous discharges.

To improve your battery you can also check what cpu governor you are using, run this on a terminal:

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

If the output is "performance" (for the 4 processors), you can change them to "ondemand" with these commands:

cpufreq-selector -g ondemand -c 0
cpufreq-selector -g ondemand -c 1
cpufreq-selector -g ondemand -c 2
cpufreq-selector -g ondemand -c 3

---

### Post by demetrius2009 on 2010-04-26
Here is my config
dima@dima-laptop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand

Ubuntu can live around 2 hours in normal use (film, coding etc.)
this information based on my own experience :)

---

### Post by tpsvca on 2010-04-26
> **jsevi83 said:**
> 
1) SOUND: speakers do not mute when headphones are plugged in. I guess we need to add to this file "/etc/modprobe.d/alsa-base.conf" a line similar to "options snd-hda-intel model=xxx" [COLOR=Red]NOT WORKING FOR ME TOO[/COLOR]

Can anyone help me? Thanks in advanced

---

### Post by demetrius2009 on 2010-04-26
Does anyone reported these bugs on lunchpad? I didn't see anything similar to Lucid there

---

### Post by jsevi83 on 2010-04-27
I just found a solution to mute the speakers when headphones are plugged in. See this thread, post 131

[http://ubuntuforums.org/showthread.php?t=1043568&page=14](http://ubuntuforums.org/showthread.php?t=1043568&page=14)

I only compiled using g++ instead of gcc



Update: see instructions in the first post.

---

### Post by jsevi83 on 2010-04-27
On this thread it is suggested a solution for hdmi sound, see post 12. I still couldn't try that.

[http://ubuntuforums.org/showthread.php?p=9178419](http://ubuntuforums.org/showthread.php?p=9178419)

---

### Post by 542 on 2010-04-28
jsevi83 - you shouldn't need the hda-verb program to get the speakers muting just the script that xtrman posted. Should make the steps a bit simpler.

I installed both as well but found it still works after I'd removed the hda-verb binary.

---

### Post by demetrius2009 on 2010-04-28
Guys, I compiled the script, run it and this helped me  to solve that annoying problem with sound!
[xtrman]("http://ubuntuforums.org/member.php?u=1060623") - is the master! Thanks a lot to everyone!!! :guitar::guitar::guitar:

---

### Post by jsevi83 on 2010-04-28
I already updated the instructions. Thanks

---

### Post by jsevi83 on 2010-04-30
Well, lucid has been finally released. Does anyone have any news on the initial problems we had? It seems that suspend and hdmi sound are the main issues now. Also the battery life seems to be not good enough.

I noticed some of you are using the 32bit version instead of the 64bit. Is there any reason for this? This is the first time I use ubuntu 64bit (since I bought this laptop), and went straight for it and didn't try the 32bit version on this laptop.

Now (after a week) I can say I already had three or four times a system freeze while doing "nothing special". That's already more than I had with my previous laptop using karmic 32bit for 6months. I don't know if this is related to the 64bit version, or to the new intel i5 core, or the integrated intel graphic card, ...

Could you share your experience about this? I also noticed that with lucid 64bit the amount of ram used on startup is much higher than in my desktop, with lucid 32bit. I am starting to doubt if I should try installing lucid 32bit or stick to my current fresh installation. Would I be able to used my 4GB of ram?

---

### Post by demetrius2009 on 2010-05-01
[Hi! jsevi83!]("http://ubuntuforums.org/member.php?u=717167")
Well as Lucid released there were a lot of updates, but these updates have hot fixed a least one of the problem, the battery life is still not good...

As for 64 bit vs. 32 bit I use 32 bit version of Ubuntu Lucid Lynx, because 64 programs, system uses more RAM (2x) its the only reason i used 32 bit.

I haven't any freezes while doing nothing or something special..

---

### Post by jsevi83 on 2010-05-01
demetrius2009, thanks for your reply. Can you use the 4GB of ram with the 32bit version? I read somewhere it's needed the 64bit version for that. I also noticed that in the pulseaudio volume applet, in the input tab I cannot choose between my internal microphone and the external one (the internal is working fine). Do you have the same issue?

I noticed my system always crashes when I try to use a program called fmit (free music instrument tuner). I don't know if it's related to a microphone problem, or what...  Also using the playstation emulator pcsxr (pcsx reloaded) crashes my system.

Any news on suspend or hdmi sound?

---

### Post by demetrius2009 on 2010-05-01
Hi, [jsevi83]("http://ubuntuforums.org/member.php?u=717167")!
Yes you right, we can't use 4Gb of RAM with 32 bit Linux, Windows, MacOS etc. The available amount of RAM will be near 3.5Gb. In my laptop I have 3gb of ram and it enough for me now... 

In my sound preferences I can't choose another microphone as you... so this is an issue in driver I guess...

Well I don't use those programs you noted, but I think this crashes related to the sound driver...maybe we should wait some time while Ubuntu development team will fix this bugs and we will be the happiest people in the world... I tried another distros of linux, hoping that they dont have such issues with the newest hardware... but ubuntu appeared most ready to support this new hardware :guitar::guitar::guitar:

P.S. I have no possibility to test HDMI sound... I have no device to test it :(

---

### Post by demetrius2009 on 2010-05-01
Found some useful information about battery life, may bu this information will help someone with new laptop:
[http://www.battery-of-laptop.com/one_display.php?pr_id=1502](http://www.battery-of-laptop.com/one_display.php?pr_id=1502)

---

### Post by 542 on 2010-05-02
jsevi83 - I'm using 64-bit and despite the problems with suspend and hdmi sound i have no unexplained freezes so far.

You can only use 3gb ram with 32-bit so I recommend 64.

---

### Post by jsevi83 on 2010-05-02
HDMI sound output is finally working!! Read the instructions from the first post.

---

### Post by jsevi83 on 2010-05-02
I found a solution to get the touchpad detected as such. Check the first post.

---

### Post by jsevi83 on 2010-05-02
Well, the system freezes I had seemed to be related to the programs themselves and their configuration. Now everything seems to be stable and fine, so I will keep my current 64bit installation. After the latest solutions, seems our biggest problems now are suspend and battery life. Maybe we have to wait for a newer kernel, but if someone finds a solution, please let us know.

---

### Post by ntomka on 2010-05-03
> **jsevi83 said:**
> After the latest solutions, seems our biggest problems now are suspend and battery life.

Battery life is OK for me, but suspend/hibernate still a problem.  After the latest touchpad solution I found a very useful (let say: must have) application: [GPointingDeviceSettings]("http://live.gnome.org/GPointingDeviceSettings"). Just install the gpointing-device-settings package and you will see. ;)

---

### Post by demetrius2009 on 2010-05-03
Hey, [ntomka!]("http://ubuntuforums.org/member.php?u=1058512")

How much time does your laptop works on battery? Using Wi-Fi, internet, music, coding, file operations etc...? :confused:

---

### Post by ntomka on 2010-05-03
> **demetrius2009 said:**
> Hey, [ntomka!]("http://ubuntuforums.org/member.php?u=1058512")

How much time does your laptop works on battery? Using Wi-Fi, internet, music, coding, file operations etc...? :confused:

Not much more than 3 hours (I've K52JR with Ati). Windows 7 does the same, so I think it's normal from lucid too. And I'm using amd64 version.

But, for my older post:
I found out there is an older version of gpointing devices app in lucid repository. Install [this]("http://packages.debian.org/squeeze/libgpds0") and then [this]("http://packages.debian.org/squeeze/gpointing-device-settings"). With this newer version you can configure that when other pointing devices are connected, the touchpad automatically tourned off. ;)

**I've needed some editing in the post!**

I found out there's a bug in the gpointing devices app gui, and when the "Disable while other devices are connected" checkbox are checked, nothing happens. You can have a workaround for it! Start the gconf-editor, then find this: /desktop/gnome/peripherals/ETPS@47@2... (it has a strange long name :D ). You can find "disable_while_other_devices_exist" option here. Enabling it solves the bug. ;)

**Update: Forget it!** It's very buggy feature. :(

---

### Post by demetrius2009 on 2010-05-03
It's very strange. I'm using 32bit ubuntu lucid... I doubt that this causes harder battery eating...
Any ideas?

---

### Post by ntomka on 2010-05-03
> **demetrius2009 said:**
> It's very strange. I'm using 32bit ubuntu lucid... I doubt that this causes harder battery eating...
Any ideas?

Wich CPU governor are you using? How does the battery under other distro/OS?

---

### Post by demetrius2009 on 2010-05-03
> **ntomka said:**
> Wich CPU governor are you using? How does the battery under other distro/OS?

I'm using "Ondemand" as I understand you. Didn't use yet in other OS

---

### Post by jsevi83 on 2010-05-03
Well demetrius2009, I have to admit I didn't check myself how long my battery lasts (I just took the word from others). But if you are listening music all the time or have screen brightness very high or make big use of the processor, it's normal it gets bellow three hours of use. Maybe you didn't compare in the exact same conditions (maybe Windows was using powersave), but I don't really know. I will check my battery life accurately and let you know.

After the touchpad solution, I tried gpointing-device-settings, but it didn't work very good to adjust the scroll speed, so I preferred to make a startup script with the options I like. I also prefer 2fingers-tap to be middle click, and 3fingers-tap right click. I also prefer horizontal-edge-scroll better than two-fingers-horizontal scroll. I also set syndaemon there. This is what I used:

synclient TapButton2=2
synclient TapButton3=3
synclient VertScrollDelta=20
synclient HorizScrollDelta=10
synclient HorizEdgeScroll=1
syndaemon -i 1 -t -d

---

### Post by demetrius2009 on 2010-05-04
> **jsevi83 said:**
> Well demetrius2009, I have to admit I didn't check myself how long my battery lasts (I just took the word from others). But if you are listening music all the time or have screen brightness very high or make big use of the processor, it's normal it gets bellow three hours of use. Maybe you didn't compare in the exact same conditions (maybe Windows was using powersave), but I don't really know. I will check my battery life accurately and let you know.


Great solution jsevi83!
I will test my battery life on different settings on Ubuntu Linux and Windows and post results here :P:P:P

---

### Post by jsevi83 on 2010-05-04
I think I found a solution to get the wireless led turned off when Fn + F2 is pressed. It's a very easy solution and you don't need to modify existing files, only to create two new files. Check the instructions on the first post.

I also created two files to get the calculator button working (Fn + KP_Enter), getting the event with "acpi_listen" and assigning an action to it "acpi_fakekey $KEY_CALC". Now it's kind of working: when I press it nothing happens, but when I press another key, gcalctool opens, so I guess it detects the key press but not the release.

Also, when I reboot and press Fn+F2 for the first time nothing happens, but if a press it a second time it works and disables the wireless aswell as its led. It always works except from the first try. Can someone help me with this?

---

### Post by thrakdug on 2010-05-07
Hi all! I'm a newish ubuntu convert and I have the k52jr so this thread  has helped me alot. 
I guess it's time for me to give a little something back. I'm tinkering  with the hotkeys now since the suspend/hibernate problem is out of my  league (though ive tried the .34 rc6 kernel it looks promising since it  doesn't freeze my system and it returns to the login screen but still  doesnt suspend properly). 
Anyway back to the hotkeys... I follwed [jsevi83]("http://ubuntuforums.org/member.php?u=717167")  lead of doing acpi_listen to get the hotkey then creating(tinkering) 2  files in the acpi folders. So far I've managed to fix the hotkeys for  calc and toggling the touchpad. here are my "action" files...

for the calc:
> 
#!/bin/sh
[ -f /usr/share/acpi-support/power-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

gcalctooland for touchpad toggle (haven't done the elantech thing yet): 
> 
#!/bin/sh
[ -f /usr/share/acpi-support/power-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

if xinput list-props "ImPS/2 Logitech Wheel Mouse" | grep "Device  Enabled" | grep 0
then 
    xinput set-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 1
else
    xinput set-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 0
fi
P.S. my batery lasts for about 2.5 hrs while watching videos.

---

### Post by jsevi83 on 2010-05-08
Thanks a lot for your action scripts, two more things solved.. I will try to update the first post tomorrow. I guess now we just have to wait for a newer kernel to solve the suspend issue.

thrakdug, do you know why the wireless hotkey fn+f2 only works from the second time on, but not the first time I press it? Should I change my action file?

---

### Post by ntomka on 2010-05-09
Thanks for the latest updates! The toucphad scripts are awesome, I really missed it!=D>:-\"\\:D/

I hope there will be permanent solutions in future releases of kernel, because after updates we need to go through the steps again and again... :roll:

**demetrius2009:** When I'm on battery I'm using powersave governor. If your battery can't last about 2-2.5 hours (3-3.5 with gma hd vga), maybe something constantly using your cpu. Try out the program 'top' in terminal, and find out is there something abnormal.

---

### Post by jsevi83 on 2010-05-09
Well, I checked it and my battery lasted about 2 hours using ondemand governor and watching some videos, wireless on, etc.

ntomka, what does it mean "(3-3.5 with gma hd vga)"? How do you get 3-3.5hours?

---

### Post by ntomka on 2010-05-09
> **jsevi83 said:**
> ntomka, what does it mean "(3-3.5 with gma hd vga)"? How do you get 3-3.5hours?

I've K52JR with ati and guessed dedicated vga need more power than integrated, so it's just a bet. :) Anyway, I've read around and tests say on slight load the gma hd version can last longer. :roll:
On battery I never watching videos or like that, just using it for work and internet so that's how I get about 3 hours. I think if it well loaded, it performs about or below 2 hours.

---

### Post by Wisp558 on 2010-05-10
Hey guys, I just recently got a A52JR, with the ATI 5470M. All the above solutions worked beautifully, thanks so much for all the effort. I think I may have a solution for your resolution issues.

All you have to do (iirc) is just set the desired resolution as available in /etc/X11/xorg.conf.

An example from the [ArchWiki]("http://wiki.archlinux.org/index.php/Xorg#Monitor_settings"):

```
Section "Screen"
   Identifier     "Screen0"
   Device         "Device0"
   Monitor        "Monitor0"
   DefaultDepth    24
   SubSection     "Display"
       Depth       24      #Color Depth
       Modes      "1280x1024" "1024x768" "800x600"  #Resolution
   EndSubSection
EndSection

```

Let me know how this works out, as I have not tried this, since my default 1366 x 768 is fine for me. This *should* force X11 to set whatever resolution you desire. 

More details are ofc available in the ArchWiki link.

I take it suspend still shows no signs of progress?

---

### Post by jsevi83 on 2010-05-11
I don't have a xorg file and I don't need more resolutions, I was just missing 1024x768 (which I have now).

For the suspend problem I didn't try the new kernel 2.6.34rc7, so I don't know if it's already solved or if we have to wait a bit longer. When there is a fix I will post it here.

---

### Post by thrakdug on 2010-05-11
> **jsevi83 said:**
> 
thrakdug, do you know why the wireless hotkey fn+f2 only works from the second time on, but not the first time I press it? Should I change my action file?

I'm not sure why it does that. Another thing i've noticed is that led won't be switch on/off if the wireless  connection is manually enabled/disabled. I read somewhere that a more robust script  is needed for that task than the toggle wireless state function in /usr/share/acpi-support/state-funcs (which is similar to what we have so far). I'll keep looking for a solution for that.     
post
For those who have the ati video card using the proprietary driver, has anyone found a solution to the splash screen issue? I tried the first solution from this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) The splash screen flickers when i try it, which defeats the purpose of why the devs switched to plymouth in the first place. Is it better then to use the open source drivers? (since it the only issue i have with the ati driver I'll probably stick with it)

---

### Post by jsevi83 on 2010-05-13
I tried kernel 2.6.34rc7. It already includes the patches for the touchpad, so little effort is needed to solve that (check the first post). The problem is that suspend is still not working...

---

### Post by demetrius2009 on 2010-05-13
Guys, BTW
I checked Battery life in Windows 7
It lasts 2 hours 30 minutes while surfing inet, listening to the inet radio etc...
Wireless on, Brightness 50% etc..
I think that there is everything is OK with power saving functions in Ubuntu :KS:KS:KS

---

### Post by sleepitoff on 2010-05-17
I followed the instructions for muting the internal speakers when headphones are plugged in, but I've still got audio coming out of both. Any ideas?

---

### Post by jsevi83 on 2010-05-17
Did you get any error when running "g++ main.cpp -o pinsensed"? Maybe you could repeat the process, just in case the original text (main.cpp) had any copy/paste mistakes.

If that doesn't work I'm afraid I cannot help you any further, as I don't understand the solution itself. I found it here
[http://ubuntuforums.org/showthread.php?t=1043568&page=14](http://ubuntuforums.org/showthread.php?t=1043568&page=14)

---

### Post by ntomka on 2010-05-17
**jsevi83**, you've made some mistake on touchpad solution in the first post! We need to edit the asus-touchpad-switch.sh not the asus-touchpad.sh file, and comment any changes in the asus-touchpad.sh (I commented all line) and then the fn+c will not work bad. At least for me this is working, but still need the [FONT="Courier New"]xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3[/FONT] command line.

I managed some notification for the toucpad switching.
[LIST=1]
[*][FONT="Courier New"]sudo aptitude install libnotify-bin[/FONT]
[*][FONT="Courier New"]sudo gedit /etc/acpi/asus-touchpad-switch.sh[/FONT]
[*]This is our touchpad switcher sh file. Add ```
notify-send -i "icon-file" "Touchpad disabled"
``` after this ```
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 0
```
[*]Add ```
notify-send -i "icon-file" "Touchpad enabled"
``` after this: ```
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
```
[*]Replace the icon-file in both lines for a full path to an icon file. I have one [[COLOR="Blue"]_here_[/COLOR]]("http://lh3.ggpht.com/_tkPjejltSPA/S_HVLhmbavI/AAAAAAAABog/4o1Oaijl2Rs/icon_multi-touch-pad.png"), but maybe you can find a better one.
[/LIST]

The only problem with this, you can't control the timeout of the notification (you can set it, but it's not working), so if you switch it rapidly, the popups can lasts long on screen. But who switches the touchpad so rapid? :)

---

### Post by thrakdug on 2010-05-17
**jsevi83**, I've edited my toggle wireless device script to something like this: 

```
#!/bin/sh
# Toggle wireless device on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy0/rfkill1/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan
# echo 1 > /sys/class/ieee80211/phy0/rfkill1/state
    
elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
# echo 0 > /sys/class/ieee80211/phy0/rfkill1/state
fi

exit 0
```I noticed that something (not sure if it's some other daemon or if it's built in the kernel)else toggles the wireless state, but there seems to be some 'lag' to it. I guess the only thing we needed to toggle was the led, and because of the 'lag' i reversed the logic. It seems to work even on the 1st try, though manually switching in the network manager applet still doesn't affect the led state.

---

### Post by jsevi83 on 2010-05-18
The file /etc/acpi/events/asus-touchpad calls /etc/acpi/asus-touchpad.sh. If you prefer to create a new action file called asus-touchpad-switch.sh then you have to modify the action field in /etc/acpi/events/asus-touchpad. Another solution is to edit directly the action file, as the event file is okay.

For the notification I use this:

notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "	      TOUCHPAD  ON" "
          Press Fn+F9 to disable"

notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-disabled.svg -t 3000 "	      TOUCHPAD  OFF" "
          Press Fn+F9 to enable"

For the wireless led, if found that if we comment out
echo 1 > /sys/class/ieee80211/phy0/rfkill1/state
echo 0 > /sys/class/ieee80211/phy0/rfkill1/state
then the led is not always synchronized with the wireless state, sometimes it's on when the wireless is off, and the other way around.

EDIT: I was wrong about the wireless switch, now instructions are updated.

---

### Post by ntomka on 2010-05-18
**jsevi83**, that touchpad icon you found looks pretty good! :) Now I use it too! :)
The notify-send's -t command line switch does nothing as I said, it's a common problem, here is the bugreport about it: [_[COLOR="Blue"]notify-send ignores the expire timeout parameter[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508"). :frown:

I see the differences between asus-touchpad and asus-touchpad-switch now, because you've edited the first post sometime and yesterday I'd needed to edit the sh file and then the fn+c combo problem got out.  So I found out there's two different asus-touchpad file wich interferes each other and after a little correction the fn+c combo problem is gone. :)

---

### Post by jsevi83 on 2010-05-18
thrakdug, you were right about the wireless action file, now instructions on the first post are updated. Thanks for pointing that out, now wireless switch button is working from the first time it's pressed.

ntomka, I think I don't have the time problem with notify-send, many of my scripts use it and they work as they are supposed to. If I set "-t 3000" notification is displayed for 3seconds.


EDIT:

I also noticed that my external microphone is not working. I cannot select it in the pulseaudio-applet; in alsamixer and gstreamer-properties there are two input devices, but only one of them (the internal microphone) is working. Can anybody confirm if they have the same issue? I'm using kernel 2.6.34 and alsa 1.0.23.

---

### Post by sleepitoff on 2010-05-18
> **jsevi83 said:**
> Did you get any error when running "g++ main.cpp -o pinsensed"? Maybe you could repeat the process, just in case the original text (main.cpp) had any copy/paste mistakes.

If that doesn't work I'm afraid I cannot help you any further, as I don't understand the solution itself. I found it here
[http://ubuntuforums.org/showthread.php?t=1043568&page=14](http://ubuntuforums.org/showthread.php?t=1043568&page=14) 

Forgot to add that part, I do an error message that states: 

"cp: cannot create regular file `/usr/local/bin/pinsensed': Text file busy" 

when I run sudo cp pinsensed /usr/local/bin/pinsensed

But the file is there in /usr/local/bin/pinsensed 

EDIT: 

I have it working now. 

I changed the input to sudo cp -f pinsensed /usr/local/bin/pinsensed and all is good. Sweeeeeeeeeeeeeeeeeet. Thanks

---

### Post by jsevi83 on 2010-05-19
I will copy again my last post in case somebody missed it.

I noticed that my external microphone is not working. I cannot select it in the pulseaudio-applet; in alsamixer and gstreamer-properties there are two input devices, but only one of them (the internal microphone) is working. Can anybody confirm if they have the same issue? I'm using kernel 2.6.34 and alsa 1.0.23.

---

### Post by chellrose on 2010-05-19
> **jsevi83 said:**
> 
[COLOR=Green]LIST OF SOLUTIONS:[/COLOR]

1) SOUND: for mutting the speakers while headphones are plugged, follow this instructions:

gedit main.cpp

# Paste the following inside, save and close.

```

*code omitted in the interest of space*

```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]g++ main.cpp -o pinsensed
sudo cp pinsensed /usr/local/bin/pinsensed
sudo pinsensed
sudo gedit /etc/init.d/rc.local

# Add the following (in red) to line 10 (under  ### END INIT INFO)

[COLOR=Red]/usr/local/bin/pinsensed[/COLOR]

# That's it. Your speakers should mute when you plug in your headphones (also after a reboot). This is not an "official" solution, but a workaround until things get solved.


This fix does mute my speakers when the headphones are plugged in... but no sound comes out of the headphones, either.  Previously both the headphones and speakers played sound simultaneously.

Has anyone else run into this problem, and if so, do you know a fix?  (I'm using a Toshiba Satellite, not an Asus... not sure if that is the root of the problem.)

Thanks :)

---

### Post by jsevi83 on 2010-05-19
I guess if it's a toshiba that is the root of the problem. Check here:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

[http://translate.google.com/translate?hl=es&langpair=fr|en&u=http://doc.ubuntu-fr.org/audio_intel_hda%3Fs%3Drealtek](http://translate.google.com/translate?hl=es&langpair=fr|en&u=http://doc.ubuntu-fr.org/audio_intel_hda%3Fs%3Drealtek)


Edit: don't forget to undo what you did (pinsensed).

---

### Post by thrakdug on 2010-05-20
> **jsevi83 said:**
> I will copy again my last post in case somebody missed it.

I noticed that my external microphone is not working. I cannot select it in the pulseaudio-applet; in alsamixer and gstreamer-properties there are two input devices, but only one of them (the internal microphone) is working. Can anybody confirm if they have the same issue? I'm using kernel 2.6.34 and alsa 1.0.23.

DId not noticee it until you pointed it out. I tried on the original .32 kernel and alsa 1.0.23, still the same issue. Its not even on the pulseaudio-applet. Another thing to work on I guess. 

Any progress on the suspend issue? I tried these links (to no avail): 
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) 

Has any body filed a bug report, that we can support?

---

### Post by zvezdogled on 2010-05-20
I would really like to thank you all for this thread, it made my life easier. Thanks

---

### Post by jsevi83 on 2010-05-21
> **thrakdug said:**
> Any progress on the suspend issue? I tried these links (to no avail): 
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) 

Has any body filed a bug report, that we can support?

I didn't find any solution or bug report about the suspend issue. If you do, please let us know. The same goes for the external microphone.

---

### Post by GiacomoPennella on 2010-05-28
Wonderful thread! I'm new to this Asus K52Jr and my impression is good! Some issue with the small necessary edit about the touchpad etc...
Only a doubt about the case: I noticed that on one corner of the case there is a small space that make it not cute stable! :( It seems do it only when the lid is open...
Do you have any suggestion?

Thank you for the precious advices about the touchpad!!!!

Giacomo Pennella
[ASUS K52JR-SX070V Cpu: I3 350M Ram 4Gb]

---

### Post by jsevi83 on 2010-05-28
> **GiacomoPennella said:**
> Wonderful thread! I'm new to this Asus K52Jr and my impression is good! Some issue with the small necessary edit about the touchpad etc...
Only a doubt about the case: I noticed that on one corner of the case there is a small space that make it not cute stable! :( It seems do it only when the lid is open...
Do you have any suggestion?

Thank you for the precious advices about the touchpad!!!!

Giacomo Pennella
[ASUS K52JR-SX070V Cpu: I3 350M Ram 4Gb]

I'm sorry I don't understand very well what you mean about the case.

---

### Post by GiacomoPennella on 2010-05-28
Ops sorry for my English....

I mean the chassis of the laptop: its basement doesn't stand perfectly on my desk and it's not a problem of the desk... neither an ubuntu's one!!

Anyway I'm only curious to know if someone has my problem...

One more: sorry for th English!!!!

---

### Post by krzysiekb on 2010-05-28
Hi, To solve suspend/resume issue follow the instructions from [this]("http://ubuntuforums.org/showpost.php?p=9180298&postcount=7") post. Don't forget to give execute permission to the newly created script by calling
```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd
```

This solution works fine for me with the mainline kernel 2.6.34. I've to check it with the original lucid kernel 2.6.32 later - or you can do this :)

Enjoy!!!

---

### Post by jsevi83 on 2010-05-28
Thanks a lot, suspend now works. I already updated the instructions on the first post.

---

### Post by jsevi83 on 2010-05-28
> **GiacomoPennella said:**
> Ops sorry for my English....

I mean the chassis of the laptop: its basement doesn't stand perfectly on my desk and it's not a problem of the desk... neither an ubuntu's one!!

Anyway I'm only curious to know if someone has my problem...

One more: sorry for th English!!!!

Ok, I get it now. I don't have this problem, maybe some foot of the laptop is broken, you could check the base carefully. I also guess it's not an ubuntu problem :P

---

### Post by ntomka on 2010-05-30
> **krzysiekb said:**
> This solution works fine for me with the mainline kernel 2.6.34. I've to check it with the original lucid kernel 2.6.32 later - or you can do this :)

I can confirm: works with kernel 2.6.32! Thanks! =D>

---

### Post by FFFUUU on 2010-06-05
> **jsevi83 said:**
> 
1) SOUND: for mutting the speakers while headphones are plugged, follow this instructions:

gedit main.cpp

# Paste the following inside, save and close.

```
/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}
```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]g++ main.cpp -o pinsensed
sudo cp pinsensed /usr/local/bin/pinsensed
sudo pinsensed
sudo gedit /etc/init.d/rc.local

# Add the following (in red) to line 10 (under  ### END INIT INFO)

[COLOR=Red]/usr/local/bin/pinsensed[/COLOR]

# That's it. Your speakers should mute when you plug in your headphones (also after a reboot). This is not an "official" solution, but a workaround until things get solved.
[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]



After first restart everything works fine, but after another one I have same issue :(. How to keep it permanent?

---

### Post by jsevi83 on 2010-06-06
If you followed correctly the instructions it should work permanently, as it does for the rest of us. My advice is that you follow the steps again, you can also check if pinsensed is running after a reboot. It should if you added it to /etc/init.d/rc.local.


PD. Anyone found a solution for the external microphone?

---

### Post by FFFUUU on 2010-06-06
> **jsevi83 said:**
> If you followed correctly the instructions it should work permanently, as it does for the rest of us. My advice is that you follow the steps again, you can also check if pinsensed is running after a reboot. It should if you added it to /etc/init.d/rc.local.


PD. Anyone found a solution for the external microphone?I've added it there and it's not permanent :/.
(i am ubuntu user since 3 days :P)

---

### Post by Gato Verde on 2010-06-07
I have an ASUS UL50VT and most of your fixes have worked well for me.  The flipped webcam issue in Skype is still troubling me.  I installed gtk-c4l and it installed fine.  In Cheese the image reacts to the gtk-c4l settings.  It does not seem to work with Skype.  

Also the touchpad is still recognized as the ImPS/2 Generic Wheel Mouse.  It is working OK including 2 finger scroll and 3 finger right click.

Any ideas?

Todd

---

### Post by thrakdug on 2010-06-08
Thanks for the hibernate/suspend solution! 

@Gato Verde, try launching skpye in the terminal using:

> LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skypeif it works just change the command in the skype launcher in your menu. or try the solutions in this [old thread.]("http://ubuntuforums.org/archive/index.php/t-997807.html")

---

### Post by jsevi83 on 2010-06-08
@Gato Verde, for the touchpad I recommend kernel 2.6.34, I use the one in ppa:ricotz/unstable. Then follow the instructions on the first page and it should work as expected.

For skype, if you are using ubuntu 64 bit, use this:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

If you are using 32 bit ubuntu, use this:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

By the way, is your external microphone working on ASUS UL50VT?

@FFFUUU, sorry but I don't know how to help you, I don't know where is the problem. Try to run "sudo pinsensed" manually to see if that works.

---

### Post by xtrman on 2010-06-13
@FFFUUU: Can you post the result of this command:
sudo cat /var/log/daemon.log | grep pinsensed

---

### Post by blackbinary on 2010-06-14
Thanks so much! I use a K52jr, and the audio coming out of the speakers + headphones have really been a killer issue. I would've had to change over to windows in the fall at school. Now i don't, and things are great!! Really made my day, i appreciate it!

---

### Post by sleepitoff on 2010-06-14
After a couple updates yesterday (side note: I have pre-released and unsupported updates checked in the repo options), the fix for muting the internal speakers no longer works. It's not that audio is coming out of both again, it's just that no audio comes out of the headphones now :confused: Should I just remove the pinsensed file and go back to scratch?

Also, to whomever said it stopped working after a reboot: After a reboot, I always had to unplug and plug the external speakers back in and it would stick again. 

EDIT
Problem solved: 
[http://ubuntuforums.org/showthread.php?p=9462461#post9462461](http://ubuntuforums.org/showthread.php?p=9462461#post9462461)

---

### Post by jsevi83 on 2010-06-15
sleepitoff, do you have an Asus K52 with Conexant 5069? I installed the alsa-driver-linuxant package, rebooted, and now my sound card is not recognized, so no sound at all. Any advice?

---

### Post by sleepitoff on 2010-06-15
Yeah, that's what I have as well. After I removed the pinsensed file, etc, I was searching around this forum and found that thread and that deb fixed my audio problem. I don't know what happened your system :( I use  KDE, by the way, and I'm not sure if that has anything to do with it and when it asked if KDE should forget about the following audio options (can't remember what they were) I selected yes to them all.

---

### Post by jsevi83 on 2010-06-15
Well, I got it working, thanks a lot (the error was an unstable kernel). Now we have fully supported audio chip!! I will update the instructions on the first post.


edit: 
It seems that this laptop is working very good with ubuntu now. The only (and last) thing I am missing is the touchpad "palm proof technology".

---

### Post by sleepitoff on 2010-06-15
Yep, this is a great notebook, I'm very happy I bought it.

---

### Post by thrakdug on 2010-06-17
Thanks for the update on the sound issues, I'm having a small problem though.

I first removed the pinsensed daemon and the [COLOR=Red][COLOR=Black]/usr/local/bin/pinsensed [/COLOR][COLOR=Black]line on [/COLOR][/COLOR]/etc/init.d/rc.local. I then installed the linuxant driver and checked if i have [COLOR=Red][COLOR=Black]1.0.23 [/COLOR][COLOR=Black]using [/COLOR][/COLOR]cat /proc/asound/version. 
Everything seems ok, internal mic works after booting up but when I plug an external mic(which works) then unplug it the internal mic won't work. Plugging the external mic again would work though. I'd have to run alsamixer then deselect and select micB as the input for the internal mic to work again.


[COLOR=Red]
[/COLOR]

---

### Post by jsevi83 on 2010-06-17
I get the same behaviour about the microphone. When I plug in a external microphone, the sound card switches to it automatically (MIC_C). But when I unplug it, the sound card switches to another input device (DMIC_J), and I have to manually change it (to MIC_B) to get the internal microphone working again.

I have no idea how can we make the internal microphone (MIC_B) the default one, so it is selected automatically when no external microphone is plugged in (instead of DMIC_J).

Also when I select Digital Stereo Duplex (IEC958 ) in the hardware tab of the pulseaudio applet, I cannot hear anything, I don't know if I'm doing something wrong. 

And there are some elements in alsamixer I don't know what they are: if the internal mic is MIC_B, and the external mic is MIC_C; what is MIC_F and DMIC_J? And what is PortD, PortE and PortG?

Please, could someone explain it a little, or point us to a link where it is explained?

---

### Post by ntomka on 2010-06-20
OK, I'm trying the new sound solution for 2 hours now, and I've flawlessly working mute/unmute and internal mic at last! Thanks!

---

### Post by Gato Verde on 2010-06-23
I got the Webcam and Touchpad issues sorted out but then I bought a new LCD TV and when I plugged in the HDMI...No sound.  The sound worked perfectly for everything except the HDMI.  I tried the HDMI sound fix in this thread and now I have no sound. 

I tried uninstalling alsa-driver-linuxant to see if it would revert.  no luck.  

I also tried the comprehensive sound problems & solutions sticky but didn't have any luck.  The computer seems to detect the soundcard when I code lspci -v into the terminal but the sound applet shows no hardware like it did before.

---

### Post by jsevi83 on 2010-06-23
@ Gato Verde> I got something similar the first time I tried linuxant. Uninstall linuxant and then do this:

1) Install kernel 2.6.34 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

You will need the headers (2 files) and the image.

2) Update alsa to 1.0.23. Reboot

3) Install linuxant and reboot.

---

### Post by Gato Verde on 2010-06-23
jsevi83,

I am already using kernel 2.6.34 


I tried to do the rest of what you suggested.  After a successful make of the package I downloaded when I ran sudo checkinstall it seemed to go OK until it failed to install. Here is the log output it suggested I look at.

(PS if it isn't obvious yet, I am not too comfortable using the command line)


"dpkg-deb: parse error, in file '/var/tmp/tmp.YY3MKC3it3/package/DEBIAN/control' near line 10 package 'src':
 empty value for version"

not sure where to go from here...willing to go back to what was working before without the HDMI sound

Todd




> **jsevi83 said:**
> @ Gato Verde> I got something similar the first time I tried linuxant. Uninstall linuxant and then do this:

1) Install kernel 2.6.34 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

You will need the headers (2 files) and the image.

2) Update alsa to 1.0.23. Reboot

3) Install linuxant and reboot.

---

### Post by jsevi83 on 2010-06-23
You don't need to compile anything, just download this:
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip)

Extract the deb file inside and double click on it. It should open with gdebi, you click on install and write your password. Then wait because the installation is long, even if it looks inactive wait till it says it is successfully installed.

I don't know why you are running "make" and "checkinstall". Are you talking about alsa-driver-linuxant?

---

### Post by Gato Verde on 2010-06-24
I had to compile alsa 1.0.23 .  The only place I could find it was at the alsa website in tar format.  If it is available as a deb somewhere that would make things allot easier.

I already have linuxant.

Todd

---

### Post by jsevi83 on 2010-06-24
You can update to Alsa 1.0.23 from this repository >>  ppa:ricotz/unstable

---

### Post by ntomka on 2010-06-24
> **Gato Verde said:**
> I had to compile alsa 1.0.23.

Why? The default alsa works fine for me with linuxant.

---

### Post by jsevi83 on 2010-06-24
I had problems when first installed linuxant. Then I installed kernel 2.6.34 and alsa 1.0.23 and everything was working fine, that's why I recommended it. If you confirm that alsa 1.0.23 is not needed, that's even easier for us.

---

### Post by ntomka on 2010-06-24
Sure! Kernel and alsa is the original version (2.6.32 and 1.0.22), everything is fine, this topic is very useful since the first solution!\\:D/
I'm happy about this, because I've ati vga with it's need of fglrx wich doesn't works well with new kernel, especially when xorg is updated too.

---

### Post by Gato Verde on 2010-06-24
I had tried a similar apt line to get the ricotz repository but it hadn't worked.  This one did...Thanks

I added the ppa:ricotz/unstable repository, uninstalled linuxant and alsa. then I reinstalled alsa 1.0.23 and linuxant and did a general update then restarted...still no luck.  

In the sound applet the hardware is still not recognized.](*,)

On my last laptop there was a conflict between Pulse audio and alsa...could this be an issue?  would getting rid of pulse help?

---

### Post by Gato Verde on 2010-06-25
Is it possible to revert to what was working (without the HDMI) before?

---

### Post by jsevi83 on 2010-06-29
I had similar problems. I uninstalled linuxant and reinstalled the kernel and alsa. Hope that helps, otherwise you could try a different kernel version. It seems that linuxant is leaving some files in /lib/modules after being uninstalled.

---

### Post by DamiRocK on 2010-07-11
Hia everyone!
First of all, i've gotta say, that i have a little brother of your  notebooks. Mine is k42 (14", and no Num-pad).
I'm glad i found this thread, because practically all of solutions  described here for k52's help for k42 too. That's great. 
But i'm still having problems with wireless switch: Fn+F2 is working,  but wireless led is always on. And when i switch to windows via  rebooting, wireless functions are turned on (i always keep it disabled  there, so i don't know how, but ubuntu makes wireless function work in  windows:D).
That were a simple problems, not so important and irritating.
The second is sleep mode and hybernation. When ubuntu goes to hibernate -  display turns blank and the white break symbol "_" appears and blinks  at the top-left corner of the display and notebook doesn't hibernate at  all.
Sleep mode is working strange. Sometimes it works, and sometimes...

So, can anybody help me? What information should i post, to make the  help easier? 
Best regards!

---

### Post by jsevi83 on 2010-07-12
The problem with the wireless led may be related to the file selected. In my laptop it is /sys/devices/platform/asus_laptop/wlan
Maybe in yours it is different. When that file has a 1, the led is on, when it has a 0 the led is off. If you find the correct file you only need to modify the script in the solution number 6.
You can check with these commands if you need to use the same files as we do:
cat /sys/class/ieee80211/phy0/rfkill*/state
cat /sys/devices/platform/asus_laptop/wlan

Hopefully both should give you an output of a 0 or a 1. On the other hand, I don't have a swap partition, so hibernation is disabled for me. Suspend is working okay though.

---

### Post by DamiRocK on 2010-07-12
I've got everything the same. But no effect.
I just put "0" in wlan file manually, restarted, and now wireless network is not available at all:
[IMG]http://img708.imageshack.us/img708/4076/ubuntuasusk52asusa52pag.png[/IMG]
(Disabled text is "Wireless network" in russian language)
And LED indicator doesn't turn off anyway...

cat /sys/class/ieee80211/phy0/rfkill*/state = 0
cat /sys/devices/platform/asus_laptop/wlan = 1

---

### Post by jsevi83 on 2010-07-13
cat /sys/class/ieee80211/phy0/rfkill*/state determines if the wireless switch is on or off. If it gives you a 0, then wireless is disabled. To enable it you need to run (as root) "echo 1 > /sys/class/ieee80211/phy0/rfkill*/state"

With "echo 0 > /sys/devices/platform/asus_laptop/wlan" the wireless led is switched off, and with a 1 is switched on.

Play with those options and create the correct file in /etc/acpi following the instructions in the first post. I don't think I can help any further, as I don't know why it's not working for you. Just in case, check carefully if you followed all the steps correctly.

---

### Post by DamiRocK on 2010-07-13
I've played a bit with echo's and finnaly it worked:) Thanks for advices!

---

### Post by ssek on 2010-07-14
Hi I'm new with ubuntu
I finished installed ubuntu 10.04 on my K52F
but I cannot connect to internet
someone can help me?

when I plug the network cable LAN the connection is etablished
but I cannot ping ubuntu.com and I can't access to a web page with firefox
it's still blank

---

### Post by DamiRocK on 2010-07-15
Visit your internet-provider site to find the instruction like "how-to set up internet connection in linux".
I tend to believe, that your ISP uses vpn connection

---

### Post by ssek on 2010-07-15
it seem that I have the same problem with Windows 7
when I try to activate the wired LAN 
it says : network not found

I get an automatic ip adress but still cannot connect to internet

is there a problem with my LAN card or operating system?

my pc on xp can still connect to internet

---

### Post by jsevi83 on 2010-07-15
With my old router I had to unplug the power cable, wait 2 minutes (with the router powered off), connect the ethernet cable to the laptop and then connect the power cable. I know it's not an ideal solution but it might work ;P

If you have the same problem with Windows 7 and Ubuntu I don't think it's related to the OS.

---

### Post by ssek on 2010-07-16
thanks I reconnected my router and could connect

---

### Post by DamiRocK on 2010-07-18
The funny thing, that i can switch-off wlan connection via Fn+F2, but i can't turn it on so...

---

### Post by ssek on 2010-07-22
I installed kernel 2.6.34
and added headphone bash command by jsevi83
speaker and headphones work
but the mic dont work anymore
can someone help ?

---

### Post by sleepitoff on 2010-07-25
anybody else with these models experiencing a lot of gui lock ups these days? I want to end them! I don't know if it's the ati catalyst causing these problems or something else.

---

### Post by jsevi83 on 2010-07-26
To use the microphone you need to open alsamixer and select the right input source (MIC_B is the internal mic).

For the graphic problem I cannot help you as I don't have ATI, my laptop has Intel GMA.

---

### Post by ssek on 2010-08-05
I cannot eject my cd drive manually (pushing the button do nothing)
I always have to do by right clicking eject

do someone have same pb?

---

### Post by jsevi83 on 2010-08-12
I have no problems to eject the cd pressing the side button. But I have some problems with the left button of the touchpad, which many times doesn't work and I have to press it again and again and then it works.

---

### Post by Wisp558 on 2010-08-12
So the webcam fix doesn't work.

I even tried downloading the latest tarball from the devs upstream and configuring it... no dice. I'd be tempted to break into the case and flip it back upright, but then it wouldn't work properly in Win7... :p

I have an Asus A52J, and the cam is a Syntek 174f:1120.

---

### Post by jsevi83 on 2010-08-13
If your webcam is still upside down, you should contact Hans > [email]hdegoede@redhat.com[/email] . He will add your model to the list of upside down models, so in the next release it will be solved.

---

### Post by techieboy on 2010-08-17
Good to know that there is this thread here that summarized ubuntu problems. 

I was trying to fix my cam but then the fix was not enough. So I looked for simpler way to get it done. I also looked into hans solution but it wasn't able to fix my problem. So figure out on my on and look into imports. And that was it. Visit my article and read on it. I made simple scripts for running skype and cheese with properly working camera.

[I write a simple article on how I fixed my inverted asus camera. You guys might wanna try this too.  ]("http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html")

:lolflag:

---

### Post by teddybar on 2010-08-20
I run commands:
echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

and now my touchpad isnt working anymore :(

synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?


Can you help me please

---

### Post by jsevi83 on 2010-08-21
teddybar, are you using kernel 2.6.34 or newer? This solution doesn't work for kernels below 2.6.34.

You could try to run again  "sudo rmmod psmouse && sudo modprobe psmouse"
Otherwise reboot. If it still doesn't work, open the file /etc/modprobe.d/psmouse.conf and erase this line >  options psmouse force_elantech=1

---

### Post by teddybar on 2010-08-22
> **jsevi83 said:**
> teddybar, are you using kernel 2.6.34 or newer? This solution doesn't work for kernels below 2.6.34.

You could try to run again  "sudo rmmod psmouse && sudo modprobe psmouse"
Otherwise reboot. If it still doesn't work, open the file /etc/modprobe.d/psmouse.conf and erase this line >  options psmouse force_elantech=1

Thx very much, is working now, but i have another problem, my internal microphone isnt working :(

I have Asus K52J

---

### Post by theprodejeff on 2010-08-30
> **jsevi83 said:**
> I just added ppa:ubuntu-audio-dev/ppa to my repositories, and installed linux-alsa-driver-modules and linux-headers-alsa-driver. After a reboot I get new channels in alsamixer, also new hardware in the pulseaudio volume applet.

That might have solved the problems with hdmi sound, but I cannot test it right now, I will have to wait till tomorrow. What I can confirm is that now I have four input sources, and any of them is working, so my microphone became useless. Also, when I plug my headphones the speakers are still sounding, but now sound is not coming out of my headphones (as it did before).

I don't know if I should start trying again different options in /etc/modprobe.d/alsa-base.conf like "options snd-hda-intel model=xxx"

Does anyone now if it is possible to apply the changes without rebooting?
@ JSEVI83,

Hello, I read your tip about the also backports. Thanks for it, it worked. Now I have sound output over HDMI. I really like my new ASUS K52Jc, but the whole hybrid hardware thing is big downside. Or maybe the kernels needs to be optimisted for the new hardware that is on the market. Anyways, thanks for the tip and if you have more tips from me please send them to me. Really appreciated.

Gtz Theprodejeff

---

### Post by krzysiekb on 2010-09-02
I've just upgraded my kernel to the version 2.6.35-02063504-generic (from kernel mainline).
Sadly there is no linuxant alsa driver available for this kernel version and my headphone output didn't work after upgrade. By googling I found the following solution which imo is way better than installing linuxant alsa driver:

1. Create file **/etc/modprobe.d/sound.conf**
```

options snd-hda-intel model=ideapad

```

2. Reboot (or reload snd-hda-intel)

Now headphone output is working again. Maybe this solution will work with older kernel versions too.

---

### Post by jsevi83 on 2010-09-04
I just tried that and it worked. But now I cannot select my input source, and only the external microphone is working. The internal microphone is not working. Any ideas? I also think this solution is better than linuxant.

---

### Post by krzysiekb on 2010-09-09
> The internal microphone is not working. Any ideas?
Yes, but it's a bit complicated because it requires to use hda verbs.

All steps should be done with root privileges.

1. Create file **/etc/modprobe.d/sound.conf**
```

options snd-hda-intel model=thinkpad

```

2. Add the following package repository
```

deb http://ppa.launchpad.net/diwic/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/diwic/ppa/ubuntu lucid main

```

and install package **snd-hda-tools**

3. Create file **/etc/init.d/hd-conexant**
```

#!/bin/bash

# AudioIn 0x14 use selector 0 -> 0x17
hda-verb /dev/snd/hwC0D0 0x14 SET_CONNECT_SEL 0

# Audio Selector 0x17 use input 0 -> 0x1a (IntMic)
hda-verb /dev/snd/hwC0D0 0x17 SET_CONNECT_SEL 0

# Configure IntMic
hda-verb /dev/snd/hwC0D0 0x1a SET_PIN_WIDGET_CONTROL 0x24

``` 

And make it executable. This script configures the soundcard.

4. Run **update-rc.d hd-conexant defaults** 
So the script will be executed at startup

5. Create file **/etc/pm/sleep.d/30_custom-hd-conexant**
```

#!/bin/sh
case "${1}" in
        hibernate|suspend)
        ;;
        resume|thaw)
                /etc/init.d/hd-conexant
        ;;
esac

```

And make it executable. This will reconfigure the soundcard after resume.

6. Reboot

7. Use alsamixer to control gain and capture level.

I've tested this with Skype and it's working perfectly.

---

### Post by jsevi83 on 2010-09-09
krzysiekb > Thanks for your solution. I just tried it. I erased the option ideapad and replaced it with thinkpad, then followed the rest of the steps. When I reboot my internal microphone is working, and when I plug in an external microphone, it gets selected automatically and the internal is disabled. But after unplugging the external microphone, the internal microphone doesn't get enabled. And in alsamixer I cannot choose any input source. Is this the way it should be? Is there any way to select manually which is the input source?

---

### Post by david2sands on 2010-09-11
I have a K52J and this post solved the last of my issues. I was surprised that so much of Lucid was a hassle, as I have been using Jaunty on older machine, and installed it in the era when the OS was pretty much plug-n-play. 

I haven't tested the batteries yet, as I use data on USB sticks, and Karmic Wubi on the wife's netbook when traveling. 

Anyway, thanks! I'm a bit surprised that pulseaudio problems where solved by installing missing stuff from the distro. I guess the packagers have blessed hardware ...

---

### Post by krzysiekb on 2010-09-11
> **jsevi83 said:**
> Is there any way to select manually which is the input source?

As far as I can see, no. To re-enable IntMic you have execute the script /etc/init.d/hd-conexant (either suspend/resume or reboot, but I guess that's not what you expect)

---

### Post by tangato on 2010-09-18
> **krzysiekb said:**
> As far as I can see, no. To re-enable IntMic you have execute the script /etc/init.d/hd-conexant (either suspend/resume or reboot, but I guess that's not what you expect)

well, after playing a lot, I can change from internal to external mic, using alsamixer via terminal. Looks that there are some aspects that gnome-alsamixer doesn't affect, or doesn't save.
Right now, for the internal mic, I have to select PortB Jack > Mic 80pc via alsamixer, and when I plug in a mic, it switches automatically.

And yes, when I unplug it, the internal is deactivated, so I have to change in alsamixer Input source> Mic B. Everything works again.

Be shure of opening sound preferences or something to monitoring the signal.

I have installed the conexant driver, runing kernel 2.6.34 under lucid.

---

### Post by krzysiekb on 2010-09-20
> **tangato said:**
> well, after playing a lot, I can change from internal to external mic, using alsamixer via terminal. 

I have installed the conexant driver, runing kernel 2.6.34 under lucid.

Sure, it works more or less as you described under kernel 2.6.34 with conexant driver installed. I was talking about mainline kernel 2.6.35.4 without conexant driver (as this version of the kernel is not (yet?) supported).

---

### Post by jsevi83 on 2010-09-21
For those of you interested, I couldn't wait anymore and installed Ubuntu Maverick 10.10 (lastest daily build). We still have some of the same issues we had with Ubuntu Lucid:

1) SOUND > everything works good (microphones, hdmi) except from the headphones, they don't mute the speakers and don't produce any sound. I tried installing linuxant but it didn't work (I guess because of the kernel). Then I tried different options in alsa-base.conf (ideapad, thinkpad, hp_laptop, dell-laptop, dell-vostro, olpc-xo-1_5). At the end, I found that the best solution is the one proposed by krzysiekb in post #121, so thanks a lot for it. I also tried alsa-backports with no luck.

2) HOTKEYS > calculator button (Fn + KP_Enter) is not working. Touchpad button (Fn + F9) is now recognized as XF86Tools, so we can use it as a keyboard shortcut to the touchpad script. Wireless button (Fn + F2) has the same problem and solution as we had before.

3) WEBCAM & SUSPEND > same problem, same solution.


About the sound solution: there is no way to select the input source. By default, the internal mic is selected. If you plug in a external mic it gets selected automatically, but when you unplug it the internal mic is not working anymore. The solution for that is to run this at the terminal:

sudo /etc/init.d/hd-conexant restart

Then the internal mic is selected again. I created an alias for that in bash_aliases (the following is not a terminal command):
alias conexant='sudo /etc/init.d/hd-conexant restart'

Whenever I want my internal mic back I just have to open a terminal and write "conexant".

---

### Post by krzysiekb on 2010-09-21
New kernel version 2.6.35.5 has been released yesterday. It includes the following [patch for hda conexant codec]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.35.y.git;a=commit;h=a6a72ec7a8343e9839f689513f6cc7b35b57487b"). In just few words it introduces new model **hp-laptop** which seems to be almost what we need - except the int mic support of course :)

To use the new hp-laptop model you have to create file **/etc/modprobe.d/sound.conf **
```
options snd-hda-intel model=hp-laptop
```

I've made an experiment and changed one function in the module - and voila, Int/Ext autodetection is working! 
Patched module is attached. It was created for [Mainline kernel 2.6.35.5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.5-maverick/").
To install the patched module just copy **snd-hda-codec-conexant.ko** file to **/lib/modules/2.6.35-02063505-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko**

PS. As far as I saw hp-laptop is also supported in kernel 2.6.36-rc5.

---

### Post by jsevi83 on 2010-09-21
krzysiekb, I just tried your solution and it works great. Thanks again. Do you think it will be possible to use your patch with maverick's official kernel, once 2.35.5 it's released?

---

### Post by krzysiekb on 2010-09-22
> **jsevi83 said:**
> Do you think it will be possible to use your patch with maverick's official kernel, once 2.35.5 it's released?

Maverick wiki says: "Beta includes the 2.6.35-19.28 kernel which is based on the 2.6.35.3 upstream stable kernel." So the short answer is no.
My patch can be applied only to the version 2.6.35.5 (and maybe higher).

---

### Post by jlesueur on 2010-09-30
For anyone interested, the suspend and touchpad solutions also apply to the Asus K72JK. Very useful. Thanks!

---

### Post by michael911 on 2010-10-11
I install new ubuntu 10.10 on my laptop asus k52f and soud play only from internal speakers. After I aply patch from post #128 and play booth headphones and internal speakers. And internal microphone don't work.

Any idea how fix it?

---

### Post by demetrius2009 on 2010-10-11
try to use pinsensed script :)

---

### Post by michael911 on 2010-10-11
which script? I don't have problem with microphone, but with speakers. Speakers still play, when I plug headphones in.

---

### Post by demetrius2009 on 2010-10-11
[http://ubuntuforums.org/showpost.php?p=9178795&postcount=131](http://ubuntuforums.org/showpost.php?p=9178795&postcount=131) this script

---

### Post by krzysiekb on 2010-10-12
> **michael911 said:**
> I install new ubuntu 10.10 on my laptop asus k52f and soud play only from internal speakers. After I aply patch from post #128 and play booth headphones and internal speakers. And internal microphone don't work.

Any idea how fix it?

Which kernel version are you using? (uname -a)

---

### Post by ssek on 2010-10-12
download the last kernel at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.7-maverick/)

install it and do the patch on #128

---

### Post by zvezdogled on 2010-10-12
i have k52 laptop with Maverick and kernel 2.6.35-22
the headphones are not working. i tried the pinsense solution but
the compile returns error 
(main.cpp:42: error: ‘umask’ was not declared in this scope)
then i tried the solution in #121 and all the sound stops working 
and the command alsamixer returnes
cannot open mixer: No such file or directory
and at least i tried #128 but with the new kernel even the xserver stopped working. so any suggestions?

---

### Post by demetrius2009 on 2010-10-12
> **zvezdogled said:**
> 
(main.cpp:42: error: ‘umask’ was not declared in this scope)


LolZ! I have just commented that 42-nd line and compiled the script, after that internal speakers get mute when inserting headphones

---

### Post by ssek on 2010-10-13
any solution for the upside down webcam?

I run the command on the first page

the webcam still upside down

---

### Post by michael911 on 2010-10-13
last update ubuntu 10.10 solved problem winth speakers

---

### Post by demetrius2009 on 2010-10-13
> **ssek said:**
> any solution for the upside down webcam?

I run the command on the first page

the webcam still upside down
did you try SOLUTION 5 from here [http://ubuntuforums.org/showpost.php?p=9162799&postcount=1](http://ubuntuforums.org/showpost.php?p=9162799&postcount=1) ???
just follow that teps, it helped me :)

---

### Post by mahalos on 2010-10-13
Well i thought i'd chime in with where i'm at with all of this..

Asus K52JC
Clean install of 64bit Ubuntu 10.10

- camera upside down (fixed via #5 on original post) tested with cheese, skype

- suspend, hibernate working thanks to #4 on original post

- sound.....internal mic works, speakers work, headphones don't. linuxant.deb fails to install

- touchpad...all good

- wireless light....still not working but haven't tried the fix

other than the hybrid intel/nvidia graphics and the sound all is good.

---

### Post by 542 on 2010-10-13
> **mahalos said:**
> Well i thought i'd chime in with where i'm at with all of this..

Asus K52JC
Clean install of 64bit Ubuntu 10.10

- camera upside down (fixed via #5 on original post) tested with cheese, skype

- suspend, hibernate working thanks to #4 on original post

- sound.....internal mic works, speakers work, headphones don't. linuxant.deb fails to install

- touchpad...all good

- wireless light....still not working but haven't tried the fix

other than the hybrid intel/nvidia graphics and the sound all is good.
Good to know mahalos, I've upgraded to 10.10 (Asus K52J) and am in a similar situation to you. 

My biggest annoyance is the sound - it fails to build the linuxant.deb for me. (same problem as this post [http://ubuntuforums.org/showthread.php?t=1592274](http://ubuntuforums.org/showthread.php?t=1592274)).

---

### Post by jsevi83 on 2010-10-14
Well, for those of you who are still having problems with sound, the solution is on post 128 ([http://ubuntuforums.org/showpost.php?p=9873430&postcount=128](http://ubuntuforums.org/showpost.php?p=9873430&postcount=128)).

1) Install kernel 2.6.35.5 (or higher) from here:   [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

2) Then run this on the terminal:  echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf

3) Download the patch from post 128 and copy the file snd-hda-codec-conexant.ko to /lib/modules/2.6.35-*******-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko

4) Reboot. 

Now there is microphone autodetection and speakers and headphones work properly.

---

### Post by ssek on 2010-10-14
> did you try SOLUTION 5 from here [http://ubuntuforums.org/showpost.php...99&postcount=1](http://ubuntuforums.org/showpost.php...99&postcount=1) ???
just follow that teps, it helped me

yeah I tried and its work for cheese
but not for skype or other applications

---

### Post by ssek on 2010-10-14
anyone how to activate customize desktop apparence?

I installed **compizconfig-settings-manager**

but super effects (as fire effect or else) don't work....

is it a problem with graphic intel ?

---

### Post by jsevi83 on 2010-10-15
For the webcam, this is the command I use to start skype (in ubuntu 64bit):
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by shrinux on 2010-10-15
Hello Everyone

Sound + 10.10 Problem!

Nothing has worked for me so far. Instead, things went worst. After installing "alsa-driver-linuxant" the sound device has gone! So, I have no sound now.

Please, help me reinstall the default driver. I need my sound device back!

I have removed "alsa-driver-linuxant". So, what's next?

Note: the "alsa-driver-linuxant" was working great with Lucid!

---

### Post by jsevi83 on 2010-10-15
I updated the first post for people who didn't read the thread, so they didn't notice we got a solution for sound problems 3 weeks ago (post 128, thanks to  krzysiekb)

---

### Post by shrinux on 2010-10-15
OK,

The current kernel is 2.6.35-22-generic-pae
Do I have to install 2.6.35.5?
If yes, Which files should I download and install?

I found the following files (Excluding the 64bit files):
[LIST]
[*]linux-headers-2.6.32-02063205-generic_2.6.32-02063205_i386.deb
[*]linux-headers-2.6.32-02063205_2.6.32-02063205_all.deb
[*]linux-image-2.6.32-02063205-generic_2.6.32-02063205_i386.deb
[*]linux-source-2.6.32_2.6.32-02063205_all.deb
[/LIST]

Thanks for updating the thread :)

---

### Post by krzysiekb on 2010-10-15
> **shrinux said:**
> Which files should I download and install?

For 32bit system:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-image-2.6.35-02063507-generic_2.6.35-02063507.201009290909_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-image-2.6.35-02063507-generic_2.6.35-02063507.201009290909_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-headers-2.6.35-02063507_2.6.35-02063507.201009290909_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-headers-2.6.35-02063507_2.6.35-02063507.201009290909_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-headers-2.6.35-02063507-generic_2.6.35-02063507.201009290909_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/linux-headers-2.6.35-02063507-generic_2.6.35-02063507.201009290909_i386.deb)

---

### Post by michael911 on 2010-10-15
I have the newest stable kernel (2.6.35-02063507-generic, x64), I aplied patch from post #128, but I have one problem.

Switch between internal speakers and headphones works fine. HDMI works fine. External microphone works fine. BUT internal microphone don't work.

Switch between internal and external microphone still don't work.

Have somebody (krzysiekb) any idea, how to fix it?

---

### Post by jsevi83 on 2010-10-15
I have tried kernel 2.6.35-23 from ppa:kernel-ppa/pre-proposed.

Using model=hp-laptop (and no patch) everything works fine except from the internal microphone, which is not working.

Then I applied the patch of krzysiekb and rebooted. Now internal/external microphone switch is working, but when i plug my headphones sound is coming out at the same time from the speakers.

So I guess the patch is designed for kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  Maybe ubuntu is using its own patches which conflict with yours, I don't know.

I hope that krzysiekb can make another patch (in case we need it) for the ubuntu official kernel once 2.6.35-23 is released.

---

### Post by shrinux on 2010-10-16
After doing the updated tweaks to fix the sound issues.
 
Speakers don't mute after connecting headphones! ](*,)
I haven't tested the mic yet.

---

### Post by krzysiekb on 2010-10-16
> **shrinux said:**
> After doing the updated tweaks to fix the sound issues.
 
Speakers don't mute after connecting headphones! ](*,)
I haven't tested the mic yet.

Don't you use 32-bit kernel, do you? Please note that patched module from the post #128 works only with 64-bit kernel.

@jsevi83: Can you please update the first post with this info?

---

### Post by tpsvca on 2010-10-16
> **krzysiekb said:**
> 
To use the new hp-laptop model you have to create file **/etc/modprobe.d/sound.conf **
```
options snd-hda-intel model=hp-laptop
```
Thees steps works perfect for asus k52f without any other steps! Thank you!

---

### Post by ntomka on 2010-10-16
> **jsevi83 said:**
> I have tried kernel 2.6.35-23 from ppa:kernel-ppa/pre-proposed.

Using model=hp-laptop (and no patch) everything works fine except from the internal microphone, which is not working.

Then I applied the patch of krzysiekb and rebooted. Now internal/external microphone switch is working, but when i plug my headphones sound is coming out at the same time from the speakers.

The issue is the same with ubuntu patched kernel 2.6.36.

---

### Post by krzysiekb on 2010-10-16
I've installed kernel 2.6.36rc8 64-bit (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/)) and the soundcard behaves exactly as with kernel 2.6.35.5. The kernel must be patched in order to make the int mic working (patch is attached).

For these of you still encountering problems with the sound card after patching the kernel:

1. Check if you're using 64-bit kernel
```
> uname -a
Linux krzys-laptop 2.6.36-020636rc8-generic #201010150908 SMP Fri Oct 15 09:10:32 UTC 2010 **x86_64** GNU/Linux
```

2. Check if modules are loaded
```

> lsmod | grep snd_hda_codec_conexant
**snd_hda_codec_conexant**    38351  1 
**snd_hda_codec**         106283  3 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec_intelhdmi
snd                    64310  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

3. Check if the module snd-hda-intel is properly configured (if not go to post #128 of this thread)
```

> cat /sys/class/sound/hwC0D0/modelname
hp-laptop

```

4. Cleanup pulseaudio
```

> killall pulseaudio
> rm -rf ~/.pulse
> pulseaudio -D

``` (or better relogin)

5. Optionally install pavucontrol to troubleshot the sound system

---

### Post by shrinux on 2010-10-16
> **krzysiekb said:**
> Don't you use 32-bit kernel, do you? Please note that patched module from the post #128 works only with 64-bit kernel.

@jsevi83: Can you please update the first post with this info?

What about 32-bit?

---

### Post by krzysiekb on 2010-10-16
> **shrinux said:**
> What about 32-bit?
Apply patch on your own or wait until someone else does it or move to 64bit

---

### Post by ntomka on 2010-10-16
> **krzysiekb said:**
> I've installed kernel 2.6.36rc8 64-bit (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/)) and the soundcard behaves exactly as with kernel 2.6.35.5. The kernel must be patched in order to make the int mic working (patch is attached).

But why don't you use ubuntu patched kernel from 2.6.36? On the vanilla mainline kernel - for example - ureadahead is not working, but on the other hand with ubuntu's kernel your patch is not working. If you can make patch for it, we could update kernel from repos, which would be awesome. :)
You can grab it from [here]("https://launchpad.net/~ricotz/+archive/unstable") or [here]("https://edge.launchpad.net/ubuntu/+source/linux/2.6.36-0.4/+build/1997218"). :)

Edit: I found out why. Conexant module isn't loaded, and sudo modprobe snd_hda_codec_conexant gives this error:
FATAL: Error inserting snd_hda_codec_conexant (/lib/modules/2.6.36-0-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko): Invalid module format

---

### Post by jsevi83 on 2010-10-16
I also think it would be better to have the patch for ubuntu kernel instead of vanilla kernel.

Ubuntu kernel 2.6.35-23 based on 2.6.35.5 can be found here  >>  ppa:kernel-ppa/pre-proposed

Ubuntu kernel 2.6.36-0.4 based on 2.6.36rc7 can be found here  >>  ppa:ricotz/unstable

---

### Post by krzysiekb on 2010-10-17
Alright, I agree with your arguments. (Patch for x86_64 only!)

---

### Post by ntomka on 2010-10-17
> **krzysiekb said:**
> Alright, I agree with your arguments. (Patch for x86_64 only!)

WOW! That was fast response! :) It works like a charm! \\:D/ Big Thank You!

---

### Post by jsevi83 on 2010-10-19
Did anyone manage to make the calculator key (FN + KP_ENTER) work? I tried the same solution we had in lucid, but it doesn't work. Any suggestions?

---

### Post by stefano.facchini on 2010-10-19
Hi, I have an Asus K52 with Ubuntu Maverick. With Lucid  the speakers did not mute when I plugged the headphones, but I could solve this problem with the pinsensed daemon (using hda-verb). Now, in maverick I have NO sound at all from headphones. In alsamixer the S/PDIF (which I think is the headphones, right?) is zerod (not mute), but I cant increase the volume. What can I do?

Thank you

---

### Post by ntomka on 2010-10-19
> **stefano.facchini said:**
> Hi, I have an Asus K52 with Ubuntu Maver...

Have you read the first post? All known solutions/workarounds are there for your problem!

---

### Post by stefano.facchini on 2010-10-20
Yes but now i hear NO sound from headphones, maybe i need to increase the volume but I don't know how. Is it related to S/PDIF in alsamixer?

---

### Post by krzysiekb on 2010-10-20
> **stefano.facchini said:**
> Yes but now i hear NO sound from headphones, maybe i need to increase the volume but I don't know how. Is it related to S/PDIF in alsamixer?

Have you tried to make diagnostic checks I suggested in  [post #159]("http://ubuntuforums.org/showpost.php?p=9983015&postcount=159")?

---

### Post by iluvatar85 on 2010-10-20
> **krzysiekb said:**
> Alright, I agree with your arguments. (Patch for x86_64 only!)This worked well, thank you!

Will this solution work even if I'll install the suggested kernel upgrade from the update manager?

---

### Post by stefano.facchini on 2010-10-21
> **krzysiekb said:**
> Have you tried to make diagnostic checks I suggested in  [post #159]("http://ubuntuforums.org/showpost.php?p=9983015&postcount=159")?
Here are the results of my experiments (with Ubuntu 10.10, kernel 2.6.35-22 from ubuntu repos):

1) Using the sound.conf from post 128 makes the headphones/speakers work correctly, but without internal mic.
2) Using the sound.conf AND the patch from post 128 turn on the internal mic, but speaker don't mute when I plug the headphones (which, at least, produce sound!)
3) Using sound.con AND the patch AND the pisensend daemon makes everything working fine!

Thank you!

---

### Post by ssek on 2010-10-21
what is the pisensend daemon??

---

### Post by bl4ze on 2010-10-22
I recently bought new laptop asus k52f. I installed Ubuntu 10.10, drivers for wireless card and ethernet card are installed, but i can't connect to my router. Wireless card even find a network. Connection is set well, because work on my other computer. What's wrong?

P.S. Sorry for my english.

---

### Post by stefano.facchini on 2010-10-22
> **ssek said:**
> what is the pisensend daemon??
You can find it here: [http://ubuntuforums.org/showthread.php?t=1043568&page=14](http://ubuntuforums.org/showthread.php?t=1043568&page=14).
It uses hda-verb to manage the speakers.

---

### Post by jsevi83 on 2010-10-22
I think pinsensed is something we don't need to use anymore. The option hp-laptop is the right thing for our sound card, and if you also need the internal microphone, you can apply the patch.

Did anyone manage to make the calculator key (FN + KP_ENTER) work? I tried the same solution we had in lucid, but it doesn't work. Any suggestions?

---

### Post by stefano.facchini on 2010-10-22
> **jsevi83 said:**
> I think pinsensed is something we don't need to use anymore. The option hp-laptop is the right thing for our sound card, and if you also need the internal microphone, you can apply the patch.

Did anyone manage to make the calculator key (FN + KP_ENTER) work? I tried the same solution we had in lucid, but it doesn't work. Any suggestions?
For me the pinsensed daemon is still required, the hp-laptop option with the patch disable the int/ext speaker.

As for the FN+ KP_ENTER, try the following as root:

1) create a file /ect/acpi/events/asus-calc containing

```

event=hotkey ATKD 000000b5
action=/etc/acpi/asus-calc.sh

```2) Create a script /etc/acpi/asus-calc.sh with

```

#!/bin/bash
. /usr/share/acpi-support/power-funcs
getXconsole
gcalctool

```and make it executable.

3) give shell commands:
```

# service acpid restart
# service acpi-support restart

```
This works for me. Maybe the hotkey code for you is different. You can discover it with
```

# service acpid stop
# cat /proc/acpi/event

```then pressing FN+KP_ENTER

---

### Post by stefano.facchini on 2010-10-22
A comment:
This method for the FN+KP_ENTER works, but starts the calculator with root privileges. Moreover, I don't think that managing the calculator from acpi events is very "clean". Is there a way to make Gnome aware of the FN+KP_ENTER key?

The same for the FN+V webcam key. I can start for example Cheese with a similar workaround, but making Gnome managing everything would be much nicer.

---

### Post by jsevi83 on 2010-10-22
The method you described for the calculator key is the same we have in the first post. For me it doesn't work as it did in Lucid.

On the other hand, the webcam key (Fn + v) is now recognized as XF86WebCam, so you can assign a function to it (like starting cheese) in gnome-shortcuts, without the need of acpi. The same applies to the splendid key (Fn + c), which is recognized as XF86Launch1. And the touchpadkey (Fn + F9) is recognized as XF86Tools.

Is there any way to get the calculator key (FN + KP_ENTER) recognized as XF86Calculator, so we don't need acpi?

---

### Post by stefano.facchini on 2010-10-22
> **jsevi83 said:**
> The method you described for the calculator key is the same we have in the first post. For me it doesn't work as it did in Lucid.

On the other hand, the webcam key (Fn + v) is now recognized as XF86WebCam, so you can assign a function to it (like starting cheese) in gnome-shortcuts, without the need of acpi. The same applies to the splendid key (Fn + c), which is recognized as XF86Launch1. And the touchpadkey (Fn + F9) is recognized as XF86Tools.

Is there any way to get the calculator key (FN + KP_ENTER) recognized as XF86Calculator, so we don't need acpi?

Yes, I didn't read accurately the previous posts :). 
For the calculator, there is a (partial) solution:

The script /etc/acpi/asus-calc.sh must contain

```

#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_CALC

```

Now FN+KP_ENTER is recognized as XF86Calculator. The solution is partial because, at least on my system, to generate the XF86Calculator event I must hit some other key after FN+KP_ENTER (try with xev and see what happens). This is strange since with the command
```

$ showkey

```
from a TTY console (NOT a terminal inside X) hitting FN+KP_ENTER generates a normal couple of "key pressed/key released" events...

---

### Post by jsevi83 on 2010-10-22
The same happens to me when using acpi_fakekey $KEY_CALC. I have to press a second key before gcalctool starts

BTW, the problem you have with sound when using hp-laptop is probably that you are using a kernel version below 2.6.35.5 (ubuntu kernel 2.6.35-22 is based on 2.6.35.4)

---

### Post by stefano.facchini on 2010-10-22
> **jsevi83 said:**
> 
BTW, the problem you have with sound when using hp-laptop is probably that you are using a kernel version below 2.6.35.5 (ubuntu kernel 2.6.35-22 is based on 2.6.35.4)
I have the same problem with kernel 2.6.35-02063505-generic, isn't this based on 2.6.35.5 :confused:

> The same happens to me when using acpi_fakekey $KEY_CALC. I have to press a second key before gcalctool starts
With xev I discovered that all the FN+something keys generates a "request MappingKeyboard" event, all but FN+KP_ENTER. Any X hacker can explain this?? In the configuration file  /usr/share/X11/xkb/keycodes I can't notice any difference between KEYCALC and the other FN+something keys

---

### Post by stefano.facchini on 2010-10-23
Ok, I discovered that the problem is acpi_fakekey. It correctly generates the keycode assigned (140 for the calculator), but forgets to generate a synchronization event. With the following patched version everything works fine on my system.

---

### Post by stefano.facchini on 2010-10-23
> **jsevi83 said:**
> 
4) SUSPEND: you need to create a new file with this commands:

sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac
```sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd




How have you discovered that this was the solution for SUSPEND?

---

### Post by jsevi83 on 2010-10-23
> **stefano.facchini said:**
> How have you discovered that this was the solution for SUSPEND?

I found it in some other thread about asus laptops, but I don't remember where.

How do we apply the patch of acpi_fakekey? Could you provide some instructions? Do we need to compile?

---

### Post by stefano.facchini on 2010-10-23
> **jsevi83 said:**
> I found it in some other thread about asus laptops, but I don't remember where.

How do we apply the patch of acpi_fakekey? Could you provide some instructions? Do we need to compile?

Yes compile it with
```

$ gcc -o acpi_fakekey-patch acpi_fakekey-patch.c

```then put the compiled file in /usr/local/bin (or elsewhere in your PATH). Now, instead of using acpi_fakekey in your scripts you can use acpi_fakekey-patch, for example in calc.sh
```

#!/bin/sh
. /usr/share/acpi-support/key-constants
acpi_fakekey-patch $KEY_CALC

```

---

### Post by jsevi83 on 2010-10-23
It works! Thanks a lot.

---

### Post by stefano.facchini on 2010-10-23
> **jsevi83 said:**
> It works! Thanks a lot.

Glad that it helped! 

BTW have you tried the hibernation (I mean to DISK, not suspension) after upgrading to Maverick? On my system it was broken and I had to create a file /etc/pm/config.d/hibernate_mode with the following content
```

HIBERNATE_MODE="shutdown"

```

---

### Post by jsevi83 on 2010-10-24
I don't use hibernation, I don't even have a swap partition, so I cannot check it. Hope it helps other users.

---

### Post by krzysiekb on 2010-10-25
> **stefano.facchini said:**
> How have you discovered that this was the solution for SUSPEND?

Read [post #64 in this thread]("http://ubuntuforums.org/showpost.php?p=9375595&postcount=64")

---

### Post by Ehol on 2010-10-25
> **stefano.facchini said:**
> Glad that it helped! 

BTW have you tried the hibernation (I mean to DISK, not suspension) after upgrading to Maverick? On my system it was broken and I had to create a file /etc/pm/config.d/hibernate_mode with the following content
```

HIBERNATE_MODE="shutdown"

```
I have a Maverick 64bit on a K52JC and hibernation works without doing nothing.
I tested it (unintentionally) when I drained completely the battery of my laptop, due to a call of my little son that kept me away for more than twenty minutes while the low battery alarm already sounded.
When I returned to the laptop, it was switched off. I turned it on again and it did a fantastic resume from hibernation.

On a side note, just using solution on post #121, without the snd-hda-tools installation, with kernel 2.6.35.22 and nothing else, solved the problem with audio.
Maybe the K52JC is an easier beast than the K52F...

In conclusion, at the moment, with a standard Ubuntu Maverick 64 bit on a K52JC, using the twaeks mentioned in this thread and no patches and no other kernels, aside from the hybrid graphics problem, only the webcam is still upside-down.

Later, I'll try to install the libv4l PPA and see if De Goede inserted our webcam in the list of upside-down ones. I'll let you know.

---

### Post by nhockey on 2010-10-25
Im planning on buying a ASUS K52JC-B1, however i cannot find the lspci info i need. can somebody please post the lspci -vv info here for me. Sorry if this isnt the right place to find this information, i been searching for hours though. :/

---

### Post by Ehol on 2010-10-26
> **nhockey said:**
> Im planning on buying a ASUS K52JC-B1, however i cannot find the lspci info i need. can somebody please post the lspci -vv info here for me. Sorry if this isnt the right place to find this information, i been searching for hours though. :/

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: c0000000-d30fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 1c77
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4149
	Capabilities: [a0] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot+
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt+ ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #17, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1432
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at d3400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at e080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4189
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a4] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at d740a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d7408000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 13f3
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at d7400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 4199
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=1 ArbSelect=Fixed TC/VC=02
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=00 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: d6000000-d73fffff
	Prefetchable memory behind bridge: 00000000d3100000-00000000d32fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #0, PowerLimit 10.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq+ LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4151
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1c77
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: d4c00000-d5ffffff
	Prefetchable memory behind bridge: 00000000d7500000-00000000d76fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #1, PowerLimit 10.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq+ LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4159
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1c77
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d3800000-d4bfffff
	Prefetchable memory behind bridge: 00000000d7700000-00000000d78fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #6, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #5, PowerLimit 10.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq+ LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4161
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1c77
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at d7407000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 1c77

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=10 <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 44
	Region 0: I/O ports at e070 [size=8]
	Region 1: I/O ports at e060 [size=4]
	Region 2: I/O ports at e050 [size=8]
	Region 3: I/O ports at e040 [size=4]
	Region 4: I/O ports at e020 [size=32]
	Region 5: Memory at d7406000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4181
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a8] SATA HBA v1.0 BAR4 Offset=00000004
	Capabilities: [b0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at d7404000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1432
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
	Region 5: I/O ports at d000 [size=128]
	Expansion ROM at d3000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [128 v1] Power Budgeting <?>
	Capabilities: [600 v1] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nouveau
	Kernel modules: nvidia-current, nouveau, nvidiafb

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1089
	Physical Slot: 1
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at d4c00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP+ BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-15-17-ff-ff-24-14-12
	Capabilities: [170 v1] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
	Subsystem: ASUSTeK Computer Inc. Device 1a07
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at d3807000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: fffffffc  Data: 0000
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 1a07
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at d3806000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: fffffffc  Data: 0000
	Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
	Subsystem: ASUSTeK Computer Inc. Device 1a07
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at d3805000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: fffffffc  Data: 0000
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
	Subsystem: ASUSTeK Computer Inc. Device 1a07
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at d3804000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: fffffffc  Data: 0000

04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1905
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 47
	Region 0: Memory at d3800000 (32-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at a100 [size=128]
	Region 3: I/O ports at a000 [size=256]
	Capabilities: [68] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [40] MSI-X: Enable- Count=8 Masked-
		Vector table: BAR=0 offset=00002000
		PBA: BAR=0 offset=00003000
	Capabilities: [70] MSI: Enable+ Count=1/8 Maskable+ 64bit+
		Address: 00000000fee0f00c  Data: 41a1
		Masking: 000000fe  Pending: 00000000
	Kernel driver in use: jme
	Kernel modules: jme

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0


```

This is my lspci.
Regarding the libv4l PPA ... Finally it works !
Now the camera is correctly reverted upside down.
Ok, now, let's wait for Nvidia Optimus support ...

---

### Post by ssek on 2010-10-28
is there an intel graphic driver for K52 on Ubuntu?

I dont know why but graphic loosk better on windows 7

---

### Post by Kojot89 on 2010-10-30
Does anybody has K52JR? I am interested if all devices work well on the newest 10.04.
According to [http://www.linlap.com/wiki/asus+k52jr](http://www.linlap.com/wiki/asus+k52jr) there are some problems with ethernet functionallity. Is it fixed already or the problem still exists?
I know there is also a problem with speakers mute when headphones plugged in and with hibernate ram. Are these problems fixed by tips posted here?
I would be grateful for a short summary of issues and their fixes.
The most important for me is information about if the ethernet problem still exists.
Thanks.

---

### Post by ntomka on 2010-10-30
> **Kojot89 said:**
> Does anybody has K52JR? I am interested if all devices work well on the newest 10.04.
According to [http://www.linlap.com/wiki/asus+k52jr](http://www.linlap.com/wiki/asus+k52jr) there are some problems with ethernet functionallity. Is it fixed already or the problem still exists?
I know there is also a problem with speakers mute when headphones plugged in and with hibernate ram. Are these problems fixed by tips posted here?
I would be grateful for a short summary of issues and their fixes.
The most important for me is information about if the ethernet problem still exists.
Thanks.

I have but I've never noticed any problem with ethernet. Whatever, everything works as it should with solutions/workarounds mentioned in the first post, and not on 10.04 but on 10.10 as it is the latest release.

---

### Post by Kojot89 on 2010-10-30
Oh, right 10.10 is the latest! Thanks for your answer, was very helpful.

---

### Post by rwmuller on 2010-10-31
A heartfelt Thank You to everyone who has contributed to this thread over its life.  I have a K52J.  I have installed Mint 10 RC based on Maverick.  The fixes for sound, webcam and touch pad all work correctly. I tried to install 10.04 but was daunted by the kernel upgrade.  
With the new release and the contributions of so many of you I now have a secure and stable Linux distro on my machine.
Thanks again and again for your willingness to help.

---

### Post by toadleyb on 2010-11-04
I have a new Asus K52F-BBR9.  I am still having the webcam upside down problem.  I have tried the fix from step 5 in the original instructions but no luck.

Anything else I can try?

---

### Post by ntomka on 2010-11-04
> **toadleyb said:**
> I have a new Asus K52F-BBR9.  I am still having the webcam upside down problem.  I have tried the fix from step 5 in the original instructions but no luck.

Anything else I can try?

Start your application this way:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so *application*

---

### Post by toadleyb on 2010-11-05
I tried that and I get the following error and then still upside down.


ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by jsevi83 on 2010-11-05
Applications like Cheese should work just fine. If you have problems with Skype, you need to run it like this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
(in case you are using ubuntu 64 bit)

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
(in case you are using ubuntu 32 bit)

I'm not sure about the 32bit command though. Can anyone confirm it?

---

### Post by toadleyb on 2010-11-05
It is cheese that I am having problems with.  I have never tried skype so don't know about that.  I am running 64 bit.

---

### Post by toadleyb on 2010-11-07
I installed Skype to see if it would work and ran it with the ld_preload command and I get the following error message and the video is still upside down


  ```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

(<unknown>:2856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2856): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2856): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2856): Gtk-WARNING **: Loading IM context type 'ibus' failed

```

---

### Post by jsevi83 on 2010-11-07
I don't know how to help you. Are you using 32 bit or 64 bit? Did you check if libv4l-0 and lib32v4l-0 are installed? Did you check if ppa libv4l is in your repositories?

Did you install skype just to check the webcam? If you only need cheese and nothing else, you can always use vertical flip as an effect.

---

### Post by toadleyb on 2010-11-07
I am using 64 bit.  I did install Skype just to test it, but now that I have installed it it would be nice if I could use it.  Vertical flip in cheese does take care of it.

I did a google search for the errors I am getting and there is a bug in launchpad but it was supposedly fixed months ago with an update.

The web cam works correctly in Windows so I know it is not a hardware problem.  I have only been using Ubuntu for a couple of months now.

---

### Post by jsevi83 on 2010-11-08
Did you check if ppa libv4l is in your repositories? Did you check if libv4l-0 and lib32v4l-0 are installed?

---

### Post by toadleyb on 2010-11-08
Yes, Yes, and Yes.  I have even reinstalled each of them.  I was going to remove and then reinstall but when I went to remove it was going to uninstall all kinds of other apps so I left it alone and just did a reinstall.

---

### Post by ig0r89 on 2010-11-08
Hello friends!
Need some help on my new Asus K52F (bought it today :P). I've installed Kubuntu 10.10 32bit (the **KDE** one). 

Question 1:
Still can't get Fn+KP_Enter to work to start Calculator. I've tried methods from first post, posts 183 and 186 (with fakekey-patch) and read good info here: [https://help.ubuntu.com/community/LaptopSpecialKeys](https://help.ubuntu.com/community/LaptopSpecialKeys)
I've tried to put another command in calc.sh - just to test if it actually executes:
```

touch /tmp/calc.sh

```And after I press Fn+KP_Enter - it creates that file! So the key combination works! It just doesn't launch Calculator. 
Here is xev result of Fn+KP_Enter:
```
KeyPress event, serial 34, synthetic NO, window 0x4e00001,
    root 0xae, subw 0x0, time 1415569, (512,736), root:(515,759),
    state 0x0, keycode 148 (keysym 0x1008ff1d, **XF86Calculator**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4e00001,
    root 0xae, subw 0x0, time 1415569, (512,736), root:(515,759),
    state 0x0, keycode 148 (keysym 0x1008ff1d, **XF86Calculator**), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```It's bind to X86Calculator but doesn't run it. The $KEY_CALC number is 140 on my system.

Actually 80% of Fn+ hotkeys doesn't work out of the box. I've successfully used patch for wi-fi LED (that's Fn+F2) But still a lot of keys doesn't work :( I'll work on that)

Qestion 2:
> **jsevi83 said:**
>   
8 ) TOUCHPAD: not detected as a touchpad, detected as "ImPS/2 Logitech  Wheel Mouse". Touchpad tab missing in System>Preferences>Mouse and  syndaemon is not working. The key to disable touchpad Fn+F9 is not  working. (SOLVED)

Palm proof technology not working.

The touchpad actually works on 10.10 (that's awesome!) And tapping also works out of the box)
What about Palm proof technology in linux? One of the main features of this touchpad and... doesn't work :rolleyes: Has anyone been working on this lately?

---

### Post by jsevi83 on 2010-11-09
For me, most of the special keys are working out of the box. Some of them don't have any function assigned, but that can be done using gnome-keybinding-properties (or equivalent in kde).

Fn + v -> I use it to start Cheese Webcam.

Fn + F9 -> I use it to disable the touchpad (the script is on the first post) 

Fn + c -> The "splendid" key is recognized by acpi-support as a touchpad key. To be able to assign a different function to it, I added a # at the beginning of the last two lines in this file /etc/acpi/events/asus-f8sv-touchpad

Fn + F2 -> It is working, just needs a fix to toggle the led.

Fn + Space -> It locks the screen, I didn't try to change that

I also miss the palm proof technology, I looked for a solution some time ago but found nothing.

---

### Post by ig0r89 on 2010-11-09
jsevi83, Thank you for the answer!
It's strange, but keys seems to be recognized by the system pretty well, but some powers stop them from working)

I tried xev with parameters:
> xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
And typing Fn+ keys, here is what I get:
> Fn+F2: 246 XF86WLAN (Working out of the box (LED - with the help from 1st post))
Fn+F3: 223 XF86Mail (Doesn't work)
Fn+F4: 158 XF86WWW (Doesn't work)
Fn+F5: 232 XF86MonBrightnessDown (Works out of the box)
Fn+F6: 233 XF86MonBrightnessUp (Works out of the box)
Fn+F7: 235 XF86Display (Works out of the box)
Fn+F8: 235 XF86Display (Haven't tested yet)
Fn+F9: 191 XF86Tools (Works with the help from 1st post)
Fn+F10: 121 XF86AudioMute  (Works out of the box)
Fn+F11: 122 XF86AudioLowerVolume (Doesn't work)
Fn+F12: 123 XF86AudioRaiseVolume (Doesn't work)
Fn+ C: 156 XF86Launch1 (Doesn't work, but should it work in linux? + I didn't have any problems with it interfering with touchpad)
Fn+ V: 220 XF86WebCam (Haven't tested yet)
Fn+ SpaceBar: 160 XF86ScreenSaver (Doesn't work)
Fn+ Up: 174 XF86AudioStop (Works out of the box)
Fn+ Down: 172 XF86AudioPlay (Works out of the box)
Fn+ Right: 171 XF86AudioNext (Works out of the box)
Fn+ Left: 173 XF86AudioPrev (Works out of the box)
Fn+KP_Enter: 148 XF86Calculator (Doesn't work)
But the Fn+KP_Enter still is bind to asus_calculator.sh script. The test with creating a temp file on that command - works.
If I run:
> . /usr/share/acpi-support/key-constants
echo $KEY_CALCI get 140. So $KEY_CALC is 140 - good.
But if I type:
> 
. /usr/share/acpi-support/key-constants
sudo acpi_fakekey-patch $KEY_CALC
Just nothing happens (((
If I type 
> 
. /usr/share/acpi-support/key-constants
sudo acpi_fakekey-patch $KEY_**MUTE**
It works - the sound mutes. 

How can KEY_CALC doesn't start calculator? Where can I look next?

---

### Post by jsevi83 on 2010-11-09
If I understood right, the keys are recognized but don't have a defined function. What I did was using gnome-keybinding-properties to assign a function to all the keys that were missing one.

Maybe the differences are between gnome and kde. In gnome you can choose your preferred applications, I set firefox as my browser and thunderbird as my mail client. Then, in gnome-keybinding-properties, most keys have a defined action:

XF86Mail starts preferred mail client out of the box
XF86WWW starts preferred browser out of the box
XF86Calculator starts gnome calculator out of the box
XF86AudioLowerVolume raises volume out of the box
XF86AudioRaiseVolume lowers volume out of the box
Fn + SPACE locks the screen out of the box

The rest I had to assign manually:

XF86Launch1 to start clementine (audio player)
XF86WebCam to start cheese
XF86Tools to start touchpad script

I don't know KDE, so I'm just guessing, but there has to be a place where you can customize keyboard shortcuts. Maybe they don't have a predefined action as they do in gnome, and you need to set them manually.

About the calculator key, I think that you got FN + KP_ENTER recognized as XF86Calculator when used "acpi_fakekey-patch $KEY_CALC". The problem could be that this key (XF86Calculator) doesn't have a predefined action in kde, and you should tell it to start your kde calculator.

---

### Post by nickmz on 2010-11-09
[I][I]I have extremely low microphone level on Asus K52F.

1. Kernel is new 
Linux my-laptop 2.6.35-23-generic #37-Ubuntu SMP Fri Nov 5 19:16:29 UTC 2010 x86_64 GNU/Linux

2. alsa-base.conf is patched with 
options snd-hda-intel model=hp-laptop

3. [/I][/I]snd-hda-codec-conexant.ko is rewritten with module from comment #164

There is low mic level on both internal and external microphones. "Analog Mic Boost" option in GNOME ALSA Mixer doesn't help at all.  

I have MS Windows 7 in dual boot - microphone works fine there. Any ideas?

---

### Post by ntomka on 2010-11-09
Run alsamixer from terminal, press F4 (capture channels) and try out the options. I also have to set *Analog Mic Boost* to 30dB to have a good mic level.

---

### Post by nickmz on 2010-11-09
I'm back to say that I've found console alsamixer really helps - and I see your reply :)

---

### Post by ig0r89 on 2010-11-09
Decided to share some last news) 

What helped me to successfully solve some bugs in ASUS K52F (the one with Core i3 M350) with Kubuntu 10.10 32bit:
1,2,3) Sound: 
Do  everything from post #121 [http://ubuntuforums.org/showpost.php?p=9826074&postcount=121](http://ubuntuforums.org/showpost.php?p=9826074&postcount=121)  
But take the snd-hda-tools for Maverick from [https://launchpad.net/~diwic/+archive/maverick ]("https://launchpad.net/%7Ediwic/+archive/maverick")
Don't forget to run alsamixer and press F4 for Capture devices or F5 to see all devices. Also be sure that your capturing device is selected (you can switch capturing devices with spacebar).
**UPD: **If you want your capturing devices change automatically (internal/external mic) follow instructions from post #1 and if you have 32bit OS take patch from post #240 [http://ubuntuforums.org/showpost.php?p=10127252&postcount=240](http://ubuntuforums.org/showpost.php?p=10127252&postcount=240)

4) Suspend - solution from 1st post (I also read here that it helps ASUS A52 and others too - so I guess you won't have problems on any asus 52 laptop model).

5) Webcam image upside down trick works from post #1. Although don't forget to run your skype with:
> 
For 64bit:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
For 32Bit:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
I've also made this automatic with this commands:
```
sudo mv /usr/bin/skype /usr/bin/skype.real
sudo nano /usr/bin/skype
```FYI: nano is just an editor if you are using Gnome - use gedit. 
In fresh /usr/bin/skype I put:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real
```Then:
```
sudo chmod +x /usr/bin/skype
```Now you can open skype from everywhere and video will be OK!

6) Wireless led - solution from 1st post works. Although the wi-fi led is always turned on when I start the OS. So Fn+F2 works for one session only (For me. Will look at it later)

7) Resolutions - worked out of the box

8) Touchpad - solution from 1st post. Although the palm proof technology is windows only(

9) Calculator with Fn+KP_Enter. I think you should assign it with: System Settings -> Shortcuts and gestures. I haven't tried it yet - do not have enough time, besides I use Calc like once in a year so that is not a priority for me)


I hope I somehow help new users with ASUS K52F ) 
Good Luck!


By the way: what is meant to happen on Fn+C. It's a "splendid" button for some asus video technology. I don't have windows to check it. What it's supposed to do and is it available for linux?

---

### Post by perlon on 2010-11-10
Ok, following the instruction from post #121 completely muted my audio. My sound card isn't recognized anymore. Can you tell me how to undo the whole procedure?

---

### Post by ig0r89 on 2010-11-10
**perlon**, do you have the /proc/asound directory?

Is your sound card recognized by the system? Check System settings-> multimedia (that's for KDE, it's different in gnome, but just find the main system settings ) What sound cards are listed there? Is there an internal audio device listed or just a "Dummy sound" ?

Does lspci find your audio device?

---

### Post by perlon on 2010-11-10
> **ig0r89 said:**
> **perlon**, do you have the /proc/asound directory?

Is your sound card recognized by the system? Check System settings-> multimedia (that's for KDE, it's different in gnome, but just find the main system settings ) What sound cards are listed there? Is there an internal audio device listed or just a "Dummy sound" ?

Does lspci find your audio device?

No, my system doesn't recognize my audio card anymore.
I'll post lspci tomorrow.
[s]Now I see another GIANT problem: I don't know how but it looks like some of those modifications touched also my Windows 7 partition!
At the first boot Windows needed to reinstall my integrated Intel video card drivers. Installed, rebooted, then I noticed my pc doesn't see anymore my nvidia card!
WTF??? Please I want to undo all![/s] (Solved)

---

### Post by perlon on 2010-11-11
So, now I can answer:

no I don't have a /proc/asound directory.
In System->Sound Settings no hardware is listed.

This is my lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
03:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
03:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```And this is lshw:
```
WARNING: you should run this program as super-user.
alberto-k52jc             
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3752MiB
     *-cpu
          product: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:e080(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d400a000-d400a00f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d4008000-d40083ff
        *-multimedia UNCLAIMED
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d4000000-d4003fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:d2c00000-d3ffffff ioport:d4100000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:d1800000-d2bfffff ioport:d4300000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 1c:4b:d6:a8:a7:0d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d1800000-d180ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:b000(size=4096) memory:d0400000-d17fffff ioport:d4500000(size=2097152)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:d0407000-d04070ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d0406000-d04060ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:d0405000-d04050ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d0404000-d04040ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:03:00.5
                logical name: eth0
                version: 03
                serial: 48:5b:39:53:7e:21
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=jme driverversion=1.0.6 latency=0 multicast=yes
                resources: irq:45 memory:d0400000-d0403fff ioport:b100(size=128) ioport:b000(size=256)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d4007000-d40073ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:e070(size=8) ioport:e060(size=4) ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32) memory:d4006000-d40067ff
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:d4004000-d4004fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
```The audio card seems to be unclaimed now.

---

### Post by perlon on 2010-11-11
up

---

### Post by ig0r89 on 2010-11-11
Today I've discovered that my internal mic isn't working :( 
I described my actions in post 216 [http://ubuntuforums.org/showpost.php?p=10095899&postcount=216](http://ubuntuforums.org/showpost.php?p=10095899&postcount=216) 

What is missing there? For internal mic? Because switching between internal/external speakers works great now.

---

### Post by jsevi83 on 2010-11-12
Read post 1. If that works for you, edit post 216 where you are recommending not the best solution

---

### Post by perlon on 2010-11-12
Someone help me please.

---

### Post by ig0r89 on 2010-11-12
**jsevi83**, the solution from 1st post is for 64bit am I right? And I haven't heard anyone to successfully use it on 32bit :(

**perlon**, as no one answers you - I'll try) 
I had exactly the same problem after I played with linuxant drivers + updated kernel and configured alsa. My /proc/asound just disappeared.
After 2 hours of reading manuals, I gave up - since I had newly installed system, I've decided to reinstall Kubuntu) Not the best solution, but It took me 30 minutes. And you struggling with your problem for 2 days already.

---

### Post by perlon on 2010-11-12
> **ig0r89 said:**
> **jsevi83**, the solution from 1st post is for 64bit am I right? And I haven't heard anyone to successfully use it on 32bit :(

**perlon**, as no one answers you - I'll try) 
I had exactly the same problem after I played with linuxant drivers + updated kernel and configured alsa. My /proc/asound just disappeared.
After 2 hours of reading manuals, I gave up - since I had newly installed system, I've decided to reinstall Kubuntu) Not the best solution, but It took me 30 minutes. And you struggling with your problem for 2 days already.

Oh well, surely reinstalling the whole system would solve my problem... :P
Anyway I'd like to avoid it, or I will do it everytime I have a minor issue. That's not a good approach, I think. First I try to reinstall pulseaudio, then I'll see what to do. Also, it would helpful if the guy in post #121 tell me how to undo all.

---

### Post by jsevi83 on 2010-11-12
The solution on post 1 works for 32 and 64 bit. But the patch is only compiled for 64 bit, so if you want to use that solution on 32bit you have to compile the patch yourself (then you could share it with the rest of 32bit users).

---

### Post by jsevi83 on 2010-11-12
perlon, why don't you undo the steps from post 121? I think it's pretty easy. Did you read and try to understand, or just copy paste?

erase these files 

/etc/modprobe.d/sound.conf
/etc/pm/sleep.d/30_custom-hd-conexant
/etc/init.d/hd-conexant

---

### Post by perlon on 2010-11-12
jsevi83, yes I tried to undo step by step and deleted the files you mentioned. But it can't detect the audio card. The only thing i didn't remove is the **snd-hda-tools, **because my software center said there were only updated software, not installed... anyway I'll give it another try asap.

---

### Post by ig0r89 on 2010-11-12
**jsevi83**, thank you for your help!
So as said in manual I need to copy snd-hda-codec-conexant.ko file to /lib/modules/2.6.35-23-generic/kernel/sound/pci/hda .
But I somehow need to get a 32bit version of this file? But how? I tried to look into snd-hda-codec-conexant.ko but I can't open it with any text editor. 

I just haven't done that before, and don't know where to start actually... :neutral:

---

### Post by jsevi83 on 2010-11-12
The package with the patch for 64bit contains two more files: patch_conexant.c and patch_conexant.c.diff. You can google to find out how to compile that (I don't know the commands, but I think it is not too difficult).

---

### Post by krzysiekb on 2010-11-12
@all_32bit_users: Just out of curiosity, ppl, why don't you go with 64bit system and make your live easier? 
(Sorry for this off-topic, but I couldn't resist)

---

### Post by jsevi83 on 2010-11-13
I was about to say the same in my last post. With a 64 bit system you make full use of your hardware. Is there any specific reason why you prefer 32bit?

---

### Post by ig0r89 on 2010-11-13
[COLOR=Gray]offtopic:[/COLOR] [COLOR=Black]As I know 32bit systems are working good on < 4Gb of RAM. 
And it's recommended to use 64bit if you have > 4Gb RAM. 
At least that's what I've read... 

I have 3Gb in my k52f.[/COLOR]

---

### Post by krzysiekb on 2010-11-13
> **ig0r89 said:**
> [COLOR=Gray]offtopic:[/COLOR] [COLOR=Black]As I know 32bit systems are working good on < 4Gb of RAM. 
And it's recommended to use 64bit if you have > 4Gb RAM. 
At least that's what I've read... 

I have 3Gb in my k52f.[/COLOR]

I respect your choice, but why don't you want to use the power of the CPU you've already paid for?
Maybe [this benchmarks]("http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks") (although a bit outdated) will convince you :)

---

### Post by mgleahy on 2010-11-15
> **krzysiekb said:**
> > The internal microphone is not working. Any ideas?
Yes, but it's a bit complicated because it requires to use hda verbs.

All steps should be done with root privileges.

1. Create file **/etc/modprobe.d/sound.conf**
```

options snd-hda-intel model=thinkpad

```

2. Add the following package repository
```

deb http://ppa.launchpad.net/diwic/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/diwic/ppa/ubuntu lucid main

```

and install package **snd-hda-tools**

3. Create file **/etc/init.d/hd-conexant**
```

#!/bin/bash

# AudioIn 0x14 use selector 0 -> 0x17
hda-verb /dev/snd/hwC0D0 0x14 SET_CONNECT_SEL 0

# Audio Selector 0x17 use input 0 -> 0x1a (IntMic)
hda-verb /dev/snd/hwC0D0 0x17 SET_CONNECT_SEL 0

# Configure IntMic
hda-verb /dev/snd/hwC0D0 0x1a SET_PIN_WIDGET_CONTROL 0x24

``` 

And make it executable. This script configures the soundcard.

4. Run **update-rc.d hd-conexant defaults** 
So the script will be executed at startup

5. Create file **/etc/pm/sleep.d/30_custom-hd-conexant**
```

#!/bin/sh
case "${1}" in
        hibernate|suspend)
        ;;
        resume|thaw)
                /etc/init.d/hd-conexant
        ;;
esac

```

And make it executable. This will reconfigure the soundcard after resume.

6. Reboot

7. Use alsamixer to control gain and capture level.

I've tested this with Skype and it's working perfectly.

This exact solution worked for me.  FWIW, I added the repository using "sudo apt-add-repository ppa:diwic/ppa", then edited the installed /etc/apt/sources.list.d/diwic-ppa-maverick.list to point to lucid instead of maverick (this saved me having to remember where to get the GPG key).  I also used ```
options snd-hda-intel model=auto
```, since I saw that mentioned somewhere, and my model is slightly different (Asus NJ71Q).  Works great (finally).

---

### Post by ig0r89 on 2010-11-16
I still didn't compile patch_conexant.c for 32bit system (

I've created a Makefile:
```
obj-m := patch_conexant.o
KDIR  := /lib/modules/$(shell uname -r)/build
PWD   := $(shell pwd)
default:
    $(MAKE) -C $(KDIR) M=$(PWD) modules

```Then I've got errors, that it can't find files:
hda_codec.h
hda_local.h
hda_beep.h
I've found them in web and put them in the patch directory.

But now I have even more errors! Here is the list: [http://txtb.in/vzP](http://txtb.in/vzP)
:(

---

### Post by krzysiekb on 2010-11-16
> **ig0r89 said:**
> I still didn't compile patch_conexant.c for 32bit system

How to apply the patch - simple but time consuming way:
1. Download appropriate kernel source
2. Unpack it
3. Overwrite patch_conexant.c
4. Build the kernel
5. Overwrite your snd-hda-codec-conexant.ko with newly compiled module

Read [this how-to]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/") to get more info about building ubuntu kernel.

Good luck!

---

### Post by ssek on 2010-11-16
sometime my ubuntu freeze without doing nothing...

normal use : playing music on audacious and, surf on internet
when the freeze come, applications seems still runing
but interface freeze and just not respond to any mouse click (maybe gnome pb?)

does anyone have same pb

I think also change ubuntu for kubuntu
which is more stable?

---

### Post by ig0r89 on 2010-11-17
Great news! I'm able to capture sound with my internal mic now!!!

Thank you **krzysiekb**!Yesterday I compiled kernel with conexant patch. It was long 2 hours) After it finished at 01:00 am I thought that this nightmare is over and copied generated snd-hda-codec-conexant.ko to /lib/modules/2.6.35-23-generic/kernel/sound/pci/hda as needed!

And It didn't help = ) #-o

I remembered 100% that my internal mic was OK when I wrote post 216 ( [http://ubuntuforums.org/showpost.php?p=10095899&postcount=216](http://ubuntuforums.org/showpost.php?p=10095899&postcount=216) ) But it stopped working later. 
Of course I was playing with alsamixer and muted/unmuted everything, - no luck.

Then I discovered that in alsamixer you can change the capture device with SPACE... - **Bingo!** I had no capturing device selected. 

How did it became unselected? Looks like I encountered the same issue as **jsevi83** here [http://ubuntuforums.org/showpost.php?p=9473344&postcount=82](http://ubuntuforums.org/showpost.php?p=9473344&postcount=82)
And as I know - patch conexant solves this issue.

SO to sum it up: to enable internal mic and sound in ASUS K52F you only need to follow rules at post 216 [http://ubuntuforums.org/showpost.php?p=10095899&postcount=216](http://ubuntuforums.org/showpost.php?p=10095899&postcount=216)

To automatically switch between internal-external mic you will need a patch_conexant. Which I attach to this post (32bit version!)

[COLOR=Gray]
PS updated my 216 post with new info[/COLOR]

---

### Post by jsevi83 on 2010-11-18
Did you try model=hp-laptop + patch? That is what works for 64bit (with kernel 2.6.35-23)

---

### Post by Kojot89 on 2010-11-18
Asus K52je, with Ubuntu 10.10 x86_64, kernel 2.6.35-22-generic.
Here is my testing report:
**1) Speakers do not mute when headphones are plugged in. (SOLVED)**

Find solution here (post #128 )
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9873430&postcount=128](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9873430&postcount=128)

Just create file:
```

sudo gedit /etc/modprobe.d/sound.conf

```and paste it:
```

options snd-hda-intel model=hp-laptop

```**2) Internal microphone does not work (SOLVED)**
Find solution here (post #121)
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9826074&postcount=121](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9826074&postcount=121)

Follow all steps but leave: ```
options snd-hda-intel model=hp-laptop
```For me options snd-hda-intel model=hp-laptop works best.
[B]
3) Webcam image is upside down. (SOLVED)[/B]

When you are running your application use:
```

export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so APPLICATION_NAME
or
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so APPLICATION_NAME

```examples```
:
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```My v4l control panel does not contain vertical flip or horizontal flip option.

**4) The led does not turn off when wireless is disabled (SOLVED)**

Follow steps in post #1.
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9162799&postcount=1](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9162799&postcount=1)

**5) Calculator button (Fn + KP_Enter) not working.**
Presented solution doesn't work for me.

**6) Touchpad - works OK, no problems**.

**7) Suspend freeze - not sure yet**
It suspends, but computer is not able to wake up. Suspending take really long time.

---

### Post by Kojot89 on 2010-11-18
**I have also a few quesions**:

1. After installing ATI graphic drivers linux tty's text is very large  and splash screen is very poor quality. Do you have any ideas how to  repair it?

Adding vga=... option to grub parameteres improve quality but it slows  down writing the text to console (ps -ea takes about 5 seconds, normally  bellow 1 second).


2. Every time I start system with AC adapter plugged in the lcd is set  to maximum brightness. Is there any possibility to set default  brightness?

---

### Post by kamil2 on 2010-11-18
> **toadleyb said:**
> I am using 64 bit.  I did install Skype just to test it, but now that I have installed it it would be nice if I could use it.  Vertical flip in cheese does take care of it.

I did a google search for the errors I am getting and there is a bug in launchpad but it was supposedly fixed months ago with an update.


Hi.
Had the same problem with Asus K52F-SX223-4. It's webcam has a different USB ID and it's not in v4l-utils 0.8.1.

I've added the new ID myself, if you're able to patch & compile v4l-utils package, here's a line that has to be inserted into lib/libv4lconvert/control/libv4lcontrol.c at the v4lcontrol_flags table:
```

   { 0x13d3, 0x5130, 0, "ASUSTeK Computer Inc.        ", "K52F",
      V4LCONTROL_HFLIPPED | V4LCONTROL_VFLIPPED },

```

Replace first 2 numbers with your USB ID (you can find out with 'lsusb') if it still doesn't work.

Otherwise just wait for the next v4l-utils version, I've sent this new entry to the maintainers and upstream.

---

### Post by s_h_a_d_o_w_s on 2010-11-21
Hey guys I have an Asus K52JR-X4 and wanted to make a post to help other people. This is for a fresh install of Ubuntu Maverick Meerkat (x64).

1) WLAN light switch works with fix on front page.

2) Double-tapping the touchpad acts as right-click, where it really should be a middle-click:

Create a file called **.xsessionrc** in your home folder (/home/**username**) and put this into it:

```
xinput set-prop 12 "Synaptics Tap Action" 0 0 0 0 1 2;
```3) Catalyst 10.11 on a fresh install. 

Update ubuntu, and once that's done, enable maverick-proposed repo in Synaptic.

Install the ubuntu driver from the panel and then remove it. I don't know why but I always need to do this or I get a black screen. Now, check for updates again. There will be a few new ones, let them update then reboot. 

Run ```
uname -a
``` to ensure you're running the 2.6.35.2**3** kernel.

Then download latest cats (now 10.11).

run ```
 
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```now cd into the directory containing the installer.

```
sudo sh ./ati-driver-installer-10-11-x86.x86_64.run --buildpkg Ubuntu/maverick
```Okay, now that'll make 4 new .deb files. We'll install them all with:

```

sudo dpkg -i fglrx*.deb
```.

After that's done, running the command ```
aticonfig
``` should **not** spit out ```
aticonfig: command not found
``` If it does, run ```
 sudo sh ./ati-driver-installer-10-11-x86.x86_64.run
``` and once the window pops up, click install driver 8.791, I agree, and let it install. Then, reboot. Now you should be up and running with latest cats.

Lastly, run ```
aticonfig --initial
``` and reboot. All should be well.

Just an FYI these might not be the "best" steps but they work for me and the gpu I have in my laptop (ati 5470). The bootup and shutdown process doesn't look very good (some blinking, visible terminal text, minor graphical anomalies) but is freaking fast (so doesn't affect bootup times. Also, the driver seems to be working very nicely for me with compiz, so that's great.

4) Sound not muting when headphones not plugged in solved with post on first page.

---

### Post by ssek on 2010-11-25
I do steps in 127 and after deleted files.

someone can explain me why my internal microphone finally work
when I deleted those files :

/etc/modprobe.d/sound.conf
/etc/pm/sleep.d/30_custom-hd-conexant
/etc/init.d/hd-conexant

---

### Post by krzysiekb on 2010-11-25
> **ssek said:**
> I do steps in 127 and after deleted files.

someone can explain me why my internal microphone finally work
when I deleted those files :

/etc/modprobe.d/sound.conf
/etc/pm/sleep.d/30_custom-hd-conexant
/etc/init.d/hd-conexant

Yes, you should not mix up solutions. Either use mode=hp-laptop + patched module or hda-verbs with these additional files. These solutions are mutually exclusive.

---

### Post by s_h_a_d_o_w_s on 2010-11-28
Hey do your laptops show the ubuntu boot logo fully during boot time or do you see text and a bit of garbled graphics errors?

---

### Post by SlowNinja on 2010-11-30
I'm having a bit of trouble on the first sound fix.
> **jsevi83 said:**
> [COLOR=Blue]UPDATE: for Ubuntu Maverick 10.10[/COLOR]

- To solve the problems relative to sound, follow this (only for ubuntu maverick 64bit).

1) You need ubuntu kernel 2.6.35-23 or higher. Open Synaptic and update the kernel in case you are using 2.6.35-22.

2) Run this command on the terminal: 

echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf

3) Download the attached file from post #164 ([http://ubuntuforums.org/showpost.php?p=9985192&postcount=164](http://ubuntuforums.org/showpost.php?p=9985192&postcount=164)). Extract the file "snd-hda-codec-conexant.ko" and copy it to this folder:

/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda

You will have to overwrite the original file (and will need root permissions).

4) Reboot.


 

There is no pci folder in /lib/modules/2.6.35-23-generic/kernel/sound 
Do I make them myself or is there something else I need to install?
I am using 10.10 64 bit 2.6.35-23-generic kernel

---

### Post by SlowNinja on 2010-11-30
Never mind. Update Manager just fixed my headers. It works now. Sorry if anybody was looking into this for me.

---

### Post by Kojot89 on 2010-12-01
> **s_h_a_d_o_w_s said:**
> Hey do your laptops show the ubuntu boot logo fully during boot time or do you see text and a bit of garbled graphics errors?

I see very low quality ubuntu splash logo during system start. Also the font of the text in terminal is greater than normal and it looks quite strange, only a few lines can be displayed on the screen at the same time.
Before installing ATI drivers there were no any problems like these.

---

### Post by luis.armandob on 2010-12-04
First: good topic, thanks guys.

I'll tell my experiences with my K52J...

I have problems with the nVidia drivers, I think because of the optimus technology. The solution was uninstall any nvidia driver and let only the intel drivers. It's ok, in spite of not be able to use the nvdia graphics card... 
So, my suggestion is: don't use nvidia drivers.

I have problems with the sound as most of the other guys. In Lucid the linuxant drivers worked ok. But in Maverick, I've tried the solution of post #164, but the microphone still don't work. Any ideas?

The other things is all ok in Maverick.

Thanks.

---

### Post by jsevi83 on 2010-12-06
Solution for sound is on the first post. That should work if you are using maverick 64 bits.

---

### Post by klarkent on 2010-12-11
> **SlowNinja said:**
> I'm having a bit of trouble on the first sound fix.


There is no pci folder in /lib/modules/2.6.35-23-generic/kernel/sound 
Do I make them myself or is there something else I need to install?
I am using 10.10 64 bit 2.6.35-23-generic kernel

How did you make Audio working? 
I created the pci/hda directory and copied the .ko file into it but it doesn't work... help me :(

---

### Post by nickmz on 2010-12-11
ASUS K52F

Is anyone happy with touchpad sensitivity level? For me it seems to be too sensitive and I do not know how to decrease it :(

---

### Post by klarkent on 2010-12-11
> **nickmz said:**
> ASUS K52F

Is anyone happy with touchpad sensitivity level? For me it seems to be too sensitive and I do not know how to decrease it :(

can't you decrease it from System/Preferences/Mouse?

---

### Post by nickmz on 2010-12-11
> **klarkent said:**
> can't you decrease it from System/Preferences/Mouse?

I can't. There is no any sensitivity control on the "Touchpad" tab. I tried the utility from "gpointing-device-settings" without any success.

Xorg.log says:

```
[    11.971] (II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    11.972] (II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
**[    11.972] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.**
[    11.972] (II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
[    11.972] (II) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    12.161] (--) ETPS/2 Elantech Touchpad: touchpad found
[    12.161] (**) ETPS/2 Elantech Touchpad: always reports core events
[    12.291] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    12.531] (--) ETPS/2 Elantech Touchpad: touchpad found
```

---

### Post by klarkent on 2010-12-11
> **nickmz said:**
> I can't. There is no any sensitivity control on the "Touchpad" tab. I tried the utility from "gpointing-device-settings" without any success.

Xorg.log says:

```
[    11.971] (II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    11.972] (II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
**[    11.972] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.**
[    11.972] (II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
[    11.972] (II) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    12.161] (--) ETPS/2 Elantech Touchpad: touchpad found
[    12.161] (**) ETPS/2 Elantech Touchpad: always reports core events
[    12.291] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    12.292] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    12.531] (--) ETPS/2 Elantech Touchpad: touchpad found
```

There is no sensitivity control in Touchpad in mine too but I can adjust sensitivity from the general tab...

---

### Post by nickmz on 2010-12-11
> **klarkent said:**
> There is no sensitivity control in Touchpad in mine too but I can adjust sensitivity from the general tab...

I have no such a control on "Touchpad" tab.

But it seems that my problem is solved. I have installed "gpointing device settings" utility and after I had decreased both "Tapping time" and "Tapping move" almost to their minimum I got very stable tap control and there were no any sporadic taps any more.

---

### Post by Bones-mx on 2010-12-12
hey thanks for the fix, I'm on K52J and works fine:P

---

### Post by orodos on 2010-12-13
Has anybody tried installing wine and running half life 2 or world of warcraft on the k52f?  I'm having a heck of a time with it, wine crashes immediately after character load in WoW, and immediately after level load in hl2.  

Spent all week trying to get these games to play.  WoW will run with the -d3d flag, but at sucky framerates, and it totally crashes with -opengl.  

I have a thread going on the wine WoW page: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

I don't think wine is the problem, and think that something didn't install right.  This computer had a fresh install of 10.10 3 days ago.  i3, intel hd graphics, 4 gigs ram.  Is anybody else having similar problems?

---

### Post by s_h_a_d_o_w_s on 2010-12-13
> **krzysiekb said:**
> I've installed kernel 2.6.36rc8 64-bit (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-rc8-maverick/")) and the soundcard behaves exactly as with kernel 2.6.35.5. The kernel must be patched in order to make the int mic working (patch is attached).

For these of you still encountering problems with the sound card after patching the kernel:

1. Check if you're using 64-bit kernel
```
> uname -a
Linux krzys-laptop 2.6.36-020636rc8-generic #201010150908 SMP Fri Oct 15 09:10:32 UTC 2010 **x86_64** GNU/Linux
```2. Check if modules are loaded
```

> lsmod | grep snd_hda_codec_conexant
**snd_hda_codec_conexant**    38351  1 
**snd_hda_codec**         106283  3 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec_intelhdmi
snd                    64310  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```3. Check if the module snd-hda-intel is properly configured (if not go to post #128 of this thread)
```

> cat /sys/class/sound/hwC0D0/modelname
hp-laptop

```4. Cleanup pulseaudio
```

> killall pulseaudio
> rm -rf ~/.pulse
> pulseaudio -D

``` (or better relogin)

5. Optionally install pavucontrol to troubleshot the sound system

Just wanna say thanks this audio patch is working great for me on Maverick x64 kernel 2.6.36-020636rc8-generic :popcorn::popcorn:

Also, it fixed my computer not being able to shut down. So if any of you have audio issues and shutdown issues, fix the audio first.

---

### Post by pesale on 2010-12-16
Good evening,
I have an Asus notebook K52JC (purchased last October):
kernel: 2.6.35-23-generic
ALSA driver version: Driver Version 1.0.23
Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

The procedure at the first page, for mute headphone, has worked perfectly, also without reboot.
Many thanks to all.

Alessio

---

### Post by k0mpjut0r on 2010-12-17
Hello,

I'm not sure it this has been discussed before, but I've had problems with starting the calculator using Fn + keypad enter in Maverick according to the guide in the beginning of this thread. I've had to do the following modifications:

**/usr/share/acpi-support/power-funcs**

line 16, change to: ```
export XAUTHORITY=/var/run/gdm/auth-for-$user*/database
```

line 26, change to: ```
export DISPLAY=":$displaynum.0"
```

**/etc/acpi/asus-calculator.sh**

so that it doesn't run as root - change last line to ```
sudo -u $user /usr/bin/gcalctool &
```

---

### Post by UpSignal on 2010-12-25
> **luis.armandob said:**
> 
So, my suggestion is: don't use nvidia drivers.


I just bought a brand new asus K52J, and the best thing about this machine, is the nvidia card. at least for me. Try to play GTA or WOW with the intel card, and then you might want to think about what you said. I don't mean to be rude or something...but dude... i love ubuntu, i really love it! But am i going to give away my nvidia card just because it's not yet compatible? no freaking way. I'll stick with windows 7 and with my superb graphics performance thank you :). 

I hope nvidia guys release a proper linux driver for this, i really do. This topic is great, because i see here all the solutions for the problems i had when i first tried to install ubuntu here, but dude...it's kinda stupid trying to fix everything on this laptop and ignoring the graphic card XD. Well, unless of course..you use the laptop to work on open office :)

---

### Post by Vi3tHoneyX on 2010-12-27
I have a K52F-BBR9 and installed 10.10 64 bit. Hibernation and suspending didn't work until I used the suspending solution posted here. Now only hibernation is a problem and it's driving me crazy! When I put my laptop into hibernation mode and try to turn it back on, the screen turns on but is blank and black. What should I do to see what's wrong and is there a solution?

---

### Post by em4o on 2010-12-27
Hey guys I love this tread, it helped me get my Asus in shape and working great. But I just did an update and my internal microphone stopped working. Any ideas or suggestions???

---

### Post by W3N4 on 2010-12-29
It stopped working me too. Don't know why.

---

### Post by jsevi83 on 2010-12-30
You have to repeat steps 3 and 4 from the first post. But this time copy the file to /lib/modules/2.6.35-24-generic/kernel/sound/pci/hda

This has to be done everytime you update the kernel.

---

### Post by W3N4 on 2010-12-30
I see. It works now, thanks.

---

### Post by tonyzhp1987 on 2011-01-01
> **jsevi83 said:**
> [COLOR=Blue]UPDATE: for Ubuntu Maverick 10.10[/COLOR]

- To solve the problems relative to sound, follow this (only for ubuntu maverick 64bit).

1) You need ubuntu kernel 2.6.35-23 or higher. Open Synaptic and update the kernel in case you are using 2.6.35-22.

2) Run this command on the terminal: 

echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf

3) Download the attached file from post #164 ([http://ubuntuforums.org/showpost.php?p=9985192&postcount=164](http://ubuntuforums.org/showpost.php?p=9985192&postcount=164)). Extract the file "snd-hda-codec-conexant.ko" and copy it to this folder:

/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda

You will have to overwrite the original file (and will need root permissions).

4) Reboot.


- To solve the webcam upside down problem, run this on a terminal:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade


- To solve the suspend and wireless-led problem, check the following solutions for Ubuntu Lucid 10.04. Alternatively, you can install a package I created which includes the fixes for suspend, wireless led and calculator button. See the attached file. It was created for maverick 64.

*******************************************************************************************************

I own an Asus A52F, twin brother of the Asus K52F. Here is a list of the problems you might find when installing Ubuntu Lucid, and their respective solutions.

[COLOR=Red]LIST OF PROBLEMS:[/COLOR]

1) SOUND: speakers do not mute when headphones are plugged in. (SOLVED)

2) SOUND: hdmi sound out not working. (SOLVED)

3) SOUND: external microphone not working. (SOLVED)

4) SUSPEND: suspend to ram freezes my laptop. (SOLVED)

5) WEBCAM: image upside down. (SOLVED)

6) Wireless LED: the led doesn't turn off when I press Fn+F2, but wireless is disabled. (SOLVED)

7) Available RESOLUTIONS: I get the maximum resolution for my screen, 1366x768, but I am missing other resolutions available in Windows. (IMPROVED)

8 ) TOUCHPAD: not detected as a touchpad, detected as "ImPS/2 Logitech Wheel Mouse". Touchpad tab missing in System>Preferences>Mouse and syndaemon is not working. The key to disable touchpad Fn+F9 is not working. (SOLVED)

Palm proof technology not working.

9 ) Calculator button (Fn + KP_Enter) not working. (SOLVED)



[COLOR=Green]LIST OF SOLUTIONS:[/COLOR]

1,2,3) SOUND: paste these commands on a terminal.

wget [www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip)
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb

Install the package and reboot. Now speakers should mute when headphones are connected, HDMI and microphones (internal & external) should be working. Open alsamixer and unmute S/PDIF (you can do that pressing "m"). Choose HDMI output from the pulseaudio volume applet (hardware tab) when needed. 

***Note: I am using Alsa 1.0.23 and Linux Kernel 2.6.34.


4) SUSPEND: you need to create a new file with this commands:

sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac
```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd


5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.


6) Wireless LED: you need to create two files and restart acpi. Follow this commands:

sudo gedit /etc/acpi/events/asus-wireless-switch
```

event=hotkey ATKD 0000005d
action=/etc/acpi/asus-wireless-switch.sh
```

sudo gedit /etc/acpi/asus-wireless-switch.sh

```
#!/bin/sh
# Toggle wireless device on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy*/rfkill*/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan	
elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
fi
```
sudo chmod +x /etc/acpi/asus-wireless-switch.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart


7) Available RESOLUTIONS: you can get 1024x768 by adding to your repositories ppa:ubuntu-x-swat/x-updates (more stable than ppa xorg-edgers). Do this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade

Then reboot and that's it. THIS IS ONLY FOR INTEL GRAPHIC CARDS > Asus K52F & Asus A52F


8 ) TOUCHPAD: I found a solution to get the Elantech touchpad detected as such (and not ImPS/2 Logitech Wheel Mouse). Follow the instructions on this post:   [http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

EDIT: if you are running 2.6.34-rc7 or later you just need to run this two commands:
echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

Then you can check your settings with "synclient -l" or with xinput list-props "ETPS/2 Elantech Touchpad"
I made a startup script to keep two fingers tap as middle click, and three fingers tap as right click, with this command:
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3

Edit this file to get the touchpad button working:

sudo gedit /etc/acpi/asus-touchpad.sh

```
#!/bin/sh
# Toggle Elantech touchpad device on Asus laptops

[ -f /usr/share/acpi-support/power-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

getXconsole

TPSTATUS=`xinput list-props "ETPS/2 Elantech Touchpad" | grep "Device Enabled" | awk '{ print $4 }'`

test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 1 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 0
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD OFF" "
     Press Fn+F9 to enable"
elif [ $TPSTATUS = 0 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD ON" "
     Press Fn+F9 to disable"
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3
fi
```

sudo service acpid restart
sudo /etc/init.d/acpi-support restart

EDIT: when pressing Fn+c (splendid button) this file is called "/etc/acpi/asus-f8sv-touchpad", and acts as Fn+F9. To solve it, uncomment that file or change it's action to something else that asus-touchpad.sh


9 ) Create two files to get the calculator button working: (if using maverick, check posts 183 and 186)

sudo gedit /etc/acpi/events/asus-calculator
```

event=hotkey (ATKD|HOTK) 000000b5
action=/etc/acpi/asus-calculator.sh
```

sudo gedit /etc/acpi/asus-calculator.sh

```
#!/bin/sh
# Start calculator on Asus K52 laptops

. /usr/share/acpi-support/power-funcs

getXconsole

gcalctool &
```

sudo chmod +x /etc/acpi/asus-calculator.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart
Hello Jsevi83, 
I am tony, i just bought Asus K52je a few days ago,  then i found out it had a lot of problems then i was using Ubuntu 10.10  64bit, but you have solved the most of my problem, you are  soooooooooooooo great guy, thank you very very very much for your help  and for sharing the information with every one.

i guess you must be the smart guy and also research area is IT programing, is this right?

---

### Post by tonyzhp1987 on 2011-01-01
Hello Jsevi83 :popcorn:

Serious sound problem

my sound card was fine when i installed ubuntu 10.10, 

but after i saw your post, i solved a lot of problems, but there is no more sound!!! the sound device has gone!
still thanks Jsevi83 a lot, because fixed my other problems.
for example i fixed the wireless LED light, calculator, suspend problems.

please please help me out,right now my world without any sound. my laptop no more sound. 

i checked the lib/modules/2.6.35-24-generic/kernel/sound
there are no more pci file and others.

please Help me!!!!!!!!! i am really beginner of ubuntu, i love it, but it made me work a lot for it.

---

### Post by jsevi83 on 2011-01-02
Open Synaptic and reinstall this package: linux-image-2.6.35-24-generic

Then follow again the first post and reboot.

---

### Post by tonyzhp1987 on 2011-01-02
Hello Jsevi83

thank you very much, i try now, i hope it will solve the problem.

Happy new year to you.

> **jsevi83 said:**
> Open Synaptic and reinstall this package: linux-image-2.6.35-24-generic

Then follow again the first post and reboot.

---

### Post by tonyzhp1987 on 2011-01-02
> **jsevi83 said:**
> Open Synaptic and reinstall this package: linux-image-2.6.35-24-generic

Then follow again the first post and reboot.

Hello Jsevi83

thank you very much i solved the problem, now i got my music world back, no more silence!!

LOL

---

### Post by blkid on 2011-01-05
hi,
i have an audio problem with my asus k52f. If i set the model hp-laptop, dell-laptop or thinkpad the headphone jack work but doesn't work the internal mic. If i set as model "laptop" the headphone jack doesn't mute the internal speaker (and the headphone are mute) but the internal mic work good.

There is a solution for this problem?

---

### Post by rabideau on 2011-01-10
Hi blkid

I think the answer is almost... there is something you can do to get the sound working if you don't mind having a messed up kernel.  See this post: [http://www.korecky.org/?p=307&langswitch_lang=en](http://www.korecky.org/?p=307&langswitch_lang=en) (under Sound Problems)

If you don't like what the alsa-linuxant 'fix' does to the current Linux kernel, which I didn't, here is how you get back with minimum (maybe no) damage:

*What I discovered is that if you use Synaptic to remove alsa-linuxant completely and then reinstall all your linux kernel modules, things go back to the before alsa-linuxant state.  That doesn't help your device, in my case speakers, but at least the errors go away.  **Maybe a future kernel will fix things.***

---

### Post by perlon on 2011-01-14
I don't understand the calculator solution written in #183-186...
Where do I put calc.sh?

---

### Post by tippyTdizzle on 2011-01-14
perlon, go to post #1 and follow step # 9. That should work and be more understandable. 

It worked for me. 

My Compliments to the diligent and industrious workers of this thread! Thanks so much! Bought my K52F-BBR9 so I could switch to Linux and this thread totally made it possible :D

-T

---

### Post by tivnanwebb on 2011-01-16
Hey,
I'm running Narwal (11.10) on an Asus N53JQ. Since installing Ubuntu I've had no sound through my speakers. I have sound through the headphone port but not through my speakers. Any help is greatly appreciated.  Anyone with this problem? Thank you.

-TW

---

### Post by perlon on 2011-01-17
> **tippyTdizzle said:**
> perlon, go to post #1 and follow step # 9. That should work and be more understandable. 

It worked for me. 

My Compliments to the diligent and industrious workers of this thread! Thanks so much! Bought my K52-BBR9 so I could switch to Linux and this thread totally made it possible :D

-T

[s]Doesn't work to me...[/s]
could someone write a step by step how to for maverick? That one is splitted into two parts, so I think I'm missing something.

EDIT: oh ok, I did it. I simply didn't change name from asus-calculator.sh to calc.sh ... :D

---

### Post by skooterz on 2011-01-18
I just received my new Asus K52DR-A1 yesterday - first thing I did was install Ubuntu 10.10. :D However, there were a few minor problems, most of which I easily fixed myself - notably the sound issue mentioned earlier in this thread. However, one issue that I can't seem to find the solution to relates to the function keys - some of them worked perfectly right out of the box, like Calculator, but others such as the Volume controls have issues. The issue I'm having with them is that they work, but they take ages to do so. I'll hit the Mute key, and then 30 seconds later it'll work. I miss my volume controls actually being useful - if someone has a suggestion or a solution I would be very grateful.

---

### Post by mahalos on 2011-01-20
right then....  i've tried figure this one out myself and haven't had any luck. i did a clean install of 64bit 10.10 the other day,followed the instructions on the first post and all is good. the problem i have is with hdmi audio to my TV. I get audio fine, it's just that I have a strange sound that appears every 10 seconds, it's sounds like something off Transformers. It's only there for a split second, but very noticeble.

things i've tried are
- booting into WIN7 to see if the same problem is there....nope all good, so cable and TV aren't the issue.

- tried outputting audio to the TV via the headphones....all good, no strange sounds.

- tried turning down all volumes on the laptop incase something was to loud...no difference.

-  tried various applications for sound and video...no difference

So i'm stuck, obviously it's some kinda digital output issue....but how to fix it??

I've included a rough recording so you may hear what i'm talking about...you may need to turn your volume up!!

any help appreciated.

---

### Post by tippyTdizzle on 2011-01-21
I'll pitch in that my audio issues are also solved... aside from not getting any via hdmi out. :( (video is fine, but audio does not go through... remains on laptop speakers)

AND, on the note of hdmi video, it has issues (with the modline, I think). Sometimes while watching fullscreen it will auto-adjust to a resolution my tv doesn't support, and then (it won't detect the hdmi port (or connection) any longer, so) i have to dual boot back into windoze to access the Intel chip (via a display controls gui) to reset the resolution. 

...

Anyone have any ideas on that issue? I think it might be needing to edit the xorg.conf file (isn't that where the modline info is?). From what I've read, I believe it's my tv more than ubuntu. Sounds like some tv's have awkward modlines... Any help, or good threads, would be appreciated :-)

---

### Post by jsevi83 on 2011-01-22
mahalos, I listened to the sample and couldn't identify any noise every ten seconds. I have no idea what could be causing it.

tippyTdizzle, to get hdmi audio you need to enable it in the sound configuration. Click on the volume icon, preferences, second tab (hardware). For the screen resolution: main menu, system, prefereces, display settings. There you can adjust the resolution and settings of a secondary screen.

---

### Post by mahalos on 2011-01-23
> **jsevi83 said:**
> mahalos, I listened to the sample and couldn't identify any noise every ten seconds. I have no idea what could be causing it.

Thanks for your reply. To be honest i listened to my sample audio again and struggled to hear it myself. It is very noticeable however and i'll endeavour to produce a better audio sample because it really is the weirdest thing ever.

---

### Post by tippyTdizzle on 2011-01-24
> **jsevi83 said:**
> mahalos, I listened to the sample and couldn't identify any noise every ten seconds. I have no idea what could be causing it.

tippyTdizzle, to get hdmi audio you need to enable it in the sound configuration. Click on the volume icon, preferences, second tab (hardware). For the screen resolution: main menu, system, prefereces, display settings. There you can adjust the resolution and settings of a secondary screen.


Thanks, jsevi83. I think I remember now having read about that elsewhere (i.e. having to enabling hdmi audio out). However, for the display it's not a resolution issue. When this issue occurs, I can go to display settings (either with the hdmi cable still plugged in, untouched, OR after unplugging it and then plugging it back in again) and the second display (my hd tv) will NOT be detected any longer. That's why I'm looking into and thinking it might be a modeline issue. If you (or anyone) have any other ideas or tests to try, I would really appreciate hearing them. 

Asus model K52F-BBR9

Thanks :popcorn:

---

### Post by joe.w.fro on 2011-01-27
Hey I just got my U52f from BestBuy and my internal mic and my audio out (and probably in) dont work. Any ideas?:confused:

---

### Post by Orazio.1985 on 2011-01-28
With this guide 90% of problem was resolved but Internal Microphone do not work!

I've a Asus K52Jc.

Some one can help me?

tnx!

---

### Post by Superpiffer on 2011-01-30
> **Orazio.1985 said:**
> With this guide 90% of problem was resolved but Internal Microphone do not work!

I've a Asus K52Jc.

Some one can help me?

tnx!
Try this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Worked for me, on Maverick...

---

### Post by W3N4 on 2011-01-30
As a user post on page 27, you have to repeat step 3. and 4. However, this time you have to copy the file to /lib/modules/2.6.35-25-generic/kernel/sound/pci/hda
Every time the kernel is updated, you have to copy the file to the newest folder, this time it is .../2.6.35-25-generic/..., next time it could be .../2.6.35-26-generic/... and so on.

---

### Post by W3N4 on 2011-01-31
Another problem has occurred with the latest kernel update 2.6.35-25..
When my headphones are plugged in, speakers don't mute. I tried repeating the procedure for Ubuntu 10.10 x64 in the first post but it doesn't help anymore.

Have you noticed the same problem since the last update ? I hope it doesn't concern just me...

---

### Post by krzysiekb on 2011-01-31
> **W3N4 said:**
> Another problem has occurred with the latest kernel update 2.6.35-25..
When my headphones are plugged in, speakers don't mute. I tried repeating the procedure for Ubuntu 10.10 x64 in the first post but it doesn't help anymore.

Have you noticed the same problem since the last update ? I hope it doesn't concern just me...

Yeah, I can confirm this. I'll try to recompile the module for this kernel version soon.

Edit:
Patch for kernel 2.6.35-25 is attached (x86_64 only!!!)
@jsevi83: Please update the first post

Enjoy!!!

---

### Post by W3N4 on 2011-01-31
Thanks a lot. This is very helpful :)
Next time (If it doesn't work again) I may try to recompile it on my own :)

---

### Post by Orazio.1985 on 2011-02-01
> **Superpiffer said:**
> Try this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Worked for me, on Maverick...
I've tried, but the microfone don't work!

---

### Post by W3N4 on 2011-02-01
If you have installed Ubuntu 10.10 x64, try what I posted several posts above:
[QUOTE=W3N4]As a user post on page 27, you have to repeat step 3. and 4. However, this time you have to copy the file to /lib/modules/2.6.35-25-generic/kernel/sound/pci/hda
Every time the kernel is updated, you have to copy the file to the newest folder, this time it is .../2.6.35-25-generic/..., next time it could be .../2.6.35-26-generic/... and so on.[/QUOTE]

---

### Post by ntomka on 2011-02-05
> **Superpiffer said:**
> Try this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Worked for me, on Maverick...

Great, it works, and now I don't need any patch to mute internal speakers on headphone connect! Thanks! \\:D/

---

### Post by UpSignal on 2011-02-09
guys, i've been reading around, there are some folks making progress in this "optimus nvidia",
check  this out: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
Does anyone made any progress on those tutorials?

---

### Post by ben178 on 2011-02-11
Hi!
I've got an Asus X52F, seems to be a close relative  -I'm still not sure though it's being sold anywhere but germany...
[http://www.computeruniverse.net/products/e90397375/asus-x52f-ex513d-freedos.asp](http://www.computeruniverse.net/products/e90397375/asus-x52f-ex513d-freedos.asp)
I'm having the same problems as described in the first post. I guessed it would be ok to post here - correct me, and I'll open another thread.
After using the method described in the first post, every application trying to use the sound card breaks down. Additionally, and oddly, Firefox now crashes when I right click at it, try to open any of the menus or open a bookmark folder from the bookmark bar. Any way to undo what I did with
```
wget [http://www.linuxant.com/alsa-driver/....0_all.deb.zip]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip")
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb
``` or even set things straight and get it to work?
:(
I had gotten intern and extern sound to work at the same time first, opening
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
and adding
```
options snd-hda-intel model=ideapad
```
...


fixing the webcam with the command line provided in the first post worked fine. thanks

---

### Post by ben178 on 2011-02-11
nice!
so I deleted this line
```
options snd-hda-intel model=ideapad
```from alsa-base.conf
while having changed nothing about the
```
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb
```- no more program crashes, sound works, headphones mute internal speaker.
NICE!
got both microphones to work as well, using
> **Superpiffer said:**
> Try this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```Worked for me, on Maverick...
only that he internal one now is incredibly low.
Thanks for all the help given (to so else in the first place, and some time ago), and sorry I panicked and posted when I destroyed the sound first - all the answers were here...

---

### Post by mr_amit on 2011-02-12
> **k0mpjut0r said:**
> Hello,

I'm not sure it this has been discussed before, but I've had problems with starting the calculator using Fn + keypad enter in Maverick according to the guide in the beginning of this thread. I've had to do the following modifications:

**/usr/share/acpi-support/power-funcs**

line 16, change to: ```
export XAUTHORITY=/var/run/gdm/auth-for-$user*/database
```

line 26, change to: ```
export DISPLAY=":$displaynum.0"
```

**/etc/acpi/asus-calculator.sh**

so that it doesn't run as root - change last line to ```
sudo -u $user /usr/bin/gcalctool &
```

Thanks for the information. I think the first post should be updated, as without these changes the acpid doesn't work properly if the script uses commands that communicates with X.

Here is my `asus-touchpad.sh`:

```

#!/bin/sh
# Toggle Elantech touchpad device on Asus laptops

[ -f /usr/share/acpi-support/power-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

getXconsole

XINPUT="sudo -u $user xinput"

TPSTATUS=`$XINPUT list-props "ETPS/2 Elantech Touchpad" | grep "Device Enabled" | awk '{ print $4 }'`

test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 1 ]; then
	$XINPUT set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 0
elif [ $TPSTATUS = 0 ]; then
	$XINPUT set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
fi


```

---

### Post by Hip-Hopapotamus on 2011-02-18
I've installed 10.10 on my Asus K52 laptop, but it only boots to the terminal.

startx shows a blank screen.

Tried to update the kernel with no success.

sudo service gdm start shows a blank screen

Ubuntu boots into the GUI from my flash drive but I'm at a loss as to what commands I should try to get this working.

---

### Post by ben178 on 2011-02-18
I've got the X52, didn't find a way to get 10.10 running from hard disk, tried to get that going far too long (I'm new to Ubuntu though).
I recommend 10.04.1; does it perfectly for me, that one works fine on X52 (almost. and after following post 1).
;)
if it's just to get the system running without much hassle

---

### Post by rlklee on 2011-02-25
> **Hip-Hopapotamus said:**
> I've installed 10.10 on my Asus K52 laptop, but it only boots to the terminal.

startx shows a blank screen.

Tried to update the kernel with no success.

sudo service gdm start shows a blank screen

Ubuntu boots into the GUI from my flash drive but I'm at a loss as to what commands I should try to get this working.

Had this same problem, same model on 10.10. Solution:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

and add to the end of the file

```
blacklist intel_ips
```

However, you shouldn't need this work around forever. I didn't. After a kernel update (can't recall to what version) it became superflous.

---

### Post by UpSignal on 2011-02-25
Guys, just for you to know...a lot of this stuff is useless now. 
I just notice that. I did a fres ubuntu 10.10 install, and the audio problems: gone. mic problems: gone.
now you just need the webcam hack, and the keyboard stuff. I think the author of this post should update in the first page. Audio hacks are no longer needed ;)
oh, and about the nvidia, as long as you don't install it, intel works great

---

### Post by jsevi83 on 2011-02-26
Well, if there are no problems now people won't be looking for a solution, so there is no need to update the first post. It should stay the way it is in case somebody HAS a problem, so they can have a solution.
I don't think users apply solutions to problems they don't have.

---

### Post by UpSignal on 2011-02-26
hey, i was just wondering, does this fix also applies to kde(kubuntu)? because here i do have the suspend problem :s. also, i'm on 32bits version

---

### Post by sicco1 on 2011-03-02
Never mind, got my stuff working :)

---

### Post by cj6814 on 2011-03-02
I successfully got the internal mic working on my A52F (10.10, 64bit) following the instructions below.  However, after the update manager took kernal from  2.6.35-25-generic to 2.6.35-27-generic the internal mic quit working.

I tried running the exact same process as below (of course making the changes in the correct kernal directory) but with no success.  In the interim I've reverted back to the 2.6.35-25-generic kernal.

Can anyone point me in the right direction for fixing this issue.

Thanks, cj6814

---------------------------

[I]1) You need ubuntu kernel 2.6.35-23 or higher. Open Synaptic and update the kernel in case you are using 2.6.35-22. The latest kernel at the moment is 2.6.35-25

2) Run this command on the terminal: 

echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf

3) Download the attached file from post #293 ([http://ubuntuforums.org/showpost.php?p=10415577&postcount=293](http://ubuntuforums.org/showpost.php?p=10415577&postcount=293)). Extract the file "snd-hda-codec-conexant.ko" and copy it to this folder:

/lib/modules/2.6.35-25-generic/kernel/sound/pci/hda

You will have to overwrite the original file (and will need root permissions).

4) Reboot.
[/I]

---

### Post by sicco1 on 2011-03-03
I got everything to work on my K52F Ubuntu 10.10 64 bit, but right now I have to perform some action every time I start my laptop.

- I want Skype to start when I start my Laptop. Just launching 'skype' via 'Startup Applications' results in the flipped webcam problem, so I tried this command:
'export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype', but skype doesn't start using this command. So I need to manually start skype every time. Any ideas?

- I want double tap on my touchpad to result in middle-mouse button functioning and triple tap to be right mouse button, so I added the following to as a 'Startup Applications' command: 'xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3' but this doesn't seem to work either after startup. I still need to enter it manually into a terminal before it works.. How can I fix this?

---

### Post by jsevi83 on 2011-03-03
For skype, created a new file with this command:

sudo gedit /usr/bin/skype-wrapper

Then copy inside the following:

> #!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"

Then add to startup applications /usr/bin/skype-wrapper


For the touchpad buttons, check the following:

[https://launchpad.net/~yurivkhan/+archive/ppa](https://launchpad.net/~yurivkhan/+archive/ppa)

---

### Post by sicco1 on 2011-03-03
Awesome, thanks!! Now everything seems to work, even scrolling with two fingers :D
This thread definitely allowed me to enjoy Ubuntu much more! Thanks again to all

---

### Post by cj6814 on 2011-03-03
Anyone else lose their internal mic when kernel 2.6.35-25-generic was upgraded to 2.6.35-27-generic via the update manager?

---

### Post by Hip-Hopapotamus on 2011-03-04
[QUOTE]> **rlklee said:**
> Had this same problem, same model on 10.10. Solution:

```
sudo nano /etc/modprobe.d/blacklist.conf
```and add to the end of the file

```
blacklist intel_ips
```However, you shouldn't need this work around forever. I didn't. After a kernel update (can't recall to what version) it became superflous.

Awesome, worked first try. Thank you man.

Having a problem with alsa-driver-linuxant. It said the build failed and to review the buld log.

Then it listed this:

dpkg: error processing alsa-driver-linuxant (--install):
 subprocess installed post-installation script returned error exit status 2

Is there any way I can post the log file?

---

### Post by krzysiekb on 2011-03-05
> **cj6814 said:**
> Anyone else lose their internal mic when kernel 2.6.35-25-generic was upgraded to 2.6.35-27-generic via the update manager?

You need to patch the kernel module /lib/modules/2.6.35-27-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko with a file from the attached archive. (Read instructions from the 1st post for more details)
I've seen a post in this thread claiming that it's not necessary to patch after fresh install anymore though noone confirmed this so far. I still need the patch. Please note that this patch is for x86_64 only. Enjoy!!!

---

### Post by jsevi83 on 2011-03-05
For those of you interested, I just tried the new Ubuntu Natty. Sound problems are gone, as it autodetects internal and external microphone. Webcam upside down is fixed too. Calculator button fixed too.
The only things that needed to be adjusted were the touchpad toggle button and the wireless led. For the rest, everything works out of the box.

Oh, I forgot to test suspend and hibernation.

---

### Post by UpSignal on 2011-03-07
> **jsevi83 said:**
> For those of you interested, I just tried the new Ubuntu Natty. Sound problems are gone, as it autodetects internal and external microphone. Webcam upside down is fixed too. Calculator button fixed too.
The only things that needed to be adjusted were the touchpad toggle button and the wireless led. For the rest, everything works out of the box.

Oh, I forgot to test suspend and hibernation.

Well done mate :D, thanks for keeping us informed :). i'm still praying for the release of a proper nouveau driver =D

Edit: By the way, is natty stable? i mean, did you have problems with intel graphics or what?

---

### Post by jsevi83 on 2011-03-08
I didn't have any problems with intel graphics, but I'm not using Natty full time (I keep Maverick till the final release). It seems like Unity needs a bit more polishing, there are still some bugs, but support for Asus K52 is excelent.

---

### Post by cj6814 on 2011-03-08
Thank you, krzysiekb.  You make the Ubuntu experience even better.

---

### Post by astjohn on 2011-03-10
> **jsevi83 said:**
> [COLOR=Blue]UPDATE: for Ubuntu Maverick 10.10[/COLOR]

- To solve the problems relative to sound, follow this (only for ubuntu maverick 64bit).

1) You need ubuntu kernel 2.6.35-23 or higher. Open Synaptic and update the kernel in case you are using 2.6.35-22. The latest kernel at the moment is 2.6.35-27

2) Run this command on the terminal: 


echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf


....


- To solve the suspend and wireless-led problem, check the following solutions for Ubuntu Lucid 10.04. Alternatively, you can install a package I created which includes the fixes for suspend, wireless led and calculator button. See the attached file. It was created for maverick 64.




I had similar issues with a fresh install on a K52J with Ubuntu 10.10 and kernel 2.6.35-27.

To fix the sound, I did not have to use any patches.  Changing alsa-base.conf did it.  I did, however, install linux-backports-modules-alsa-maverick-generic prior to this when trying an older fix.

Then I applied jsevi83's package for the rest.  Thanks jsevi83!

---

### Post by paologab on 2011-03-16
for the record
asus x52f (lshw report it as k52f, like its mobo) with conexant codec works perfectly with the patch (post #315) either with 2.6.35-27 and 2.6.35-28

this post is like a gold mine, thanks everybody!


> **jsevi83 said:**
> For those of you interested, I just tried the new Ubuntu Natty. Sound problems are gone, as it autodetects internal and external microphone. Webcam upside down is fixed too. Calculator button fixed too.
The only things that needed to be adjusted were the touchpad toggle button and the wireless led. For the rest, everything works out of the box.

Oh, I forgot to test suspend and hibernation. :D

---

### Post by san000 on 2011-03-19
Thank you very much guys. This post made everything work fine in my K52J.

---

### Post by zovalik on 2011-03-20
Asus k52 is sold with for ex. i3 (with Intel GPU) and ATI or Nvidia GPU.
As far as i know Ubuntu have a big problem with hybrid graphic cards.
So here is my question: is there in BIOS option that allow to shout down Intel GPU and use only ATI or Nvidia GPU? I know 

Sorry for my English, i hope you will understand me ;)

---

### Post by UpSignal on 2011-03-20
> **zovalik said:**
> Asus k52 is sold with for ex. i3 (with Intel GPU) and ATI or Nvidia GPU.
As far as i know Ubuntu have a big problem with hybrid graphic cards.
So here is my question: is there in BIOS option that allow to shout down Intel GPU and use only ATI or Nvidia GPU? I know 

Sorry for my English, i hope you will understand me ;)

Not possible. Intel is needed, as is its main graphic card. You only use nvidia when playing high graphics demanding games or apps. But, in ubuntu you can only use intel now.
What you can do is shut down nvidia when using the battery. 

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by zovalik on 2011-03-20
> **UpSignal said:**
> Not possible. Intel is needed, as is its main graphic card. You only use nvidia when playing high graphics demanding games or apps. But, in ubuntu you can only use intel now.
What you can do is shut down nvidia when using the battery. 

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

Are you have K52 series laptop? 
There are some laptops with special option in BIOS that disable Intel GPU. I want to know: Do K52 laptops have this option? 

In ASUS laptops BIOS, it is called "VGA Mode SELECT". But I don't know what specific laptops have this option  :/.

I found that Lenovo Y560 have this option in BIOS.

---

### Post by UpSignal on 2011-03-20
Mine is k52JC,i don't have any option on the bios, and it's updated

---

### Post by zovalik on 2011-03-20
> **UpSignal said:**
> Mine is k52JC,i don't have any option on the bios, and it's updated

Thank you for help. I have only 1 question for you. Do you use Intel GPU on Ubuntu? How with HD video? Is it fine or is it slide-show?

---

### Post by UpSignal on 2011-03-20
> **zovalik said:**
> Thank you for help. I have only 1 question for you. Do you use Intel GPU on Ubuntu? How with HD video? Is it fine or is it slide-show?

Yes, intel works out of the box. no need to install aditional drivers :)

---

### Post by cj6814 on 2011-03-22
> **krzysiekb said:**
> You need to patch the kernel module /lib/modules/2.6.35-27-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko with a file from the attached archive. (Read instructions from the 1st post for more details)
I've seen a post in this thread claiming that it's not necessary to patch after fresh install anymore though noone confirmed this so far. I still need the patch. Please note that this patch is for x86_64 only. Enjoy!!!

krsysiekb, 

thanks again for updating the sound patch for me (26-27).  After going from 2.6.35-27 to 2.6.35-28 (kernel) the sound patch no longer works.  The patch that is posted in post 315 is still for 27.  Can a schmuck like me put together a patch specific to each kernel or is this something best left to the professionals?

Also, would a fresh install on my A52F take care of these issues once and for all (not quite sure if it's been confirmed after reading through the posts)?

Thanks,

---

### Post by krzysiekb on 2011-03-22
> **cj6814 said:**
> After going from 2.6.35-27 to 2.6.35-28 (kernel) the sound patch no longer works.  The patch that is posted in post 315 is still for 27.
Patch for 2.6.35-28 is attached

> **cj6814 said:**
> 
Also, would a fresh install on my A52F take care of these issues once and for all (not quite sure if it's been confirmed after reading through the posts)?
I don't know. I hope that upgrade to 11.04 will solve this sound problem.

---

### Post by cj6814 on 2011-03-24
> **krzysiekb said:**
> Patch for 2.6.35-28 is attached


I don't know. I hope that upgrade to 11.04 will solve this sound problem.

This patch isn't doing it for me this time.  Anyone else have success with the patch using 2.6.35-28?

Thanks

---

### Post by sirEliah on 2011-03-25
I made it work on 2.6.35-28. After installing linux-alsa-driver-modules-2.6.35-28-generic with dependencies it begun working, for the first time since 2.6.35-25 kernel.

---

### Post by krzysiekb on 2011-03-25
> **sirEliah said:**
> I made it work on 2.6.35-28. After installing linux-alsa-driver-modules-2.6.35-28-generic with dependencies it begun working, for the first time since 2.6.35-25 kernel.

Confirmed.

Here is what I did. Steps 1 and 2 are necessary to revert the patched module
[LIST=1]
[*]Remove custom options for snd-hda-intel module
Edit /etc/modprobe.d/alsa-base.conf or /etc/modprobe.d/sound.conf and remove line 
```
options snd-hda-intel model=hp-laptop
```
[*]Restore original kernel (get rid of the patch)
```
sudo aptitude reinstall linux-image-2.6.35-28-generic
```
[*]Install linux-alsa-driver-modules
```

sudo apt-add-repository ppa:ubuntu-audio-dev/ppa
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-2.6.35-28-generic

```
[*]Restart
[/LIST]

---

### Post by 542 on 2011-03-27
Not sure if this is useful to many people yet, but might be in the future. Also, for me this was done on Arch Linux not Ubuntu, but I imagine that it should work for any distro.

On my K52J using kernel 2.6.37 I couldn't get both the microphone working as well as the headphone jack detection. If I added 'options snd-hda-intel model=hp-laptop' the jack detection would work but not my internal mic and if I removed the line vice versa.

In the latest stable kernel from kernel.org ( 2.6.38 ) there seems to be a new 'asus' snd-hda-intel option. I compiled 2.6.38 and added the line to my /etc/modprobe.d/alsa-base.conf file:

options snd-hda-intel model=asus

For me this made everything work nicely. As 11.04 is (I'm guessing) going to have kernel 2.6.38 this might be useful for others.

---

### Post by cj6814 on 2011-03-28
> **krzysiekb said:**
> Confirmed.

Here is what I did. Steps 1 and 2 are necessary to revert the patched module
[LIST=1]
[*]Remove custom options for snd-hda-intel module
Edit /etc/modprobe.d/alsa-base.conf or /etc/modprobe.d/sound.conf and remove line 
```
options snd-hda-intel model=hp-laptop
```
[*]Restore original kernel (get rid of the patch)
```
sudo aptitude reinstall linux-image-2.6.35-28-generic
```
[*]Install linux-alsa-driver-modules
```

sudo apt-add-repository ppa:ubuntu-audio-dev/ppa
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-2.6.35-28-generic

```
[*]Restart
[/LIST]

Thank you krzysiekb and 542.  I followed the steps provided by krzysiekb and the internal mic didn't work.  However, I tried the fix mentioned by 542 and it all appears to be working.

Follow the steps exactly as outlined by krzysiekb then do the following:

Edit /etc/modprobe.d/sound.conf and change  
```
options snd-hda-intel model=thinkpad
```
to
```
options snd-hda-intel model=asus
```

Then reload alsa
```
sudo alsa force-reload
```

This worked for me (A52F - Meerkat - 2.6.35-28 - 64bit).  Thanks to those who showed us what to do.

---

### Post by Eberbachl on 2011-04-02
Sound, including microphone is working beautifully out of the box on 11.04 Alpha3.

...but the webcam fix on page one of this thread no longer works... my image is upside down again.

Arghhh.... :(

Any ideas?

---

### Post by rabideau on 2011-04-02
I am using beta 1 (11.04) and everything seems to work (out of the box!!!), webcam, mic, and most special keys (Fn)--:)  the only one that does not work out of the box is the track pad on-off Fn combo.

---

### Post by UpSignal on 2011-04-09
Its awesome the progress being made. Anyway, i'm out. Just couldn't stand not having nvidia working. I love ubuntu and all...but, i spent some money on this laptop, and right now only windows 7 gives me the full potential of it. I'm not turning my back on linux. Just until nvidia and the optimus technology starts working :)
If you don't care about any game in the world, then intel its cool for compiz and such. But it's really a pain for gaming.
I'm following the news about hybrid graphics on linux. And as soon as they got it working, i'll be back. good luck gentlemen

---

### Post by dj8nw on 2011-04-11
Hey guys,

i've already tried 11.04 - 64 Bit on A52F.
Fn-Shortcuts worked out-of-the-box,
microphone problem was fixed with replacing patched-conexant-driver-kernel-2.6.35-27

but what won't work is webcam.

with lsusb i got:
```

Bus 002 Device 007: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 002 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```That means to me that it doesn't appear at all?!

Does anyone have a fix for that problem?

Bye, Sven

---

### Post by amiller2571 on 2011-04-14
Has anyone made any progress with the Nvidia card yet? It is the only thing stopping me from switching my notebook to Ubuntu :( I use Ubuntu on my desktop and love every minute of it. Even though I messed up my login screen, but it is still usable, I'll fix it when 11.04 is out of beta.

Well I lied, I have a graphics class that requires Photoshop that is stopping me form switching to Ubuntu also. It will be my last graphics class, so the only classes I will have left are programming classes :) which I love.

---

### Post by Yellow Pasque on 2011-04-14
> **amiller2571 said:**
> Has anyone made any progress with the Nvidia card yet?
No, and don't hold your breath...

---

### Post by diegorusso on 2011-04-14
> **dj8nw said:**
> Hey guys,

i've already tried 11.04 - 64 Bit on A52F.
Fn-Shortcuts worked out-of-the-box,
microphone problem was fixed with replacing patched-conexant-driver-kernel-2.6.35-27

but what won't work is webcam.

with lsusb i got:
```

Bus 002 Device 007: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 002 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```That means to me that it doesn't appear at all?!

Does anyone have a fix for that problem?

Bye, Sven

Same problem with 10.10 64bit

---

### Post by evez on 2011-04-16
Hi I have tried your solution:
5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.


Unfortunately it didn't do it for me. The problem with my webcam is only on skype (turned upside down). (I'm using 10.10 on an ASUS K4OIN Series). Any other ideas for the webcam? Cheers

---

### Post by bacchusmarsh on 2011-04-16
hey i worked my way through the list and nothing seems to have been fixed?

worst part is i now have no sound...
Please help!

i returned this error log:

 rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
echo skipping rm -f alsa-kernel/include/version.h
skipping rm -f alsa-kernel/include/version.h
rm -fr .tmp_versions
rm -f Module.symvers
find include/sound -name "*.h" -type l | xargs rm -f
rm -fr include/generated
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.35-28-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-28-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/2.6.35-28-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i686
checking for ISA DMA API... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for usb_endpoint_dir_in and related functions... yes
checking for usb_endpoint_xfer_control... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for fmode_t... yes
checking for hrtimer_get_expires... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.23
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
checking for kernel linux/usb/ch9.h... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for bool... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
(cd include/sound && ln -s ../../alsa-kernel/include/*.h .)
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in include acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hrtimer.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hrtimer.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/sgbuf.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm_native.c:2:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2223: note: this is the location of the previous definition
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/pcm_native.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [compile] Error 2

---

### Post by bacchusmarsh on 2011-04-16
never mind i am just going to have to reinstall, everything is broken now :(

i did the lucid list and probably should have done the maverick one at the top...

---

### Post by karlicos on 2011-04-16
Some news:
I've just installed Ubuntu 11.04 Natty(beta 2), on my K52Jc laptop and:
1) Speakers mute when headphones are plugged in.
2) Both external and internal mic are working fine.
3) Fn+KP_Enter starts calculator, as expeceted.
Unfortunately, webcam image is still upside down, and suspending and hibernating freezes laptop.

---

### Post by jsevi83 on 2011-04-18
The solution for the suspend/hibernation problem is on the first post (the same instructions for lucid/maverick/natty).

About the webcam, I start skype with this command (for ubuntu 64bit):

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by r109chaos on 2011-04-21
I would like to confirm that jsevi83's Suspend fix works on my ASUS UL80j! Thank you and slac-in-the-box!

I found his thread here: [http://www.linuxquestions.org/questions/slackware-14/asus-ul80j-suspend-to-ram-fix-871958/](http://www.linuxquestions.org/questions/slackware-14/asus-ul80j-suspend-to-ram-fix-871958/)

I will also look at the other solutions jsevi83 suggested. Thanks a bunch guys!!! <3

---

### Post by evez on 2011-04-21
Suspend fix works for me too, but webcam still not working properly. Jsevi83's suggestion (sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade) didn't do it for me.. Not sure what to do..

---

### Post by jsevi83 on 2011-04-28
I'm using Natty and almost everything is working perfect (i will update the first post soon). The only problem I have is that the laptop won't shut down or reboot when using the battery (no problem when the ac cable is connected). It shows the usplash screen and freezes there...

Anyone knows a solution?

---

### Post by krzysiekb on 2011-04-29
> **jsevi83 said:**
> The only problem I have is that the laptop won't shut down or reboot when using the battery (no problem when the ac cable is connected).

My upgrade to natty has just finished. Reboot with ac cable disconnected works fine for me. Did you do fresh install or made upgrade?

---

### Post by jsevi83 on 2011-04-29
I updated from an alpha or beta I installed some weeks ago. I guess I will just make a clean install.

---

### Post by UpSignal on 2011-04-30
Can anyone test this?

[http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html](http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html)

some progress there

---

### Post by jsevi83 on 2011-05-02
First post updated for Natty 11.04

---

### Post by astjohn on 2011-05-02
All,

I have recently upgraded to Natty and applied jsevi83's awesome patch.

As far as I can tell, everything is working except for my internal mic.

I removed the alsa-base, pulse-audio, and linux-alsa-driver-modules.  Then I re-installed just the alsa-base and pulse-audio packages after a reboot.

Unforunately, this didn't work.  I would really like to avoid a fresh install.

Any ideas?

[http://i.imgur.com/PDeCz.png](http://imgur.com/PDeCz)

[http://i.imgur.com/0MrZE.png](http://imgur.com/0MrZE)

---

### Post by 542 on 2011-05-02
> **astjohn said:**
> All,

I have recently upgraded to Natty and applied jsevi83's awesome patch.

As far as I can tell, everything is working except for my internal mic.

I removed the alsa-base, pulse-audio, and linux-alsa-driver-modules.  Then I re-installed just the alsa-base and pulse-audio packages after a reboot.

Unforunately, this didn't work.  I would really like to avoid a fresh install.

Any ideas?

[http://i.imgur.com/PDeCz.png](http://imgur.com/PDeCz)

[http://i.imgur.com/0MrZE.png](http://imgur.com/0MrZE)

You could try just leaving all the sound modules/packages as the ubuntu default and adding the line to the end of /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=asus
```

and then:

```
sudo alsa force-reload
```

Worked for me on Arch Linux with 2.6.38 kernel, so worth a shot at least.

---

### Post by perlon on 2011-05-03
I've a different problem with the wireless led: when I resume my laptop after a suspension (stand-by), the led is off. Anyway the wireless connection works correctly. To turn on the led I need to disable the wireless connection and re-enable it.
The solution in the first post solved my problem on maverick, now on natty it doesn't. Any clues?

---

### Post by astjohn on 2011-05-04
> **542 said:**
> You could try just leaving all the sound modules/packages as the ubuntu default and adding the line to the end of /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=asus
```

and then:

```
sudo alsa force-reload
```

Worked for me on Arch Linux with 2.6.38 kernel, so worth a shot at least.

Thanks for your suggestion.  Unfortunately it didn't work.  Removing the line entirely also did not work.  Any chance you could post / pm me your alsa-base.conf so I can compare?

---

### Post by 542 on 2011-05-04
> **astjohn said:**
> Thanks for your suggestion.  Unfortunately it didn't work.  Removing the line entirely also did not work.  Any chance you could post / pm me your alsa-base.conf so I can compare?

Hm, I remember needing that line with the first version of the 2.6.38 kernel to get the microphone working but just removed the line and the headphone muting and the microphone are both working fine, so that line isn't needed any more in my case at least.

I'm running the packaged arch linux kernel version 2.6.38.4 and my lspci looks like:

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc RV710/730
```

I've got an Asus K52J. Not sure if I can be much help now it's working for me with the default setup but let me know if you want any other info.

---

### Post by astjohn on 2011-05-04
> **542 said:**
> .....

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc RV710/730
```

I've got an Asus K52J. Not sure if I can be much help now it's working for me with the default setup but let me know if you want any other info.

Here's my output - also with a K52J.
```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

and

```
$ uname -rv
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011

```

Any chance you could please send me your alsa-base.conf?

---

### Post by jsevi83 on 2011-05-06
I did a clean install of Natty and I don't have an alsa-base.conf file, and sound (including mic) is working perfect. Hope this helps you.


ls /etc/modprobe.d/

blacklist-ath_pci.conf  blacklist.conf  blacklist-firewire.conf  blacklist-framebuffer.conf  blacklist-oss.conf  blacklist-rare-network.conf  blacklist-watchdog.conf  oss-compat.conf


cat /etc/modprobe.d/oss-compat.conf

install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

---

### Post by perlon on 2011-05-06
Any tip for my issue?

---

### Post by sabcio on 2011-05-06
Has anyone tried connecting k52jc to external monitor?

In my case it fails. I get a black screen and only holding the power button for 8 sec helps.

---

### Post by 542 on 2011-05-07
> **astjohn said:**
> Here's my output - also with a K52J.
```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

and

```
$ uname -rv
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011

```

Any chance you could please send me your alsa-base.conf?

Hey, sorry for late reply. Similar to jsevi83, I don't even have an alsa-base.conf anymore.

```
$ ls /etc/modprobe.d/
framebuffer_blacklist.conf  modprobe.conf  usb-load-ehci-first.conf
```

```
$ cat /etc/modprobe.d/*
blacklist aty128fb
blacklist atyfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist kyrofb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist radeonfb
blacklist rivafb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
blacklist udlfb
blacklist uvesafb
blacklist viafb
blacklist vmlfb
blacklist vt8623fb
#
# /etc/modprobe.d/modprobe.conf (for v2.6 kernels)
#
install ohci_hcd /sbin/modprobe ehci_hcd ; /sbin/modprobe --ignore-install ohci_hcd $CMDLINE_OPTS
install uhci_hcd /sbin/modprobe ehci_hcd ; /sbin/modprobe --ignore-install uhci_hcd $CMDLINE_OPTS

```

---

### Post by ePierre on 2011-05-12
Hello there!

I had some issues with 10.10, so I installed 11.04 on my Asus K52.

Now my internal microphone works out of the box, same for the the headphones.

I tried to connect the HDMI to my BenQ TV (1920x1080), but the available resolutions do not include 1920x1080. It only includes the following resolutions:
- 1280x1024
- 1280x768
- 1280x720
- 1024x768
- 800x600
- 640x480
- 720x400

Also, my TV is 60Hz but Ubuntu only allows me to select 50Hz for this monitor.

I'm using the open source drivers, not the fglrx ones.

As for the HDMI sound output, it's extremely strange.

If I select HDMI Output in the Hardware tab from the sound panel, not only I don't get any output sound, but if I try to open any media (video, music), **the playing will go fast forward and I won't hear a thing!**

I checked that, in alsamixer, the S/PDIF was not mute, and here is lspci output:
```
lspci | grep HDMI
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

So two questions:
1. How to activate full HD HDMI output on my TV (if possible avoid using fglrx proprietary drivers)?
2. How can I use my HDMI output for sound?

Thanks in advance!

(I checked the previous replies, but there is no mention of Ubuntu 11.04, so...)

---

### Post by kernelles on 2011-05-13
@jsevi83 Thanks for this fix! I downloaded your .deb package to fix suspend/resume issues in Natty on my Asus K52J, and it worked perfectly, didn't even have to reboot. 

I had filed a bug here, which has been confirmed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754192)

It is low priority so far, as only myself and one other user have come forward. If anyone else has this Suspend/Resume issue with Natty on an Asus K52 laptop, please go to the bug's link above, login in (register if you need to), and click on the green "This bug affects 2 people. Does this bug affect you?" link, near the top. This will help bump it up in the queue, so an official fix will be released sooner.

---

### Post by astjohn on 2011-05-14
*@jsevi83, @542*

Thanks for your help guys.  After trying a few more things, I finally gave up and did a fresh install.

*@kernelles* - I have confirmed your bug.  Cheers.


With jsevi83's fixes stated on the first page, everything works really well!

---

### Post by rabideau on 2011-05-27
I've tried the fix in 366 and still suspend gets hung (more often than not). I'm runnung an Asus k52f 64 bit with Natty 64 bit and Unity. I am running a new kernel 2.6.39-0 generic (perhaps that is the culprit) ...Any other ideas???

---

### Post by krzysiekb on 2011-05-31
Wifi in my A52 slows down dramatically after disconnecting AC cable.  
I found that this issue is related to power mgmt. I guess it does too agressive power saving.
After turning pwr mgmt off the card is working at max speed again. 
```
iwconfig wlan0 power off
```

Is any of you experiencing similar behavior?
Do you know better solution for that?

---

### Post by jsevi83 on 2011-06-01
I solved the same issue with this command:

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

---

### Post by krzysiekb on 2011-06-01
jsevi83, thanks a lot for you reply. I noticed that you already added this solution to the first post too. Thanks!

---

### Post by UpSignal on 2011-06-06
Guys, according to linux hybrid graphics blog:

> Testers needed: intel/nvidia: bumblebee now with 32bit and 64bit support
For all of you with an intel/nvidia hybrid laptop under Linux interested in getting the nvidia card to work and willing to spend a bit of time testing, please have a try at the latest bumblebee release:

sudo apt-get install git
# type password
git clone [https://github.com/MrMEEE/bumblebee.git](https://github.com/MrMEEE/bumblebee.git)
cd bumblebee/
sudo ./install.sh
optirun glxgears
# check the speed and compare to running:
glxgears

If you get stuck at any point, generate a bug report with:
sudo sh ./install-files/bumblebee-bugreport

Create a bugreport on github (URL below) and email [email]mj@casalogic.dk[/email] the
bug report along with the issue number:

[https://github.com/MrMEEE/bumblebee/issues](https://github.com/MrMEEE/bumblebee/issues)

Anyone tested this already on asus k52jc?

---

### Post by paologab on 2011-06-06
hi

did anyone tested the new bioses 214 or 215 released on may? mine is 212 and is working fine ... I wouldn't like to have a new brick

any way to know what are the improvements (the 215 states "Fix: WLAN LED can't work normal")

edit: flashed with 215, works as usual

:P

---

### Post by jactry on 2011-06-06
> **UpSignal said:**
> Guys, according to linux hybrid graphics blog:



Anyone tested this already on asus k52jc?

I did.  Easy to install and works very well on my K52JC.

As a result, TORCS (the 3D racing car game) now runs and looks way better.  The battery last longer too which I appreciate.  I sure will do some other comparisons.

I guess the downside is an increase of system ressources due to a second X server and VirtualGL.  Anyway the author definitely deserves a thumbs up for this major breakthrough and again the video performance improvement is very significant.

---

### Post by jsevi83 on 2011-06-07
paologab, how did you flash the new bios 215? I didn't find any explanation on how to do it.

Edit: OK, I did it. Asus k52 bios contains an utility called EasyFlash (on the advanced tab of the bios) to update itself safely.

---

### Post by carlobycarlo on 2011-06-11
Thank you so much from Sicily.
Ubuntu lucid works great now!

---

### Post by UpSignal on 2011-06-19
> **jactry said:**
> I did.  Easy to install and works very well on my K52JC.

As a result, TORCS (the 3D racing car game) now runs and looks way better.  The battery last longer too which I appreciate.  I sure will do some other comparisons.

I guess the downside is an increase of system ressources due to a second X server and VirtualGL.  Anyway the author definitely deserves a thumbs up for this major breakthrough and again the video performance improvement is very significant.

Yeah, i just got nvidia working too. It's cool. I'm running Kubuntu natty, anyway we just need a way to make "Kwin" to use nvidia for its desktop effects. Intel sucks a bunch doing that job.

---

### Post by Abi79 on 2011-07-09
Hello! I am running into the same wireless led problem on my K52De as DamiRocK here: [http://ubuntuforums.org/showthread.php?p=9576897#post9576897](http://ubuntuforums.org/showthread.php?p=9576897#post9576897)

Fn+F2 is working, but the led is always on.
I ran  cat /sys/class/ieee80211/phy0/rfkill*/state and  cat /sys/devices/platform/asus_laptop/wlan. Both give me an output of 1 when the wireless is enabled, and 0 when it isn't.

I've already PMed DamiRocK, but in the meantime does anyone know of a solution to this? Thanks!

---

### Post by k.mooijman on 2011-07-10
I have a strange problem 
i have both Gnome and KDE installed when running Gnome my system is stable but running KDE it sometimes , when not in use, turns off my screen and locks the system
i can still get to the ssh via wired network but killing xorg duos not release the system.
can someone help please 
   Thanks 
           Kasper

---

### Post by dnj on 2011-07-27
[SIZE=3]Hi - inexperienced newcomer here! :D

If I read this thread correctly will I be right in thinking that 11.04 will work pretty much out of the box on a Asus X52F-EX582V. I was planning on a dual boot system with the pre-installed Windows 7.

I was planning on getting this one:
[http://www.coopelectricalshop.co.uk/products/ProductDetail.asp?ProductCode=ASU-COM-X52F_EX582V-BR](http://www.coopelectricalshop.co.uk/products/ProductDetail.asp?ProductCode=ASU-COM-X52F_EX582V-BR)

Could anyone confirm if this is right please? Any pointers on what I am proposing would be greatly appreciated.

Thanks in advance. :D
[/SIZE]

---

### Post by jsevi83 on 2011-07-27
Yes, it will work out of the box, it is almost the same model. On the first post you can find the problems you will find and their solutions.

---

### Post by paologab on 2011-08-10
hi there

new bios rev. 218
Fix: The system couldn't enter Easy Flash in BIOS Setup menu's "Easy Flash" item.
[http://support.asus.com/download.aspx?SLanguage=en&p=3&s=126&m=X52F&os=&hashedid=SJKDH9D27XPNf4u9](http://support.asus.com/download.aspx?SLanguage=en&p=3&s=126&m=X52F&os=&hashedid=SJKDH9D27XPNf4u9)

I'll try it in a couple of week

---

### Post by LoganDimond on 2011-08-17
The speakers don't mute when the headphones are plugged in and the microphone doesn't seem to work at all. I tried the solution for the sound (in the first post) and got this. I have kernel 2.6.39 and an asus k52f

---

### Post by jsevi83 on 2011-08-20
What version of ubuntu are you using? I think you mixed solutions from older versions. Read again the first post, for ubuntu natty 11.04 sound is working out of the box.

---

### Post by LoganDimond on 2011-08-31
> **jsevi83 said:**
> What version of ubuntu are you using? I think you mixed solutions from older versions. Read again the first post, for ubuntu natty 11.04 sound is working out of the box.

I have natty 11.04 ubuntu studio.

---

### Post by jsevi83 on 2011-09-04
> **LoganDimond said:**
> I have natty 11.04 ubuntu studio.

In Ubuntu Natty 11.04 sound should work out of the box without issues. If it doesn't in your case I'm sorry but I don't know how to help you.

---

### Post by mordan on 2011-09-11
Hello everyone,

this thread has been a life saver for me I want to thank everyone of you guys and especially the creator, THANK YOU!

Also this is my first post here:)

I have a couple of questions if you guys can help or point me to the right direction, and yes i know you've heard this like a million times but I am too a n00b in the linux os, so... ok my first question concerns skype... the solution does not work it keeps showing upside down and the only way i can do the cam chat thing is using the share screen option from skype and opening a different program like cheese, if you have any suggestions ill be happy to try, and also something that i dont know if i should be posting here, but anyway, before going to 11.04 i was on 10.10, i was using xbmc to watch my movies etc, and had a hard time settings up the hdmi of HD5470 giving me the 5.1 sound to my receiver, i had managed that by typing $ aplay -L and finding the plughw option, copied and pasted in the audio settings of xbmc using custom option and it worked, now it does not... any suggestions?

Thanks in advance for any advice and corrections and thanks again for the woderfull work!

Keep up the good work:)

Mordan

---

### Post by rabideau on 2011-09-11
I am now running 11.10 with 0 problems in sound or camera... skype or no skype.  Just a thought.

---

### Post by mordan on 2011-09-11
> **rabideau said:**
> I am now running 11.10 with 0 problems in sound or camera... skype or no skype.  Just a thought.

Thank you for the very quick response my friend:)

So are you talking about 11.10 x64? If yes I'll download right away.

again thank you

Mordan

---

### Post by jsevi83 on 2011-09-12
Ubuntu 11.10 is not stable yet. I am using 11.04 64bit and everything works great. The webcam in skype works as expected with this command:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

If that is not working you could check if the terminal shows any error. Also you can check that lib32v4l-0 is installed.

About the sound: open the sound preferences and select HDMI output in the hardware tab. Then you select 5.1 in totem, vlc, gnome-mplayer, etc. and that's it.

---

### Post by mordan on 2011-09-12
> **jsevi83 said:**
> Ubuntu 11.10 is not stable yet. I am using 11.04 64bit and everything works great. The webcam in skype works as expected with this command:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

If that is not working you could check if the terminal shows any error. Also you can check that lib32v4l-0 is installed.

About the sound: open the sound preferences and select HDMI output in the hardware tab. Then you select 5.1 in totem, vlc, gnome-mplayer, etc. and that's it.

ok when i type the command in the terminal i get this... which i don't really understand:


LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2377): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2377): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2377): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2377): Gtk-WARNING **: Loading IM context type 'ibus' failed


yes the lib32v4l-0 is installed.

also I was about the vlc that settings does not work and on the xbmc still no sound i get a "Failed to initialize the audio device".

Thanks again for your responses, I also want to say that I use the Skype edition 2.2.0.35 Beta... if that helps, I'll try the 11.10 just to see if things are working better.

---

### Post by mordan on 2011-09-13
I cannot install the 11.10 it errors and restarts the laptop.

---

### Post by jsevi83 on 2011-09-13
Is the webcam still upside down when you run skype with this command?

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

What is the problem with vlc? Did you try with totem? If you want sound through HDMI and 5.1, fist choose HDMI as output in ubuntu's sound preferences. Then in your mediaplayer you should select pulseaudio and 5.1.

Maybe you need to install vlc-plugin-pulse

In vlc audio preferences, choose pulseaudio and activate dolby surround (even if it is automatic).

---

### Post by mordan on 2011-09-13
> **jsevi83 said:**
> Is the webcam still upside down when you run skype with this command?

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

What is the problem with vlc? Did you try with totem? If you want sound through HDMI and 5.1, fist choose HDMI as output in ubuntu's sound preferences. Then in your mediaplayer you should select pulseaudio and 5.1.

Maybe you need to install vlc-plugin-pulse

In vlc audio preferences, choose pulseaudio and activate dolby surround (even if it is automatic).

yes its still upside down and the terminal gives me the above errors, also vlc has choppy video wich i cannot fix no matter what option i choose, I installed fedora 15 skype problem is still there, I am really frustrated with this...

---

### Post by jsevi83 on 2011-09-14
Are you using Ubuntu 64bit or 32bit? Do you have an Asus A52 or K52? I'm afraid I don't know how to help you, the solutions suggested work for the rest of us. Does you laptop have an ATI video card? Maybe someone can help you with that, my laptop has an Intel video card and I don't have problems with it.

---

### Post by mordan on 2011-09-15
> **jsevi83 said:**
> Are you using Ubuntu 64bit or 32bit? Do you have an Asus A52 or K52? I'm afraid I don't know how to help you, the solutions suggested work for the rest of us. Does you laptop have an ATI video card? Maybe someone can help you with that, my laptop has an Intel video card and I don't have problems with it.

Hello again and sorry for the delayed answer but I'm working a crazy amount of hours... so I got an A52J with the following specs:

CPU: i3 350M
RAM: 4GB
GPU: ATI 5470 1GB
HDD: 500GB

Ubuntu distros I've tried are all 64 bit 10.4 10.10 11.04 11.10 and Fedora 15 (wich i guess is irrelevant but it has the same issues)

thanks again for all your answers I really appreciate any help I can get.

---

### Post by paologab on 2011-09-25
> **mordan said:**
> I cannot install the 11.10 it errors and restarts the laptop.

hi did you try before with the live-cd? was it working nice?

I`m writing from the 64bit beta2 iso mounted w/grub with wifi connection and all stuff *mic, wbcam, audio etc) seems working fine

the same was with beta 1

Did you find anything in the release notes ?

just to let us know too before install ;)

---

### Post by rabideau on 2011-09-25
I have been working for at least a month on 11.10 with few hardware related problems.  A couple special Fn keys don't work but that's about it.

---

### Post by rabideau on 2011-10-05
Looks like the Skype webcam uspide down image problem and dead wireless after suspend problems are now back on the scene with 11.10.

Skype upside down video fixed via (terminal commands): 
&#8226; sudo mv /usr/bin/skype /usr/bin/skype.real 
&#8226; sudo gedit /usr/bin/skype

Enter the following code into the gedit file:
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

Save the file and close gedit.

Then enter the following command in terminal:
sudo chmod +x /usr/bin/skype

restart skype

Now you can open skype from everywhere and video will be OK!

As for the suspend problem, I used the following:

ath9k Network Fix (from suspend)
Solved by creating a custom script inside /etc/pm/sleep.d with the name ath.sh.
chmod +x

This is the version I use now, other is buggy, hope this helps everyone with an ASUS laptop and use suspend:

#!/bin/sh

case "$1" in
    hibernate|suspend)
        nmcli nm sleep true

        rmmod ath9k
        ;;
    thaw|resume)
        modprobe ath9k

        nmcli nm sleep false
        ;;
    *) exit $NA
        ;;
esac

Save the file and exit gedit.

---

### Post by tpsvca on 2011-10-11
I'm just wondering:
9.10, 10.04, 10.10, 11.04 and finaly 11.10 almost the same probs with the asus k52/52
skype camera upside down, (with every edition)
problems with wi-fi (slow down network on 9.10 and 11.10),
problems with sound, (jack not working 10.04)
problems with fn keys, (with every edition)
problems with suspend/hibernate (with every edition)
and finaly problems with instalation: 11.10...
sad... do i need to change my laptop or OS? there is the question :)

---

### Post by UpSignal on 2011-10-13
> **tpsvca said:**
> I'm just wondering:
9.10, 10.04, 10.10, 11.04 and finaly 11.10 almost the same probs with the asus k52/52
skype camera upside down, (with every edition)
problems with wi-fi (slow down network on 9.10 and 11.10),
problems with sound, (jack not working 10.04)
problems with fn keys, (with every edition)
problems with suspend/hibernate (with every edition)
and finaly problems with instalation: 11.10...
sad... do i need to change my laptop or OS? there is the question :)

with windows 7 you get the max performance out of your laptop. the question you should ask yourself is: " do i love linux enough to give away some of my laptop functions? "

---

### Post by arukaddp on 2011-10-14
Hi all,

Just curious, did anyone install the newly released 11.10?

If so, any feedback would be much appreciated!

Alex

---

### Post by perlon on 2011-10-15
I upgraded from 11.04 64-bit to 11.10 64-bit yesterday, the issues or disappointing things I've experienced so far are the following:

Issues:
- webcam on Firefox doesn't work anymore. I installed from Software Centre flash player 11 (so 64-bit). Now when I go on cam sites (eg. ubiqq.com) the popup asking for cam access permissions is showing up, but it doesn't work and I can't choose any option.
- compiz seems slow: the flickering windows feature is activated but works only after a few number of times shaking of a window.
- I'm not sure, but backlight screen and volume settings are not saved when you shutdown the computer.
- System monitor closes slowly and sometimes hangs up. 

Disappointing things:
- I can't calibre the colors of my laptop screen nor the webcam from system settings-> color. (but is not necessary)
- Installing Openjdk JDK 7 installs also the 6th version... is it normal?
- why the hell I can't choose the startup application anymore? it shows up only ubuntu one... 
- I can't figure out anymore how to set some personal wallpapers changing with time.
- this is from 11.04: Rhythmbox isn't installed but on dash it's still showed with a white icon. How to remove it?

---

### Post by jsevi83 on 2011-10-15
First post updated with instructions for Ubuntu Oneiric 11.10. Fixes are easy and fast to apply, I'm sure in Windows you will have some different issues more time consuming (for those of you complaining about issues not even present in Ubuntu).

---

### Post by tpsvca on 2011-10-15
> **UpSignal said:**
> with windows 7 you get the max performance out of your laptop. the question you should ask yourself is: " do i love linux enough to give away some of my laptop functions? "

problems solved - still friend with ubuntu :D
problem was in my usb flashcard where i had instaled ubuntu 4 instalation. ;)
thanks jasevi83 4 .deb package that solved all my probs(suspend is working on the fly, but still have probs with hipernating).

---

### Post by jsevi83 on 2011-10-15
Sorry but I cannot test hibernation. I never use it so I don't have a swap partition. Maybe someone else can help with that.

---

### Post by jsevi83 on 2011-10-15
There is a bug report for the three finger tap issue here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/873482](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/873482)


I added a startup application with the following commands to adjust some touchpad settings (maybe it helps someone):

xinput set-int-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 8 0 0 0 0 1 2 3

synclient SingleTapTimeout=300; synclient MaxDoubleTapTime=300; synclient MaxTapTime=300; synclient FingerLow=10; synclient FingerHigh=15

synclient PalmDetect=1; synclient PalmMinWidth=5; synclient PalmMinZ=150

---

### Post by perlon on 2011-10-17
> **perlon said:**
> I upgraded from 11.04 64-bit to 11.10 64-bit yesterday, the issues or disappointing things I've experienced so far are the following:

Issues:
- webcam on Firefox doesn't work anymore. I installed from Software Centre flash player 11 (so 64-bit). Now when I go on cam sites (eg. ubiqq.com) the popup asking for cam access permissions is showing up, but it doesn't work and I can't choose any option.
- compiz seems slow: the flickering windows feature is activated but works only after a few number of times shaking of a window.
- I'm not sure, but backlight screen and volume settings are not saved when you shutdown the computer.
- System monitor closes slowly and sometimes hangs up. 

Disappointing things:
- I can't calibre the colors of my laptop screen nor the webcam from system settings-> color. (but is not necessary)
- Installing Openjdk JDK 7 installs also the 6th version... is it normal?
- why the hell I can't choose the startup application anymore? it shows up only ubuntu one... 
- I can't figure out anymore how to set some personal wallpapers changing with time.
- this is from 11.04: Rhythmbox isn't installed but on dash it's still showed with a white icon. How to remove it?

The second issue is magically disappeared, the third one is confirmed.
Any help?

---

### Post by jsevi83 on 2011-10-17
perlon, I can confirm some of the issues:

- Screen brightness is not saved.
- I cannot apply the color profiles (icm files) taken from Splendid utility (from Windows, you can download them from Asus). Is it just me?
- Gnome system monitor closes slowly (but doesn't hang up).

About the startup applications, check this:

[http://ubuntuforums.org/showpost.php?p=11341040&postcount=2](http://ubuntuforums.org/showpost.php?p=11341040&postcount=2)

---

### Post by perlon on 2011-10-18
Thanks jsevi83 for that fix, it works.
Now the first issues I'd like to solve are the webcam in FF (but I contacted adobe for this) and the screen brightness and audio state that are not saved.

---

### Post by jsevi83 on 2011-10-18
Did you install adobe-flash-properties-gtk? Maybe you need it to configure something...  You could try this on the terminal:

sudo apt-get install adobe-flash-properties-gtk

---

### Post by perlon on 2011-10-18
No, but I saw those settings are the same of the online configuration tool, so I don't need it.


Btw, did anyone try this?
If it works properly on our Asus, it solves the kernel 3.0 battery consumption .

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

### Post by jsevi83 on 2011-10-19
I read about new kernels having an issue with battery consumption, but I didn't experience it with Ubuntu 11.04 or 11.10.


Update: after reading the link, it looks like adding i915.i915_enable_rc6=1 to the grub options reduces battery usage when using Unity and video playback. For games it increases the battery usage, but also increases the frames per second. I will test it when I have some time. (Just in case, this is only for Intel GPU).

---

### Post by jsevi83 on 2011-10-21
For now we can solve the three finger tap issue with the instructions here:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

---

### Post by deadvirus on 2011-10-22
Thanks for this thread guys! :D 

I have a K52Jc with 4GB of RAM but the system monitor only shows 3.7GB of RAM. free -m also only shows that amount. 

I'm using the 64bit version of Oneiric. In the 32bit PAE version it also showed 3.7GB.

Any ideas?

---

### Post by arukaddp on 2011-10-23
> **deadvirus said:**
> Thanks for this thread guys! :D 

I have a K52Jc with 4GB of RAM but the system monitor only shows 3.7GB of RAM. free -m also only shows that amount. 

I'm using the 64bit version of Oneiric. In the 32bit PAE version it also showed 3.7GB.

Any ideas?
I believe you need to use the 64bit version so that all 4GB would be recognised.

---

### Post by arukaddp on 2011-10-23
After testing the 11.10 LiveCD I confirm that most of the problems are gone. The webcam which was the most annoying is gone from all applications except Skype. 
I don't have the courage to do an update, but I will probably do a fresh install... I have no faith in what I, as a noob, have done to my existing install :D

(K52F with Intel graphics board and 3GB of RAM)

---

### Post by jsevi83 on 2011-10-23
If your video card has 256mb of shared memory, it means it takes it from the 4gb of ram. So you have 3.7gb of ram left.

---

### Post by deadvirus on 2011-10-25
> **arukaddp said:**
> I believe you need to use the 64bit version so that all 4GB would be recognised.

I'm already using the 64bit version.

> **jsevi83 said:**
> If your video card has 256mb of shared memory, it means it takes it from the 4gb of ram. So you have 3.7gb of ram left.

Oh right!!! I forgot that integrated video cards used shared memory... duh to me!

---

### Post by sabcio on 2011-10-26
Hi, anyone install gnome-shell?

When I try gnome-shell --replace I get the following error
```
Xlib:  extension "GLX" missing on display ":0.0".

(gnome-shell:6708): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.

```

It did work with LiveCD.
Asus K52JC fresh Ubuntu 11.10 install.

---

### Post by Loocio on 2011-10-29
Hi to everyone

i'm finishing solving some problems i have with ubuntu 10.04.3LTS 64b freshly installed on a new [ASUS X52F-EX1197V](http://www.shoppydoo.it/prezzo-notebook-asus_x52f_ex1197v.html), using all the solutions proposed on this thread

i made thirst a “try-installation” to test the OS aside the pre-installed windows 7, then try to solve the problems; some things go right (points 4, 6 & the second part of 8), some others i don't care by now (points 7,  9 & the first part of 8), but i can't fix points 1+2+3 and point 5!
anyway, i decided to completely remove ******* windows and keep only ubuntu; i've re-done the procedurs to solve the points above, but before re-taking useless actions on points 1,2,3 and 5, i want to ask some advices


1) SOUND (points 1 and 3, can't check the hdmi exit not having the cable): if i follow the instructions, i solve the problems 1 and 2, BUT then it's the internal microphone that stops working, that for me it's worst... and that's why i haven't re-done the procedure on this current re-installation of ubuntu: now i have the internal micro working but not the external -which i don't care- and speakers do not mute when headphones are plugged in!
It's possible to solve only problem 1 -the headphones- without “touching” the mics? Or, how can i fix the internal mic problem that comes out following the instructions?
On the “try-installation” I've already checked levels with alsamixer and i think that wasn't the problem...

below you can see sound card and kernel in use on this new installation 

```


lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

uname -r
2.6.32-34-generic

```

and i copy&paste the content of the file /etc/modprobe.d/alsa-base.conf

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```


and that's how i see the channels on alsamixer (again, on this un-modified installation)

[[IMG]http://img267.imageshack.us/img267/4869/schermatau.jpg[/img]](http://imageshack.us/photo/my-images/267/schermatau.jpg/)

some ideas?



2) WEBCAM (point 5) whit this procedure nothing changes... [here](http://wiki.ubuntu-it.org/Hardware/Notebook/AsusP52F) i found this advice:

> Webcam

The integrated webcam returns images flipped vertically. Install the package [xserver-xorg-video-v4l](apt://xserver-xorg-video-v4l)to solve the problem.

do you think it's a valuable solution?



Really thanks to everyone can help me, and for now thanks to jsevi83 for all the solutions and this thread, it really helps me!
Sorry for my bad english, and, i've to precise that i don't want to skip to a newer ubuntu system

bye!

lucio

---

### Post by Grasber on 2011-10-29
OMG! Suspend problem solved for me! Thanks!!!!! You're awesome!! :D :D :D

---

### Post by paceco on 2011-10-31
ASUS K52J: iT cannot return from sleep state to live session : blank black screen: I had ubuntu 11.04, but these problems were not present (asus k52.deb) : Now I have 11.10 and i have installed asus-k52_2.0.deb. Hibernation works properly. What can I do I.m quite new on ubuntu linux: Thanks advance and kind regards!

---

### Post by sabcio on 2011-11-03
Hi,
do you have problems with numeric keypad and ubuntu 11.10? Mine doesnt work, either the built in one nor on a external keyboard.

---

### Post by paologab on 2011-11-04
hi, thnk very much for the little deb!

I'm now with 10.10 64 bit & gnome shell 
to get it working I had to remove all unity related items

now I cannot use the double tapping on the touch pad to simulate the left click of the mouse, even if I enabled it in the mouse config item (mouse click with touchpad)

Is not a so big problem, but I use to do it so each time I try ...

any clou?

thanks paolo

---

### Post by jsevi83 on 2011-11-05
Maybe you need to try some different options with synclient. You can list your configuration running "synclient -l" in a terminal. For the double tap I use:

synclient MaxDoubleTapTime=300

If that works for you, you can create a script with it and add it to the startup applications.

---

### Post by paologab on 2011-11-05
> **jsevi83 said:**
> Maybe you need to try some different options with synclient. You can list your configuration running "synclient -l" in a terminal. For the double tap I use:

synclient MaxDoubleTapTime=300

If that works for you, you can create a script with it and add it to the startup applications.

done with 250

perfect, thank you very much jsevi!:popcorn:

---

### Post by Loocio on 2011-11-08
sorry, but no one reply because my post is too long?

> **Loocio said:**
> Hi to everyone

i'm finishing solving some problems i have with ubuntu 10.04.3LTS 64b freshly installed on a new [ASUS X52F-EX1197V](http://www.shoppydoo.it/prezzo-notebook-asus_x52f_ex1197v.html), using all the solutions proposed on this thread

i made thirst a “try-installation” to test the OS aside the pre-installed windows 7, then try to solve the problems; some things go right (points 4, 6 & the second part of 8), some others i don't care by now (points 7,  9 & the first part of 8), but i can't fix points 1+2+3 and point 5!
anyway, i decided to completely remove ******* windows and keep only ubuntu; i've re-done the procedurs to solve the points above, but before re-taking useless actions on points 1,2,3 and 5, i want to ask some advices


1) SOUND (points 1 and 3, can't check the hdmi exit not having the cable): if i follow the instructions, i solve the problems 1 and 2, BUT then it's the internal microphone that stops working, that for me it's worst... and that's why i haven't re-done the procedure on this current re-installation of ubuntu: now i have the internal micro working but not the external -which i don't care- and speakers do not mute when headphones are plugged in!
It's possible to solve only problem 1 -the headphones- without “touching” the mics? Or, how can i fix the internal mic problem that comes out following the instructions?
On the “try-installation” I've already checked levels with alsamixer and i think that wasn't the problem...

below you can see sound card and kernel in use on this new installation 

```


lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

uname -r
2.6.32-34-generic

```

and i copy&paste the content of the file /etc/modprobe.d/alsa-base.conf

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```


and that's how i see the channels on alsamixer (again, on this un-modified installation)

[[IMG]http://img267.imageshack.us/img267/4869/schermatau.jpg[/img]](http://imageshack.us/photo/my-images/267/schermatau.jpg/)

some ideas?



2) WEBCAM (point 5) whit this procedure nothing changes... [here](http://wiki.ubuntu-it.org/Hardware/Notebook/AsusP52F) i found this advice:



do you think it's a valuable solution?



Really thanks to everyone can help me, and for now thanks to jsevi83 for all the solutions and this thread, it really helps me!
Sorry for my bad english, and, i've to precise that i don't want to skip to a newer ubuntu system

bye!

lucio

---

### Post by jsevi83 on 2011-11-08
In the screenshot of Alsamixer I see "Mic" and "Mic 1", being "Mic" selected (you can see "CATTURA"). Did you try selecting "Mic 1" (with spacebar?)

The solution for the webcam should work, with what programs do you have issues? There were issues only with Skype, which has to be started like this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by Loocio on 2011-11-09
@ jsevi83

ok for the webcam, thank you, i just thought that the problem with skype can be solved forever, but it's ok to start it from the terminal

about 1+2+3 points (audio and mic problems), the screenshot of alsamixer is BEFORE doing the solution you suggested in the first post, and the situation is 
- AUDIO speakers OK, but don't mute when i plug in the headphones
- MIC internal is OK, external doesn't work (maybe because i've not selected CATTURA) but i don't care

if i follow your instructions (of the first post of this thread) then the situation becomes:
- AUDIO speakers everything's ok (they mute when i plug in the headphones)
- MIC internal DOESN'T WORK at all (i'm sorry not having the alsamixer screenshot of this situation, because was on a previous installation)

so, the questions are :
- It's possible to solve only problem 1 -the headphones- without “touching” the mic? 
- Or, how can i fix the internal mic problem that comes out following the instructions? if you can "accompany" and help me, i will retry following your instructions and then we can manage to solve the mic problem ;D

thank you for the patience and sorry for my bad english

---

### Post by jsevi83 on 2011-11-09
I reinstall ubuntu every six months, so I don't use Lucid for a long time. In the first 15 pages you will find the solutions we tried, but I think to remember that installing alsa-driver-linuxant was the best option. Maybe you have to choose the internal microphone from alsamixer after installing alsa-driver-linuxant and rebooting.

---

### Post by Loocio on 2011-11-10
ok, i'm from a very weak internet connection, but i will try as soon as i can (maybe some days...ahi hai)

only another question before re-trying, if we can't manage to get the mic working after installing alsa-driver-linuxant, it's possible to "come back" to previous configuration uninstalling alsa-driver-linuxant?

---

### Post by perlon on 2011-11-10
Fixes for screen brightness and system sound not saved on every pc startup.

**Brightness fix:**

Edit rc.local file:

```
sudo gedit /etc/rc.local
```Before the line "#exit 0" , add this string:

```
echo 0 > /sys/class/backlight/acpi_video0/brightness
```and remove the # from the line "#exit 0". 

Now, you can change the value 0 in the value you want (from 0 to 10) to adjust the brightness level you prefer.
Example:
```
echo 6 > /sys/class/backlight/acpi_video0/brightness
```[B]

System sound fix:[/B]
Create a new script file with this code in it:
```
#!/bin/bash
amixer sset 'Master' 70% unmute &> /dev/null
```Change the 'Master' value with the name of your speaker (check it with alsamixer) and adjust the 70% audio level as you desire.
Save the script in a folder and add that script to the startup applications.

---

### Post by bacchusmarsh on 2011-12-04
Webcam problem 11.10:
I do this and get this

maxine@maxine-K52F:~$ locate v4l1compat.so
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
maxine@maxine-K52F:~$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compqt.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compqt.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(skype.real:3423): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype.real:3423): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype.real:3423): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype.real:3423): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

**please help me this is driving me crazy.** i have tried absolutley every suggestion to get the webcam flipped in skype but nothing is working.

PS i had it working in 10.10 but could not tell you which method i used now...

---

### Post by jsevi83 on 2011-12-04
I have Ubuntu 11.10 64bit and skype is working properly (camera not upside down) with this command:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by bacchusmarsh on 2011-12-04
thanks.
i took apart my screen and turned the webcam over !;) I noticed it was upside down in windows too, so i figured it was just mounted upside down in the k52f.

all hail the screw driver

---

### Post by jsevi83 on 2011-12-04
wow, that's one drastic solution :D

Because there are many laptop models with the webcam upside down (on porpouse, no accident), there is a linux library with a list of those models to invert the image from the driver. Some people have problems using the webcam with 32bit applications (like skype) on 64bit systems, but the webcam is working properly on other 64bit applications. I guess that solution works for you if you are only using the webcam with Skype or Google Talk Plugin, but the image will be upside down for other applications, like Cheese or Pidgin...

---

### Post by arukaddp on 2011-12-05
I just installed 11.10 and almost everything is honky-dory, no major issues. This, until I removed the AC power from the laptop and noticed that the automatic dimming of the screen is not working... does anyone else have this issue?

---

### Post by jsevi83 on 2011-12-07
It is working ok in my laptop. You should check dconf-editor > org > gnome > settings-daemon > plugins > power. There you can find idle-brightness, iddle-dim-time, iddle-dim-battery, etc.

---

### Post by arukaddp on 2011-12-07
> **jsevi83 said:**
> It is working ok in my laptop. You should check dconf-editor > org > gnome > settings-daemon > plugins > power. There you can find idle-brightness, iddle-dim-time, iddle-dim-battery, etc.

Hi jsevi83,

The thing is that in dconf there is no setting for something like 'dim-battery'. My issue is not with idle, as after idling for a while the screen will dim, but with dimming when removing the AC adapter. It was working fine in 11.04. Some board discussions suggest that it is a bug.

On another note, the backlight settings in the GUI are almost non-existent. Hope this will be fixed until 12.04.

---

### Post by jsevi83 on 2011-12-08
I think in gnome2 it was possible to set the default brightness for ac mode and battery separately, so when removing the ac cable you could see a difference. In gnome3 this options are not there anymore, in fact you cannot set the default brightness from dconf-editor at all.

---

### Post by Loocio on 2012-01-18
hi, i'm back with audio problems (points 1 and 3) on ubuntu 10.04 LTS 64b ;D

i've installed new alsa drivers [http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip)

now the speakers mute when headphones are plugged in, BUT the internal mic doesn't work...(as with old driver version...)

file /etc/modprobe.d/alsa-base.conf :

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```

alsamixer: 

[[IMG]http://img406.imageshack.us/img406/6770/alsa1.jpg[/IMG]](http://imageshack.us/photo/my-images/406/alsa1.jpg/)

[[IMG]http://img688.imageshack.us/img688/958/alsa2.jpg[/IMG]](http://imageshack.us/photo/my-images/688/alsa2.jpg/)

[[IMG]http://img641.imageshack.us/img641/2001/alsa3.jpg[/IMG]](http://imageshack.us/photo/my-images/641/alsa3.jpg/)

ideas?

---

### Post by jsevi83 on 2012-01-18
Did you try changing the input source? It's a long time since I had 10.04 installed, so I don't remember. Check if there is an answer in the pages of this thread.

---

### Post by Loocio on 2012-01-20
@jsevi83 so many thanks, solved with this post

> **tangato said:**
> well, after playing a lot, I can change from internal to external mic, using alsamixer via terminal. Looks that there are some aspects that gnome-alsamixer doesn't affect, or doesn't save.
Right now, for the internal mic, I have to select PortB Jack > Mic 80pc via alsamixer, and when I plug in a mic, it switches automatically.

And yes, when I unplug it, the internal is deactivated, so I have to change in alsamixer Input source> Mic B. Everything works again.

Be shure of opening sound preferences or something to monitoring the signal.

I have installed the conexant driver, runing kernel 2.6.34 under lucid.

now the only problem is hdmi, but i suppose the solution it's something similar...i will try when i'll have an hdmi cable available

this is the best ubuntu-thread ever!

---

### Post by jsevi83 on 2012-01-20
For HDMI open the sound preferences and in the second tab (hardware) you can choose Digital Stereo HDMI Output.

---

### Post by UpSignal on 2012-01-29
Guys, just for you to know, Nvidia is already working on our laptop, just check this out: [http://wiki.bumblebee-project.org/FAQ](http://wiki.bumblebee-project.org/FAQ)
working 100%, just tried playing world of warcraft with nvidia on.

Btw, i moved to LinuxMint, since ubuntu is forcing users to use unity and it's looking like windows vista. no unity here lagging the system, actually i get better FPS on mint than i did on ubuntu.
good luck guys

---

### Post by arukaddp on 2012-02-01
Hello everyone, 

I seem to have developed a new issue, but I don't know yet if this is a laptop specific or general problem. 

I remember that recently under 11.10 there was a X update, or something similar... since then when my screen tries to turn off (it's set to turn off after 30 minutes) during the dimming-to-off process the screen flickers, something like white flashes across the screen... and I can't really find similar issues on google.

Other people have observed this issue?

---

### Post by jsevi83 on 2012-02-05
I don't have that flicker issue, maybe it's related to the graphic card. I have an integrated Intel card, if you have ATI maybe there is some update for it...

---

### Post by arukaddp on 2012-02-05
> **jsevi83 said:**
> I don't have that flicker issue, maybe it's related to the graphic card. I have an integrated Intel card, if you have ATI maybe there is some update for it...

I am also on Intel... After I took a closer look, the issue seems to be manifesting after waking up from suspend mode.

---

### Post by jfever311 on 2012-02-09
nevermind.................

---

### Post by henged on 2012-03-08
i still seem to be having problems with the 'palm detection' 
i running kubuntu on the k52f and the touchpad is still hyper sensitive.

Anyone with any guides to settings or something i've missed?
cheers

---

### Post by jsevi83 on 2012-03-09
In system settings > mouse you can set the sensibility of the touchpad. About palm detection, you can use synclient to set the touchpad parameters, and gsettings to make them load on every reboot. Create a text file called "touchpad-settings.sh" in your user folder, paste inside the following three lines and save it:

synclient PalmDetect=1
synclient PalmMinWidth=5
synclient PalmMinZ=150


Then paste in a terminal the following:

chmod +x touchpad-settings.sh
gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command /home/`whoami`/touchpad-settings

---

### Post by henged on 2012-03-13
> **jsevi83 said:**
> In system settings > mouse you can set the sensibility of the touchpad. About palm detection, you can use synclient to set the touchpad parameters, and gsettings to make them load on every reboot. Create a text file called "touchpad-settings.sh" in your user folder, paste inside the following three lines and save it:

synclient PalmDetect=1
synclient PalmMinWidth=5
synclient PalmMinZ=150


Then paste in a terminal the following:

chmod +x touchpad-settings.sh
gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command /home/`whoami`/touchpad-settings

cheers, i'll give it a go.

---

### Post by henged on 2012-03-15
> **jsevi83 said:**
> In system settings > mouse you can set the sensibility of the touchpad. About palm detection, you can use synclient to set the touchpad parameters, and gsettings to make them load on every reboot. Create a text file called "touchpad-settings.sh" in your user folder, paste inside the following three lines and save it:

synclient PalmDetect=1
synclient PalmMinWidth=5
synclient PalmMinZ=150


Then paste in a terminal the following:

chmod +x touchpad-settings.sh
gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command /home/`whoami`/touchpad-settings


Actually, before i do give it a go, i have a question:
i notice in your instructions that i'm essentially going to use the 'gnome.settings-daemon'. I'm rather inexperienced in terms of linux (as you may have guessed...) and so considering i'm using kde/kubuntu, do these instructions to use gnome.settings still apply?
Many thanks for the continued help.

---

### Post by jsevi83 on 2012-03-15
I think so, maybe someone can confirm it. Anyway, you can try the three synclient commands in a terminal, if it works then follow the rest of the process. It's very easy to undo in case it doesn't work.

---

### Post by jsevi83 on 2012-04-24
Updated instructions for Ubuntu Precise Pangolin 12.04

---

### Post by henged on 2012-04-27
> **jsevi83 said:**
> Updated instructions for Ubuntu Precise Pangolin 12.04
just updated my kubuntu to precise, thanks as ever for the .deb.
Much appreciated:KS

---

### Post by raulmonda on 2012-05-01
Im using Ubuntu 11.10 and i installed Skype. The video is upside down. i tried to launch it from console and i got the following ERROR:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored
```.

Im new in Ubuntu, former windows user, and i dont know how to fix this problem.
Any help will be higly appreciated.

---

### Post by 542 on 2012-05-01
> **raulmonda said:**
> Im using Ubuntu 11.10 and i installed Skype. The video is upside down. i tried to launch it from console and i got the following ERROR:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored
```.

Im new in Ubuntu, former windows user, and i dont know how to fix this problem.
Any help will be higly appreciated.

Hi raulmonda,

Can you please try the following:

Check if the v4l1compat.so file exists:
```
ls /usr/lib32/libv4l/v4l1compat.so
```

If the file is missing, it is either that the needed package isn't installed or that it is located in a different place.

These are the steps for 12.04, I think they're the same for 11.10:

```
sudo apt-get install libv4l-0:i386
```

And then run with:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by cj6814 on 2012-05-03
Just upgraded from 10.10 -> 11.04 -> 11.11 -> 12.04.  When I hit 12.04 my touchpad quit working (Asus A52F).

During upgrade I saved a copy of asus-touchpad.sh (/etc/acpi/asus-touchpad.sh) that I had originally modified to work with 10.10 as I was warned that it would be replaced.  Since the touchpad wasn't working in 12.04 I reverted to the saved file but no luck.

1) anyone have this issue? and if so what did you do to solve it.
2) being in a hurry I didn't save a copy of the asus-touchpad.sh that was generated with the upgrade.  Where can I get that file?

Thanks for any help.

---

### Post by jsevi83 on 2012-05-03
All features of the touchpad are working out of the box in Ubuntu 12.04, so you don't need /etc/acpi/asus-touchpad.sh. If you upgraded from previous versions of Ubuntu, the changes you made to make the touchpad work properly may be causing some problems. I think you have two options, one is to undo the changes you made in previous versions, the other (the one I would do) is a clean install. If you followed the instructions on this thread when using previous versions of Ubuntu, it should be easy to undo any changes related to the touchpad.

---

### Post by amaroq74 on 2012-05-04
> **cj6814 said:**
> 

1) anyone have this issue? and if so what did you do to solve it.


The problem in my case was the line:
options psmouse force_elantech=1

in 

modprobe.d/psmouse.conf

---

### Post by briguy on 2012-05-16
> **542 said:**
> Hi raulmonda,

Can you please try the following:

Check if the v4l1compat.so file exists:
```
ls /usr/lib32/libv4l/v4l1compat.so
```

If the file is missing, it is either that the needed package isn't installed or that it is located in a different place.

These are the steps for 12.04, I think they're the same for 11.10:

```
sudo apt-get install libv4l-0:i386
```

And then run with:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

I'm having the same issue after upgrading my laptop to 12.04.  I have the files:

```
locate v4l1compat.so
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
```

but using LD_PRELOAD with either of them I get the same message:


```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

---

### Post by jsevi83 on 2012-05-17
I also get that error message, but the webcam is not upside down anymore.

---

### Post by PS93S on 2012-05-23
> **briguy said:**
> I'm having the same issue after upgrading my laptop to 12.04.  I have the files:

```
locate v4l1compat.so
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
```

but using LD_PRELOAD with either of them I get the same message:


```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Hi everybody!

I got the same error, but also:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(skype.real:3182): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(skype.real:3182): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(skype.real:3182): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(skype.real:3182): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

```

the video is stil upsidedown.

Thanks for your help.

---

### Post by jsevi83 on 2012-05-28
I have no idea why it is not working for you. Are you using ubuntu 64bit? All I can think of is using some application to flip vertically the image. You can try gtk-v4l, download and install from here:

[https://launchpad.net/~libv4l/+archive/ppa/+sourcepub/1158608/+listing-archive-extra](https://launchpad.net/~libv4l/+archive/ppa/+sourcepub/1158608/+listing-archive-extra)

You will have to use it after every reboot, your settings won't be kept.

---

### Post by firefox_user2 on 2012-06-02
jsevj83.....Thank you.

I have an Asus laptop u52F that had a suspend issue.
I applied the fix you posted using the automated link.
After the installation was complete, I closed the laptop lid and it suspended.
After a couple of minutes, I opened the lid, nothing happened until I hit the enter key and then the hard drive kicked in, the system reappeared and everything seemed to work OK.

Many beans to you!!:popcorn:

---

### Post by An6r3w on 2012-06-15
Hello

Among new users of Linux i tried to get rid of windows several times but I always hit a brick wall and couldn't find a fix for my problem so I got back to windows. My problem is that I have Ubuntu 12.04 freshly updated tried the ATI driver direct download or the one given by ubuntu update and software center. Got Diablo 2 to work but Halo or NFS didn't get along with my video card. Any suggestions, roll back to earlier Ubuntu, older versions of the driver?? Linux is working fine movies playing 3D is an issue I think.

---

### Post by An6r3w on 2012-06-15
By the way thanks for the w-lan led solution worked from the first try :)

---

### Post by UpSignal on 2012-07-02
> **An6r3w said:**
> Hello

Among new users of Linux i tried to get rid of windows several times but I always hit a brick wall and couldn't find a fix for my problem so I got back to windows. My problem is that I have Ubuntu 12.04 freshly updated tried the ATI driver direct download or the one given by ubuntu update and software center. Got Diablo 2 to work but Halo or NFS didn't get along with my video card. Any suggestions, roll back to earlier Ubuntu, older versions of the driver?? Linux is working fine movies playing 3D is an issue I think.

no matter what "they say" .... linux sucks at gaming, and probably will always suck.
you know, i was like you....always coming again to windows. Tried dozens of times and always coming back. until i quit playing warcraft and whatever.
These simple steps:

1 - Quit gaming
2 - Install linux

For the daily use of my laptop, ubuntu fits all my needs and i'm pretty happy. But if you still like playing games, forget it dude. No matter tutorials or hacks you do, your FPS will always be lower than windows. But that's my opinion and experience

---

### Post by ssrublev on 2012-07-13
Dropbox link to the file asus-k52_1.0_precise.deb doesn't work, file not found.

---

### Post by jsevi83 on 2012-07-13
I know, but posts cannot be edited anymore, so I cannot modify the first page. Here is the new link:

[http://dl.dropbox.com/u/62752658/asus-k52_1.1.deb](http://dl.dropbox.com/u/62752658/asus-k52_1.1.deb)

---

### Post by deadvirus on 2012-10-18
What about Ubuntu 12.10? Does everything work well?

---

### Post by jsevi83 on 2012-10-22
> **deadvirus said:**
> What about Ubuntu 12.10? Does everything work well?

Didn't install it yet, I've been busy, but I guess some of the issues/solutions would be the same as in Precise. Anyway, I cannot edit the first post anymore, so maybe a new thread needs to be done. I don't think users are going to search through all the pages of this thread to find an updated tutorial...

---

### Post by Bestiomannaro on 2012-10-24
@jsevi83 at #474: Thank you for you tips, now my Asus K52 is a working like a charm. Please open a new thread on Quantal whenever you have time to. Your work is higly appreciated :P

---

### Post by astjohn on 2012-11-07
> **jsevi83 said:**
> Didn't install it yet, I've been busy, but I guess some of the issues/solutions would be the same as in Precise. Anyway, I cannot edit the first post anymore, so maybe a new thread needs to be done. I don't think users are going to search through all the pages of this thread to find an updated tutorial...

I'm just wondering if you started another thread?

Also, one thing that I've been ignoring for a while is that this fix seems to make my fan go crazy after screen lock.  The screen will fade to black as normal, but then the fan kicks it into high speed until I unlock the screen. Has anyone else experienced this?

It does not occur if I remove the patch, but then of course I lose all these wonderful fixes.

---

### Post by jeffrets on 2012-11-09
I have a problem with 12.10 and the battery on my Asus k52. 

If the battery has run down and I connect power the:
[INDENT]keyboard keys will not auto-repeat
numpad keys don't work 
the function keys work but only after after a long delay[/INDENT]

In the syslog file contains a long list of:
[INDENT]: Unknown key 58 pressed
: Unknown key 57 pressed
: Anacron 2.3 started on 2012-11-09
: Will run job `cron.daily' in 5 min.
: Jobs will be executed sequentially[/INDENT]

the log updates every 10 seconds so the log file get large very quickly (10 - 15MB)  

[INDENT]The only way I have found to fix this is:
Switch off
Remove the battery
Boot the computer into Ubuntu check log file
Switch off
Replace battery[/INDENT]

The fault has cleared, until the next time!

Anyone know a permanent solution?:confused:

---

### Post by jeffrets on 2012-11-16
Its looks like the key 57 / 58 fault is a hardware problem. It also occurs when in Windows 7. In Windows 7, running on AC, running on Battery icons flash in the middle of the screen. The other symptoms, such as no auto key repeat, are the same to.

What I have done:

[INDENT]cleaned the fan, the keyboard was getting hot[/INDENT]
[INDENT]Fully charged the battery with the computer off[/INDENT]

Everything is working fine.

---

### Post by ben178 on 2012-11-27
hi!
thanks so much to all contributers for all the workarounds I have found in this thread over time.

Just switched from 10.04 to 12.04 tonight. I'm using Gnome 3, rollback, so far it's not TOO bad (though what HAS changed from Gnome 2 seems to have changed rather for worse, as far as I can see...)

Well, what I wanted to ask you:
I have to use the
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```command to run skype with video working right. is there an easy way to make the tray icon launch Skype like this?
Simply pasting the terminal command, noob style, doesn't work.
If someone has an idea, I'd be happy to be able to open skype with a simple click :)

thanks in advance,
Benja

---

### Post by zhzhwcn on 2013-02-28
> **jsevi83 said:**
> [COLOR=Blue]UPDATE: Ubuntu Precise Pangolin 12.04[/COLOR]

Everything works out of the box except suspend and toggling wireless led. You can install this pacakge to solve them: [http://dl.dropbox.com/u/62752658/asus-k52_1.0_precise.deb](http://dl.dropbox.com/u/62752658/asus-k52_1.0_precise.deb)

Or if you prefer, you can solve things manually:


**- SUSPEND:** you need to create a new file with these commands:

sudo gedit /etc/pm/sleep.d/20_custom-asus-k52
```
#!/bin/sh

case "${1}" in
        hibernate|suspend)
              # Switch USB buses off
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Switch wireless off
              nmcli nm sleep true
              rmmod ath9k
              echo 0 > /sys/devices/platform/asus_laptop/wlan
        ;;
        resume|thaw)
              # Switch USB buses on
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Switch wireless on
              modprobe ath9k
              nmcli nm sleep false
              echo 1 > /sys/devices/platform/asus_laptop/wlan
        ;;
esac
```sudo chmod +x /etc/pm/sleep.d/20_custom-asus-k52



**- WIRELESS LED:** you need to create two new files with these commands:

sudo gedit /etc/acpi/asus-k52-wireless-led.sh

```
#!/bin/sh
# Toggle Wireless LED on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy*/rfkill*/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan

elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
fi
```sudo chmod +x /etc/acpi/asus-k52-wireless-led.sh


sudo gedit /etc/acpi/events/asus-k52-wireless-switch

```
# /etc/acpi/events/asus-k52-wireless-switch
# This is called when the user presses the wireless button (Fn+F2) on the ASUS K52
# and calls /etc/acpi/asus-k52-wireless-led.sh for further processing.

event=hotkey (ATKD|HOTK) 0000005d
action=/etc/acpi/asus-k52-wireless-led.sh

```



If you are using the 64bit version, the webcam will be upside down in 32bit applications (like Skype). To fix that you need to install a new package with this command:

sudo apt-get install libv4l-0:i386

And then run Skype with this command:

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype


*******************************************************************************************************


[COLOR=Blue]Ubuntu Oneiric Ocelot 11.10[/COLOR]

Almost the same issues as in Ubuntu Natty. I created a package to solve them which you can download here:

[http://ubuntuone.com/0q8b4sJUu0geFIgu8x3WOH](http://ubuntuone.com/0q8b4sJUu0geFIgu8x3WOH)

If you prefer to solve things manually, follow the instructions from Ubuntu Natty. Wireless will also be disabled after suspend, you can solve it reading this post:

[http://ubuntuforums.org/showpost.php?p=11312574&postcount=399](http://ubuntuforums.org/showpost.php?p=11312574&postcount=399)

To get the touchpad hotkey working (Fn + F9) you have to open System Settings > Keyboard > Shortcuts and create a custom shortcut pointing to the touchpad script  /etc/acpi/asus-k52-touchpad.sh

There is a bug which doesn't allow the use of three finger tap on the touchpad, hope there is a fix soon. On the other hand, palm detection is finally working.

For now we can solve the three finger tap issue with the instructions here:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

*******************************************************************************************************

[COLOR=Blue]Ubuntu Natty 11.04[/COLOR]

Almost everything is working out of the box. To solve issues with suspend to ram and wireless led check the solutions for Ubuntu Lucid. To use the touchpad key (fn+f9), save the touchpad script in the solutions for Ubuntu Lucid and map it to the key.

I created a package which automatically solves issues with suspend and wireless led. It also contains the touchpad script, you can use gnome-binding-properties to create a new combination which executes  /etc/acpi/asus-k52-touchpad.sh

Package:  [http://ubuntuone.com/p/puF/](http://ubuntuone.com/p/puF/)


For the webcam I didn't have to do anything, it's working ok. The only thing is that I'm using Ubuntu 64bit, and for 32bit applications that use the webcam (example: skype) the image is upside down. To solve it I run it like this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

There is a nice utility in the official repositories called 'guvcview' which lets you configure some settings of the webcam (you can invert or mirror the image, for example). I recommend it.


If wifi slows down after disconnecting AC cable, run this command:

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

*******************************************************************************************************

[COLOR=Blue]Ubuntu Maverick 10.10[/COLOR]

- To solve the problems relative to sound, run this on a terminal:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)


Then reboot your laptop. If still have any problems, check page 34 ( [http://ubuntuforums.org/showthread.php?t=1460790&page=34](http://ubuntuforums.org/showthread.php?t=1460790&page=34) )


- To solve the webcam upside down problem, run this on a terminal:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade


- To solve the suspend and wireless-led problem, check the following solutions for Ubuntu Lucid 10.04.

*******************************************************************************************************

[COLOR=Blue]Ubuntu Lucid 10.04[/COLOR]

I own an Asus A52F, twin brother of the Asus K52F. Here is a list of the problems you might find when installing Ubuntu Lucid, and their respective solutions.

[COLOR=Red]LIST OF PROBLEMS:[/COLOR]

1) SOUND: speakers do not mute when headphones are plugged in. (SOLVED)

2) SOUND: hdmi sound out not working. (SOLVED)

3) SOUND: external microphone not working. (SOLVED)

4) SUSPEND: suspend to ram freezes my laptop. (SOLVED)

5) WEBCAM: image upside down. (SOLVED)

6) Wireless LED: the led doesn't turn off when I press Fn+F2, but wireless is disabled. (SOLVED)

7) Available RESOLUTIONS: I get the maximum resolution for my screen, 1366x768, but I am missing other resolutions available in Windows. (IMPROVED)

8 ) TOUCHPAD: not detected as a touchpad, detected as "ImPS/2 Logitech Wheel Mouse". Touchpad tab missing in System>Preferences>Mouse and syndaemon is not working. The key to disable touchpad Fn+F9 is not working. (SOLVED)

Palm proof technology not working.

9 ) Calculator button (Fn + KP_Enter) not working. (SOLVED)



[COLOR=Green]LIST OF SOLUTIONS:[/COLOR]

1,2,3) SOUND: paste these commands on a terminal.

wget [www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip")
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb

Install the package and reboot. Now speakers should mute when headphones are connected, HDMI and microphones (internal & external) should be working. Open alsamixer and unmute S/PDIF (you can do that pressing "m"). Choose HDMI output from the pulseaudio volume applet (hardware tab) when needed. 

***Note: I am using Alsa 1.0.23 and Linux Kernel 2.6.34.


4) SUSPEND: you need to create a new file with this commands:

sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac
```sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd


5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.


6) Wireless LED: you need to create two files and restart acpi. Follow this commands:

sudo gedit /etc/acpi/events/asus-wireless-switch
```

event=hotkey ATKD 0000005d
action=/etc/acpi/asus-wireless-switch.sh
```sudo gedit /etc/acpi/asus-wireless-switch.sh

```
#!/bin/sh
# Toggle wireless device on Asus K52 laptops

WLANSTATUS=`cat /sys/class/ieee80211/phy*/rfkill*/state`

test -z $WLANSTATUS && exit 1

if [ $WLANSTATUS = 0 ]; then
echo 0 > /sys/devices/platform/asus_laptop/wlan    
elif [ $WLANSTATUS = 1 ]; then
echo 1 > /sys/devices/platform/asus_laptop/wlan
fi
```sudo chmod +x /etc/acpi/asus-wireless-switch.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart


7) Available RESOLUTIONS: you can get 1024x768 by adding to your repositories ppa:ubuntu-x-swat/x-updates (more stable than ppa xorg-edgers). Do this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade

Then reboot and that's it. THIS IS ONLY FOR INTEL GRAPHIC CARDS > Asus K52F & Asus A52F


8 ) TOUCHPAD: I found a solution to get the Elantech touchpad detected as such (and not ImPS/2 Logitech Wheel Mouse). Follow the instructions on this post:   [http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

EDIT: if you are running 2.6.34-rc7 or later you just need to run this two commands:
echo "options psmouse force_elantech=1" | sudo tee -a /etc/modprobe.d/psmouse.conf
sudo rmmod psmouse && sudo modprobe psmouse

Then you can check your settings with "synclient -l" or with xinput list-props "ETPS/2 Elantech Touchpad"
I made a startup script to keep two fingers tap as middle click, and three fingers tap as right click, with this command:
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3

Edit this file to get the touchpad button working:

sudo gedit /etc/acpi/asus-touchpad.sh

```
#!/bin/sh
# Toggle Elantech touchpad device on Asus laptops

[ -f /usr/share/acpi-support/power-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

getXconsole

TPSTATUS=`xinput list-props "ETPS/2 Elantech Touchpad" | grep "Device Enabled" | awk '{ print $4 }'`

test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 1 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 0
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD OFF" "
     Press Fn+F9 to enable"
elif [ $TPSTATUS = 0 ]; then
xinput set-prop "ETPS/2 Elantech Touchpad" "Device Enabled" 1
notify-send -i /usr/share/icons/hicolor/scalable/actions/touchpad-enabled.svg -t 3000 "        TOUCHPAD ON" "
     Press Fn+F9 to disable"
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3
fi
```sudo service acpid restart
sudo /etc/init.d/acpi-support restart

EDIT: when pressing Fn+c (splendid button) this file is called "/etc/acpi/asus-f8sv-touchpad", and acts as Fn+F9. To solve it, uncomment that file or change it's action to something else that asus-touchpad.sh


9 ) Create two files to get the calculator button working: (if using maverick, check posts 183 and 186)

sudo gedit /etc/acpi/events/asus-calculator
```

event=hotkey (ATKD|HOTK) 000000b5
action=/etc/acpi/asus-calculator.sh
```sudo gedit /etc/acpi/asus-calculator.sh

```
#!/bin/sh
# Start calculator on Asus K52 laptops

. /usr/share/acpi-support/power-funcs

getXconsole

gcalctool &
```sudo chmod +x /etc/acpi/asus-calculator.sh
sudo service acpid restart
sudo /etc/init.d/acpi-support restart

Hi, I am using Ubuntu 12.10 X64, my laptop is Asus X32U . The WIFI connection is working good but the WIFI LED on the laptop is not working at all. the _lspci -nn | grep 0280_ result is
```
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) 
```

could you help me this?

---

### Post by paologab on 2013-05-07
Hi
I've upgraded to 13.04 (64bit) and the touchpad is unusable (with any DM I have: gnome shell, cinnamom, with or without effect): gestures uncontollable, sliding scrambled
anyone with similar behaviour and, hopefully, solution?
paolo :p

edit:

it happens only with ethernet cable connected; with it disconnected or wifi I've no problems...

---

