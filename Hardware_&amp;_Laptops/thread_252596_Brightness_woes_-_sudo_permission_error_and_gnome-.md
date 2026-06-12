---
title: "Brightness woes - sudo permission error and gnome-power-manager"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by TabletGuy on 2006-09-07
Hi all,

Can anyone help me solve the problem with setting brightness.

I am using a Motion Computing M1400 tablet pc. I want to be easily able to change the brightness.

Gnome-power-manager does not have a brightness slider for my machine so to change the brightness I need to do this:

1. Change to root:
sudo su

2. Adjust brightness using echo;
echo 10 > /proc/acpi/video/GFX0/LCD/brightness

When I try to use sudo to do this ie:
sudo echo 10 > /proc/acpi/video/GFX0/LCD/brightness

I get an error:
echo 10 > /proc/acpi/video/GFX0/LCD/brightness

This makes changing the brightness a real hassel. Is there anyway I can get gnome-power-manager to have its brightness slider bars?

Thanks

---

### Post by jko21 on 2006-09-08
Hi,

I am using a Sony vaio fe-21m and i had also some problems with the brightness. I couldn't change it whatever i did. I tried change it by the gnome-power-manager and nothing was happening. Then i tried with that echo command ( i don't remember the excact comand now, something like yours : "echo 10 > /proc/acpi/video/GFX0/LCD/brightness" ) but again nothing. 

Then a friend told me that he changed the brightness with the command smartdimmer ( Ubuntu has the package installed ). 
$ smartdimmer -h
nVIDIA SmartDimmer adjustment tool version 0.1.

Usage: smartdimmer [OPTION]...

Options:
        -g  --get               Query brightness level.
        -s  --set <level>       Set brightness level (1-21)
        -i  --increase          Increase brightness with one level.
        -d  --decrease          Decrease brightness with one level.
        -h  --help              Prints this help text.

I am not sure if this can help you, but it worked for me.

Besides if you want to make it easier, you can go to Configuration Editor 
( $ gconf-editor ) and add the command in metacity  
( /apps/metacity/keybinding_commands )
 
command_1 : /usr/bin/smartdimmer -d
command_2 : /usr/bin/smartdimmer -i

Then go to /apps/metacity/global_keybindings :

run_command_1 : (shortcut key) <Super>F5
run_command_2 : (shortcut key) <Super>F6

Because the Fn key doesn't work i have for shortcut key the Super key (windows key). So if you had eg. Fn+F5 for decrease the brightness in windows, here you can have Super+F5.

Good Luck :)

---

### Post by hughsient on 2006-10-27
> **TabletGuy said:**
> Hi all,
This makes changing the brightness a real hassel. Is there anyway I can get gnome-power-manager to have its brightness slider bars?


You need to either:

a) add generic (old style) acpi brightness support into HAL. Bad plan.
b) wait until the backlight class is used (you'll need a 2.6.19rc3 kernel for this) and use a pretty new HAL.

The brightness changing has always been pretty rubbish in Linux, but that's something we are trying to fix. This should all "just work" for edgy+1.

Thanks,

Richard Hughes.

---

### Post by benste on 2008-03-27
I know this is an older thread, but can someone tell me how to use smartdimmer in the gnome power management?
+ Thx vm for the gconf clue!! It's working.

Does someone know wheather 8.10 will support sony acpi FN keys? 8.04 seems not support it

---

