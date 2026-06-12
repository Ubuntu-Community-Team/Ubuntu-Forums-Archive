---
title: "Ubuntu 11.04 on a Thinkpad T420"
date: 2011-05-03
forum: Hardware
---

### Post by robin.nightingale on 2011-05-03
Hello i just got a Thinkpad T420 and tested it today.
The Machines are still pretty new and not a lot of users own one so i thought i gonna share me experiences with you and start a **T420 Threat**.

So my model is the: T420 4180W1H with the following Configurations:

Core i5-2520M (2.50GHz), 4GB RAM, 500GB 7200rpm HD, 14.0in HD+ LED BL 1600x900, 1GB nVidia NVS 4200M, CDRW/DVDRW, Intel 802.11bgn wireless, Bluetooth, 1GB Ethernet, UltraNav, Secure chip, Kamera, Fingerprint reader, 9 Cell Akku.
[B]
Out of the Box works :[/B]

Camera,SD Card Reader, external Monitor, Lan/Wlan, Sound, Microphone, Media Keys, CD/DVD Drive

**with a littel work:**

The Nividia Graficcard, Install the Drivers via the additional drivers tool and restart. unfortunatly it appears to be that the nvidia driver does not support hybrid graphics cards, or NVIDIA Optimus.
So youll  need to go into the bios and turn off Optimus and force the system to use the discrete graphics card. 

 

**Doesent Work**

You cant Controle the Fan Via Thinkfan. And the Fan is running all the Time at least with 1800 rpm. Its not realy loud bit i prefer total silence.But i think in future this will be better cause this machine is pretty new. But if you have any tips and advices for me, how to controle the fan please let me know.

**As far iam real satisfied with the notebook, it runs natty pretty stabel and install is very easy.**

---

### Post by bjordan1979 on 2011-05-26
Awesome news. I'm glad to hear that overall it works well. I'm planning to get a T420 soon with almost the same setup as you. I definitely want the Nvidia graphics for the 1600x900 resolution alone!

Optimus / Hybrid graphic support is improving a little bit (or I should say being worked on).

Check out the Bumblebee project. No auto switching yet but it appears you can launch specific apps to use the Nvidia card. E.g. "ptirun64 <application>", etc.

Project:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

Brief Article:
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

Quick question. On the T420 can you swap the Fn and Control key in the BIOS? I know that's something they added a while back. I hope it's still there because Fn being on the outside drives me nuts!

---

### Post by mejo on 2011-05-26
yes, it's possible to switch the fn and ctrl keys in bios on a t420.

and about the fan control: i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)


I didn't give bumblebee a try yet, though it looks promissing.

other (minor) issues with t420 and ubuntu natty are:

