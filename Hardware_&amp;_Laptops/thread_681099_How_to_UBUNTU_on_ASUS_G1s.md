---
title: "How to UBUNTU on ASUS G1s"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by HoMie_G on 2008-01-28
Hey,

This is a "how to" to get UBUNTU running on the ASUS G1s. All of the information here is compiled mostly from the UBUNTU forums.

(From ClockworkAvian with a little add ons :D)
Working out of the box:

    * bluetooth
    * wifi
    * multimedia keys on the bottom
    * nv driver at proper resolution (using restricted drivers).
    * SD Card reader
    * Wired ethernet
    *CD/DVD Burning/Reading
    * Mic and speakers/sound 

Not tested by me:

    * CF/XD/MMS readers
    * any video out
    * lightscribe burning (reading works great)
    * ESATA port

Not working:
   *wireless LAN LED
   *Mouse LED (the green one in the asus g1 icon near near the touch pad)
   *Toggling between laptop LCD and External screen (this probably works i just do not know how to do it yet, i do not know how to do it through any video out put, please help :S)

Working with a little tweaking:
   1.Web cam (not at max quality)
   2.OLED screen
   3.Blue email led (using thunderled plugin for thunderbird)
   4.Hibernating/suspending
   5. Mx518 mouse buttons
   6.Flashy green LED lights on the side of the screen
   7.touch pad button to toggle between using the touch pad or not
   


1. Webcam:

You might not need to install the first 2 lines, it won't hurt if you do:

```
sudo apt-get install libsdl1.2-dev

sudo apt-get install subversion

sudo chmod +x install-webcam.sh

sudo ./install-webcam.sh
```

(Make sure the downloaded script is on the desktop and that you are running the code when you are on your desktop)

Note: If the camera does not load after double clicking on the camera icon that appeared on the desktop, you might have to change ownership of a  group called "video" . 
 

2. For the OLED:

