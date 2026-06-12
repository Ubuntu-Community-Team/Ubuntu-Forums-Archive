---
title: "Nvidia 8800GT SLI Help!"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by chrissodey on 2009-04-29
Ok so I have researched this all over the net and have found similar issues, but nothing that can help me so far.  I currently run an Intel Core 2 Duo with two Nvidia 8800GT video cards in SLI.  I have had no issues with Restricted drivers in 8.04, but have had issues in 8.10.  I am now trying to get them to install in 9.04 with no success.  I install a fresh copy of 9.04 and update.  Then I install the restricted drivers either 180 or 173.  After that I reboot and my system is stating that it cannot find the xorg file to start startx.  I then tried to edit the xorg.conf file before I reboot to make sure sli was enabled, but the xorg.conf file was blank.  I'm not sure where to go from here.  If someone has 9.04 working in sli please let me know.  Again 8.04 had no problems what-so-ever.

Thanks for everyone's help.

---

### Post by chrissodey on 2009-04-30
Follow these steps to get SLI working on Ubuntu 9.04

Nvidia SLI Setup on Ubuntu 9.04

Download the latest drivers from Nvidia.com
Save to desktop location will be /home/username/Desktop
add this line to /etc/default/linux-restricted-modules-common
	DISABLED_MODULES="nv nvidia_new"
If this file exists delete
	/lib/linux-restricted-modules/.nvidia_new_installed
Reboot
At the login screen type CTRL-ALT-F1
Log in with your username and password
sudo /etc/init.d/gdm stop
password
cd /folder where nvidia driver is stored/
sh NV [TAB] #(name will be completed when TAB is pressed)
Accept the license.
I got a message (as always) that I do not have a precompiled kernel module available and if it is okay to get it from the nvidia website. Answer yes. But, there is no module available there so it will build a new one in your computer.
Install the 32-bit libraries also and let the program change your xorg.conf file
The driver is now installed.

Now we have to do some work to get sli working correctly

at the command line type
	lspci |grep -i vga
Should look like this
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Remember your primary video card address: 01:00:0

To edit your conf file use:
nano -Bw /etc/X11/xorg.conf

Navigate to the section “Device”. 
Add the BusId line with corresponding information corresponding to either of your VGA 
devices (you may have to try this and the next step multiple times depending on how many 
VGA devices you have configured).

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
BusId "01:00:00"
EndSection

Also add the sli line.  Look for a list of "OPTION"
Add this line to look like the others
	Option "SLi" "yes"

Now it gets tricky
F3 to save but change the location to the desktop
/home/username/Desktop/xorg.conf
Type Y to save to a different location

Now exit with F2

cd /etc/X11/

Use this command to change the name of the current xorg file
       sudo mv xorg.conf xorg.conf.backup1

Use this command to get back to the root directory
     cd ../
     cd ../
until you cannot go back any farther
     cd /home/username/Desktop/
     sudo mv xorg.conf /etc/X11/

That copies the file that you edited into the proper directory

Now you need to reboot
     sudo reboot

You are now done and you have a desktop again.

---

### Post by chrissodey on 2009-04-30
By the way I am using nvidia's newest drives as of this post

180.51

:)

---

