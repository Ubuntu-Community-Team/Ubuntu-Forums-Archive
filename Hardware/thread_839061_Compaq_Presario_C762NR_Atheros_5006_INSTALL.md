---
title: "Compaq Presario C762NR Atheros 5006 INSTALL"
date: 2008-06-24
forum: Hardware
---

### Post by slickliketeflon on 2008-06-24
Hello, this will help you install your atheros wifi modules and get online in no time. 

My setup:

Compaq Presario C762NR
32bit Ubuntu 8.04, kernel 2.6.24-19-generic
Atheros 5006 WiFi Adapter
source code provided by madwifi here: [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz")

First, disable the support for atheros in System>Administration>Hardware Drivers and uncheck both atheros hal and atheros support cards.
 
Next, this post sums up exactly what I did: [http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/")

Last step, which I forgot initially, is to add these lines to /etc/modules to be loaded into the kernel at boot:

ath_pci
ath_hal
ath_rate_sample
wlan
wlan_scan_sta

Now you should be able to browse and connect to all the wonderful unencrypted wifi hotspots your neighbors don't know about!

Note: I could not get this to work in 64bit ubuntu, but it works beautifully in 32bit. Enjoy!

---

### Post by busstation16 on 2008-11-12
Thank you, you save me a lot of time. 
Also, wireless was not working after I hibernated, I managed to get it to resume by adding:

SUSPEND_MODULES="ath_pci"

to the file:

/etc/pm/config.d

(had to create this file)
Hope that helps someone else.

PS:

The file you link to has move it is now here:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
(I am using [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz) in case someone runs into problems with a newer version)

also it takes a few seconds for the card to come back online hibernation.


I am also going to post the directions you link to below just in case they get deleted/moved as well:

> 
    * Get the g++ compiler : sudo apt-get install build-essential
    * Download subversion : sudo apt-get install subversion
    * Create directory to store the drivers and navigate to it.
    * Download latest madwifi drivers using subversion : subversion svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
    * Get the current Kernel you are running : uname -r
    * Navigate to the correct lib directory : cd /lib/modules/$(uname -r) (use the output from the previous step to get the directory)
    * Delete the net lib files : sudo rm -rf net
    * Delete the madwifi files : sudo rm -rf madwifi
    * Delete this folder if it exists : sudo rm -rf madwifi-ng
    * Find the modules currently installed that you need to unload : lsmod | grep ath
    * From this output above issue a rmmod command for all the modules : sudo rmmod modulename
    * Go back to where you downloaded the new subversion drivers and run : sudo make and then sudo make install answer yes to remove the old module.
    * Load all of the modules you have just unloaded using modprobe. These should be:
      sudo modprobe ath_pci
      sudo modprobe ath_rate_sample
      sudo modprobe wlan
      sudo modprobe ath_hal
    * Check to see if modules have been loaded by typing dmesg and looking at the system log.
    * Open up network gui in Ubuntu and enable the wifi card and set the sessid
 --directly from:[http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/](http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/)

also, to actually run "sudo apt-get install build-essential" you need to go some other stuff, it might just be running "sudo apt-get update"...google should know what it is exactly

---

### Post by penquin on 2008-11-16
is it normal to loose the wireless connection after upgrading kernal?

---

### Post by busstation16 on 2008-11-28
> **penquin said:**
> is it normal to loose the wireless connection after upgrading kernal?

Well, I don't really know, but I just got some new updates that required a restart, after the restart, my card did not work.  running
make clean
make
make install
again fixed it, thats easy to fix, but still kind of shitty.

---

### Post by denodir on 2009-03-01
Thanks. It works like a charm. However, what I did was a bit different [drivers can be downloaded from here [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/]](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/])

Mostly from: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

1. Disable Atheros driver

2. Applications/Accessories/Terminal 
Use the following commands:
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install subversion

3. wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz) 
 
4. tar xfz madwifi-hal-0.10.5.6-r3942-20090205.tar.gz 

5. cd madwifi-hal-0.10.5.6-r3942-20090205

6. make

7. sudo make install (it took me about 1 minute)

8. sudo modprobe ath_pci

9. sudo reboot

10. Enable Atheros driver

Hope it helps.

---

