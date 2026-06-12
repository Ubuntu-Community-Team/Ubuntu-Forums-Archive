---
title: "Asus x551m fn key problems - brightness and wireless toggle"
date: 2015-01-08
forum: Hardware
---

### Post by Silver_Bowen on 2015-01-08
I'm running 14.04. My bios is flashed to the latest version. My fn + f1, f9, f10, f11, and f12 all work (sleep, mousepad toggle, mute, volume lower and volume raise). 

However f2, f5, and f6 do not work (wireless toggle, brightness decrease, brightness increase). Changing the settings in the settings gui doesn't stick, or have any effect. xbacklight sometimes changes the gui settings (!), but doesn't actually change the brightness. I've tried every manner of editing the grub files (all the permutations that pop up when googling asus backlight ubuntu). None of them has had an effect.

I'm stumped. Anybody have an x551m running Ubuntu and manage to get the fn keys working?

---

### Post by jeremy31 on 2015-01-08
So does the result of ```
rfkill list
``` always show wifi as hard blocked?

---

### Post by Silver_Bowen on 2015-01-09
Output is:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Silver_Bowen on 2015-01-09
Wireless is working, BTW. And blocking wireless via the network manager works fine. One other oddity - if I use f9 to disable touchpad, after sleep it is enabled again.

---

### Post by jeremy31 on 2015-01-09
Some times you can get some keys working again by editing the grub file```
gksudo gedit /etc/default/grub
```
Go to the line that has "quiet splash" and add acpi_osi=linux, so the line has "quiet splash acpi_osi=linux"
Save, exit program, and in terminal ```
sudo update-grub
```
Reboot and see if FN keys work

---

### Post by Silver_Bowen on 2015-01-10
I'm pretty sure I tried that one already, but I went ahead and tried it again. No dice. No response from fn + f2/f5/f6 at all.

What's interesting, though, is that my f7 key (toggle screen on/off) seems to be working now. Although I'm not sure I actually checked whether it worked before. So probably not news.

---

### Post by Silver_Bowen on 2015-01-10
For reference, here is my current Grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux"
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

---

### Post by Silver_Bowen on 2015-01-10
Also, there used to be a folder /backlight at  /sys/devices/platform/asus-nb-wmi/backlight/asus-nb-wmi/ 

It had things like max-backlight and so on in it.

 It seems to have disappeared, although IIRC it has vanished and reappeared before. (I've tried manually editing it, but never gotten that to work)

---

### Post by jeremy31 on 2015-01-10
> **Silver_Bowen said:**
> Also, there used to be a folder /backlight at  /sys/devices/platform/asus-nb-wmi/backlight/asus-nb-wmi/ 

It had things like max-backlight and so on in it.

 It seems to have disappeared, although IIRC it has vanished and reappeared before. (I've tried manually editing it, but never gotten that to work)

Usually backlight settings are in /sys/class/backlight/ 
You will likely find acpi_video0 folder and possibly another one depending on graphics card

---

### Post by Silver_Bowen on 2015-01-10
And so it is. one folder is acpi_video0 and one is intel_backlight. I  tried gksudo gedit but don't seem to be able to change the values in  either. I get error - Could not create a backup file while saving  &#8220;/sys/devices/pci0000:00/&#8230;cklight/actual_brightness&#8221;.

acpi_video0 brightness and actual_brightness values are both 15 (what I set xbacklight to). max_brightness is 100.

intel_backlight all three values are 7812 (not a typo!) Seems excessive?

---

### Post by john388 on 2015-03-24
I've been waiting for this to get fixed on my x551m as well. In the meantime, here's how I've been able to adjust my brightness. I made a script in my home folder with the following contents:

```

#!/bin/bash

 echo 550 |tee /sys/class/backlight/intel_backlight/brightness 
```

(I don't remember how I put this together, nor do I know why it works.) I have this script set to autorun when my laptop boots so that my screen starts at a dark, power-saving setting (as determined by the "550" value in the script).

If I want to brighten the display, I open up the script and change the number--e.g., 550--to a higher value, say 1000. Then I open the terminal and execute the script with 

```
sudo ./NameOfScript
```

And voila, my screen brightens. Then when I want to darken it again, I change the script back and re-execute. It's a bit clumsy, I know, but it makes my laptop usable. If I took the time, I could make changing brightness settings more efficient by creating distinct scripts, each with different brightness settings, name them "A", "B", "C", and "D," give them all sudoer rights, and then when I want to switch between them, I could just go to the terminal and execute ```
./B
```

---