- Microphone mute key does not function (Bug #751471)
- HDAPS not working by default
- issues with graphics: sometimes freezes, sometimes login doesn't work. didn't discover these issues lateley, but at the beginning I had problems, and some bugreports do exist as well.

greetings,
 jonas
****

---

### Post by mejo on 2011-05-26
Ah, I forgot something: did anyone get the docking station to work with ubuntu? I'm not sure whether the one they sent to me is broken, or whether it simply doesn't work with ubuntu.

Whatever I connect to the Docking station (usb keyboard, mouse, dvi monitor, ...) ubuntu ignores it. only exception is the power connector.

I hope to find a solution for that soon.

Greetings,
 jonas

---

### Post by bjordan1979 on 2011-05-30
Which Intel WiFi card did you get? 

 I was planning on going with the "Intel Centrino Advanced-N 6205" WiFi  card, but I'm leaning towards the "Ultimate-N 6300" instead just to max  it out. Trying to figure out if it's worth the extra $20. :/

According to ThinkWiki the N 6205 works with kernel 2.6.37 and newer and the N 6300 card with kernel 2.6.34 and newer.

---

### Post by mejo on 2011-05-31
Hey, news about the docking station: my claims above are wrong. USB devices and power connector work with the 'mini dock series 3' docking station.

Big problems on the other hand with external monitor: an external monitor connected to the docking station dvi slot is not detected by ubuntu at all. But that may be related to the bios setting to only use internal graphics (intel), and ignore the discrete graphics (nvidia). If I remember correctly, DVI and Display Port are only supported by the discrete nvidia graphics.

But even with the VGA slot I ran into problems: ubuntu detects the external monitor, but the upper 1/5 of display are broken. Both on internal and external display.

This sucks, as without external monitor, a docking station is rather useless.

@bjordan1979: My T420 has a Ultimate-N 6300. It worked out of the box with Ubuntu Natty, and didn't make problems yet.

---

### Post by Wlo on 2011-05-31
Hi.

I can't get my external monitor to work on my T420.  It doesn't get detected.

Seems like it's down to this but here, [https://bugs.launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/+bug/737349](https://bugs.launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/+bug/737349) .

Anyone have a workaround?

Cheers.

---

### Post by bjordan1979 on 2011-05-31
> **mejo said:**
> @bjordan1979: My T420 has a Ultimate-N 6300. It worked out of the box with Ubuntu Natty, and didn't make problems yet.

Thanks, I ordered a T420 last night and did get the N 6300 WiFi card. Now for the wait to get it! :/

---

### Post by mejo on 2011-05-31
> **Wlo said:**
> 
I can't get my external monitor to work on my T420.  It doesn't get detected.

Seems like it's down to this but here, [https://bugs.launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/+bug/737349](https://bugs.launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/+bug/737349) .

Anyone have a workaround?


To which slot did you connect the external monitor? To VGA, DVI or Display Port? Do you use a docking station, or is the monitor connected directly to the ThinkPad?

And which graphic controller are you using? Does the ThinkPad have Nvidia Optimus support? Is it enabled? Or did you manually set either of integrated or discrete graphics?

Greetings,
 jonas

---

### Post by Wlo on 2011-05-31
> **mejo said:**
> To which slot did you connect the external monitor? To VGA, DVI or Display Port? Do you use a docking station, or is the monitor connected directly to the ThinkPad?

Connected directly via VGA cable.  Both with and without the "additional drivers" driver.  Although oddly when I go into additional drivers now the driver is listed as just "nvidia_current" (I thought it said a version number last time I used one) and it says "This driver is activated but not in use".

> And which graphic controller are you using? Does the ThinkPad have Nvidia Optimus support? Is it enabled? Or did you manually set either of integrated or discrete graphics?

I've disabled Optimus in the BIOS and am just using discrete.  Had to do this previously on my T410/Maverick when it worked fine.  This also worked with Windows so I know the cable and monitor are okay.

Full spec of my machine is below.  Please let me know if any more info is useful.  Thanks.

Wlo

 - Intel Core i7-2620M Processor (2.70GHz, 4MB L3)
 - Genuine Windows 7 Professional 64
 - Genuine Windows 7 Professional 64 US English
 - 14.0 HD+ (1600 x 900) LED Backlit Display, Mobile Broadband Ready
 - NVIDIA NVS 4200M Graphics with Optimus Technology, 1GB DDR3 Memory
 - 8 GB PC3-10600 DDR3 SDRAM 1333MHz SODIMM Memory (2 DIMM)
 - Keyboard UK English
 - 720p HD Camera
 - 500 GB Hard Disk Drive, 7200rpm
 - DVD recordable multiburner
 - Express Card Slot & 4 in 1 Card Reader
 - 6 cell Li-Ion Battery -  55+
 - Country Pack United Kingdom
 - Bluetooth 3.0
 - Intel Centrino Ultimate-N 6300 (3x3 AGN)
 - Integrated Wireless Wide Area Network upgradable
 - Language Pack UK English

---

### Post by mejo on 2011-05-31
> **Wlo said:**
> 
Connected directly via VGA cable.  Both with and without the "additional drivers" driver.  Although oddly when I go into additional drivers now the driver is listed as just "nvidia_current" (I thought it said a version number last time I used one) and it says "This driver is activated but not in use".

I've disabled Optimus in the BIOS and am just using discrete.  Had to do this previously on my T410/Maverick when it worked fine.  This also worked with Windows so I know the cable and monitor are okay.


Did you try to use the integrated intel graphics instead of nvidia? As written above, in my case the intel graphics controller at least detects the external VGA monitor, but the display is broken in the upper 1/5 of screen.

Greetings,
 jonas

---

### Post by robin.nightingale on 2011-06-01
I got also Problems with the external Monitor with intel Graphics. The intel graphics controller detects the external VGA monitor and i can see the main panel and the mouse arrow but all windows on the external screen stay black.

---

### Post by Wlo on 2011-06-08
Have tested with internal graphics set.  On classic (non Unity) mode I can get my external monitor to work, just at a low res  (1024x768 I think).

---

### Post by donniezazen on 2011-06-08
Does Intel HD graphic card work by default on T420? What driver do you use for Intel HD?

Is Bumblebee stable enough to use on productive machine? Any good tutorials. Do i have to set Optimus as my graphic card and 'detection enabled' if i install Bumblebee.

How is battery life of T420 on Ubuntu?

Thanks.

---

### Post by mejo on 2011-06-08
integrated intel graphics work out of the box. even unity works like a charm.

here is what I just posted in thread [http://ubuntuforums.org/showthread.php?p=10909862#post10909862](http://ubuntuforums.org/showthread.php?p=10909862#post10909862):

for me, nearly everything worked out of the box with natty narwhal on my t420. here's a list (from memory) of issues i remember:

- need to disable nvidia optimus in BIOS. either choose internal intel  graphics (saves power, satisfying for me) or discrete nvidia graphics.  work is in progress though, to support optimus for linux. see [1].

- the fan runs all the time. you need to install thinkfan and manually  add newer temperature sensors to its config file in order to make it  work on the t420. See [2] (german) for further information

- battery lifetime was very short without tweaks. with integrated intel  graphics, thinkfan running, and tlp installed and configured, i get up  to 7,5 hours now.

- the microphone mute button doesn't work. didn't find a solution for that one yet. [3] [4]

- both speakers mute button and wireless hotbutton behave in an  unexpected way. for the wireless hotbutton that seems to be a feature  (see [5]), for the speakers mute button I hope a fix is found soon.

- issues with external monitor. regardless whether I use the docking  station or directly plot my monitor into the vga connector, the screen  is somehow broken and cluttered. hope this will be fixed with kernel  & video driver update soon.

all in all I have to say that I'm pretty satisfied with ubuntu 11.04 on my t420, given that it's pretty new hardware.

also see the following thread: [http://ubuntuforums.org/showthread.php?p=10886666](http://ubuntuforums.org/showthread.php?p=10886666)

greetings,
 jonas

[1] [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
[2] [http://thinkpad-wiki.org/Thinkfan#Ke..._Kernel_2.6.38]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38")
[3] [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/751471]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751471")
[4] [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/408903]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903")
[5] [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/773558]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773558")

---

### Post by donniezazen on 2011-06-09
> **mejo said:**
> yes, it's possible to switch the fn and ctrl keys in bios on a t420.

and about the fan control: i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)


I didn't give bumblebee a try yet, though it looks promissing.

other (minor) issues with t420 and ubuntu natty are:

- Microphone mute key does not function (Bug #751471)
- HDAPS not working by default
- issues with graphics: sometimes freezes, sometimes login doesn't work. didn't discover these issues lateley, but at the beginning I had problems, and some bugreports do exist as well.

greetings,
 jonas
****

The fan is definetly annoying. I am unable to follow thinkwiki. Can you explain point 2,3 and 6?

2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'

and 

6. reload kernel module 'thinkpad_acpi'


I am stuck at the second step in thinkwiki

>  sudo modprobe -rv thinkpad_acpi && sudo modprobe -v thinkpad_acpi
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
rmmod /lib/modules/2.6.38-10-generic/kernel/drivers/char/nvram.ko
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/char/nvram.ko 
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko fan_control=1 fan_control = 1
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.38-10-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Thanks.

---

### Post by drende on 2011-06-09
Do you install ubuntu 32bit or 64bit on the 420s?

---

### Post by mejo on 2011-06-09
> **soham_1207 said:**
> The fan is definetly annoying. I am unable to follow thinkwiki. Can you explain point 2,3 and 6?

2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'

and 

6. reload kernel module 'thinkpad_acpi'


all right, lets see:

you add a kernel module to the list in the config file /etc/modules if you want your system to load the kernel module automatically during the boot process. You can add it by either editing the file with you favourite text editor (gedit, vim, ...), or with the following command:

```
$ sudo echo "coretemp" >> /etc/modules
```afterwards you need to load the kernel module manually, as it's only loaded automatically beginning with the next reboot. load the module the following way:

```
$ sudo modprobe coretemp
```that's it, now the module 'coretemp' should be loaded (check with '$ lsmod')

now about step 6. you reload a kernel module with 'modprobe -r':

```
$ sudo modprobe -r thinkpad_acpi
```> **soham_1207 said:**
> 

I am stuck at the second step in thinkwiki

     
> sudo modprobe -rv thinkpad_acpi && sudo modprobe -v thinkpad_acpi
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
rmmod /lib/modules/2.6.38-10-generic/kernel/drivers/char/nvram.ko
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/char/nvram.ko 
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko fan_control=1 fan_control = 1
FATAL: Error inserting thinkpad_acpi  (/lib/modules/2.6.38-10-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko):  Unknown symbol in module, or unknown parameter (see dmesg)                      


First, what's the content of /etc/modprobe.d/options? This file should not exist at all on recent systems. Please post the content of this file.

Second, according to the error message, you load the kernel module thinkpad_acpi with the options 'fan_control=1 fan_control = 1'. I guess that the second option (fan_control = 1) with the spaces between option and value produces the error.

You should check, where these options are set. Post the output of the following:

```
$ grep -ri thinkpad /etc/modprobe.d/
```

---

### Post by mejo on 2011-06-09
> **drende said:**
> Do you install ubuntu 32bit or 64bit on the 420s?

i run ubuntu 64bit on a t420

---

### Post by donniezazen on 2011-06-09
> **mejo said:**
> i run ubuntu 64bit on a t420

I have amd64 bit version installed.

---

### Post by donniezazen on 2011-06-09
Thank you for your help. It seems to be working now. Do you use the default settings provided in /etc/thinkfan.conf or some other?

> donnie@donnie-laptop:~$ cat /proc/acpi/ibm/fan
status:		enabled
speed:		3357
level:		3
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
donnie@donnie-laptop:~$ grep -ri thinkpad /etc/modprobe.d/
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control=1 


---

### Post by donniezazen on 2011-06-09
I get this error ACPI:Unable to dock when i shut down. I do not have a docking station.

---

### Post by mejo on 2011-06-09
> **soham_1207 said:**
> Thank you for your help. It seems to be working now. Do you use the default settings provided in /etc/thinkfan.conf or some other?

hey, great to hear that it's working for you as well. yes, I use the default settings in thinkfan.conf, didn't see a reason yet, to change them.

and about the acpi error: I didn't see that one yet.

---

### Post by donniezazen on 2011-06-09
I am getting 3-4 of battery life with integrated graphic card and thinkfan. My thinkfan runs at level 3 with 3000-3500 RPM because temperature of my system lingers around 55-60 degrees. I will intall TLP later today and may be Bumblebee this weekend.

Any other tweak that you did. I go 3-4 hours when i was mostly surfing net.

---

### Post by mejo on 2011-06-10
Hey,

I get up to 6,5 hours of battery with thinkfan, integrated graphics, power saving options enabled in BIOS, and TLP installed. If I remember correctly, TLP increased battery time a lot. I also disable bluetooth whenever I don't need it.

Ah, and I run the 2.6.39-0-generic kernel from ppa:kernel-ppa/ppa. According to launchpad bug #760131[1], Natty stock 2.6.38 kernel raises power consumption significantly compared to 2.6.37. Several comments suggest that 2.6.39 increases the situation. A patched 2.6.38 kernel is also linked. You might want to follow the bugreport on your own.

For me thinkfan uses level 0-2 most of the time. Maybe it's related to TLP and 2.6.39 kernel.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by donniezazen on 2011-06-10
> **mejo said:**
> Hey,

I get up to 6,5 hours of battery with thinkfan, integrated graphics, power saving options enabled in BIOS, and TLP installed. If I remember correctly, TLP increased battery time a lot. I also disable bluetooth whenever I don't need it.

Ah, and I run the 2.6.39-0-generic kernel from ppa:kernel-ppa/ppa. According to launchpad bug #760131[1], Natty stock 2.6.38 kernel raises power consumption significantly compared to 2.6.37. Several comments suggest that 2.6.39 increases the situation. A patched 2.6.38 kernel is also linked. You might want to follow the bugreport on your own.

For me thinkfan uses level 0-2 most of the time. Maybe it's related to TLP and 2.6.39 kernel.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)


Thanks for your help.

I have made changes to BIOS, updated kernel to 2.6.39.0, installed thinkfan,tlp and using it with discrete graphic card. My fan runs continuously at level 3. I am thinking about trying 2.6.40 rc to see if it helps reduce power consumption which is over 23 Watt hours according to powertop and bring temp down. Also i might switch to integrated graphic card as their is not much use.

---

### Post by donniezazen on 2011-06-10
I changed my graphic card to Nvidia Optimus and enabled OS detection. This will help me use discrete card when playing games in Windows and use Ubuntu for all other work.

Just by changing graphic card temp has dropped by 3-4 degrees and fan now runs on 0-1-2 level. I am guessing this should let my computer go idle when not is use. I have also started getting 150 or lesser wake per second in 20 W or less power usage according to powertop.

Kernel 2.6.40 is still on list along with bumblebee.

---

### Post by mejo on 2011-06-11
> **soham_1207 said:**
> I changed my graphic card to Nvidia Optimus and enabled OS detection. This will help me use discrete card when playing games in Windows and use Ubuntu for all other work.

Just by changing graphic card temp has dropped by 3-4 degrees and fan now runs on 0-1-2 level. I am guessing this should let my computer go idle when not is use. I have also started getting 150 or lesser wake per second in 20 W or less power usage according to powertop.

Kernel 2.6.40 is still on list along with bumblebee.

Great to hear that things improved for you. Please report back when you gave kernel 2.6.40 and bumblebee a try.

---

### Post by robin.nightingale on 2011-06-11
I connected my machine to the minidock 3 today and usb, power and lan are working. But no result for the headphone jack and the vga monitor. Does anybody have an idea ?

---

### Post by donniezazen on 2011-06-14
I have been using Win 7 for past couple of days. I have to confess. It runs amazingly good on this machine. I get excellent battery life like 6-7 hours. The temperature stays 44-49 degrees which keep fan shut off and same plenty of battery.

Changing to integrated display card reduced power consumption and temperature significantly but due to higher power consumption in kernel 2.6.38/39 i can't the same battery life as i get with win 7. Kernel 3.0 has been released today in OO. let's see if they fixed the issue.

I installed bumblebee. Installation and use is just cake walk. It works smoothly only thing is developers are still working to get it done automatically. But all you have to do i run optirun64 application and it uses your nvidia card.

---

### Post by VValdo on 2011-06-14
Hey I've got a w520 here (coming from a mac) and just wanted to add a few notes.

* haven't tried thinkfan yet but I'm about to do so..
* ditto bumblebee/new kernel.
* there is a bug on the w520 where the computer "stutters", at least with the integrated driver.  This is most visible if you do a full-screen screensaver-- your machine "locks up" every few seconds.  The [workaround]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065") right now is to do this from root:

> echo 1 > /sys/module/i915/parameters/semaphores


Also-- for anyone considering thinkfan, don't forget you have more sensors, namely:

> sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/platform/coretemp.4/temp1_input
sensor /sys/devices/platform/coretemp.6/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

I am going with default speeds for now with an eye on the temps-- I installed lm_sensors + sensor-applet from apt so I can keep an eye on speeds and stuff.. sometimes I see it drops down to 0 RPM...  hovering around 40-50C so I guess that's good... haven't stress tested it yet.
Aside from this and a few other small issues, I gotta say I'm pretty impressed.

---

### Post by Wlo on 2011-06-14
This link, [http://www.ubuntu.com/certification/hardware/201102-7230:201102-7315](http://www.ubuntu.com/certification/hardware/201102-7230:201102-7315) , mentions that "The system is available in some regions with a special image of Ubuntu pre-installed by the manufacturer.".  Is it possible to obtain that anywhere?

Thanks.

---

### Post by bjordan1979 on 2011-06-17
I got my T420 yesterday. After trying to get the Nvidia card to work (in discrete mode) on Ubuntu 10.10 but having no luck I've given up and installed 11.04.

Have you guys noticed any battery drain with 11.04? Apparently there's an issue in the latest kernels that are causing battery drain. See this article:

[http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA](http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA)

I haven't run 11.04 enough to know yet. I'm thinking about running 11.04 long enough to figure out what all pieces are in play to get the Nvidia drivers to work and then switching back to 10.10 until this gets sorted out.

---

### Post by donniezazen on 2011-06-17
> **bjordan1979 said:**
> I got my T420 yesterday. After trying to get the Nvidia card to work (in discrete mode) on Ubuntu 10.10 but having no luck I've given up and installed 11.04.

Have you guys noticed any battery drain with 11.04? Apparently there's an issue in the latest kernels that are causing battery drain. See this article:

[http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA](http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA)

I haven't run 11.04 enough to know yet. I'm thinking about running 11.04 long enough to figure out what all pieces are in play to get the Nvidia drivers to work and then switching back to 10.10 until this gets sorted out.


I have noticed a steep battery drain in Natty. I have tried thinkfan, tlp and Kernel 3.0 but fan runs all the time and temperature remains around 55 degrees. I am back on Win 7 for now as i get excellent battery life, low temperature and no fan sound. I have been gaming a lot on this superb hardware which is another reason for me to ditch Ubuntu for the moment.

---

### Post by mejo on 2011-06-19
> **soham_1207 said:**
> I have noticed a steep battery drain in Natty. I have tried thinkfan, tlp and Kernel 3.0 but fan runs all the time and temperature remains around 55 degrees. I am back on Win 7 for now as i get excellent battery life, low temperature and no fan sound. I have been gaming a lot on this superb hardware which is another reason for me to ditch Ubuntu for the moment.

As written above, thinkfan should work on the T420 once you added the new temperature sensors to thinkfan.conf. If your fan still runs all the time, please paste the output of 'cat /proc/acpi/ibm/fan' and take a look at the top power/cpu- consuming processes. You can do so by starting 'top' in the terminal, and and pressing 'P' to sort the processes by CPU usage.

---

### Post by bjordan1979 on 2011-06-19
I'm still having issues getting the Nvidia NVS 4200 video card to work in 11.04 and/or 10.10. I'm going to keep messing with it though.

---

### Post by nrundy on 2011-06-19
> **robin.nightingale said:**
> Hello i just got a Thinkpad T420 and tested it today.
The Machines are still pretty new and not a lot of users own one so i thought i gonna share me experiences with you and start a **T420 Threat**.
 

**Doesent Work**

You cant Controle the Fan Via Thinkfan. And the Fan is running all the Time at least with 1800 rpm. Its not realy loud bit i prefer total silence.But i think in future this will be better cause this machine is pretty new. But if you have any tips and advices for me, how to controle the fan please let me know.

**As far iam real satisfied with the notebook, it runs natty pretty stabel and install is very easy.**

robin, the fan noise is because Linux is running at a much higher temperature. Run the machine with Windows 7 and you'll have much cooler temperatures and the fan will hardly ever comes on.

I switched all my laptops over to Windows 7 solely because of the temperature issue. I'm worried running ubuntu is going to wreck my laptop.

---

### Post by donniezazen on 2011-06-19
> **mejo said:**
> As written above, thinkfan should work on the T420 once you added the new temperature sensors to thinkfan.conf. If your fan still runs all the time, please paste the output of 'cat /proc/acpi/ibm/fan' and take a look at the top power/cpu- consuming processes. You can do so by starting 'top' in the terminal, and and pressing 'P' to sort the processes by CPU usage.

> **nrundy said:**
> robin, the fan noise is because Linux is running at a much higher temperature. Run the machine with Windows 7 and you'll have much cooler temperatures and the fan will hardly ever comes on.

I switched all my laptops over to Windows 7 solely because of the temperature issue. I'm worried running ubuntu is going to wreck my laptop.

Thinkfan does it's work well but i agree to nrundy. I am losing 2-3 hours of battery life due to high temperature and higher power usage. I am back on Win 7 because it doesn't make sense to run your laptop at 5-6 degrees higher temperature.

---

### Post by nrundy on 2011-06-19
> **soham_1207 said:**
> Thinkfan does it's work well but i agree to nrundy. I am losing 2-3 hours of battery life due to high temperature and higher power usage. I am back on Win 7 because it doesn't make sense to run your laptop at 5-6 degrees higher temperature.


On my box, Ubuntu was running at 55 Celsius at idle! Win7 is at 28-30 Celsius. If it was a few degrees, I'd still prolly be on Ubuntu. But the temps on linux are totally out of control. It's literally melting some folks laptops and causing forced shutdowns.

---

### Post by donniezazen on 2011-06-19
> **nrundy said:**
> On my box, Ubuntu was running at 55 Celsius at idle! Win7 is at 28-30 Celsius. If it was a few degrees, I'd still prolly be on Ubuntu. But the temps on linux are totally out of control. It's literally melting some folks laptops and causing forced shutdowns.

That's just too high of a difference. I had TLP, thinkfan, kernel-ppa and integrated graphic card in use. My Ubuntu temp was over 55 degrees and windows 7 temperature is usually 40-44 degrees. It made fan run at level 3 and 3500 rpm according to thinkfan configuration.

---

### Post by nrundy on 2011-06-19
> **soham_1207 said:**
> That's just too high of a difference. I had TLP, thinkfan, kernel-ppa and integrated graphic card in use. My Ubuntu temp was over 55 degrees and windows 7 temperature is usually 40-44 degrees. It made fan run at level 3 and 3500 rpm according to thinkfan configuration.

Just reporting the numbers the sensors gave me. I was concerned that maybe the temp readings I was getting in ubuntu were somehow different because of the fact that they were being reported in ubuntu instead of Win7. So I did the following:

1.) from a completely cool laptop I started Win7 and run it at idle with no powersave for a half hour, then checked temp; it was 30 Celsius.

2.) I turned of the box, let it cool for hours. Booted into ubuntu 11.04. Let it sit at idle for a half hour. Then I shutdown and immediately booted into Win7. The temp as reported by Win7 = 55 Celsius. I left Win7 running and gradually watched the temp go down into the low 30s over the next half hour.

---

### Post by bjordan1979 on 2011-06-20
Has anyone figured out how to remap the browser back/forth keys to something else? I'd like to map them to move between virtual desktops. I haven't started looking into it yet, just curious.

---

### Post by mejo on 2011-06-20
> **bjordan1979 said:**
> Has anyone figured out how to remap the browser back/forth keys to something else? I'd like to map them to move between virtual desktops. I haven't started looking into it yet, just curious.

This is a very good idea!

And actually it's very easy to do: Simply configure the keys in settings for keyboard shortcuts. Only problem is, that unity doesn't manage the virtual desktops in a row. Thus you cannot change from the right upper virtual desktop to the left lower one and vice versa by using the 'change to left/right virtual desktop' keys.

---

### Post by donniezazen on 2011-06-20
[https://launchpad.net/~mj-casalogic/+archive/bumblebee/](https://launchpad.net/~mj-casalogic/+archive/bumblebee/)

Bumblebee is now available in Launchpad. I tried it from github which worked flawlessly.

---

### Post by VValdo on 2011-06-20
Cool trying bumblebee..

in the meanwhile, is anyone seeing this with 2.6.39.x:

```
Jun 20 19:26:05 laptop kernel: [ 2619.382846] CPU7: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382849] CPU3: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382852] CPU2: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382855] CPU5: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382858] CPU1: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382861] CPU4: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.382863] CPU0: Package power limit notification (total events = 2297)
Jun 20 19:26:05 laptop kernel: [ 2619.384116] CPU7: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384118] CPU3: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384120] CPU2: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384122] CPU4: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384124] CPU0: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384127] CPU5: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384129] CPU1: Package power limit normal
Jun 20 19:26:05 laptop kernel: [ 2619.384130] CPU6: Package power limit normal
Jun 20 19:27:23 laptop kernel: [ 2697.012203] [Hardware Error]: Machine check events logged
```

I've gotten this pretty much every time I build.  And my fan is going in state 7:


```
/proc/acpi/ibm$ more fan
status:		enabled
speed:		3851
level:		7
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
```

Sensors are warm but not ridiculous:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +74.0°C  (crit = +99.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +76.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 1:      +76.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 2:      +70.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 3:      +72.0°C  (high = +86.0°C, crit = +100.0°C)  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3842 RPM
```

But mcelog is reporting overheating...

```

Jun 20 19:29:52 laptop mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
Jun 20 19:29:52 laptop mcelog: HARDWARE ERROR. This is *NOT* a software problem!
Jun 20 19:29:52 laptop mcelog: Please contact your hardware vendor
Jun 20 19:29:52 laptop mcelog: MCE 0
Jun 20 19:29:52 laptop mcelog: CPU 7 THERMAL EVENT TSC 581128f91ab 
Jun 20 19:29:52 laptop mcelog: TIME 1308623392 Mon Jun 20 19:29:52 2011
Jun 20 19:29:52 laptop mcelog: Processor 7 below trip temperature. Throttling disabled
Jun 20 19:29:52 laptop mcelog: STATUS c000000088260c00 MCGSTATUS 0
Jun 20 19:29:52 laptop mcelog: MCGCAP c09 APICID 7 SOCKETID 0 
Jun 20 19:29:52 laptop mcelog: CPUID Vendor Intel Family 6 Model 42
Jun 20 19:29:52 laptop mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
Jun 20 19:29:52 laptop mcelog: HARDWARE ERROR. This is *NOT* a software problem!
Jun 20 19:29:52 laptop mcelog: Please contact your hardware vendor
Jun 20 19:29:52 laptop mcelog: MCE 1
Jun 20 19:29:52 laptop mcelog: CPU 3 THERMAL EVENT TSC 581128faf38 
Jun 20 19:29:52 laptop mcelog: TIME 1308623392 Mon Jun 20 19:29:52 2011
Jun 20 19:29:52 laptop mcelog: Processor 3 below trip temperature. Throttling disabled
Jun 20 19:29:52 laptop mcelog: STATUS c000000088260c00 MCGSTATUS 0
Jun 20 19:29:52 laptop mcelog: MCGCAP c09 APICID 3 SOCKETID 0 
Jun 20 19:29:52 laptop mcelog: CPUID Vendor Intel Family 6 Model 42
Jun 20 19:29:52 laptop mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
Jun 20 19:29:52 laptop mcelog: HARDWARE ERROR. This is *NOT* a software problem!
Jun 20 19:29:52 laptop mcelog: Please contact your hardware vendor
Jun 20 19:29:52 laptop mcelog: MCE 2
Jun 20 19:29:52 laptop mcelog: CPU 2 THERMAL EVENT TSC 581128fc43e 
Jun 20 19:29:52 laptop mcelog: TIME 1308623392 Mon Jun 20 19:29:52 2011
Jun 20 19:29:52 laptop mcelog: Processor 2 below trip temperature. Throttling disabled
Jun 20 19:29:52 laptop mcelog: STATUS c000000088260c00 MCGSTATUS 0
Jun 20 19:29:52 laptop mcelog: MCGCAP c09 APICID 2 SOCKETID 0 
Jun 20 19:29:52 laptop mcelog: CPUID Vendor Intel Family 6 Model 42
Jun 20 19:29:52 laptop mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
Jun 20 19:29:52 laptop mcelog: HARDWARE ERROR. This is *NOT* a software problem!
Jun 20 19:29:52 laptop mcelog: Please contact your hardware vendor
Jun 20 19:29:52 laptop mcelog: MCE 3
Jun 20 19:29:52 laptop mcelog: CPU 5 THERMAL EVENT TSC 581128fdf2c 
Jun 20 19:29:52 laptop mcelog: TIME 1308623392 Mon Jun 20 19:29:52 2011
Jun 20 19:29:52 laptop mcelog: Processor 5 below trip temperature. Throttling disabled
Jun 20 19:29:52 laptop mcelog: STATUS c000000088260c00 MCGSTATUS 0
Jun 20 19:29:52 laptop mcelog: MCGCAP c09 APICID 5 SOCKETID 0 
Jun 20 19:29:52 laptop mcelog: CPUID Vendor Intel Family 6 Model 42
Jun 20 19:29:52 laptop mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
Jun 20 19:29:52 laptop mcelog: HARDWARE ERROR. This is *NOT* a software problem!
Jun 20 19:29:52 laptop mcelog: Please contact your hardware vendor
Jun 20 19:29:52 laptop mcelog: MCE 4

....


```

Others have [reported]("http://marc.info/?l=linux-kernel&m=130606930631131&w=2") [this]("http://ubuntuforums.org/showthread.php?p=10962698#post10962698") as well.


Anyone else?  My kernel:

Linux laptop 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

using thinkfan, but as you can see the fan is in state 7, which is maxed out..

W

---

### Post by Artemis3 on 2011-06-21
There is a power regression issue introduced in Linux 2.6.38 (yes, the one in Natty), it's been talked about in at least [Phoronix](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1) and [Tom's Hardware](http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html) among others.

Do try to stick to kernel version 2.6.37 or less (you can install it from the [mainline ppa](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) while this issue is documented and solved. The Phoronix guy is doing a bunch of power usage tests to fully demonstrate the extent of the problem, but it is already known **the problem occurred in 2.6.38** and has not been fixed.

[url=http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1][img]http://www.phoronix.com/data/img/results/linux_mobile_uffda/1.png[/img]
[img]http://www.phoronix.com/data/img/results/linux_mobile_uffda/2.png[/img][/url]
[[img]http://media.bestofmicro.com/P/7/293803/original/battlife1104.png[/img]](http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html)

I don't know if it's related (still waiting the results) but not properly controlling the processor power states might explain something...

---

### Post by VValdo on 2011-06-21
Hmmm...  I didn't know about this.  I can't imagine this is resulting in these (hopefully wrong) reports of overheating... but nevertheless I might back off, assuming that all the modules I'm using will still work on this newer hardware... I guess it should.

has anyone else seen these errors?

---

### Post by mejo on 2011-06-21
Hey Vvlado,

I didn't notice the issues you describe yet, but now that I checked syslog and mcelog, I realized that my system has exactly the same issues. It even reports the 'Package power limits' to syslog when thinkfan has level 0 or 1.

Also running linux kernel 2.6.39-0 from kernel ppa.

---

### Post by VValdo on 2011-06-21
Well I've got some updates...

I just tried 2.6.37 and did a 20-minute build.

"Hardware Error" == gone.  Not a peep in the logs or suggestion of any issues.  This is a definite kernel-related regression.

Other observations from .37-- you'll lose full resolution w/the intel driver (it doesn't autodetect 1920x1080) as well as two-finger scrolling and wifi.

So for now, I'm going to trust lm_sensors that I am not in fact overheating or overvolting or something weird and stay with .39...  I'm not sure if someone needs to report this or if it's being looked at already...

Glad that I'm not the only one with this issue though :)

---

### Post by mejo on 2011-06-21
I suggest that you report this to the kernel hackers. You already posted the link to a bugreport ([https://bugzilla.kernel.org/show_bug.cgi?id=36182](https://bugzilla.kernel.org/show_bug.cgi?id=36182)), so maybe adding your information there would be a good starting point. If this is a regression, then it should be fixed by the kernel hackers.

---

### Post by VValdo on 2011-06-21
I'll try to remember to update the bug tomorrow.  Feel free, anyone & everyone.

A quick update though that makes this a little less of a freakout situation-- I was bold and did a [burnin test]("http://www.mersenne.org/freesoft/")-- ran a CPU burning app on all cores for 20 minutes or so.  I saw those same errors as described above in the log... temps were reported as steady at 73-75C...  and the cpu stress test seemed to pass w/o errors.

Take it for what it will, but I wonder if these errors are as bad as they suggest.

---

### Post by bjordan1979 on 2011-06-21
**Edit: Never mind I finally got it working. I'll leave everything below just for context though.**

> **robin.nightingale said:**
> 
**with a littel work:**

The Nividia Graficcard, Install the Drivers via the additional drivers tool and restart. unfortunatly it appears to be that the nvidia driver does not support hybrid graphics cards, or NVIDIA Optimus.
So youll  need to go into the bios and turn off Optimus and force the system to use the discrete graphics card.

I cannot for the life of me get the NVidia card to work, it's about to drive me fscking insane. I wanted to use 10.04 or 10.10 but gave up and decided to install Natty to try to get it working. I installed (64bit) and during the install it downloaded updates. On first boot I have the nvidia-currrent drivers installed and active but not in use.

I run nvidia-xconfig to configure the xorg.conf, shutdown, boot into BIOS set it to discrete and when I boot it hangs after "Checking battery state .....". Basically meaning X had a fatal crash and didn't start.

If I switch over to a terminal and check the Xorg.0.log I get the error "No Screens Found"

Here's my full Xorg.0.log:

```

[     5.452] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[     5.452] X Protocol Version 11, Revision 0
[     5.452] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     5.452] Current Operating System: Linux bjordan-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[     5.452] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=35b430d2-5850-40e6-862c-4bcbd61c734f ro quiet splash vt.handoff=7
[     5.452] Build Date: 21 May 2011  11:48:41AM
[     5.452] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[     5.452] Current version of pixman: 0.20.2
[     5.452]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.452] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.452] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 21 16:14:39 2011
[     5.452] (==) Using config file: "/etc/X11/xorg.conf"
[     5.452] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.452] (==) ServerLayout "Layout0"
[     5.452] (**) |-->Screen "Screen0" (0)
[     5.452] (**) |   |-->Monitor "Monitor0"
[     5.452] (**) |   |-->Device "Device0"
[     5.452] (**) |-->Input Device "Keyboard0"
[     5.452] (**) |-->Input Device "Mouse0"
[     5.452] (==) Automatically adding devices
[     5.452] (==) Automatically enabling devices
[     5.452] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.452]     Entry deleted from font path.
[     5.452] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.452]     Entry deleted from font path.
[     5.452] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.452]     Entry deleted from font path.
[     5.453] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.453]     Entry deleted from font path.
[     5.453] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.453]     Entry deleted from font path.
[     5.453] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     5.453] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.453] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     5.453] (WW) Disabling Keyboard0
[     5.453] (WW) Disabling Mouse0
[     5.453] (II) Loader magic: 0x7e0280
[     5.453] (II) Module ABI versions:
[     5.453]     X.Org ANSI C Emulation: 0.4
[     5.453]     X.Org Video Driver: 10.0
[     5.453]     X.Org XInput driver : 12.3
[     5.453]     X.Org Server Extension : 5.0
[     5.453] (--) PCI:*(0:0:2:0) 8086:0126:17aa:21d0 rev 9, Mem @ 0xf1400000/4194304, 0xe0000000/268435456, I/O @ 0x00006000/64
[     5.453] (--) PCI: (0:1:0:0) 10de:1057:17aa:21d0 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[     5.454] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[     5.454] (II) LoadModule: "extmod"
[     5.455] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     5.455] (II) Module extmod: vendor="X.Org Foundation"
[     5.455]     compiled for 1.10.1, module version = 1.0.0
[     5.455]     Module class: X.Org Server Extension
[     5.455]     ABI class: X.Org Server Extension, version 5.0
[     5.455] (II) Loading extension MIT-SCREEN-SAVER
[     5.455] (II) Loading extension XFree86-VidModeExtension
[     5.455] (II) Loading extension XFree86-DGA
[     5.455] (II) Loading extension DPMS
[     5.455] (II) Loading extension XVideo
[     5.455] (II) Loading extension XVideo-MotionCompensation
[     5.455] (II) Loading extension X-Resource
[     5.455] (II) LoadModule: "dbe"
[     5.455] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     5.455] (II) Module dbe: vendor="X.Org Foundation"
[     5.455]     compiled for 1.10.1, module version = 1.0.0
[     5.455]     Module class: X.Org Server Extension
[     5.455]     ABI class: X.Org Server Extension, version 5.0
[     5.455] (II) Loading extension DOUBLE-BUFFER
[     5.455] (II) LoadModule: "glx"
[     5.455] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[     5.466] (II) Module glx: vendor="NVIDIA Corporation"
[     5.466]     compiled for 4.0.2, module version = 1.0.0
[     5.466]     Module class: X.Org Server Extension
[     5.466] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[     5.466] (II) Loading extension GLX
[     5.466] (II) LoadModule: "record"
[     5.467] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     5.467] (II) Module record: vendor="X.Org Foundation"
[     5.467]     compiled for 1.10.1, module version = 1.13.0
[     5.467]     Module class: X.Org Server Extension
[     5.467]     ABI class: X.Org Server Extension, version 5.0
[     5.467] (II) Loading extension RECORD
[     5.467] (II) LoadModule: "dri"
[     5.467] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     5.467] (II) Module dri: vendor="X.Org Foundation"
[     5.467]     compiled for 1.10.1, module version = 1.0.0
[     5.468]     ABI class: X.Org Server Extension, version 5.0
[     5.468] (II) Loading extension XFree86-DRI
[     5.468] (II) LoadModule: "dri2"
[     5.468] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     5.468] (II) Module dri2: vendor="X.Org Foundation"
[     5.468]     compiled for 1.10.1, module version = 1.2.0
[     5.468]     ABI class: X.Org Server Extension, version 5.0
[     5.468] (II) Loading extension DRI2
[     5.468] (II) LoadModule: "nvidia"
[     5.468] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     5.477] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.477]     compiled for 4.0.2, module version = 1.0.0
[     5.477]     Module class: X.Org Video Driver
[     5.479] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[     5.479] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.480] (++) using VT number 7

