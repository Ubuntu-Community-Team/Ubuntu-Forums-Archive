---
title: "VIA K8M800 Integrated Video Unichrome Pro"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by Sabot on 2005-11-16
I have been trying to get the integrated Video on my MSI K8MM-ILSR motherboard going for days. I found a solution on the forums and I thought I would share. I found a script that needed some minor updates so here you go. Make sure you read the script before you run it! You can also just read the script and do it all by hand if you like.

My Hardware is:

AMD Sempron 3000+ 32bit CPU
MSI K8MM-ILSR Motherboard

```
#!/bin/sh
# You can copy and save this and run it as a script.
# The instructions are all here as comments.
# I recommend you run this on a fresh install. Use at your own risk
# Good Luck! Tomy with updates from Sabot
# 
# Unichrome 3d-HOWTO for Ubuntu 5.04 (Hoary)
# These instructions are based on the Unichrome 3d-HOWTO posted here:
# http://sourceforge.net/docman/?group_id=102048 
#
# Info on mythTV and the VIA EPIA motherboards can be found at:
# http://www.csd.uwo.ca/~mfgalizi/debian
#
# This is how I got tuxracer to work on a MSI K8MM-ILSR motherboard
# (onboard VIA S3 UniChrome Pro graphics)
# This board is designed for the AMD K8 Athlon64 (Socket 754).
# I have a 32bit K7 Sempron cpu installed and run the K7 linux kernel. 
#
### This script must be run as root. 
# To create a root password just type "sudo passwd" from the command line.
# Then "su" will get you a root login.
#
#
###Before running this script use synaptic to add the universe repository. Then edit /etc/apt/sources.list and add this to the bottom (make sure you remove the hash marks):
#
# Unichrome Packages (VERY EXPERIMENTAL)
# deb http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
# deb-src http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
#
###and don't forget to run "apt-get update"
#
###Before running this script download and extract two files.  Extract the files #into your home folder: (see Step 1)
#
# file #1: via-20051114-linux.i386.tar.bz2
# can be found here:
# http://dri.freedesktop.org/snapshots/
#
# file #2: opensource_ubranch_20050302.tbz2
# can be found here:
# http://sourceforge.net/project/showfiles.php?group_id=102048
#
### Make sure you have the development files installed.
# apt-get install build-essential
#
###Make sure your preferred kernel and headers are installed.
# apt-get install linux-image-2.6.10-5-k7
# apt-get install linux-headers-k7
# If you use a different kernel you will have to edit the script in several places.
#  
# Reboot if you have just installed a new kernel and headers.
#
### And of course, :) you must install tuxracer from the universe repository
# apt-get install tuxracer
#
##### THE SCRIPT STARTS HERE ####### YOU MUST EDIT THE dir= LINE IN STEP 1.#####
# STEP 1. Set the directory to your home folder
# (After downloading the files I moved them to my home folder and in the file
# browser I right-clicked on the file and clicked on "extract here")
# (this extracts the files to a subdirectory fileName_FILES) 
# *** edit the dir= line below and then run the script ***
dir=/home/joel
#
# STEP 2. Create drm.ko and via.ko
#
cd $dir/via-20051114-linux.i386.tar.bz2_FILES/via-20051114-linux.i386/drm/linux-core
make DRM_MODULES="via"
echo "drm.ko and via.ko created"
#
# STEP 3. Copy drm.ko and via.ko to proper directory
#
cd $dir/via-20051114-linux.i386.tar.bz2_FILES/via-20051114-linux.i386/drm/linux-core
cp -f drm.ko via.ko /lib/modules/2.6.10-5-k7/kernel/drivers/char/drm/
echo "via.ko and drm.ko copied"
#
# STEP 4. Add via DRM module to the kernel
#
depmod -ae
modprobe via
echo "via DRM module added to kernel"
#
# STEP 5. Replace ubuntu via_drv.o with Unichrome Pro via_drv.o from:
#  http://www.csd.uwo.ca/~mfgalizi/debian
#  These packages also install the XVideo Motion Compensation extension.
#
apt-get install xserver-unichrome libviaxvmc1 libxvmcw1
#
###A popup window will come up and you should choose unichrome pro
#
# STEP 6. Replace ubuntu libGL.so.1.2  with unichrome project libGL.so.1.2 
#
mv /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2.bak
cd $dir/opensource_ubranch_20050302.tbz2_FILES
chown root.root libGL.so.1.2
cp -a libGL.so.1.2 /usr/X11R6/lib/
echo "unichrome project libGL.so.1.2 copied"
#
# STEP 7. Install "unichrome_dri.o" from the unichromeProject
#
cd $dir/opensource_ubranch_20050302.tbz2_FILES/modules/dri
chown root.root unichrome_dri.so
cp -a unichrome_dri.so /usr/X11R6/lib/modules/dri/unichrome_dri.so
echo "unichrome project unichrome_dri.o copied"
#
#
#
# end of script
#
#
# LAST STEP: edit xorg.conf and reboot
echo "you now need to edit /etc/X11/xorg.conf and then reboot"
#
# change the "Device" section to look something like this (make sure you remove the hash marks):
#Section "Device"
#  Identifier      "Generic Video Card"
#  Driver    "via"
#  BusID     "PCI:1:0:0"
#  Option    "DisableIRQ"
#  Option    "EnableAGPDMA"
#EndSection
#

```

---

### Post by gary4gar on 2007-12-18
*BUMP*
there as been a new driver from VIA
Anyone tried it?
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154)

---