[http://howto.landure.fr/gnu-linux/ubuntu-gutsy-gibbon/asus-oled-for-ubuntu-7-10-gutsy-gibbon](http://howto.landure.fr/gnu-linux/ubuntu-gutsy-gibbon/asus-oled-for-ubuntu-7-10-gutsy-gibbon)

Just follow the "Fast and obfuscated" it will work in no time. (this is to install the time and date on the OLED).

Also:

[http://lapsus.berlios.de/asus_oled.html](http://lapsus.berlios.de/asus_oled.html)

this is to put images on the OLED screen. It also has the option of turning off the OLED completely. (have not tried it).

3.To use the email LED (the blue one next to the media buttons) use thunderbird email client with thunderled plugin. (have not tired it)

4A. Hibernating/suspending 

for uswsusp to work, you have to configure a swap partition. My swap partition is 400MB, i sometimes have problems waking up from suspending but i do not know if it is because i have a 400MB swap partition. If anyone can elaborate on hibernating/suspending using this method (uswsusp) please do. I always have to unmount my external hard drives or else they give me "unsafe removal" bubble when i wake up from hibernating/suspending. 

to check your swap partition go to the console and type:

```
$ free -m
```


to install hibernating/suspending:

```
sudo apt-get install uswsusp
```

To reconfigure:

```
dpkg-reconfigure uswsusp
```

to use hibernate/suspending:

```
sudo s2disk
```

or

```
sudo s2both
```

4B. To make this way the default way of hibernating/suspending, just follow the instructions on the link below. Make sure to test it out a couple of times first before editing the script. (this method is working somewhat perfectly on my system. sometimes when i wake up from hibernating, only a white screen with a mouse pointer pops up, i typed in my user name and password, and it worked. So the menu is there, you just cant see it.  

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

5. Visit the following link to configure most logitech mice including the Mx518

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

6. Thanks to adam_r:
 To make the green LED lights work (they will just be a solid light they do not flash which, in my opinion, is not annoying) 

```
sudo modprobe -r asus_acpi
sudo modprobe asus-laptop
```
 
to switch them on:
```
sudo echo 1 > /sys/class/leds/asus\:gaming/brightness
```

to switch them off:

```
sudo echo 0 > /sys/class/leds/asus\:gaming/brightness
```

if switching on and off gives you a permission denied error then use:

to switch them on:
```

su
<enter root password>
echo 1 > /sys/class/leds/asus\:gaming/brightness

``` 

to switch them off:
```

su
<enter root password>
echo 0 > /sys/class/leds/asus\:gaming/brightness

``` 

7.for the touchpad, this sums it up: (thanks to adam_r)

```
sudo apt-get install iasl
cat /proc/acpi/dsdt > dsdt
iasl -d dsdt
```

NOTE: I DID NOT EDIT MY DSDT FILE BECAUSE I DID NOT FINE WHAT IT WAS ASKING FOR. THANKS TO NAMAIN WHO TRIED IT OUT. I JUST SKIPPED THE EDITING STEP AND IT WORKED!! 

Edit dsdt.dsl file, and:
    * change all _T_0 to T0 and all _T_1 to T1
    * if you don't like warnings change all Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF)
    * change the line 4456 from 'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}' to 'If (LEqual (^^^P0P2.VGA.DOSF, 0x04)) {}' 

then:

```
iasl -tc dsdt.dsl
```

now you'll get 2 files, dsdt.hex and dsdt.aml, the hex file is if you want to recompile the kernel with a custom dsdt, you dont need that.
the **dsdt.aml** cp to /etc/initramfs-tools:

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo mkinitramfs -o /boot/initrd.img-<uname -r>
{type uname -r in console to check you'r version)
```

of course you have to:

```
sudo apt-get install gsynaptics
```

Back up your xorg just incase you mess up something.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then:
```
sudo gedit /etc/X11/xorg.conf
```

find the part about the toucpad and insert the line:     Option         "SHMConfig" "on"
it probebly should look like this:
```

Section "InputDevice"

    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
    Option         "CorePointer" "true"

EndSection
```

Don't restart yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not start. But don't worry that's why we backed up the previous file. If X fails to start then you will end up in a text console. Log in and type the following to rename the current xorg.conf and restore the previous file:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

now Reboot, and hopefully it will load with no errors, if something goes wrong, restore it from the back up you made.

Feel free to add your own. I hope in the end this how to is completed so that all the features of the G1S are used. Please correct me if i have any mistakes i'm still new to Ubuntu. 

Thanks,
HoMie_G

---

### Post by Namain on 2008-01-29
I've got an ASUS G1s-B2, and I've found that the Kernel suspend and hibernate both seem to work.

However, after resuming neither of my network cards (ethernet and wireless) seem to be detected by NetworkManager.  I've found that uswsusp's s2disk works perfectly, but s2ram freezes my system on resume.

To install the s2disk command:
# sudo apt-get install uswsusp

---

### Post by adam_r on 2008-01-30
uswusps - for suspend/hibernate
custom DSDTfor the touchpad button (gentoo G1 wiki)

for the leds:
```

modprobe asus-laptop
echo 1 > /sys/class/leds/asus\:gaming/brightness

```

---

### Post by HoMie_G on 2008-01-31
> **Namain said:**
> I've got an ASUS G1s-B2, and I've found that the Kernel suspend and hibernate both seem to work.

However, after resuming neither of my network cards (ethernet and wireless) seem to be detected by NetworkManager.  I've found that uswsusp's s2disk works perfectly, but s2ram freezes my system on resume.

To install the s2disk command:
# sudo apt-get install uswsusp

I installed it and when i use it, this is what happens:

$ sudo s2disk
s2disk: Could not stat the resume device file. Reason: No such file or directory

---

### Post by HoMie_G on 2008-01-31
> **adam_r said:**
> uswusps - for suspend/hibernate
custom DSDTfor the touchpad button (gentoo G1 wiki)

for the leds:
```

modprobe asus-laptop
echo 1 > /sys/class/leds/asus\:gaming/brightness

```

When i enter the first line, it says:

FATAL: Error inserting asus_laptop (/lib/modules/2.6.22-14-generic/kernel/drivers/misc/asus-laptop.ko): No such device


and about the touchpad, i went on gentoo g1 wiki. It does not say anything about the button to toggle between enabling/disabling the touchpad.

---

### Post by adam_r on 2008-02-01
> **HoMie_G said:**
> I installed it and when i use it, this is what happens:

$ sudo s2disk
s2disk: Could not stat the resume device file. Reason: No such file or directory

setup your swap correctly:
```
dpkg-reconfigure uswsusp
```

> When i enter the first line, it says:

FATAL: Error inserting asus_laptop (/lib/modules/2.6.22-14-generic/kernel/drivers/misc/asus-laptop.ko): No such device

first you have to unload asus_acpi:
```
sudo modprobe -r asus_acpi
```
then do the rest

> and about the touchpad, i went on gentoo g1 wiki. It does not say anything about the button to toggle between enabling/disabling the touchpad
just the part about making a custom DSDT table (ACPI), dont even recompile the kernel, just put the dsdt.aml file in /etc/initramfs-tools/ and type:
```
sudo mkinitramfs -o /boot/initrd.img-2.6.22-14-generic
```

---

### Post by HoMie_G on 2008-02-03
> **adam_r said:**
> setup your swap correctly:
```
dpkg-reconfigure uswsusp
```



first you have to unload asus_acpi:
```
sudo modprobe -r asus_acpi
```
then do the rest



just the part about making a custom DSDT table (ACPI), dont even recompile the kernel, just put the dsdt.aml file in /etc/initramfs-tools/ and type:
```
sudo mkinitramfs -o /boot/initrd.img-2.6.22-14-generic
```

ok i unloaded the asus_acpi i, now i get a permission denied error. I kinda did something stupid so i guess it's my fault. the first time i did it i inserted "sudo" before the second line of code. is that why it isn't working ?

```
$ sudo modprobe -r asus_acpi
$ modprobe asus-laptop
$ echo 1 > /sys/class/leds/asus\:gaming/brightness
bash: /sys/class/leds/asus:gaming/brightness: Permission denied

```


about the touchpad,
I'm sorry but i have no clue what all this stuff is... where is the dsdt.aml file?  where do you get it from to edit it? i do not want to play around and end up having to install a fresh copy of ubuntu.


if you could, a step by step method of doing it would be much appreciated :D 
Thank you so much, the hibernating is working now :D but do i have to unmount my external hard drives before hibernating? every time i wake my computer from hibernating a "safely remove hardware" bubble pops up.

HoMie_G

---

### Post by adam_r on 2008-02-04
ok this is how to do this:

```
**sudo** modprobe -r asus_acpi
**sudo** modprobe asus-laptop
```

now for the led, i think you need to be root, so if
```
**sudo** echo 1 > /sys/class/leds/asus\:gaming/brightness
```
dosent work so try
```
su
<enter root password>
echo 1 > /sys/class/leds/asus\:gaming/brightness
```

for the touchpad, this sums it up:

```
sudo apt-get install iasl
cat /proc/acpi/dsdt > dsdt
iasl -d dsdt
```



Edit dsdt.dsl file, and:
    * change all _T_0 to T0 and all _T_1 to T1
    * if you don't like warnings change all Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF)
    * change the line 4456 from 'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}' to 'If (LEqual (^^^P0P2.VGA.DOSF, 0x04)) {}' 

then:

```
iasl -tc dsdt.dsl
```

now you'll get 2 files, dsdt.hex and dsdt.aml, the hex file is if you want to recompile the kernel with a custom dsdt, you dont need that.
the **dsdt.aml** cp to /etc/initramfs-tools:

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo mkinitramfs -o /boot/initrd.img-<uname -r>
{type uname -r in console to check you'r version)
```

of course you have to:

```
sudo apt-get install gsynaptics
```

and:
```
sudo gedit /etc/X11/xorg.conf
```

find the part about the toucpad and insert the line:     Option         "SHMConfig" "on"
it probebly should look like this:
```

Section "InputDevice"

    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
    Option         "CorePointer" "true"

EndSection
```

now Reboot, and you'r done

---

### Post by HoMie_G on 2008-02-04
> **adam_r said:**
> ok this is how to do this:

```
**sudo** modprobe -r asus_acpi
**sudo** modprobe asus-laptop
```

now for the led, i think you need to be root, so if
```
**sudo** echo 1 > /sys/class/leds/asus\:gaming/brightness
```
dosent work so try
```
su
<enter root password>
echo 1 > /sys/class/leds/asus\:gaming/brightness
```

for the touchpad, this sums it up:

```
sudo apt-get install iasl
cat /proc/acpi/dsdt > dsdt
iasl -d dsdt
```



Edit dsdt.dsl file, and:
    * change all _T_0 to T0 and all _T_1 to T1
    * if you don't like warnings change all Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF)
    * change the line 4456 from 'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}' to 'If (LEqual (^^^P0P2.VGA.DOSF, 0x04)) {}' 

then:

```
iasl -tc dsdt.dsl
```

now you'll get 2 files, dsdt.hex and dsdt.aml, the hex file is if you want to recompile the kernel with a custom dsdt, you dont need that.
the **dsdt.aml** cp to /etc/initramfs-tools:

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo mkinitramfs -o /boot/initrd.img-<uname -r>
{type uname -r in console to check you'r version)
```

of course you have to:

```
sudo apt-get install gsynaptics
```

and:
```
sudo gedit /etc/X11/xorg.conf
```

find the part about the toucpad and insert the line:     Option         "SHMConfig" "on"
it probebly should look like this:
```

Section "InputDevice"

    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
    Option         "CorePointer" "true"

EndSection
```

now Reboot, and you'r done

Thank you so much, i will try it out today. By the way, can i turn the LED on and off?

---

### Post by adam_r on 2008-02-04
sudo echo 0 > /sys/class/leds/asus\:gaming/brightness
turns it off

go to /sys/class/leds, you have more leds there.

---

### Post by HoMie_G on 2008-02-04
led lights are working!! the "How to" Is now updated

---

### Post by HoMie_G on 2008-02-04
> **adam_r said:**
> ok this is how to do this:

Edit dsdt.dsl file, and:
    * change all _T_0 to T0 and all _T_1 to T1
    * if you don't like warnings change all Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF)
    * change the line 4456 from 'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}' to 'If (LEqual (^^^P0P2.VGA.DOSF, 0x04)) {}' 




I went to my dsdt.dsl file located in my home directory (after i ran all the commands you posted prior to the quoted text), there are no "_T_0" and no "_T_1" 
the second line about the warnings. Do i change every Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF) ?? so in that case i have to do it manually right ?
line 4456 is does not contain 
"'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}"
it contains:

"RSV0,   1, "

I did not continue running the rest and wanted to double check with you.

Thanks again Adam_r

HoMie_G

---

### Post by Namain on 2008-02-05
> **HoMie_G said:**
> I went to my dsdt.dsl file located in my home directory (after i ran all the commands you posted prior to the quoted text), there are no "_T_0" and no "_T_1" 
the second line about the warnings. Do i change every Acquire (MUTE, 0xSOMETHING) to Acquire (MUTE, 0xFFFF) ?? so in that case i have to do it manually right ?
line 4456 is does not contain 
"'If (LAnd (^^^P0P2.VGA.DOSF, 0x04)) {}"
it contains:

"RSV0,   1, "

I did not continue running the rest and wanted to double check with you.

Thanks again Adam_r

HoMie_G

I checked on my G1s-B2 and I didn't have any of those lines either.  Don't worry though, just skip that step, change your Xorg.conf, like it says in the howto and the touchpad disable button will work.

Also I tested the SD card slot and it works out of the box on Gutsy.

---

### Post by HoMie_G on 2008-02-05
yeah, tried it. it worked. now the only important stuff i need to fix is the toggling between my laptop screen and external screen... 

can anyone help??????

---

### Post by adam_r on 2008-02-05
> **HoMie_G said:**
> yeah, tried it. it worked. now the only important stuff i need to fix is the toggling between my laptop screen and external screen... 

can anyone help??????

this accually worked for me once on feisty, but i didnt really care so i dont know how, but i think you need to tweak it with nvidia-settings, find out first how to move bitween screens from command-line and then go from there.

i think it's not worth the truoble, nvidia-settings works fine.

---

### Post by HoMie_G on 2008-02-05
> **adam_r said:**
> this accually worked for me once on feisty, but i didnt really care so i dont know how, but i think you need to tweak it with nvidia-settings, find out first how to move bitween screens from command-line and then go from there.

i think it's not worth the truoble, nvidia-settings works fine.

i tried: 

```
gksudo nvidia-settings
```


and finally got the display to work on my other screen. However, if i pick "Separate X screen" i get to use my lap top screen but not the other screen. When i use the mouse it only works on my laptop screen. The desktop displayed on the other screen is not even my desktop. It has the same background and thats it. I do not know how to control it or anything. it looks just like a screen shot of my desktop with no icons.

If i click twin view mode. the display pops up on both screens, but now i cant even control the laptop from the laptop screen or from the other screen. And only the other screen has my user name log in window, the laptop screen is just an orange background and with a mouse pointer i can move and do nothing with.

i want to be able to shift between my laptop screen and my other screen (when i say "other screen" i mean the external one). Preferably using fn-f8 just like in windows.


Thanks again,

HoMie_G

---

### Post by HoMie_G on 2008-02-05
By the way, is the restricted driver that that is downloaded and installed through ubuntu the same driver from nvidia.com ?? if not, which one should i use? I am currently running the restricted one and i just downloaded one from nvidia.com. the only reason i'm playing around with the driver is that i do not know if i am running my video card at full steam as i have not played any hard core games on ubuntu. and maybe switching screens will work if i install the drivers from nvidia.com. 

Thanks,
HoMie_G

---

### Post by adam_r on 2008-02-05
> **HoMie_G said:**
> By the way, is the restricted driver that that is downloaded and installed through ubuntu the same driver from nvidia.com ?? if not, which one should i use? I am currently running the restricted one and i just downloaded one from nvidia.com. the only reason i'm playing around with the driver is that i do not know if i am running my video card at full steam as i have not played any hard core games on ubuntu. and maybe switching screens will work if i install the drivers from nvidia.com. 

Thanks,
HoMie_G

dont install the drivers from nvidia, if you want to try newer drivers read about "envy" just make sure you remove the nvidia driver you have before installing envy.

> and finally got the display to work on my other screen. However, if i pick "Separate X screen" i get to use my lap top screen but not the other screen. When i use the mouse it only works on my laptop screen. The desktop displayed on the other screen is not even my desktop. It has the same background and thats it. I do not know how to control it or anything. it looks just like a screen shot of my desktop with no icons.

If i click twin view mode. the display pops up on both screens, but now i cant even control the laptop from the laptop screen or from the other screen. And only the other screen has my user name log in window, the laptop screen is just an orange background and with a mouse pointer i can move and do nothing with.

this is not somthing i can help you with, you need a lot of reading about nvidia-settings and xorg.conf on how to operate dual screens.

about the dual screens, i never got "seperate X" to work, but twin view works fine, you can play around with your mouse out of bounds - you will see it will move to the other screen. if you play in nvidia settings under X server Configuration Settings --> layout , you can move the screens around and decide which screen is where, you can allso put them on top of each other and get the exact same window on both screens - but this only works well if you have the same resolution on both screens.

---

### Post by HoMie_G on 2008-02-06
As a side question... does anyone know how to use amarok with the multimedia buttons on the laptop?? 

i tried changing the "global shortcuts" and pressing the corresponding buttons to each command. It changes but does not work.

Any tips ?

---

### Post by Namain on 2008-02-08
I've been playing around trying to get Suspend and Hibernate working better. I've still got some bugs in how the wireless works after resume.

Anyway I just wanted to warn everyone, DO NOT install the ubuntu-laptop-mode package.  This will remove the acpi-support and laptop-mode-tools packages and it will break the "fn" key bindings on this laptop.

---

### Post by Namain on 2008-02-08
I've been having trouble with NetworkManager on my laptop.  When I lose a connection due to:
1. going out of range/too much interference
2. after suspend/hibernate and resume
I'm unable to reconnect.  dmesg says "wlan0: link is not ready", but I haven't found any useful suggestions on how to fix this.

So I did some searching and found wicd (pronounced wicked).  It seems to work much better on the G1s than NetworkManager, but seems to be a little less mature of a project.  Check it out at [wicd.sourceforge.net](wicd.sourceforge.net).

wicd will re-connect properly after it looses a signal, and can keep multiple encryption schemes for one network name (ESSID), because it will identify networks based on the access point's MAC address.

---

### Post by HoMie_G on 2008-02-08
> **Namain said:**
> I've been having trouble with NetworkManager on my laptop.  When I lose a connection due to:
1. going out of range/too much interference
2. after suspend/hibernate and resume
I'm unable to reconnect.  dmesg says "wlan0: link is not ready", but I haven't found any useful suggestions on how to fix this.

So I did some searching and found wicd (pronounced wicked).  It seems to work much better on the G1s than NetworkManager, but seems to be a little less mature of a project.  Check it out at [wicd.sourceforge.net](wicd.sourceforge.net).

wicd will re-connect properly after it looses a signal, and can keep multiple encryption schemes for one network name (ESSID), because it will identify networks based on the access point's MAC address.

Thanks i will try it out... since we are in the subject, i have never been able to log on any encrypted network. I go to the University of Toronto and not once have i been able to log on to the wireless network. Also, i tried the ryerson wireless, still a no go. 

the only way i got on the network is following the instructions on here:

[http://ubuntuforums.org/showthread.php?t=334120](http://ubuntuforums.org/showthread.php?t=334120)

i got to log on for a few minutes on utorwin (university of Toronto wireless network) then it never connected again.
note: both ryerson and U of T need pass phrases to log on, then a user name to use the internet.
I will try wicd and see if it somehow solves this problem.

Thanks,
HoMie_G

---

### Post by Namain on 2008-02-08
Sorry, looks like I was wrong, I'm still sometimes having the same issue when I go out of range of the wireless network.

As far as connecting to a wireless network with encryption on network manager, if you are using WEP, you may have to specify that you are using an ASCII key (if you are using one).  At my University I can't just say WEP passphrase, and it works, I have to specify WEP Hex, or WEP ASCII and enter the corresponding key.
You may have to specify the same way with WPA

On wicd, it will scan for networks, and give you a list of all of the networks it sees (similar to the Windows XP wireless applet).
In order to use encryption on any network, you must go into the drop-down menu for the network (here you can check off the "connect to this network automatically" checkbox)
Then the "Advanced Settings" drop-down, check off the "Use Encryption" checkbox, select the type of encryption that the network uses (WPA1/2, WEP and various other schemes)
Type the network key into the textbox.
Finally, you can collapse both drop down menus, and click the "Connect" hyperlink (the blue letters).  This will connect you to the selected network.

---

### Post by HoMie_G on 2008-02-08
> **Namain said:**
> Sorry, looks like I was wrong, I'm still sometimes having the same issue when I go out of range of the wireless network.

As far as connecting to a wireless network with encryption on network manager, if you are using WEP, you may have to specify that you are using an ASCII key (if you are using one).  At my University I can't just say WEP passphrase, and it works, I have to specify WEP Hex, or WEP ASCII and enter the corresponding key.
You may have to specify the same way with WPA

On wicd, it will scan for networks, and give you a list of all of the networks it sees (similar to the Windows XP wireless applet).
In order to use encryption on any network, you must go into the drop-down menu for the network (here you can check off the "connect to this network automatically" checkbox)
Then the "Advanced Settings" drop-down, check off the "Use Encryption" checkbox, select the type of encryption that the network uses (WPA1/2, WEP and various other schemes)
Type the network key into the textbox.
Finally, you can collapse both drop down menus, and click the "Connect" hyperlink (the blue letters).  This will connect you to the selected network.

well its all good, i just installed wicd but my old network manger is gone, how do i get it back if i wanted to?

---

### Post by HoMie_G on 2008-02-08
Never mind, apparently when you install wicd, the network manager uninstalls.  if you want it back you have to reinstall it. i think im going to try out wicd for a bit first though.

to check the network manager 

```
nm-applet
```

to install it

```
sudo apt-get install network-manager-gnome

```

Peace,

HoMie_G

---

### Post by adam_r on 2008-02-11
> **HoMie_G said:**
> As a side question... does anyone know how to use amarok with the multimedia buttons on the laptop?? 

i tried changing the "global shortcuts" and pressing the corresponding buttons to each command. It changes but does not work.

Any tips ?

keytouch works great, look it up in synaptic

---

### Post by Namain on 2008-02-11
> **HoMie_G said:**
> As a side question... does anyone know how to use amarok with the multimedia buttons on the laptop?? 

i tried changing the "global shortcuts" and pressing the corresponding buttons to each command. It changes but does not work.

Any tips ?

I found that if you remove the gnome shortcut keys for Play/Pause, Stop, Skip to next track, and skip to previous track, then re-add the keys in amarok's global shortcuts, it will work.

To do so, use System -> Preferences -> Keyboard Shortcuts.  A Gnome preferences window will come up.
Then pretend that you are going to assign a new shortcut to each of these keys, but hit backspace instead of assigning a key.  This will remove the assignment.
Next start up Amarok, and assign the media buttons to the intended keys.  You may or may not have to restart Amarok after you assign these keys.
 I had to restart, but I had Amarok running when I was removing Gnome's shortcut keys.

---

### Post by Namain on 2008-02-11
alright I've finally fixed my issues with my wireless not working after I go out of range.  What happens is that I will go out of range of an access point, and when I am in range of another on the same network, my laptop will not re-associate to the network.

  I just have to reload the iwl4965 driver using the following commands:
```

# sudo modprobe -r iwl4965
# sudo modprobe iwl4965

```

The problem is I haven't found a good place to put this to fix my wireless automatically.  For now I've put the attached shell script on my desktop and just run it whenever I have this problem.  Note that it uses gksu in order to get the permissions required to reload the modules.

---

### Post by Namain on 2008-02-13
Hey guys!

I found a wiki, specifically for the G1S line of laptops.  It's at [http://asusg1s.wikidot.com/](http://asusg1s.wikidot.com/). I've been porting the stuff we've been talking about here to the Ubuntu part of the wiki.  Feel free to help out!

---

### Post by hsfelix on 2008-02-25
Hello there guys!

I have a G1s, and i'm new on ubuntu, so I tried your posts to see if I could manage to install g1s at 100%.

All things have worked perfectly!!!

However, got 1 question for you:

It's my mistake or the sound is to low? Even when you push it to top... yeah, it's high, but in XP, doesn't use to play higher?

Many thanks and keep up the good work!!!

---

### Post by HoMie_G on 2008-03-03
> **hsfelix said:**
> Hello there guys!

I have a G1s, and i'm new on ubuntu, so I tried your posts to see if I could manage to install g1s at 100%.

All things have worked perfectly!!!

However, got 1 question for you:

It's my mistake or the sound is to low? Even when you push it to top... yeah, it's high, but in XP, doesn't use to play higher?

Many thanks and keep up the good work!!!

Im glad everything is working fine.
regarding the sound, i do not really hear the difference between playing in XP or UBUNTU. The built in speakers are **** anyways.  let us know if you find out anything :D

---

### Post by Bazilio on 2008-03-21
Does anybody have a problems with webcamera?
it works out of box for me, but image is upside-down.

In windows system it works perfect, webcam detects as D-Max_GD-5A35, device PID code: USB\VID_174F&PID_5A35

In linux it detects as Sonix Technoogy Co., Ltd USB 2.0 Camera

String with "syntek" about my webcam:
```

bazilio@ASUSG1S:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
Bus 006 Device 002: ID 174f:5a35 Syntek
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
```

```
bazilio@ASUSG1S:~$ lsmod | grep video
video 18060 0
uvcvideo 57480 0
compat_ioctl32 2304 1 uvcvideo
videodev 29312 1 uvcvideo
v4l1_compat 15364 2 uvcvideo,videodev
v4l2_common 18432 2 uvcvideo,videodev
usbcore 138632 7 xpad,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
```

Can anyone solve the problem?

---

### Post by DryGoatAir on 2008-04-08
Just a quick question:

Do you use the 32-bit or the 64-bit version of Ubuntu? I have the AK005C model with an Intel Centrino T7500 Core 2 Duo, which is 64-bit. Has any of you tried?

Thanks!

---

### Post by Bazilio on 2008-04-09
32-bit Kubuntu 7.10 KDE 3.5.9

---

### Post by Namain on 2008-04-15
I'm having the same problem with the webcam image being upside-down and haven't found a solution.  I'm running Ubuntu 7.10 i386

---

### Post by pacrep on 2008-05-05
Anyone got an idea how to display cpu, gpu temperature on the oled. Any examples would be great.

I'm using this as the driver:

```
http://falcon.landure.fr/pool/gutsy/asusoled/asusoled_0.02bzr20071230-1_i386.deb
```

---

### Post by pasisti on 2008-05-08
I'm about to buy the Asus G1Sn laptop and install Ubuntu in dualboot. Thank you very much for this guide!

My only concern is that this guide is written for 7.10 (which was the newest back then), but I'm getting the current 8.04 version. Has something changed in the new version that affects this guide? Has someone tried the Ubuntu 8.04 on this laptop?

---

### Post by Kapokin on 2008-05-23
> **pasisti said:**
> I'm about to buy the Asus G1Sn laptop and install Ubuntu in dualboot. Thank you very much for this guide!

My only concern is that this guide is written for 7.10 (which was the newest back then), but I'm getting the current 8.04 version. Has something changed in the new version that affects this guide? Has someone tried the Ubuntu 8.04 on this laptop?

I bought the Asus G1Sn laptop just recently and having used Ubuntu as my main OS for a few years now, I naturally wanted to install it on my G1Sn as well. Dual boot was my intention right from the start, since I use Vista for gaming, and the installation itself was a breeze. Ubuntu 8.04 installed on my machine without any problems and GRUB was automatically configured to include Vista as well. Both operating systems also booted up without any problems.

However, as many threads on this forum, as well as others have indicated, depending on your graphics card, it isn't necessarily easy to get the Nvidia drivers to work on 8.04. Infact, I myself found it downright impossible and I'm currently just waiting for Nvidia to release their final 173.08 drivers. The Nvidia 9500 GS graphics card inside Asus G1Sn doesn't work with any of the older drivers, if I've understood correctly, and despite all my efforts, I couldn't get the 173.08 beta drivers to work. At the moment I have to use my Ubuntu on 800x600 resolution with a generic VESA driver. I'm not really asking for help with the drivers, just stating my experiences. I believe I've tried pretty much all the tricks I managed to find concerning the subject, but since nothing seems to help, I hope the final drivers solve the problem.

Because the low resolution isn't very pleasant to use, I haven't tested Ubuntu Hardy much further. I installed some updates and programs without any problems and the wireless connection works out of the box, so I imagine I'll be quite satisfied with my Ubuntu G1Sn once the I get the display drivers right.

If someone has had more luck with the Nvidia beta drivers, or any other experiences with G1Sn and Ubuntu, I'd be happy to hear!

---

### Post by cygnis1 on 2008-05-24
What kind of tweaking did you do to Thunderled?  I can't seem to get it to work.

---

### Post by Bazilio on 2008-05-24
> **cygnis1 said:**
> What kind of tweaking did you do to Thunderled?  I can't seem to get it to work.
me too. I just leave that useless thing alone.

---

### Post by Ev1L on 2008-05-27
> **Bazilio said:**
> me too. I just leave that useless thing alone.
i would like to have the blue led back in business, sometimes it results to be useful to distract me from serious things :D

i thought it stopped working because i copied thunderbird profile from windows, and there were .exe files in the folder, but removing and reinstalling makes the same.

i tried to manually turn on/off the led and it works.

so, how did you make your working? (question for those above proud of the working blue led)

Update: I solved with the new beta from [http://leonardoprosperi.com/home/projects](http://leonardoprosperi.com/home/projects)

---

### Post by Namain on 2008-06-06
> **Bazilio said:**
> Does anybody have a problems with webcamera?
it works out of box for me, but image is upside-down.

In windows system it works perfect, webcam detects as D-Max_GD-5A35, device PID code: USB\VID_174F&PID_5A35

In linux it detects as Sonix Technoogy Co., Ltd USB 2.0 Camera

String with "syntek" about my webcam:
```

bazilio@ASUSG1S:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
Bus 006 Device 002: ID 174f:5a35 Syntek
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
```

```
bazilio@ASUSG1S:~$ lsmod | grep video
video 18060 0
uvcvideo 57480 0
compat_ioctl32 2304 1 uvcvideo
videodev 29312 1 uvcvideo
v4l1_compat 15364 2 uvcvideo,videodev
v4l2_common 18432 2 uvcvideo,videodev
usbcore 138632 7 xpad,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
```

Can anyone solve the problem?

Best solution I've found it to use the Cheese webcam viewer and use the "flip" effect to put the image right side up.

---

### Post by Namain on 2008-06-06
> **cygnis1 said:**
> What kind of tweaking did you do to Thunderled?  I can't seem to get it to work.

I didn't have to do any tweaking.  Just make sure that you have the asus_acpi module loaded instead of the asus-laptop

```

# sudo modprobe -r asus-laptop
# sudo modprobe asus_acpi

```

EDIT: looks like they actually have added support in the above mentioned beta for the asus-laptop module.

---

### Post by gektor on 2008-06-21
Please help. I don't understand  how to install nvidia drivers on ubuntu?
I can't turn on compiz. I try to install all versions of 100. nvidia drivers.Only NVIDIA-Linux-x86-100.14.09-pkg1 help me-my resolution now 1680x1050,but compiz still not running. I install envy, but it writes:"ENVY ERROR: Your Operative System does not seem to be supported by Envy".Help!!!!Get me full instruction how i can turn on compiz on my asus g1s,please.My video is Nvidia 8600m gt.:lolflag: I want to see beatifull desctop effect's:(  (don't advise Vista!!!)
P.S.:Sorry for my awful english.:(

---

### Post by Ev1L on 2008-06-21
i am not sure about the packages names, but more or less as far as i know, you just have to install nvidia-drivers-new, nvidia-glx-new, restricted-drivers (you should enable them from system->administration->hardware drivers), then you go to system->preferences->appearance and there you find different levels of compiz graphic.
for a finer tuning there is also a compiz applet to install i guess

---

### Post by gektor on 2008-06-21
i'd install all of this.But when i enable restricted-drivers, my resolution become 800x600

---

### Post by Ev1L on 2008-06-21
look if in xorg.conf you're using driver nvidia

---

### Post by gektor on 2008-06-21
Maybe i'm use wrong version of driver?Nvidia geforce 8600m gt,which version is needed?

---

### Post by Ev1L on 2008-06-21
I have Asus G1 with nvidia 7700:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "true"
EndSection

you should have "nvidia" driver
if you have it already, then we have to think about something else.
which ubuntu are you using? and which kernel?

---

### Post by gektor on 2008-06-21
If i write Driver "nvidia", it say"unknown device",set resolution 800x600 and reset this line to "vesa".I think it's because i use wrong driver,but i use NVIDIA-Linux-x86-100.14.19-pkg1 or NVIDIA-Linux-x86-100.14.09-pkg1.
One more sorry for my worse English

---

### Post by Ev1L on 2008-06-21
where do you write nvidia?
have you tried sudo nvidia-settings?

---

### Post by gektor on 2008-06-21
In Xorg.conf
Yes,but when i reboot it resets settings and disable nvidia drivers,and nvidia settings feature says:"You do not appear to be using the nvidia X driver.Please edit your X configuration file " and restart X server.But when i restart X server,it's all like before.

---

### Post by Ev1L on 2008-06-21
ok, did you manually installed drivers from nvidia website?
that could create some inconsistency with ubuntu drivers, but on the other hand it should work as long as you don't update the kernel, then you'll have to reinstall, but at least you have it working.

if you want you could try this:
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

these should be the latest and i hope your card is supported (the same card on my desktop is working)

---

### Post by gektor on 2008-06-21
I try envy.And compiz is turn ON!!!!!!!Yahoooo.But resolution is 1440x900(((

---

### Post by gektor on 2008-06-21
Ohh,it's all ok.Resolution now 1680x1050. Thanks for help a lot,Ev1l.

---

### Post by sprechkaese on 2008-07-09
Hi there,

i'm pretty new to linux at all and i installed the ubuntu on my asus g1s. now as i try to install the cam by that 4 code-lines i got some troubles...

> **HoMie_G said:**
> 
```
sudo apt-get install libsdl1.2-dev

sudo apt-get install subversion

sudo chmod +x install-webcam.sh

sudo ./install-webcam.sh
```


the first and second line work, and i got some stuff i downloaded there without knowing what happens... but well.. dont care ;)

but when i try the third line, the console says:
```
chmod: Access to „install-webcam.sh“ not possible: No such file or directory
``` 

Note: i got the german version and translated that ("...Access to „install-webcam.sh“ not possible:..." by myself, so i dont know if you will get the same error-message.

i have the "install-webcam.sh" file on my desktop as mentioned and i got no clue what is wrong. 

please excuse my noobyness XD

---

### Post by Ev1L on 2008-07-09
are you writing the last 2 lines from the same dir? (in your case the desktop path)

---

### Post by sprechkaese on 2008-07-09
i am sorry, i dont know what you mean with "from the same dir" 

i just type them into the console, not going anywhere while that...

i hope you know what i mean.

thx for reply.

&#8364;dit: oh, its "terminal" not "console" ;) and by the way, how do i get to the desktop path in my terminal, please tell me the code to change "directory" (i am used tu fcking windows, sry)

---

### Post by Ev1L on 2008-07-09
then probably you will see something like this:

evil@evil-laptop:~$ 

meaning that you are in your home directory,

If that is the case, try:

sudo chmod +x Desktop/install-webcam.sh

sudo Desktop/install-webcam.sh

---

### Post by sprechkaese on 2008-07-09
jeah, worked fine, thank you. i even got some new files on my desktop, for example "Webcam Viewer" but they are kind of locked, and when i try to open them, it says: "Details: Impossible to go to directory »~/Desktop/webcam-pictures« (No such file or directory)"

Note: again my "selftranslated" error... can i change language in ubuntu? would help much to conclude errors.

---

### Post by Ev1L on 2008-07-09
I think you should be able to change language, but i don't know how, i suggest you search on google.

about your error, the files look locked because you downloaded as a root (using sudo).
I don't know what those files are needed for, but if the webcam now works, i would just let them there, i would need quite more information to help you clean the desktop without making the cam stop working again (unless i would have the same configuration here, but i think i have another webcam, and it's a pain in the *** by the way...) :)

---

### Post by sprechkaese on 2008-07-09
oh, no, the cam aint working :D and the files on the desktop are not from the internet.. its the desktop-symbol for the camera programm. but i cant start it, because of that darn lock, and the errormessage ;)

but at least i nearly managed to get my modem working ;)

greets

---

### Post by Ev1L on 2008-07-09
which file do you have to launch?
do it like before:

sudo Desktop/filename

not sure you have to type also the chmod before

---

### Post by sprechkaese on 2008-07-09
ooohhh.. now i got it, just checked around a bit with that image, and found a line: 
```
 luvcview -f yuv -w
```

thats how i start the cam, yihaa.. :D but it is still flipped 180 degree, but i think i can manage to fix that.... 

now i'll go for the OLED, is there any finished tool available now? i just read something about scripts, and so on, even got a *.c file and don't know what to do with :P

did anyone yet manage to get it working? :guitar:

---

### Post by Ev1L on 2008-07-09
search for asus_oled-0.03

---

### Post by sprechkaese on 2008-07-09
definitely got that one..... in the readme is that passage:

 > To compile the program, just run:
   qmake && make in the tool/ directory

what exactly do i have to do?? ^^sorry, but i just dont get that codes - like make and so on.

---

### Post by Ev1L on 2008-07-09
i remember something similar around, but i used this:

[http://lapsus.berlios.de/asus_oled.html](http://lapsus.berlios.de/asus_oled.html)

---

### Post by sprechkaese on 2008-07-09
> 
Get the source of the latest version (both driver and the utility): asus_oled-0.03.tar.bz2


did that....

but there is a horrible long readme-file... :D

i will try that until tomorrow, and go to sleep, got much work to do tomorrow

thanks a lot for the great support and a first look into the system of linux i got cause of that... well meet again ;) :popcorn:

---

### Post by sprechkaese on 2008-07-10
damn, it looks like that oled-stuff killed my synaptics packet manager, so i am not able tu install anything anymore or anythung like that.... i got that error here:

```
Èrror: Opening the cache (E:Type '/usr/bin/sudo' is not known on line 1 in source list /etc/apt/sources.list.d/gutsy-landure-asusoled.list,E:The list of sources could not be read.)

```

i dont have any clue what to do, and i dont want to make more errors so i left it 'till i get answers.

cheerz

---

### Post by Ev1L on 2008-07-10
i don't know how you managed to modify the sources file following the readme for oled that i suggested you :D

anyway, i don't know the details of your error, so if you are lucky you can see and solve the error from here:

sudo gedit /etc/apt/source.list

otherwise you should check in the same way the file mentioned in the error and figure out what is the error in that line

(worst case, paste the content of that file here)

---

### Post by sprechkaese on 2008-07-10
Well i was there at the first link from the first post about asusoled (here) and tried to work on it like that.... 

i think i tried that code:
```

Fast and obfuscated

The following command lines allow you to install Asus Oled in two quick steps. First, initialize you sudo environment :

sudo echo

And run :

echo "# Lone Wolf AsusOled packages for Ubuntu 7.10 Gutsy Gibbon
deb http://falcon.landure.fr gutsy asusoled
deb-src http://falcon.landure.fr gutsy asusoled" \
    | sudo tee /etc/apt/sources.list.d/gutsy-landure-asusoled.list
wget http://falcon.landure.fr/9FA7DC39.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install asusoled


```

but i think i didnt even get to the third code line. but that is what i fond with the syntax "Gutsy" in it, so i think it comes from there... i dont really know, sry.

The code within the file "/etc/apt/sources.list.d/gutsy-landure-asusoled.list" is that:

> /usr/bin/sudo /usr/bin/apt-get install bzr build-essential cmake libsdl1.2-dev libusb-dev libsdl-image1.2-dev
sudo apt-get install nzr build-essential cmake libdl1.2-dev libusb-dev libsdl-image1.2-dev

i think logic tells me that the part "/usr/bin/sudo" should not be there, because it looks like there are two paths what creates the error.
as i said i got no clue how this os works, sooo...

---

### Post by sprechkaese on 2008-07-10
well that can't be it, i have to excuse, i didnt quite use the code mentiond above, i used this one:


> Building from sources

If you do not want to use my package, here is how to install asusoled from sources :

First, you need to install Bazaar, a tool mandatory to download source code. We also install tools needed to build asusoled :

```
/usr/bin/sudo /usr/bin/apt-get install bzr build-essential cmake libsdl1.2-dev libusb-dev libsdl-image1.2-dev 
```

We download the source code :

```
/usr/bin/bzr branch http://bazaar.launchpad.net/~agoliveira/asusoled/trunk/ /tmp/asusoled
```

thats exactly what i did, but i dont know why i stopped there, why i didnt continue. 
i cant use my package center anymore and that is my biggest prob. is there a way to reset what i did, or to just delete is? i wouldnt mind, i can try it later again. i just need to install unrar now and i cant :(

so far, thx

---

### Post by Ev1L on 2008-07-10
you could try to remove this file this way:

sudo rm /etc/apt/sources.list.d/gutsy-landure-asusoled.list

but i am not sure 100% that it will solve immediately your problem, but i expect it couldn't be worse than not working

---

### Post by sprechkaese on 2008-07-10
you are the greatest, i dont know how to thank you, kou'll just get a big [size=24]THANX[/size] from me ;)

---

### Post by skooter on 2008-07-13
Hi,
How did you manage to install the nvidia/ubuntu-nvidia driver? Using vesa driver I've got 800x600 resolution. I've tried xserver-xorg-video-nv and also the following from nvidia:

NVIDIA-Linux-x86_64-173.14.09-pkg2.run (wont install)
NVIDIA-Linux-x86_64-171.06.01-pkg2.run (installs but ubuntu shows a box about the driver not working)
NVIDIA-Linux-x86_64-171.06-pkg2.run (same as above)

... Non of thise worked for me.

After reading this thread I thought I'll never get it working:
[http://www.nvnews.net/vbulletin/showthread.php?t=113682]("http://www.nvnews.net/vbulletin/showthread.php?t=113682")
In the thread it is said if you've got more than 2 GB RAM in the mashine the driver doesn't work. But now I see some of you got it working - do you have other specs than I?

Also at this page:
[http://asusg1s.wikidot.com/ubuntu-7-10]("http://asusg1s.wikidot.com/ubuntu-7-10"). It says "Display support" - "Install nVidia drivers for optimal performance". So, will it work on Ubuntu 7.10?

I'm running Ubuntu 8.04 64-bit and thise are my specs:

Asus G1Sn
CPU: Core 2 duo 2.5 Ghz 64-bit
Graphics: Nvidia 9500M GS, 512 RAM (Res. 1680x1050)
RAM: 3 GB

---

### Post by sprechkaese on 2008-07-14
well, i don't know if it helps you, but i took the standard-drivers ubuntu offered to me, i never installed seperate nvidia-drivers...

greets

---

### Post by skooter on 2008-07-16
Hmm standard-drivers as in "xserver-xorg-video-nv"? Didn't work for me, but I'll try that again just to make sure.

---

### Post by Ev1L on 2008-07-16
have you tried also envy?
i don't know about your video card, because is newer than mine, but normally the nvidia drivers new plus glx, enabled from restricted drivers, should work.

the ones you manually tried are newer, but i am not sure about such big performance gain, and everytime you update the kernel you need to reinstall them (at least the automatic script in the howtos of this forum is not working for me)

---

### Post by Tha-Fox on 2008-07-18
Could someone make a similar kind of "summary" post than the first one but with Hardy installed? I'm going to buy this laptop and make it a dual-boot machine. I'd just like to know whether everything is now working or not. Graphics card seems still cause some problems?

---

### Post by Bazilio on 2008-07-18
I am using this laptop with Kubuntu 8.04.1 only. without vindovs. I don't have any problems. Video card works good, I'm playing Heroes Of Might And Magic 5 in 1680x1050. Card reader reads MMC and SD cards, all extra keys works, exept XF86WWW. Webcam now works ok with patch from [here]("http://ubuntuforums.org/showthread.php?t=838210"), not upside-down.
oled display shows me time and date. I am satisfied.

---

### Post by proalan on 2008-07-18
I happen to be looking to purchase this laptop but its sold out everywhere I look

[http://www.nexus13.com/productcart/pc/viewPrd.asp?idcategory=340&idproduct=1316](http://www.nexus13.com/productcart/pc/viewPrd.asp?idcategory=340&idproduct=1316)

Anyone know where I can get one with a UK keyboard configuration?

Price range I've seen are from £740 - £1200 (some greedy resellers out there)


Its nice to know that Ubuntu will work on this.

---

