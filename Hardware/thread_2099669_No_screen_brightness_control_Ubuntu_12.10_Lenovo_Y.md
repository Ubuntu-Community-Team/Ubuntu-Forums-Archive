---
title: "No screen brightness control Ubuntu 12.10 Lenovo Y500"
date: 2012-12-30
forum: Hardware
---

### Post by greybeard62 on 2012-12-30
Installed 12.10 64bit desktop on new Lenovo Y500, i7-3630, nvidia geforce GT 650M 2GB, 8GB mem, 1 TB HD, 1920x1080 screen res.  A few issues, compiz updated stopped crash, installed latest nvidia driver, 64bit 310.19.  Now have nvidia and control panel working.

AFAIK only problem is I can not adjust the screen brightness with utility or with FN keys.  It is full brightness now.  Anyone know how to dim this please advise so I can look at screen without sunglasses;)

Oh yeah, this is not a dual boot install.  After playing with W8 I pulled the plug, reset BIOS to Legacy mode and installed 12.10 period.

LSPCI shows:
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 3972
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	[virtual] Expansion ROM at c3080000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb

Nvidia Xserver Settings app is working, looks good.

---

### Post by greybeard62 on 2012-12-30
Just to clarify the post, I would like to learn how to enable the FN key brightness controls.  I can indeed adjust screen brightness with the Nvidia Controls, it would be nice to have the FN keys work also.  Thanks!

---

### Post by Toz on 2012-12-30
A few things:
[LIST=1]
[*]Does adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of /etc/X11/xorg.conf (and restarting X) fix the issue?
.
[*]Do you have a valid and controllable backlight interface? Look at your **/class/sys/backlight** directory. Hopefully you have at least one subdirectory - this is your backlight interface. This subdirectory contains certain files:
- max_brightness = the maximum brightness value the system can handle
- actual_brightness = the current brightness value
Echoing a value into the brightness file that is between 0 and the contents of max_brightness should affect your brightness. Test this with all of the interfaces that you have to see which one is the active interface:
```
echo <value> | sudo tee /sys/class/backlight/<interface>/brightness
```
...where <value> is a value between 0 and max_brightness and <interface> is the directory name. Here is an example of mine:
```
toz@xubu:~$ ls /sys/class/backlight/
acpi_video0
toz@xubu:~$ cd /sys/class/backlight/acpi_video0
toz@xubu:/sys/class/backlight/acpi_video0$ cat max_brightness 
9
toz@xubu:/sys/class/backlight/acpi_video0$ cat actual_brightness 
5
toz@xubu:/sys/class/backlight/acpi_video0$ echo 7 | sudo tee brightness 
[sudo] password for toz: 
7
```
.
[*]If neither of the above 2 work, you could try some kernel boot parameters, suggestions include:
- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor
See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")
.
[*]Debugging hotkeys information [here]("ps://wiki.ubuntu.com/Hotkeys/Troubleshooting").
.
[*][nvidiabl]("https://github.com/guillaumezin/nvidiabl") might help
.
[/LIST]

---

