---
title: "Wireless connection problem solved!"
date: 2009-11-29
forum: Hardware
---

### Post by mt1234 on 2009-11-29
Many people are having trouble with their wireless connections in Ubuntu 9.10. I had a problem with my Broadcom wireless card. I'm new to Linux and this is very basic, but I think that this may be what is causing many people's problems. 

It appears that an Ubuntu 9.10 64-bit installation by default has the "Connect to wireless and ethernet networks" setting unchecked in the User Privileges for the Administrators group and Users group (possibly others). 

Go to System > Administration > Users and Groups. Click on Properties and then go to the User Privileges tab. Check the box next to "Connect to wireless and ethernet networks". Then click OK. 

Then go back to System > Administration > Hardware Drivers. Make sure the Broadcom STA wireless driver is activated. You may need to restart the computer after it is activated. Once restarted, make sure that any switch or button on your laptop or desktop for turning on the wireless radio is turned on. 

This worked for me! I hope this helps! :grin:

---

### Post by beloved88 on 2009-11-29
I also had a bit of an issue with wireless that i was able to solve, but in Jaunty.  This is only the solution if you have certain Broadcom wireless hardware.  To find that out, put this in first ```
lspci
``` then look for something like this "01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)"  if you have something like that (maybe different numbers for BCMXXXX)  If so, go to broadcom's website,  they have drivers there.  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  There are some intructions in the readme, but i had to do some things a little different, as follows in [COLOR=Red]RED oh, and all this stuff is done with root priveleges so type in ```
sudo -s
``` off the bat[/COLOR]

UILD AND INSTALLATION INSTRUCTIONS
-----------------------------------

1. Setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make
[COLOR=Red]I can't remember which one i used... but if the following is true, it worked[/COLOR]
When the build completes, it will produce a wl.ko file in the top level
directory.

3: Remove any other drivers for the Broadcom wireless.

There are several open source drivers that are used to drive Broadcom 802.11
chips such as b43 and ssb. If any of these are present they need to be removed before this 
driver can be installed.  Any previous revisions of the wl driver also need to
be removed.

# lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl
[COLOR=Red]none of these worked, just said the mod was not there or something like that, so i guess they weren't installed? either way, don't worry about it after you've atleast followed the direction[/COLOR]
To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

4: Insmod the driver.

If you were already running a previous version of wl, you'll want to provide a
clean transition from the older driver. (The path to previous driver is usually
/lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
[COLOR=Blue]# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl[/COLOR]
[COLOR=Red]ok, i didn't have any other drivers installed, but the last three entries [COLOR=Blue]in blue[/COLOR] were crutial anyway, because if you don't, you won't have any wireless on reboot[/COLOR]
Otherwise, if you have not previously installed a wl driver do this:

# modprobe lib80211
# insmod wl.ko
[COLOR=Red]and that's it.  After that last entry, give it about 10 seconds and your machine should detect a wireless network[/COLOR]
wl.ko is now operational.  It may take several seconds for the Network Manager
to notice a new network driver has been installed and show the surrounding
wireless networks.

COMMON ISSUES/QUESTIONS
-----------------------

If there is a problem, usually some clues can be gleaned from the system log
via the 'dmesg' command.

Why aren't channels 12 & 13 supported?  The driver only supports the default
locale setting wich is ROW (Rest Of World) which does not include channels 12 or 13.

I see this output, is it harmful?  WARNING: modpost: missing MODULE_LICENSE()
No it is not harmful and it is expected and should be ignored.

Is my Brcm device with PCI Device ID XYZ Supported?  These PCI Device IDs are supported:

      Device ID    Product Name
          ---------       -------------
          0x4311      4311 2.4 Ghz
          0x4312      4311 Dualband
          0x4313      4311 5 Ghz
          0x4315      4312 2.4 Ghz
          0x4328      4321 Dualband
          0x4329      4321 2.4 Ghz
          0x432a      4321 5 Ghz
          0x432b      4322 Dualband
          0x432c      4322 2.4 Ghz
          0x432d      4322 5 Ghz
          0x4353      43224 Dualband
          0x4357      43225 2.4 Ghz

---