[     5.480] (EE) No devices detected.
[     5.480] 
Fatal server error:
[     5.480] no screens found
[     5.480] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[     5.480] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     5.480] 


```Here's my Xorg.config

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```For the guys that have it working in discrete mode will you please share your Xorg.conf? 

If anyone has any insights I'd greatly appreciate it. I've spent the past few nights fighting this and will continue tonight. It's about to drive me crazy.

I noticed dmesg | grep nvid gives me the following line:

nvidia: module license 'NVIDIA' taints kernel.

From what I've read that's just a warning about it being proprietary so I don't think that's an issue.

---

### Post by VValdo on 2011-06-21
Sorry-- as of now I'm still using the Intel driver so don't have much to say on nVidia yet...

for anyone who wants to contribute to the bug report on the "hardware error" issue, the bug can be found here:

[https://bugzilla.kernel.org/show_bug.cgi?id=36182](https://bugzilla.kernel.org/show_bug.cgi?id=36182)

---

### Post by donniezazen on 2011-06-22
> Linux donnie-laptop 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 09:08:47 UTC 2010 x86_64 x86_64 x86_64 GNU/Linux

Maverick kernel, TLP, Integrated graphic card, and Thinkfan. The temperature stays around 50. The fan runs on level 1 or 2. I might get good battery life with this setup.

Which kernel in mainline ppa is stable maverick kernel? The that i have installed has messed up with sound. I have no sound.

Changing to integrated graphic card made a big difference in battery. If i keep it so, i won't be able to use bumblebee.

The temp is still 4-5 degrees higher in present setup.

---

### Post by VValdo on 2011-06-22
Hmmm I'm getting total lockups about once a day still-- 11.04, 2.6.39.0...  w520.

Nothing in the logs at all.  It's as if nothing happened at all.

Symptoms:  ping stops, ui unresponsive.  total lock.

Anyone else?

---

### Post by donniezazen on 2011-06-23
I set bios to default and did a clean install. Unity showed up without any driver install which is sweet. When ever i have problem with xorg two things usually works.

rm /etc/X11/xorg.conf

or

dkpg-reconfigure xserver-xorg

After installing 2.6.37 it would take me to black screen with cursor. I would just restart gdm to get to unity desktop.

---

### Post by bjordan1979 on 2011-06-23
> **VValdo said:**
> Hmmm I'm getting total lockups about once a day still-- 11.04, 2.6.39.0...  w520.

Nothing in the logs at all.  It's as if nothing happened at all.

Symptoms:  ping stops, ui unresponsive.  total lock.

Anyone else?

On 11.04 I was having complete lockups as well. UI stopped responding, couldn't switch to a terminal or anything and would have to hard reset. If I removed xorg.conf and switched back to integrated it worked fine. My lockups were very often on the following setup.

Natty 11.04
Kernel: 2.6.38-8-generic
Nvidia: 270.41.06
X version: 11.0
X vendor version: 1.10.1

Mine also started happening after I installed xubuntu-desktop and connected to WiFi. Although considering switching off the Nvidia driver solved the issue I tend to think it was still related to that. Unfortunately I wiped the machine before backing up any of the logs.

---

### Post by VValdo on 2011-06-24
The thing is, I'm having the lockups and I'm using integrated solely right now.

100% UI lockup.  Ping stops.  Everything stops.  and NOTHING in any log that I've found.

It's like it freezes hard.  Kernel does'nt oops.. nothing.

---

### Post by mejo on 2011-06-24
> **VValdo said:**
> The thing is, I'm having the lockups and I'm using integrated solely right now.

100% UI lockup.  Ping stops.  Everything stops.  and NOTHING in any log that I've found.

It's like it freezes hard.  Kernel does'nt oops.. nothing.

I discover lockups as well since two days. My feeling is that this is since firefox was upgraded to version 5, but that may be unrelated. Do you know of bugreports regarding this issue?

---

### Post by VValdo on 2011-06-24
No... no bug reports.  I'm not sure even how to qualify it... don't know what's causing it.  If you're having these lockups as well, can you post the kernel, machine-type, and anything else you might think is relevant?  Symptoms, etc...

I can't imagine it's Firefox 5.. I think I was having this before that, and I don't know how a browser would lock it up so hard the kernel isn't oopsing into the logs...

---

### Post by mejo on 2011-06-24
> **VValdo said:**
> No... no bug reports.  I'm not sure even how to qualify it... don't know what's causing it.  If you're having these lockups as well, can you post the kernel, machine-type, and anything else you might think is relevant?  Symptoms, etc...

I can't imagine it's Firefox 5.. I think I was having this before that, and I don't know how a browser would lock it up so hard the kernel isn't oopsing into the logs...

Ok, here are some details:

- ThinkPad T420 (Intel Core i5 Processor, 6GB RAM, 40GB SSD Harddisk, integrated Intel Graphics)
- up-to-date Ubuntu 11.04 64bit, encrypted rootfs (dm-crypt+LUKS), Unity desktop with default settings
- 2.6.39-0-generic kernel from kernel PPA
- thinkfan with updated temperature sensors in config
- TLP from linrunners PPA installed and activated

The lockups I discover are hard freezes. Nothing happens until I reset the Laptop by pressing the power button for several seconds. I discovered these lockups only while browsing with firefox so far, but that may be for the reason that I use firefox most of the time on this laptop.

And, most imporantly: I didn't discover these lockups in the beginning. I discover them since some days, before that they didn't happen.

---

### Post by VValdo on 2011-06-24
Interesting-- we're using the same kernel, but different CPUs, different machines (W520 & T520), different processor (I have an i7)...  we have in common thinkfan, the same kernel, the same overall OS..  I think I had the freeze with both unity and classic, although I'm not 100% sure as I recently switched from old gnome to new...  I did have this freeze about once a day pre-firefox 5 though, w/a non-cryptfs system.  Temperature was not an issue-- it froze while I was running gkrellm and I saw nothing unusual there.  Load wasn't even high.. I was just typing or something when BAM.  Ice cold.

Which video driver were you using?
  
W

PS--- I LOVE this keyboard.. it's ridiculous how good it is.. I wonder if they make standalone USB keyboards with the Thinkpad feel... will have to look into this.
> **mejo said:**
> Ok, here are some details:

- ThinkPad T420 (Intel Core i5 Processor, 6GB RAM, 40GB SSD Harddisk, integrated Intel Graphics)
- up-to-date Ubuntu 11.04 64bit, encrypted rootfs (dm-crypt+LUKS), Unity desktop with default settings
- 2.6.39-0-generic kernel from kernel PPA
- thinkfan with updated temperature sensors in config
- TLP from linrunners PPA installed and activated

The lockups I discover are hard freezes. Nothing happens until I reset the Laptop by pressing the power button for several seconds. I discovered these lockups only while browsing with firefox so far, but that may be for the reason that I use firefox most of the time on this laptop.

And, most imporantly: I didn't discover these lockups in the beginning. I discover them since some days, before that they didn't happen.

---

### Post by bjordan1979 on 2011-06-24
> **VValdo said:**
> PS--- I LOVE this keyboard.. it's ridiculous how good it is.. I wonder if they make standalone USB keyboards with the Thinkpad feel... will have to look into this.

I agree and alreday looked into it! Here ya go. :D

[http://www.amazon.com/ThinkPad-USB-Keyboard-with-TrackPoint/dp/tags-on-product/B002ONCC6G](http://www.amazon.com/ThinkPad-USB-Keyboard-with-TrackPoint/dp/tags-on-product/B002ONCC6G)

They also make a version with a touch pad. Only issue is no numberpad.

---

### Post by jonathanysp on 2011-06-29
Apparently there is a workaround for the Linux kernel power regression bug: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

Im waiting for my T420 to come, can someone try this and see if it helps with the battery life and overheating?

---

### Post by VValdo on 2011-06-29
Wow this is great.  Glad I still check this thread.  I'm gonna give it a shot...

Update:  well it didn't kill my system.  I'm getting an hour extra being reported, but only time will tell..

---

### Post by jonathanysp on 2011-06-29
Oh thats nice, how about the temperatures?

---

### Post by VValdo on 2011-06-29
Temps are low.. about what they were.  Not sure about battery life yet.. it's always hard to compare. But seems to work on the w520 without any issue.

---

### Post by donniezazen on 2011-06-29
You always get a better temp and battery life with only integrated graphic card. I will run Phoronix test suite to see if it actually makes any difference. You can't do that if you play games.

Phoronix also reported on twitter that he found another work around to get about 8% more battery juice.

Lets see how it goes.

---

### Post by VValdo on 2011-06-29
ARGH.  I just had another HARD freeze.  Integrated Intel driver, 2.6.39-0.

Everything froze and NOTHING in any log I can find, including kernel logs. Is anyone else having similar symptoms?

One thing-- I was playing music at the time, and it got caught in a loop-, same 2 second clip cycling over and over.

Update:  I've just updated the kernel to 3.0rc5.  One thing I notice immediately is I have a "wireless" light next to bluetooth under the monitor.  I will report if I get another freeze.

Again, this is w520.

---

### Post by wangston on 2011-06-29
yup, i have this problem too. seems to be related to suspend, and maybe to plugging in the power? and i can't find anything in the logs either.

i wasn't running thinkfan before, just installed it today, i have a fantasy that the lack of fan at all (w/o thinkfan the fan was never running, now it comes on every now and then) was causing the crashes and now that i have thinkfan things will be better. i know from your previous posts that you've already got thinkfan...

---

### Post by VValdo on 2011-06-30
Yeah... the thing is.. I don't think there were any power events during my freezes.  I'm just sitting here, activley using the computer and then... lock.

This last time is the first time I was playing sound at the same time and got in the 1 second loop as if it were playing whatever it was in the buffer and just re-dumping it... dunno.

Let's see if this new kernel does anything...  if I get the freeze again, I'll report here.

---

### Post by VValdo on 2011-06-30
More notes:

after updating to linux 3.0rc5 the thermal sensors have moved (so update them in /etc/thinkfan.conf).  There are more too.

```
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/coretemp.0/temp4_input
sensor /sys/devices/platform/coretemp.0/temp5_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/thermal/thermal_zone0/temp
```

---

### Post by VValdo on 2011-07-07
Update a week later-- after moving to 3.0rc5 I haven't had a SINGLE freeze of any sort.

---

### Post by VValdo on 2011-07-08
Final update from me, since this is a T420 thread-- anyone else who has a W520 there's a [thread dedicated to that machine]("http://ubuntuforums.org/showthread.php?t=1780703").

---

### Post by johanneswilm on 2011-07-10
Hi,
most of the instructions here worked. Yet when I tried to update to kernel 3.0rc5 or 3.0rc6, I get a kernel paging oops right when X11 is supposed to start. My system is mainly natty, the kernel images are oneiric though and I also had to grab the module-init-tools from oneiric.

I have a T420 -- 4177-Q5U to be precise. Did any of you have similar experiences? Anyone with suggestions on what to do about this? Did the freezing problems with kernel 2.6.38 also happen for T420 owners or only those with T520?

---

### Post by johanneswilm on 2011-07-10
after updating the entire system to oneiric, using the official kernel-3.0 image, and deleting the /run-folder the kernel oops disappeared.

---

### Post by donniezazen on 2011-07-10
What is kernel paging oops?

---

### Post by johanneswilm on 2011-07-10
it's just some bug. don't worry about it as long as you stick to the official ubuntu packages.

---

### Post by amerikkanu on 2011-07-19
Hi guys and thanks for the help.  I've pretty much got thinkfan up and running, but I don't have the file

/sys/devices/virtual/hwmon/hwmon0/temp1_input

for sensor to refer to in /etc/thinkfan.conf.  What does this sensor refer to?  (motherboard temp?)  And how can I find it?  Or is the file generated by some command I've missed?  Thanks!

---

### Post by donniezazen on 2011-07-19
> **amerikkanu said:**
> Hi guys and thanks for the help.  I've pretty much got thinkfan up and running, but I don't have the file

/sys/devices/virtual/hwmon/hwmon0/temp1_input

for sensor to refer to in /etc/thinkfan.conf.  What does this sensor refer to?  (motherboard temp?)  And how can I find it?  Or is the file generated by some command I've missed?  Thanks!

Did you check out FAQ section of [http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)

> sudo apt-get install lm-sensors
> sudo sensors-detect
Enter all the way till end. They it asks you to save everything. Write yes and then enter.
> find /sys/devices -type f -name "temp*_input"
This will provide you list of sensor files.
Make sure you put sensor before each line. Reboot. And you are all set.

---

### Post by amerikkanu on 2011-07-19
Wow, thanks for the quick reply!  Yeah, I went through the basic setup and Thinkfan is running.  I would just like to get that last sensor up and running.  And I'd been to that German wiki page, but got stuck with his find command.  Thanks for giving me the correct one!  Unfortunately, it just returns

```
$ find /sys/devices -type f -name "temp*_input"
/sys/devices/platform/coretemp.0/temp1_input
/sys/devices/platform/coretemp.2/temp1_input

```

So what is my missing sensor monitoring?  Motherboard?  I must have such a sensor?  Thanks again.

---

### Post by amerikkanu on 2011-07-19
I forgot to mention a possibly crucial detail:  I've upgraded to the 2.6.39-3 kernel.  So maybe there's not yet support in this kernel for my mysteriously missing sensor?  I'll get to googling on that

---

### Post by jonathanysp on 2011-07-22
Has anyone gotten suspend to work properly? When i suspend, the screen turns black (but blacklight still on) and the power button, caps lock light and the moon flashes quickly. Everything is locked up and the only way to do anything else is to hold the power button to force shutdown the laptop. I'm on the 2.6.38-10-generic-pae kernel.

---

### Post by mejo on 2011-07-23
> **jonathanysp said:**
> Has anyone gotten suspend to work properly? When i suspend, the screen turns black (but blacklight still on) and the power button, caps lock light and the moon flashes quickly. Everything is locked up and the only way to do anything else is to hold the power button to force shutdown the laptop. I'm on the 2.6.38-10-generic-pae kernel.

I discover the same bug when trying to suspend to RAM. This is with amd64 2.6.38-10-generic kernel.

This is a severe issue, as it might lead to damaged hardware. Suspend to RAM is the default for several situations (closing lid, idling in battery mode, ...). To me it already happend twice that I didn't recognize the crash immediately. The laptop got extremely hot as the cpu seems to run crazy in these crashes.

Here's a bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842)

In the buglog, someone claimed, that the kernel from [m https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065/comments/38]("http://ubuntuforums.org/m%20https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065/comments/38") fixes the issue. I didn't try it out yet.

---

### Post by jonathanysp on 2011-07-23
> **mejo said:**
> I discover the same bug when trying to suspend to RAM. This is with amd64 2.6.38-10-generic kernel.

This is a severe issue, as it might lead to damaged hardware. Suspend to RAM is the default for several situations (closing lid, idling in battery mode, ...). To me it already happend twice that I didn't recognize the crash immediately. The laptop got extremely hot as the cpu seems to run crazy in these crashes.

Here's a bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842)

In the buglog, someone claimed, that the kernel from [m https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065/comments/38]("http://ubuntuforums.org/m%20https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065/comments/38") fixes the issue. I didn't try it out yet.

mm i might give it a try, then i'll report back

---

### Post by mejo on 2011-07-23
> **jonathanysp said:**
> mm i might give it a try, then i'll report back

Just installed it myself. Three attempts to suspend to RAM all were successfully with new kernel. Seems like the kernel really fixes the suspend to ram issues with sandybridge.

Btw, the 2.6.38-11 kernel from natty-proposed should also have the patches applied. Didn't check that one though. Will wait until it goes to natty-updates, and see whether suspend keeps working. The changelog for 2.6.29-11 11.47 mentions three fixed bugs with i915 issues: #761065, #791752 and #793702

In case you check the kernel from proposed, feel free to report back.

---

### Post by jonathanysp on 2011-07-23
> **mejo said:**
> Just installed it myself. Three attempts to suspend to RAM all were successfully with new kernel. Seems like the kernel really fixes the suspend to ram issues with sandybridge.

Btw, the 2.6.38-11 kernel from natty-proposed should also have the patches applied. Didn't check that one though. Will wait until it goes to natty-updates, and see whether suspend keeps working. The changelog for 2.6.29-11 11.47 mentions three fixed bugs with i915 issues: #761065, #791752 and #793702

In case you check the kernel from proposed, feel free to report back.

It doesnt seem work to work for me (i tried the 3.0-1 pae one), which kernel are you using? and do you have to apply the patch manually or are the debs already patched?

---

### Post by mejo on 2011-07-24
> **jonathanysp said:**
> It doesnt seem work to work for me (i tried the 3.0-1 pae one), which kernel are you using? and do you have to apply the patch manually or are the debs already patched?

where did you fetch that 3.0-1 kernel? I didn't try 3.0 yet, and I'm not even aware of Ubuntu 3.0 kernel binaries. Is the 3.0-1 kernel you were testing is a mainline/vanilla kernel.org kernel? I don't know whether the [i915 patch to Fix gen6 (SNB) GPU stalling]("https://patchwork.kernel.org/patch/879532/") ([version 2]("https://patchwork.kernel.org/patch/892002/")) made it into the official 3.0 kernel yet.

The two kernels I was refering two are:

1. A kernel binary provided by Canonical Developer Robert Hooker in order to adress bug [#761065]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065"). It's basicly the Ubuntu Natty 2.6.38-10 10.44 kernel with the [i915-Fix-gen6-SNB-GPU-stalling patch]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/3.0-rc3-i915-Fix-gen6-SNB-GPU-stalling.patch") applied. The binaries are published on [kernel.ubunut.com/~sarvatt/]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/").

2. The [official Ubuntu Natty 2.6.38-11 11.47 kernel]("https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-11.47"), currently sitting in the [Natty Proposed Queue]("ftp://ftp.ubuntu.com/ubuntu/dists/natty-proposed/"), and waiting to be pushed to [Natty Updates]("ftp://ftp.ubuntu.com/ubuntu/dists/natty-updates/"). As already written, I'm not sure whether that one includes the mentioned [patch]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/3.0-rc3-i915-Fix-gen6-SNB-GPU-stalling.patch") at all. But I guess that it does.

---

### Post by gwpenn on 2011-07-24
I have the same problem described in  [comment 83]("http://ubuntuforums.org/showpost.php?p=11074988&postcount=83") on a new natty install running on a Thinkpad T410s with integrated graphics.  However, the patched 2.6.38-10 kernel does not fix the issue for me and neither does the proposed 2.6.38-11 kernel.

Suspend works fine on the latest live cd image, which is kernel 2.6.38-8.  However, running that kernel on the installed system, I still have the suspend issue.  

I'd appreciate any ideas.

---

### Post by jonathanysp on 2011-07-24
> **mejo said:**
> where did you fetch that 3.0-1 kernel? I didn't try 3.0 yet, and I'm not even aware of Ubuntu 3.0 kernel binaries. Is the 3.0-1 kernel you were testing is a mainline/vanilla kernel.org kernel? I don't know whether the [i915 patch to Fix gen6 (SNB) GPU stalling]("https://patchwork.kernel.org/patch/879532/") ([version 2]("https://patchwork.kernel.org/patch/892002/")) made it into the official 3.0 kernel yet.

The two kernels I was refering two are:

1. A kernel binary provided by Canonical Developer Robert Hooker in order to adress bug [#761065]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065"). It's basicly the Ubuntu Natty 2.6.38-10 10.44 kernel with the [i915-Fix-gen6-SNB-GPU-stalling patch]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/3.0-rc3-i915-Fix-gen6-SNB-GPU-stalling.patch") applied. The binaries are published on [kernel.ubunut.com/~sarvatt/]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/").

2. The [official Ubuntu Natty 2.6.38-11 11.47 kernel]("https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-11.47"), currently sitting in the [Natty Proposed Queue]("ftp://ftp.ubuntu.com/ubuntu/dists/natty-proposed/"), and waiting to be pushed to [Natty Updates]("ftp://ftp.ubuntu.com/ubuntu/dists/natty-updates/"). As already written, I'm not sure whether that one includes the mentioned [patch]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/3.0-rc3-i915-Fix-gen6-SNB-GPU-stalling.patch") at all. But I guess that it does.

ohh i got downloaded the 3.0 kernels from the oneiric folder just to try it out since it was newer, anyways i'll try the older patch one out now

---

### Post by jonathanysp on 2011-07-25
ok, i tried the 2.6.38 patched kernel from the site but it still doesnt work. Were you using the x64 kernel? I also tried getting the one from natty-proposed but it still doesnt work. Maybe it works best right now with the x64 kernel, but its kinda hard switching from a x86 to x64 installation. Do you have any ideas?

Also, what are you thinkfan.conf settings? I find that my fan always kicks in to full speed pretty easily.

---

### Post by mejo on 2011-07-25
> **jonathanysp said:**
> ok, i tried the 2.6.38 patched kernel from the site but it still doesnt work. Were you using the x64 kernel? I also tried getting the one from natty-proposed but it still doesnt work. Maybe it works best right now with the x64 kernel, but its kinda hard switching from a x86 to x64 installation. Do you have any ideas?

Yes, I'm using the 64bit kernel (amd64 hardware and system), and for me the patched kernels seem to have fixed the issues. At least suspend didn't crash the system since I use the 2.6.38-10 10.44+lp761065 kernel.

> **jonathanysp said:**
>  Also, what are you thinkfan.conf settings? I find that my fan always kicks in to full speed pretty easily.

my /etc/thinkfan.conf contains the following settings:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

(0,    0,    55)
(1,    48,    60)
(2,    50,    61)
(3,    52,    63)
(4,    56,    65)
(5,    59,    66)
(7,    63,    32767)

the threshold values are the default ones, at least I didn't tweak them. my impression is, that with the current kernel and pcie_aspm=force as boot argument, the fan stays quite calm. i've the feeling that with the 2.6.38-10 10.44+lp761065 kernel the laptop even stays cooler than before.

---

### Post by jonathanysp on 2011-07-26
maybe i should give the 64bit kernel a try, since i have 8gb of ram. Are there any drawbacks to using that kernel?

---

### Post by mejo on 2011-07-26
> **jonathanysp said:**
> maybe i should give the 64bit kernel a try, since i have 8gb of ram. Are there any drawbacks to using that kernel?

I'm not aware of any drawbacks of 64bit systems. You even can run 32bit applications there when you install the 32bit libraries.

Running a 64bit kernel with 32bit userland should work as well. But third-party kernel drivers (e.g. proprietary video drivers like fglrx or nvidia) will not work. I haven't tested this yet though, as I always install 64bit userland with 64bit kernel.

---

### Post by jonathanysp on 2011-07-26
> **mejo said:**
> I'm not aware of any drawbacks of 64bit systems. You even can run 32bit applications there when you install the 32bit libraries.

Running a 64bit kernel with 32bit userland should work as well. But third-party kernel drivers (e.g. proprietary video drivers like fglrx or nvidia) will not work. I haven't tested this yet though, as I always install 64bit userland with 64bit kernel.

ahh ok, cause before i heard about 64bit not having flash support and other compatibility issues. But that seems to be fixed now. I shall try out 64bit then.

---

### Post by mejo on 2011-07-26
> **jonathanysp said:**
> ahh ok, cause before i heard about 64bit not having flash support and other compatibility issues. But that seems to be fixed now. I shall try out 64bit then.

I'm not aware of any remaining issues, except that proprietary 32bit software in some cases is slightly slower on a 64bit system. this is the case for flash, but the difference is not notable to me at all. additionally, adobe just released a 64bit flash beta version, so it's only a matter of time until native 64bit flash is available.

apart from these rare cases, 64bit usually performs better than 32bit in most cases.

See also [the 32bit_and_64bit article at help.ubuntu.com]("https://help.ubuntu.com/community/32bit_and_64bit").

---

### Post by Shuur on 2011-07-27
Hi all!
I just recieved my Thinkpad T420 4238-A71 (intel i7, Nvidia Optimus, 500GB HD,...).

I installed Ubuntu Natty 64bit, disabled Optimus in the bios and set to discrete graphics and it works fine!:D

I followed the instruction to force ASPM [here]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") and installed powertop And I now have 5h40min of autonomy on my battery which I find great. (thanks for the link)

I still have a problem and I'm surprised to not be able to find any mentions of this problem...:(

**I'm not able to set the brightness of my LCD**. When I press the button (Fn Home or Fn End), I see the indication in the upper right corner changing but I don't see the brightness actually changing...

According to [thinkwiki]("http://www.thinkwiki.org/wiki/LCD_Brightness"), I should be able to do this from /proc/acpi/[video]("http://www.thinkwiki.org/wiki/LCD_Brightness#")/VID1/LCD0/brightness, the problem is that this file doesn't exist on my computer. I don't find it anywhere in the /proc/acpi folders...

I found this though : 
/etc/acpi/asus-brn-down.sh
/etc/acpi/asus-brn-up.sh

I could try to use [thinkpad_acpi]("http://www.thinkwiki.org/wiki/Thinkpad-acpi"). but apparently it's no longer recommended since kernel 2.6.27 and I'm using :

```
Linux halT420 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```So, are you able to set the brightness of your LCD and do you know why I can't?

Thanks!

---

### Post by donniezazen on 2011-07-27
> **Shuur said:**
> Hi all!
I just recieved my Thinkpad T420 4238-A71 (intel i7, Nvidia Optimus, 500GB HD,...).

I installed Ubuntu Natty 64bit, disabled Optimus in the bios and set to discrete graphics and it works fine!:D

I followed the instruction to force ASPM [here]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") and installed powertop And I now have 5h40min of autonomy on my battery which I find great. (thanks for the link)

I still have a problem and I'm surprised to not be able to find any mentions of this problem...:(

**I'm not able to set the brightness of my LCD**. When I press the button (Fn Home or Fn End), I see the indication in the upper right corner changing but I don't see the brightness actually changing...

According to [thinkwiki]("http://www.thinkwiki.org/wiki/LCD_Brightness"), I should be able to do this from /proc/acpi/[video]("http://www.thinkwiki.org/wiki/LCD_Brightness#")/VID1/LCD0/brightness, the problem is that this file doesn't exist on my computer. I don't find it anywhere in the /proc/acpi folders...

I found this though : 
/etc/acpi/asus-brn-down.sh
/etc/acpi/asus-brn-up.sh

I could try to use [thinkpad_acpi]("http://www.thinkwiki.org/wiki/Thinkpad-acpi"). but apparently it's no longer recommended since kernel 2.6.27 and I'm using :

```
Linux halT420 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```So, are you able to set the brightness of your LCD and do you know why I can't?

Thanks!

[http://www.andresclari.com/blog/enable-nvidia-brightness-control-in-ubuntu-10-04/](http://www.andresclari.com/blog/enable-nvidia-brightness-control-in-ubuntu-10-04/)

---

### Post by mejo on 2011-07-27
> **Shuur said:**
> Hi all!
I could try to use [thinkpad_acpi]("http://www.thinkwiki.org/wiki/Thinkpad-acpi"). but apparently it's no longer recommended since kernel 2.6.27 and I'm using :

```
Linux halT420 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```


I was surprised to read that thinkpad_acpi was depreciated now, but then checked the thinkpad_acpi link you gave, and found the following info box:

> 
As of kernel 2.6.27 the thinkpad-acpi bay and dock drivers should no  longer be used. Instead use the standard ACPI bay and dock drivers. As  of kernel 2.6.31 the thinkpad-acpi bay and dock drivers have been  removed completely.


I understand it the way that only that the bay and dock drivers are depreciated since 2.6.27, not that the whole thinkpad_acpi module is depreciated. But I might be wrong.

Sidenote: setting brightness works out of the box with integrated intel graphics, but be related to the discrete nvidia graphics.

---

### Post by drende on 2011-07-28
Good to hear, Shuur, that it all worked for you this simple! Did you just install 11.04 64bit, with all updates? No kernel rebuilds etc?

How about suspend/resume?

And can you get an external monitor to work with it?

Do any of you think a T420s will work equally fine? Is there any important differences except tighter dimensions and weight?

---

### Post by Shuur on 2011-07-28
Thanks a lot donniezazen, brightness control works now! :P

Yes I just installed Ubuntu 11.04 64bit with all the updates, no kernel rebuild.

Suspend/resume and hibernate also works.

And my Samsung FullHD external monitor works flawlessly on the VGA port!

EDIT : I spoke too soon, suspend resume doesn't work every time apparently...

---

### Post by mejo on 2011-07-28
> **Shuur said:**
> 
Yes I just installed Ubuntu 11.04 64bit with all the updates, no kernel rebuild.

Suspend/resume and hibernate also works.
[...]
EDIT : I spoke too soon, suspend resume doesn't work every time apparently...

As I mentioned earlier in this thread, suspend/resume issues on 64bit Natty have disappeared here since I upgraded to the kernel from [http://kernel.ubuntu.com/~sarvatt/lp761065/natty/](http://kernel.ubuntu.com/~sarvatt/lp761065/natty/)

Maybe you want to give it a try as well, and report back.

---

### Post by donniezazen on 2011-07-28
I don't think installing any kernel will improve performance unless their is a bug, all of these kernels suffer from same power regression issues.

Dual monitor worked initially but i can't get it to work now. If i turn off the LCD both screens go black.

Anyways, i get frustrating battery life, constant fan noise and no optimus i am back to Win 7.

---

### Post by jonathanysp on 2011-07-29
> **mejo said:**
> I'm not aware of any remaining issues, except that proprietary 32bit software in some cases is slightly slower on a 64bit system. this is the case for flash, but the difference is not notable to me at all. additionally, adobe just released a 64bit flash beta version, so it's only a matter of time until native 64bit flash is available.

apart from these rare cases, 64bit usually performs better than 32bit in most cases.

See also [the 32bit_and_64bit article at help.ubuntu.com]("https://help.ubuntu.com/community/32bit_and_64bit").

Ok, i just reinstalled everything with the 64bit kernel and everything works perfectly. Suspend/resume works even without the patched kernel which is interesting.

But the new nvidia drivers from the bumblebee repos seems to be causing things to go weird, anybody experienced this?

---

### Post by robbel on 2011-07-29
> **jonathanysp said:**
> But the new nvidia drivers from the bumblebee repos seems to be causing things to go weird, anybody experienced this?
Yes, there was a bug with update-alternatives, at least for me. There are some bug reports about this here
   [https://github.com/MrMEEE/bumblebee/issues/493#issuecomment-1662510](https://github.com/MrMEEE/bumblebee/issues/493#issuecomment-1662510)
and here:
   [https://github.com/MrMEEE/bumblebee/issues/489](https://github.com/MrMEEE/bumblebee/issues/489)

I think they were already working on a fix.
Cheers!

---

### Post by nrundy on 2011-07-29
> **mejo said:**
> all right, lets see:

you add a kernel module to the list in the config file /etc/modules if you want your system to load the kernel module automatically during the boot process. You can add it by either editing the file with you favourite text editor (gedit, vim, ...), or with the following command:

```
$ sudo echo "coretemp" >> /etc/modules
```afterwards you need to load the kernel module manually, as it's only loaded automatically beginning with the next reboot. load the module the following way:

```
$ sudo modprobe coretemp
```that's it, now the module 'coretemp' should be loaded (check with '$ lsmod')

now about step 6. you reload a kernel module with 'modprobe -r':

```
$ sudo modprobe -r thinkpad_acpi
```First, what's the content of /etc/modprobe.d/options? This file should not exist at all on recent systems. Please post the content of this file.

Second, according to the error message, you load the kernel module thinkpad_acpi with the options 'fan_control=1 fan_control = 1'. I guess that the second option (fan_control = 1) with the spaces between option and value produces the error.

You should check, where these options are set. Post the output of the following:

```
$ grep -ri thinkpad /etc/modprobe.d/
```

Why isn't all this stuff done by the ubuntu developers so it works on a default install of Ubuntu on the T420? I mean the thinkpad is on the certified ubuntu list afterall.

---

### Post by rewyllys on 2011-08-28
> **nrundy said:**
> Why isn't all this stuff done by the ubuntu developers so it works on a default install of Ubuntu on the T420? I mean the thinkpad is on the certified ubuntu list afterall.
@nrundy: Your question is a good one. I'm surprised that this previously quite active thread has gone dormant for the last four weeks.

As I'm currently seriously considering purchasing a ThinkPad T420s, I'd like to ask whether people who have posted in this thread have found any further problems occuring with their laptops.

Have any other T420s owners had problems and/or successes with this model?

Thanks in advance for any responses.

---

### Post by wangston on 2011-08-28
*> *Why isn't all this stuff done by the  ubuntu developers so it works on a default install of 
> Ubuntu on the  T420? I mean the thinkpad is on the certified ubuntu list afterall.

The certified list is kind of a joke. There's a specific configuration of thinkpad that is certified with a specific build of 10.10 - you can't get this build on your own, only from thinkpad - but somehow they are allowed to claim that the whole line is certified. It's total crap.

> **rewyllys said:**
> @nrundy: Your question is a good one. I'm surprised that this previously quite active thread has gone dormant for the last four weeks.

As I'm currently seriously considering purchasing a ThinkPad T420s, I'd like to ask whether people who have posted in this thread have found any further problems occuring with their laptops.

Have any other T420s owners had problems and/or successes with this model?



On 11.04, on my T420, mutliple monitors don't work right, and there's a fair amount of instability. I'd say I get 2 crashes every 3 days, and there are occasional issues with the GUI that require restart to fix (windows look weird, etc.). You might have better luck with NVIDIA graphics - my understanding is that the intel graphics are not supported by 11.04. Hoping that 11.10 will bring some improvement, but windows is a better option if you want everything to work (or a T420 is a worse option if you want ubuntu)

---

### Post by donniezazen on 2011-08-28
I have not used Ubuntu since i got my T420.

---

### Post by rewyllys on 2011-08-28
> **wangston said:**
> *> *Why isn't all this stuff done by the  ubuntu developers so it works on a default install of 
> Ubuntu on the  T420? I mean the thinkpad is on the certified ubuntu list afterall.

The certified list is kind of a joke. There's a specific configuration of thinkpad that is certified with a specific build of 10.10 - you can't get this build on your own, only from thinkpad - but somehow they are allowed to claim that the whole line is certified. It's total crap.



On 11.04, on my T420, mutliple monitors don't work right, and there's a fair amount of instability. I'd say I get 2 crashes every 3 days, and there are occasional issues with the GUI that require restart to fix (windows look weird, etc.). You might have better luck with NVIDIA graphics - my understanding is that the intel graphics are not supported by 11.04. Hoping that 11.10 will bring some improvement, but windows is a better option if you want everything to work (or a T420 is a worse option if you want ubuntu)

Wangston,

Many thanks for your candid and informative comments.  

It's clear that I need to do a good bit more research and thinking before I order a T420s (if, in fact, I wind up doing so).:(

---

### Post by ultimatebuster on 2011-09-01
How did you guys get external monitor working? Everytime I unplug my monitor from VGA, I get only the cursor, which turns into colored bars. CTRL+ALT+F2 doesn't work either, which will actually hide the cursor.

Any ideas? I want to be able to use my dual monitor setup if possible.

---

### Post by redfox1160 on 2011-09-03
> **rewyllys said:**
> Wangston,

Many thanks for your candid and informative comments.  

It's clear that I need to do a good bit more research and thinking before I order a T420s (if, in fact, I wind up doing so).:(

I run 11.04 using the NVIDIA graphics, not the Intel graphics. I have a 9 cell battery, so it will last about 6 hours; but it does not freeze or have any graphical errors. Also, it runs at 46 degrees Celsius (except when I run some programs).

---

### Post by donniezazen on 2011-09-03
I tried Oneiric Beta 1 today. External monitor worked seamlessly with Nouveau. The only regret was a temperature of 65-80 degrees Celsius.

---

### Post by donniezazen on 2011-09-08
Guys i have seen 10 degrees reduction in temperature after adding pcie_aspm=force i915.i915_enable_rc6=1 instead of pcie_aspm=force to /etc/default/grub. Sick, i am back on Ubuntu.

Source:- [https://bbs.archlinux.org/viewtopic.php?id=125954](https://bbs.archlinux.org/viewtopic.php?id=125954)

PS: I have disabled Nvidia GPU for time being.

---

### Post by redfox1160 on 2011-09-08
> **donniezazen said:**
> Guys i have seen 10 degrees reduction in temperature after adding pcie_aspm=force i915.i915_enable_rc6=1 instead of pcie_aspm=force to /etc/default/grub. Sick, i am back on Ubuntu.

Source:- [https://bbs.archlinux.org/viewtopic.php?id=125954](https://bbs.archlinux.org/viewtopic.php?id=125954)

PS: I have disabled Nvidia GPU for time being.

I have a few (noobish) questions about this:

What does
```
pcie_aspm=force i915.i915_enable_rc6=1
```
actually do? 

In the link you posted, one user said that they experienced higher power usage when not idle if they have pcie_aspm set to that. Do you notice any change in power usage from this?

You mentioned that you have the Nvidia GPU disabled, do you think that enabling this will effect the temperature?

Thanks!

---

### Post by donniezazen on 2011-09-08
> **redfox1160 said:**
> I have a few (noobish) questions about this:

What does
```
pcie_aspm=force i915.i915_enable_rc6=1
```
actually do? 

In the link you posted, one user said that they experienced higher power usage when not idle if they have pcie_aspm set to that. Do you notice any change in power usage from this?

You mentioned that you have the Nvidia GPU disabled, do you think that enabling this will effect the temperature?

Thanks!

Phoronix discovered a couple of power regression issues with linux. Google it, if you want details. My power usage has gone down from 25W to 15-17W.

I find Arch Linux a lot better compared to Ubuntu because i have seen power going down to 9-12W which is awesome.

Disabling Nvidia helps a lot. I have seen temperature going down by a couple of degrees which slows down the fan hence giving you some more battery juice. I guess Ubuntu/Linux doesn't handle Nvidia Optimus as well as windows does.

I think 15-17W is still on high side. I want it to be around 13W.

Nonetheless, I am able to use Ubuntu after a long time.

---

### Post by donniezazen on 2011-09-08
Try it and check your power usage using powertop.

---

### Post by redfox1160 on 2011-09-08
> **donniezazen said:**
> Try it and check your power usage using powertop.

It didn't work well for me (using Nvidia card). My temperature stayed about the same 46 - 50 degrees C, and my power usage stayed around 20W.

---

### Post by redfox1160 on 2011-09-09
> **donniezazen said:**
> Try it and check your power usage using powertop.

Maybe I'm editing the file incorrectly? This is what my /etc/default/grub looks like: 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# Added 9/8/11
pcie_aspm=force i915.i915_enable_rc6=1
```
[http://paste.ubuntu.com/685741/](http://paste.ubuntu.com/685741/)

---

### Post by donniezazen on 2011-09-09
> **redfox1160 said:**
> It didn't work well for me (using Nvidia card). My temperature stayed about the same 46 - 50 degrees C, and my power usage stayed around 20W.

46-50 is awesome. What modifications have you done to your system? I get 65 degrees and 25W with basic installation. It drives my system crazy, battery last for hardly 2-4 hours. How is your battery life.

> **redfox1160 said:**
> Maybe I'm editing the file incorrectly? This is what my /etc/default/grub looks like: 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# Added 9/8/11
pcie_aspm=force i915.i915_enable_rc6=1
```
[http://paste.ubuntu.com/685741/](http://paste.ubuntu.com/685741/)

You do not add it at the end of file but change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by redfox1160 on 2011-09-09
> **donniezazen said:**
> 46-50 is awesome. What modifications have you done to your system? I get 65 degrees and 25W with basic installation. It drives my system crazy, battery last for hardly 2-4 hours. How is your battery life.



You do not add it at the end of file but change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

I haven't made any changes to my system besides those needed to get Thinkfan running ([http://ubuntuforums.org/showthread.php?t=1749186#9](http://ubuntuforums.org/showthread.php?t=1749186#9)). My battery lasts about 5 hours (9 cell). I haven't really taken time to test but it usually says 5 hours remaining (give or take 45 minutes) when I unplug the AC adapter.

I also changed the BIOS so that the Nvidia card is used.

---

### Post by rewyllys on 2011-09-11
> **donniezazen said:**
> . . . . You do not add it at the end of file but change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
Donniezazen,
Many thanks for the clarification!:p

My T420 arrived day before yesterday, and I'm happily installing Ubuntu 11.04 on it, so far without any problems <fingers crossed>. The many tips concerning the T420 in these forums have been a GREAT help!!

---

### Post by redfox1160 on 2011-09-11
> **rewyllys said:**
> Donniezazen,
Many thanks for the clarification!:p

My T420 arrived day before yesterday, and I'm happily installing Ubuntu 11.04 on it, so far without any problems <fingers crossed>. The many tips concerning the T420 in these forums have been a GREAT help!!

Oh, looks like I was doing it wrong!

---

### Post by redfox1160 on 2011-09-11
> **donniezazen said:**
> 46-50 is awesome. What modifications have you done to your system? I get 65 degrees and 25W with basic installation. It drives my system crazy, battery last for hardly 2-4 hours. How is your battery life.



You do not add it at the end of file but change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

Okay, I edited the file correctly, and now I am getting ~50 degrees C and only 17.6W

---

### Post by mejo on 2011-09-15
Hello,

Since some weeks, I discover system freezes every now and then. Not sure, what causes them, but if I remember correctly, every time they happen, I listen to music with banshee, and firefox is running.

The freeze is a hard freeze that I'm only able to solve by pressing the power button for several seconds. Neither change to the console works, nor does waiting for minutes help anything. The music doesn't stop, but plays the last second in an endless loop.

I'm running up to date Ubuntu 11.04 with most recent 2.6.38-11-generic amd64 kernel.

Does anybody else discover these kind of hard freezes on a T420? I'm a bit worried whether I might discover hardware issues. The laptop is merely half a year old.

---

### Post by ultimatebuster on 2011-09-21
> **mejo said:**
> Hello,

Since some weeks, I discover system freezes every now and then. Not sure, what causes them, but if I remember correctly, every time they happen, I listen to music with banshee, and firefox is running.

The freeze is a hard freeze that I'm only able to solve by pressing the power button for several seconds. Neither change to the console works, nor does waiting for minutes help anything. The music doesn't stop, but plays the last second in an endless loop.

I'm running up to date Ubuntu 11.04 with most recent 2.6.38-11-generic amd64 kernel.

Does anybody else discover these kind of hard freezes on a T420? I'm a bit worried whether I might discover hardware issues. The laptop is merely half a year old.

I have the same issue. I think this is related to power unplugging/plugging in. The thinkpad sometimes will have power connection problem..

---

### Post by redfox1160 on 2011-09-24
I just got a new Vizio TV, and my laptop is not outputting through the VGA port. I'm using the NVIDIA card, so this may be causing the problem; however, I don't have time to mess with settings right now. Has anyone else run into this problem? Thanks.

---

### Post by eeperson on 2011-09-26
> **redfox1160 said:**
> I just got a new Vizio TV, and my laptop is not outputting through the VGA port. I'm using the NVIDIA card, so this may be causing the problem; however, I don't have time to mess with settings right now. Has anyone else run into this problem? Thanks.

My understanding is that the Nvidia graphics provides output to the displayport and the Intel graphics provides output for the VGA port.  So you need to switch to Intel graphics to use the VGA port.

---

### Post by ultimatebuster on 2011-09-29
When I unplug my VGA cable, the entire interface freezes..

Is anyone also experiencing the same issue?

---

### Post by Amirhossein on 2011-10-07
> **ultimatebuster said:**
> I have the same issue. I think this is related to power unplugging/plugging in. The thinkpad sometimes will have power connection problem..

I had similar issues with power. Unplugging the power caused the laptop to freeze. I believe this is due to broken EFI implementation of ACPI in these machines. So, I disabled EFI (in system bios) and changed to legacy boot. This resolved the issue and almost all other occasional freezes. I'm yet to figure out how to get the back-light keys to work.

---

### Post by ultimatebuster on 2011-10-09
Backlight? What backlight? Thinklight? That works perfectly for me by just doing Fn + PgUp.

Does disabling EFI have any other side effects?

Also, thread for 11.10: [http://ubuntuforums.org/showthread.php?p=11326588](http://ubuntuforums.org/showthread.php?p=11326588)

---

### Post by devlindeboree on 2011-10-10
i've got a literally brand new t420 sitting here (i7, 8gb ram, intel graphics only, 1 hard drive) that i'm preparing to install ubuntu on, and had a couple questions.

1.  should i install 11.10 instead of 11.04?

2.  in terms of actually installing ubuntu, my general plan was to finishing setting up windows, defrag in windows, shrink the HD partition in windows, reboot into windows and make sure things look ok.  then install ubuntu via the ubuntu installer in a dual boot configuration (not wubi).  if  anyone has any advice on my proposed approach, or this process in general, i'd appreciate it.  

i recently installed ubuntu 11.04 on a t400 in a dual boot configuration.  the install went smoothly, but afterwards initially i experienced some fairly major instability with the windows OS.  frequently after i'd use ubuntu, my subsequent boot into windows would fail (start up repairs galore).  in this particular set up i used the ubuntu utility (in their installer) to shrink the windows partition, and i did not reboot into windows after altering this partition size prior to installing ubuntu.  2 months later everything works  (mostly) great, but i'd prefer to avoid that this time around if possible...

thanks.

---

### Post by ultimatebuster on 2011-10-13
Most things works under T420 for 11.04, though a couple of workarounds are needed as indicated by a couple of threads in the forum.

---

### Post by mejo on 2011-11-14
I discover issues with shutting down Ubuntu Oneiric on my T420 lately. Most of the times, the laptop is not halted and powered off, but instead reboots. Does anybody discover similar issues?

---

### Post by Insi5464 on 2011-11-15
I've been running 11.10 on my T420 for about a month now. Almost everything is working perfectly. I am not using a dock. I only have three real issues:
1. Some external monitors work perfectly with it, while others, mainly widescreen monitors shift the display to the left, cutting off the menus from view. Anybody got an idea of how to fix this?

2. I engaged the NmLk at one point to test it out, and it does work. However, something in the system still believes that it is on, even after numerous restarts. Nothing is acting like the NmLk is on, but at the lock screen (not the login screen), there is a warning saying that the NumLock is on, even though it does not act like it. This is not a problem as far as I can tell, but an annoyance.

3. I can't assign the ThinkVantage button to do anything.

Otherwise, this is the perfect hardware-OS combination, in my opinion.

---

### Post by coverup1128 on 2011-11-20
I am still playing with Ubuntu 11.10 and Fedora 16 LiveCDs the main reason being a better external monitor support in Fedora 16.

In Ubuntu, when the laptop is docked and Fn+F7 is pressed, my two monitors switch into mirror mode. If I untick the "Mirrior" button, the diesktop extends across the two monitors but only the leftmost 17" 4x3 monitor actially displays the screen and the unity panel. The 22" monitor on the right turns off, although the gnome-display shows that it is on. I have to click the off button, apply changes, then click on again, apply changes again to actually get it to display the screen. This routinely crashes compiz (or so the message says)

In Fedora, docking/undocking works seemlessly. I only need to put the unit on the dock, or lift it off the dock, The switching displays on and off, and extending the display just works!  

I am wondering whether this is because F16 ships with kernel 3.1, while Ubuntu 10.10 uses 3.0.x kernel. Anybody here has upgraded the kernel to 3.1?

Edit: Oh, on Thinkvantage button... I read somewhere that Thinkvantage button stops working if the grub is installed in the MBR. Makes me wonder whether pressing this button generates acpi events or any codes?

---

### Post by agnul on 2011-11-21
> **Insi5464 said:**
> 2. I engaged the NmLk at one point to test it out, and it does work. However, something in the system still believes that it is on, even after numerous restarts. Nothing is acting like the NmLk is on, but at the lock screen (not the login screen), there is a warning saying that the NumLock is on, even though it does not act like it. This is not a problem as far as I can tell, but an annoyance.
Same issue here, any idea how to fix it? Also, since there is no num-lock led on the keyboard, is there some indicator I can use?

---

### Post by agnul on 2011-11-24
As per the caps lock issue there's a [a bug open in launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/841541"). It seems thinkpads handle two separate num-lock keys, one for the internal keyboard and another for an external usb keyboard, and the two sometimes get mixed up.

---

### Post by lddm00 on 2011-11-26
HI!.
I purchased a T420 a month ago and in general I'm very comfortable and satisfied with the laptop. 

I also experienced the issue of the external monitor only working in the "mirror mode" and shutting down when the laptop screen is turned off. The workaround I have founded is using the 3.1.0 Kernel, then the only problem is that the Ubuntu login screen is not displayed as before, this is solved if you reload the graphical environment (using  for example ctrl+alt+F5 and then ctrl+alt+F7).

About the power+temperature+battery life issues. In light load state (browsing, checking e-mail, writing reports), with the 3.1.0 Kernel I get 50°C, 3500 RPM (fan speed) and aprox 3 hours of battery life. In the 2.6.38 "original natty" Kernel I get like 10°C degrees below and fan speed at 1900-2000 RPM.

I already proved the >  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"
and didn't experienced any improvement. Any ideas of how to improve the situation or why that option is not making any changes? Maybe I'm doing it wrong..

Cheers,
Luis

---

### Post by mejo on 2011-11-28
> **lddm00 said:**
> 
About the power+temperature+battery life issues. In light load state (browsing, checking e-mail, writing reports), with the 3.1.0 Kernel I get 50°C, 3500 RPM (fan speed) and aprox 3 hours of battery life. In the 2.6.38 "original natty" Kernel I get like 10°C degrees below and fan speed at 1900-2000 RPM.

I already proved the <ETC_DEFAULT_GRUB CHANGES>
and didn't experienced any improvement. Any ideas of how to improve the situation or why that option is not making any changes? Maybe I'm doing it wrong..

The changes to /etc/default/grub look correct. did you run 'sudo update-grub' afterwards? You can verify that the changes reached grub.conf by looking into /boot/grub/grub.conf. You should find the options in every linux kernel menuentry, at the line starting with 'linux'.

---

### Post by lddm00 on 2011-11-28
> **mejo said:**
> The changes to /etc/default/grub look correct. did you run 'sudo update-grub' afterwards? You can verify that the changes reached grub.conf by looking into /boot/grub/grub.conf. You should find the options in every linux kernel menuentry, at the line starting with 'linux'.

Thanks Mejo for you kind advise. Since I wasn't sure if I ran the command sudo update-grub last time I did some new tests. What I found is that using the option "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1" I decrease the power usage. From aprox 20.3 watts to 13.4 watts, that give me extra battery life:). About the temperature issue, I didn't found any change, the CPU temp remains the same as also the fan RPM maintains in the same value. I also proved booting windows 7 and I get the same temperatures (around 50-60°C), so I think is not really a problem. It's just very rare because, when using Kernel 2.6.38 I get like 10°C degrees below and fan speed at 1900-2000 RPM.

About the NumLock problem,I'm not experiencing this problem in the Thinkpad T420 with Ubuntu 11.04. But I have experienced that problem when using an old IBM R40 with Ubuntu 10.04, I solved that problem back then using the "numlockx" package. When installed, run the command "numlockx off" in a terminal to disable NumLock.

Hope that's works,
Cheers,
Luis

---

### Post by agnul on 2012-01-18
My problem with num-lock is that the (laptop's) keyboard is working in "normal" mode (no num-lock, no need to run numlockx) but evolution and gnome-screensaver still show the "num-lock on" warning sign. Plugging an external keyboard and pressing num-lock on that removes the warning sign, but only until next boot. Just a minor annoyance, but an annoyance none the less.

---

### Post by coverup1128 on 2012-01-20
I implemented mejo's method for fan speed control. The fan runs much quieter, but it does not seem to turn off completely. I can hear the fan working even though the output of   
cat /proc/acpi/ibm/fan shows 0 speed and status `disabled'. Can somebody confirm this?

Another issue is suspend to RAM. The laptop goes to sleep and wakes up OK, but the battery power continues to trickle away at a low rate while the laptop is suspended. This makes me wonder whether it suspends fully. Eg, unlike other Thinkpads I owned, it does not beep when suspends/resumes. 

If thius helps, I am on Ubuntu 11.04 32bit with PAE kernel.

---

### Post by donniezazen on 2012-01-20
> **coverup1128 said:**
> I implemented mejo's method for fan speed control. The fan runs much quieter, but it does not seem to turn off completely. I can hear the fan working even though the output of   
cat /proc/acpi/ibm/fan shows 0 speed and status `disabled'. Can somebody confirm this?

Another issue is suspend to RAM. The laptop goes to sleep and wakes up OK, but the battery power continues to trickle away at a low rate while the laptop is suspended. This makes me wonder whether it suspends fully. Eg, unlike other Thinkpads I owned, it does not beep when suspends/resumes. 

If thius helps, I am on Ubuntu 11.04 32bit with PAE kernel.

The least my fan goes is around 2000 RPM. Suspend does consume energy but hibernation will not.

---

### Post by Lekensteyn on 2012-01-21
There is now a more reliable method for disabling the nvidia video card which survives suspend: Bumblebee (in combination with bbswitch). Installation instructions can be found on [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969)

---

### Post by coverup1128 on 2012-01-21
I hear some noise when /proc/acpi/ibm/fan shows that the fan is disabled, its speed is 0, and control level is 0. My understanding is that the fan must be completely steady in this case.

I don't have Nvidia, it's all Intel laptop. The the power drain is quite noticeable (4-6% per hour), compared with my Asus EeePC under Ubuntu 10.04 Netbook Remix, which can be on standby for days with very little battery power drained.

---

### Post by donniezazen on 2012-01-30
[http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38](http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38)

Thinkpad wiki is down and i need to generate the list of sensor files for thinkfan.conf. Does anyone know the command?

EDIT:-Found it.

---

### Post by agnul on 2012-02-20
I think this is an old issue and not specific to the t420 but did anyone manage to get a decent sound volume without turning up the slider to 100%? On my system (plain 11.10 install) I can barely hear a thing unless I crank the volume to the max.

---

### Post by donniezazen on 2012-02-20
> **agnul said:**
> I think this is an old issue and not specific to the t420 but did anyone manage to get a decent sound volume without turning up the slider to 100%? On my system (plain 11.10 install) I can barely hear a thing unless I crank the volume to the max.

Have you turned your volume to the full in alsamixer?

In a terminal

```
alsamixer
```

Turn everything up to max except beep.

---

### Post by agnul on 2012-02-20
In alsamixer I have sliders for "Master", "PCM", "S/PDIF 1", "S/PDIF 2", "S/PDIF 3" and "Beep". PCM is set to 100%, the three "S/PDIF" sliders are at 0 and I can't change them, and Beep is at 10%. Turning up the "Master" slider works fine but it looks like it's doing the same thing of turning up the slider in the notification area to 100. 

I'm not sure who's right here ;-) either sound is OK and I'm just complaining about the slider scale being almost useless, or sound is not OK and there's a tweak hidden somewhere I should use to fix it.

---

### Post by donniezazen on 2012-02-20
> **agnul said:**
> In alsamixer I have sliders for "Master", "PCM", "S/PDIF 1", "S/PDIF 2", "S/PDIF 3" and "Beep". PCM is set to 100%, the three "S/PDIF" sliders are at 0 and I can't change them, and Beep is at 10%. Turning up the "Master" slider works fine but it looks like it's doing the same thing of turning up the slider in the notification area to 100. 

I'm not sure who's right here ;-) either sound is OK and I'm just complaining about the slider scale being almost useless, or sound is not OK and there's a tweak hidden somewhere I should use to fix it.

Volume is low in general and you can amplify it. I think in sound menu.

---

### Post by donniezazen on 2012-02-21
Has anyone tested or have a view on what to use TLP or Laptop-mode-tools?

---

### Post by agnul on 2012-02-23
Haven't tested them, in fact I just discovered TLP's existance. Have no clue about processor/kernel details but the optical drive power off sounds cool, maybe using it the drive won't rot away unused like on my previuos laptops. WiFi power adjustment on the other hand is a PITA, on windows is active by default and before discovering it I thought I had a broken wifi. :???:

---