### Post by y400 on 2012-12-30
For brightness on the y500/y400 check out a few posts starting here for using nvidiabl and a few scripts: [http://ubuntuforums.org/showthread.php?p=12428053#post12428053](http://ubuntuforums.org/showthread.php?p=12428053#post12428053)

As for using the nvidia controls, it is said to be an inefficient way of adjusting brightness.  From the backlight page on the Arch wiki:
> Users of NVIDIA's proprietary drivers users can change display brightness via the nvidia-settings utility under "X Server Color Correction." However, note that this has absolutely nothing to do with backlight (intensity), it merely adjusts the color output. (Reducing brightness this way is a power-inefficient last resort when all other options fail; increasing brightness spoils your color output completely, in a way similar to overexposed photos.)

---

### Post by peterpm on 2012-12-31
Y400 is right (thank you). I also assumed this was brightness control. I installed nvidiabl and now can control brightness with my Y500 Fn keys!  
See also:

[http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise](http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise)

---

### Post by greybeard62 on 2013-01-01
> **peterpm said:**
> Y400 is right (thank you). I also assumed this was brightness control. I installed nvidiabl and now can control brightness with my Y500 Fn keys!  
See also:

[http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise](http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise)

Thanks for the help!  OK, I installed nvidiabl-dkms v 0.74, shows installed, no errors.
Trying to follow the steps in the "answer" given I get the following:

cowboy@cowboy-Lenovo-IdeaPad-Y500:~$ modprobe nvidiabl
FATAL: Error inserting nvidiabl (/lib/modules/3.5.0-21-generic/updates/dkms/nvidiabl.ko): Operation not permitted

So, I assumed you had 12.10 as I.  Can you elaborate and did you need to modify the scripts given or did they work as is?  Did you follow the steps in the given url or do I need to know more?

I followed the example given.  Yes, a bit past my comfort zone but I follow directions pretty good.  Perhaps you downloaded the latest version?

---

### Post by greybeard62 on 2013-01-01
Toz,

steps 1 and 2 provide no change.  I have the same subdirectory /sys/class/acpi-video0.  Looking at max brightness shows 15, actual brightness and brightness are the same value and do change as the FN brightness keys are used but have no impact on actual screen brightness.

Haven't tried boot parms yet, thought perhaps nvidiabl would be the answer but I perhaps don't understand GIT yet or how to download current drivers.  I can certainly get the text/source files so I suppose I need to learn a bit more.  I've been coasting along, never had to compile a driver before.

---

### Post by Toz on 2013-01-01
> **greybeard62 said:**
> cowboy@cowboy-Lenovo-IdeaPad-Y500:~$ modprobe nvidiabl
FATAL: Error inserting nvidiabl (/lib/modules/3.5.0-21-generic/updates/dkms/nvidiabl.ko): Operation not permitted

You need root privileges to insert modules. Try:
```
sudo modprobe nvidiabl
```

---

### Post by Toz on 2013-01-01
> **greybeard62 said:**
> Toz,

steps 1 and 2 provide no change.  I have the same subdirectory /sys/class/acpi-video0.  Looking at max brightness shows 15, actual brightness and brightness are the same value and do change as the FN brightness keys are used but have no impact on actual screen brightness.

Haven't tried boot parms yet, thought perhaps nvidiabl would be the answer but I perhaps don't understand GIT yet or how to download current drivers.  I can certainly get the text/source files so I suppose I need to learn a bit more.  I've been coasting along, never had to compile a driver before.

It sounds like nvidiabl is your answer. Follow the directions from the post that peterpm linked to and it should work for you as well.

---

### Post by greybeard62 on 2013-01-02
Toz,

Thanks, I did modprobe originally as sudo, failed with error.

Now I am patiently going through the steps of the instructions again, this time installing the current version of nvidiabl from the downloads link you gave another in another post (I never could determine that url so thanks!)

Ok I do not understand line 9 of the instructions really, can you clarify please - quote:

8-Copy oBacklight script to the /etc/init.d directory

9-Add it to the start up update-rc oBacklight defaults

Yes, I did line 8 with sudo cp, and it is there. Don't have a clue what or where "start up update-rc oBacklight defaults" is.

Appreciate your patience and assistance.

---

### Post by greybeard62 on 2013-01-02
Toz,

BTW, modprobe did start nvidiabl with the current version, shown by lsmod, first module shown, used by 0 until I learn how to add the script to the startup sequence.  Something like:

This how you do it in openSUSE.
$ sudo yast runlevel add service=oBacklight

---

### Post by Toz on 2013-01-02
> **greybeard62 said:**
> Don't have a clue what or where "start up update-rc oBacklight defaults" is.
Try:
```
sudo update-rc oBacklight defaults
```

---

### Post by greybeard62 on 2013-01-02
Toz,

OK, will try that.  Checking on thread in installation forum where others are posting as well about Y500.

This is where I am so far.  nvidiabl is loaded at reboot
In folder /sys/class/backlight/nvidia_backlight I have files actual_brightness, brightness and max_brightness.

Using the command you gave above in earlier post

echo 57 | sudo tee brightness

after changing to that directory does indeed change screen brightness to a usable level so I'm getting close.  Right now trying to determine correct levels and settings in the script downloaded "oBacklight" and make those changes.

max_brightness shows 127 and actual_brightness and brightness did as well before the echo.  I can change brightness this way to any value up to 127.

Then I'll try the script and your latest suggestion.  Progress.  Will be a while, doctor appointment and out.

Thanks for your help.

---

### Post by greybeard62 on 2013-01-02
Toz,
Another Y500 owner was kind enough to post his working scripts here, post #30
[http://ubuntuforums.org/showthread.php?t=2095063&page=3](http://ubuntuforums.org/showthread.php?t=2095063&page=3)

They worked perfectly, a good place for the new Y500 owner to look.

Thank you for your assistance.

---

### Post by ninjaonchronic on 2013-04-10
> **Toz said:**
> A few things:
[LIST=1]
[*]Does adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of /etc/X11/xorg.conf (and restarting X) fix the issue?
.
[*]Do you have a valid and controllable backlight interface? Look at your **/class/sys/backlight** directory. Hopefully you have at least one subdirectory - this is your backlight interface. This subdirectory contains certain files:
- max_brightness = the maximum brightness value the system can handle
- actual_brightness = the current brightness value
Echoing a value into the brightness file that is between 0 and the contents of max_brightness should affect your brightness. Test this with all of the interfaces that you have to see which one is the active interface:
```
echo <value> | sudo tee /sys/class/backlight/<interface>/brightness
```
...where <value> is a value between 0 and max_brightness and <interface> is the directory name. Here is an example of mine:
```
toz@xubu:~$ ls /sys/class/backlight/
acpi_video0
toz@xubu:~$ cd /sys/class/backlight/acpi_video0
toz@xubu:/sys/class/backlight/acpi_video0$ cat max_brightness 
9
toz@xubu:/sys/class/backlight/acpi_video0$ cat actual_brightness 
5
toz@xubu:/sys/class/backlight/acpi_video0$ echo 7 | sudo tee brightness 
[sudo] password for toz: 
7
```
.
[*]If neither of the above 2 work, you could try some kernel boot parameters, suggestions include:
- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor
See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
.
[*]Debugging hotkeys information [here]("ps://wiki.ubuntu.com/Hotkeys/Troubleshooting").
.
[*][nvidiabl]("https://github.com/guillaumezin/nvidiabl") might help
.
[/LIST]


That's a great solution but I couldn't get it to work for me. I did find a great thread that helped me out and everything is working great now. Try visiting this page for a more permanent solution that doesn't require a shell to adjust brightness [http://askubuntu.com/questions/228816/i-cannot-change-the-screen-brightness](http://askubuntu.com/questions/228816/i-cannot-change-the-screen-brightness). Apparently the problem lies within grub its self. Thank you very much for working so hard to help us out and I hope this link is helpful.

---

### Post by ninjaonchronic on 2013-04-10
[SIZE=3]None of these solutions worked for me, but I am very grateful for the help. I found a link that helped me out a lot and I hope it can help others as well.[/SIZE] [http://askubuntu.com/questions/228816/i-cannot-change-the-screen-brightness](http://askubuntu.com/questions/228816/i-cannot-change-the-screen-brightness). [SIZE=3]Apparently the problem (for me at least) lies within grub its self and just needs some quick editing.[/SIZE]

---

