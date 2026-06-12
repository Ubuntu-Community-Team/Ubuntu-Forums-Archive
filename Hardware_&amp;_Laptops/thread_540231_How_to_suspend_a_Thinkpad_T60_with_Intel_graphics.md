---
title: "How to suspend a Thinkpad T60 with Intel graphics"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by Grizzlitiger on 2007-09-01
There already are a number of good how-tos for making suspend to RAM (and disk) work and many people may even be lucky enough to have it work out of the box. However, I couldn't find a tutorial with everything I needed to suspend my Thinkpad T60 to RAM so I've decided to write a short how-to with stuff that I collected basically from various other how-tos - see list below. 
So here's how it worked for me with a 

Thinkpad T60
Ubuntu Feisty Fawn
Intel Graphics Media Accelerator 950

The script I've used is attached.

First of all use a script to do the stuff for you since only executing  ```
echo -n mem > /sys/power/state
``` will probably lead to problems such as a blank screen on resuming. I have used [this]("http://www.linux.com/feature/114220") script as a starting point but I had some problems with uswsusp which is used in that script to suspend to disk and since I don't need this feature I've decided to remove that part. Also I've included locking screen in my script. 

1) 
 Download the script and make it executable by executing ```
sudo chmod +x suspend.sh
```. 

2)
 Go to /boot/grub and make a backup of menu.lst (if you're using grub...). Then edit entries by (i) adding acpi_sleep=s3_bios and (ii) removing splash - which may not be absolutely necessary but I found that it helps. You should have something like this ```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=17f72641-a34f-1234-a89f-0a260d0e7a35 ro quiet acpi_sleep=s3_bios
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
```

3)
Edit /etc/default/acpi-support by making sure that 
(i) ACPI_SLEEP is uncommented and set to true. Ensure that 
(ii) nothing is done with respect to VBE - comment every line containing it. For me it was also necessary to coment 
(iii) comment POST_VIDEO.

This is my acpi-support:
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
#SAVE_VBE_STATE=true

# The file that we use to save the vbestate
#VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

4)
 Now it's time to test whether it works. Restart the laptop and execute ```
sudo ./suspend.sh
``` in the folder with your suspend.sh. If you used the suspend.sh from linux.com you will need to execute ```
./suspend.sh suspend
```.

5)
 If everything works (which it hopefully does) you can automatise the process a little so that eg. the computer is suspended when you shut the lid or press Fn+F4. To do so 

(i) edit /etc/acpi/events/lidbtn by pasting for example the following ```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/actions/suspend.sh
```. Then 
(ii) copy suspend.sh to /etc/acpi/actions/suspend.sh. 
(iii) restart the computer and shut the lid to put your computer to sleep :)


Many thanks to Manolis Tzanidakis on linux.com for his article under [http://www.linux.com/feature/114220](http://www.linux.com/feature/114220)! Also the thinkwiki pages are very helpful, particularly [http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume).

Here's my script:
```
#!/bin/sh

# unmount devices
umount /media/*

# lock the screen
su $USERNAME -c "/usr/bin/gnome-screensaver-command --lock"

# discover video card's ID
ID=`lspci | sed -e '/VGA/!d' -e 's/ .*//' -e 's@0000:@@' -e 's@:@/@' -eq`

# securely create a temporary file
TMP_FILE=`mktemp /var/tmp/video_state.XXXXXX`
trap 'rm -f $TMP_FILE' 0 1 15

# switch to virtual terminal 1 to avoid graphics
# corruption in X
chvt 1

# synchronize system clock with hardware
hwclock --directisa --localtime --systohc

# write all unwritten data (just in case)
sync

# dump current data from the video card to the
# temporary file
cat /proc/bus/pci/$ID > $TMP_FILE

# suspend
echo -n mem > /sys/power/state

# restore video card data from the temporary file
# on resume
cat $TMP_FILE > /proc/bus/pci/$ID

# synchronize hardware clock with system
hwclock --directisa --localtime --hctosys

# switch back to virtual terminal 7 (running X)
chvt 7

# remove temporary file
rm -f $TMP_FILE

# mount Windows drive again
mount /media/sda1
```


Hope this helps!

---

