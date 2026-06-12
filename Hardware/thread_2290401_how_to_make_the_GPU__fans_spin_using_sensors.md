---
title: "how to make the GPU  fans spin using sensors"
date: 2015-08-12
forum: Hardware
---

### Post by mastablasta on 2015-08-12
The GPU fans still do not spin when using OpenGL. it seems they wills ping when running videos and such. but when using OpenGL (minecraft and similar) they are just not spinning for unknown reason. this causes an overheat. where is the problem? I was thinking that maybe it is connected to sensors packages. I installed psensor when I had issues with CPU overheating and I tried to monitor where the overheating occurs. Minecraft used to work just fine but now as the fans don't start spinning it overheats the GPU and it crashes.

how could I solve this? I am on opensource Radeon drivers on old ATI 9600 GPU.

I tried replacing the card (with AMD and NVidia)  but it didn't work. :( so I am back to trying to find the solution with existing card. since it used to work perfectly some time ago.

---

### Post by tristan16 on 2015-08-12
This almost sounds like hardware failure to me. Do the fans spin at all when you first turn the computer on (in BIOS)? Did you make any noticeable change before the fans stopped spinning? If shown, what does psensor say for fan RPM and % power?

---

### Post by mastablasta on 2015-08-13
no fans spin only when it get's too hot not when turning on the PC. they don't spin when running some openGL application. I've noticed that they spin normally when running other applications - it would turn on and spin. 

psenosr doesn't show anything as it doesn't detect the fan on GPU. it only shows the fans on motherboard.

I remembered that the thing worked fine before I installed psensor. I had installed it only to monitor CPU temp which was overheating - reapplied the past and reattached it better - all fine there now. a bnit warm but within parameters.

but on GPU I noticed that it's not spinning. but it does with certain applications. like DirectX stuff on wine. note that GPu doesn't get strained with any software based stuff like doom or old dos games or anything like that. also movies, flash videos... all good. for now it looks only opengl that is getting the freeze.

also if it's hardware failure it would never spin not sometimes yes, sometimes no.

---

### Post by mastablasta on 2015-08-30
i tried to boot the old 14.04 DVD, instaleld glmark2 to it and ran it. sure enough the fans start to spin and system doesn't crash. 

how could i get back to default setup without doing a reinstall? i am not sure if it's the sensor package or perhapse it could also be the fact i changed many cards and installed uninstalled installed... drivers for them. but eventually i had to come back to this card which was the only one that worked norally. i checked the BIOS setting and set the voltage for AGP to high. not sure if it will help or not.

i think it's a strange motherbaord, btu also drivers are bad for linux. for example radeon HD 3650 (officially supported on this PC) works well on linux (live) in my PC, but when i moved it here (thinking i could replace the old card with this newer card and use the brand new card on my PC) the card worked really slow. deskop was slow, cursor moved slow... you woudl say bad driver, but it doesn't seem to be the case as it works well on the other PC.

i am now still searching for older PCIe or AGP card that could replace the radeon 9600.

---

### Post by dino99 on 2015-08-30
the first thing to glance at is dmesg warnings/errors about these sensors: are they all well detected and running without warning/error ?
then the catalyst settings might also help to check abnormal parameters (card set to either 'performance', 'powersaving' or alike)

---

### Post by mastablasta on 2015-08-31
there are no warnings that i can find. i am no longer sure if it's the sensors or one of the driver's install reinstall, PPA install, ppa purge, testing drivers instal, testing drivers purge... that maybe somewhere somehow it messed it up or some residual or wrong config file remained. i am not sure sensors even detect the card temperature. still what i though is if it's possible to use sensors to force it to spin faster or at some speed. in Windows there are various GUi programs where you can set the fan speeds. usefull if you do overclocking.

it's the opensource driver (so no catalyst).

---

### Post by Yellow Pasque on 2015-08-31
> Controlling the fan speed directly is not possible (and would be very dangerous).
-- [http://wiki.x.org/wiki/RadeonFeature/#index3h2](http://wiki.x.org/wiki/RadeonFeature/#index3h2)

---

### Post by mastablasta on 2015-09-01
yes, well i got distracted by that colourful table on numerous occasions it seems...
thanks, i will have another (better) look at that page.

---

### Post by mastablasta on 2015-09-04
So i have a few additional questions after reading the site and before burning the card :)


> You can select the methods via sysfs.  Echo "dynpm" or "profile" to /sys/class/drm/card0/device/power_method
and
> Select the profile by echoing the selected profile to /sys/class/drm/card0/device/power_profile.

there is no such file. what does echoing mean - does it create this file? i though this would add something to the existing file. :-O

the next one is a bit troubling:
> [h=2]Linux kernel parameters[/h]Try *modinfo -p radeon* to find up-to-date parameters.


and when i tried that i got this among others (other  parameters look ok = most on auto or seem to be correct):
```
agpmode:AGP Mode (-1 == PCI) (int)

```
which according to their table means

[TABLE="class: mointable"]
[TR]
[TD]Option  [/TD]
            [TD]Values  [/TD]
            [TD]Default value[SUP]1[/SUP]  [/TD]
            [TD]Explanation[/TD]
        [/TR]
        [TR]
            [TD]radeon.agpmode  [/TD]
            [TD]1, 2, 4, 8, -1  [/TD]
            [TD]0  [/TD]
            [TD]AGP mode, -1 for PCI/PCIe mode[/TD]
[/TR]
[/TABLE]

yeah PCI mode on an AGP card?

anyway checking it here: /sys/class/drm/card0/device/driver/module/holders/radeon/parameters/

it gives 8 which should indicate AGP 8 mode.

quite confusing and difficult to read as each value is in it's own file. quite confusing. i mean compared to some server settings where all would be in a few files.

---

### Post by Yellow Pasque on 2015-09-04
modinfo -p just gives you information on the parameters. It does not tell you what your system has for their values. So if sysfs says agpmode is 8, then it's 8.

> there is no such file. 

First of all, make sure you have permissions when dealing with sysfs. This will give you root permissions (be careful).
```
sudo -s
```
It's also possible your card doesn't support power management, according to the wiki.

> what does echoing mean - does it create this file?
echo means exactly what it sounds like - print what it's given back to stdout. And when it's used with redirection, it's a quick way to create/edit a file without bothering with a text editor, like:
```
echo dynpm > /sys/class/drm/card0/device/power_method
```
[http://www.guru99.com/linux-redirection.html](http://www.guru99.com/linux-redirection.html)

---

### Post by mastablasta on 2016-01-04
Finally some time on my hands and - solved.

Changed two settings in BIOS. i set AGP voltage to high from and turned off CPU quiet fan or something like that.  now the GPU fan turns well and the CPU fan turns faster propperly cooling the CPU. at the same time it is not any louder at least not to me. before CPU also had high temp75-85 C when under load. this now dropped to a more comfortable 60 C.


a celebration followed with a 2 hour minecraft session. :popcorn:

---

### Post by Yellow Pasque on 2016-01-04
Wow. That's a hot box. Glad it's solved though

---

