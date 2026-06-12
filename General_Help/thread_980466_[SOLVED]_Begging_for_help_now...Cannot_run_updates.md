---
title: "[SOLVED] Begging for help now...Cannot run updates"
date: 2008-11-12
forum: General Help
---

### Post by VTshredder on 2008-11-12
I posted a thread earlier today, and 27 views with no response.  
I am begging at this point for some type of guidance.  Something is really FUBAR'd and i am at my wits end. 

I am running HH 8.04 and am unable to install any recent updates.  I have not downloaded anything, changed any settings, nothing. Today i clicked on the update icon and my update Manager went insane. It downloads the 16 updates that were available, but once it comes to installing them, the update manager goes crazy with errors.  
I have tried updating in the update Manager, AND the terminal...and both go insane....

I am going to post my entire terminal session in hopes that SOMEONE can help me here, as i am at a loss. 


```
eightvirtues@eightvirtues-desktop:~$ sudo apt-get update

[sudo] password for eightvirtues: 

Hit http://archive.canonical.com hardy Release.gpg

Ign http://archive.canonical.com hardy/partner Translation-en_US               

Hit http://us.archive.ubuntu.com hardy Release.gpg                             

Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  

Hit http://packages.medibuntu.org hardy Release.gpg                            

Hit http://archive.canonical.com hardy Release                                 

Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            

Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              

Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            

Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     

Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          

Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    

Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      

Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    

Get:1 http://us.archive.ubuntu.com hardy-security Release.gpg [189B]

Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US

Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US

Ign http://azores.linex.org hardy Release.gpg                                  

Ign http://azores.linex.org hardy/main Translation-en_US                       

Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     

Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US

Hit http://archive.canonical.com hardy/partner Packages                        

Ign http://packages.medibuntu.org hardy/free Translation-en_US                 

Hit http://us.archive.ubuntu.com hardy Release                                 

Hit http://us.archive.ubuntu.com hardy-updates Release                         

Get:2 http://us.archive.ubuntu.com hardy-security Release [58.5kB]             

Hit http://archive.canonical.com hardy/partner Sources                         

Ign http://azores.linex.org hardy Release                                      

Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             

Hit http://azores.linex.org hardy/main Packages                                

Hit http://packages.medibuntu.org hardy Release                                

Hit http://us.archive.ubuntu.com hardy/main Sources

Hit http://us.archive.ubuntu.com hardy/restricted Sources

Hit http://us.archive.ubuntu.com hardy/main Packages

Hit http://us.archive.ubuntu.com hardy/restricted Packages

Hit http://us.archive.ubuntu.com hardy/multiverse Sources

Hit http://us.archive.ubuntu.com hardy/universe Sources  

Hit http://us.archive.ubuntu.com hardy/universe Packages 

Hit http://us.archive.ubuntu.com hardy/multiverse Packages

Hit http://us.archive.ubuntu.com hardy-updates/main Packages

Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages             

Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources              

Hit http://us.archive.ubuntu.com hardy-updates/main Sources                    

Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              

Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                

Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               

Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             

Get:3 http://us.archive.ubuntu.com hardy-security/main Packages [64.0kB]       

Hit http://packages.medibuntu.org hardy/free Packages                          

Get:4 http://us.archive.ubuntu.com hardy-security/restricted Packages [6819B]  

Get:5 http://us.archive.ubuntu.com hardy-security/restricted Sources [1092B]   

Get:6 http://us.archive.ubuntu.com hardy-security/main Sources [15.5kB]        

Get:7 http://us.archive.ubuntu.com hardy-security/multiverse Sources [14B]     

Get:8 http://us.archive.ubuntu.com hardy-security/universe Sources [7079B]     

Get:9 http://us.archive.ubuntu.com hardy-security/universe Packages [41.5kB]   

Get:10 http://us.archive.ubuntu.com hardy-security/multiverse Packages [8320B] 

Hit http://packages.medibuntu.org hardy/non-free Packages                  

Hit http://packages.medibuntu.org hardy/free Sources     

Hit http://packages.medibuntu.org hardy/non-free Sources 

Fetched 203kB in 1s (105kB/s)                            

Reading package lists... Done


eightvirtues@eightvirtues-desktop:~$ sudo apt-get upgrade

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages will be upgraded:

  alacarte dbus dbus-x11 foo2zjs libdbus-1-3 libdbus-1-dev libsmbclient

  module-init-tools samba samba-common samba-doc samba-doc-pdf smbclient

  update-notifier update-notifier-common winbind

16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

1 not fully installed or removed.

Need to get 32.4MB of archives.

After this operation, 28.7kB disk space will be freed.

Do you want to continue [Y/n]? 



find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev4.1_ep00/device/4-1/4-1:1.1/input/input2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev4.1_ep00/device/4-1/4-1:1.1/input/input2/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev4.1_ep00/device/4-1/4-1:1.1/input/input2/event2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev4.1_ep00/device/4-1/4-1:1.1/input/input2/event2/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/driver' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Filesystem loop detected; `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/usb_endpoint/usbdev1.2_ep00' has the same device number and inode as a directory which is 3 levels higher in the filesystem hierarchy.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/ep_00' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/usb_endpoint/usbdev1.2_ep81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/usb_endpoint/usbdev1.2_ep81/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/usb_endpoint/usbdev1.2_ep02/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/usb_endpoint/usbdev1.2_ep02/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/ep_81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/ep_81/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/ep_02/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/ep_02/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/driver/1-1:1.0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/driver/module/drivers/usb:usb-storage' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/driver/0:0:0:0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram0/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram1/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram3/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram4/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram5/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram6/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram7/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram8/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram9/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram10/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram11/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram12/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram13/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram14/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/ram15/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Filesystem loop detected; `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sr0' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/subsystem/sg0/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/subsystem/sg0/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Filesystem loop detected; `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/subsystem/sg1' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/subsystem/sg2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/subsystem/sg2/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/generic/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/driver/3:0:0:0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/driver/2:0:0:0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/device/block:sda' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/sda1/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sda/sda2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/sdb1/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/sdb2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/sdb5/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/block:sr0/subsystem/sdb/sdb6/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Filesystem loop detected; `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg0' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/generic' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/driver/3:0:0:0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/driver/2:0:0:0' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram0/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram1/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram2/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram3/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram4/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram5/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram6/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

find: Symbolic link `/etc/skel/.wine/dosdevices/z:/sys/devices/platform/pcspkr/subsystem/devices/i8042/serio0/subsystem/devices/serio1/input/input7/subsystem/input1/device/subsystem/devices/usb1/driver/module/drivers/usb:hub/2-0:1.0/usb_endpoint/usbdev2.1_ep81/subsystem/usbdev1.2_ep00/device/1-1:1.0/host2/target2:0:0/2:0:0:0/subsystem/devices/0:0:0:0/generic/subsystem/sg1/device/block:sda/subsystem/ram7/subsystem' is part of a loop in the directory hierarchy; we have already visited the directodpkg: error processing base-files (--configure):

 subprocess post-installation script killed by signal (Interrupt)

Errors were encountered while processing:

 base-files

E: Sub-process /usr/bin/dpkg returned an error code (1)


```

The above error after i click yes, will go on forever until i force it to cancel.  

HELP!!!!!!:confused:

---

### Post by hansdown on 2008-11-12
Hi VTshredder.

Have you tried running sudo dpkg --confiure -a  in the terminal?

---

### Post by VTshredder on 2008-11-12
Thanks for the reply hans...actually i have.  And i do get the same exact error messages.  They second i type in my password after that command, the terminal goes crazy with the above error messages related to find: symbolic link

---

### Post by hansdown on 2008-11-12
I notice some of the programs have to do with wine.
Is this an avenue to follow?

---

### Post by VTshredder on 2008-11-12
Honestly, no its not.  My wine usage is slim to none to be honest. 
Any way around it?

Also for the record i have de-selected some of the updates and run the update manager with just a few updates (not all just the ones that looked vital).  I get the same issues with most updates de-selected...and i have been playing around with the update manager to see if it has to do with one update or another...still no progress.

---

### Post by ciscosurfer on 2008-11-12
> **VTshredder said:**
> Honestly, no its not.  My wine usage is slim to none to be honest. 
Any way around it?Since your WINE usage is slim to none, get rid of WINE and start again.  You've got symbolic links in loops (meaning they are linked back on themselves) in the directories mentioned.  You can either traverse to those directories and remove the bad links, or remove WINE and begin the update procedure again.

---

### Post by VTshredder on 2008-11-12
Thanks for the reply cisco!

I have now removed wine using the dpkg command, and according to the terminal it was removed successfully.  Even when i go back into Add/Remove programs is shows i no longer have wine installed.

BUT, after running the updates again....i still get the same insanity when the available updates are being installed.

---

### Post by zvacet on 2008-11-12
You removed wine pckage but you still have **.wine** folder in you home directory under hidden files.Delete that folder too and see if that help.Try with 

```
sudo apt-get update && sudo apt-gwet upgrade
```

---

### Post by ciscosurfer on 2008-11-13
@VTshredder,

Open a root nautilus window```
gksudo nautilus
```Traverse to and open the **/etc/skel** directory, hit **Ctrl+H** to show hidden files, right-click the **.wine** directory, select delete, begin update process one more time.

---

### Post by Yellow Pasque on 2008-11-13
Configuration files will be left over unless you --purge wine (or mark for "complete removal" in Synaptic).

---

### Post by ciscosurfer on 2008-11-13
> **Temüjin said:**
> Configuration files will be left over unless you --purge wine (or mark for "complete removal" in Synaptic).Good point :-D

---

### Post by VTshredder on 2008-11-13
Thanks again Cisco...
This is what i get when i run that command:```
eightvirtues@eightvirtues-desktop:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:7594): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSseahorse nautilus module shutdown

--- Hash table keys for warning below:
--> file:///root

(nautilus:7594): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:7594): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

```

---

### Post by Yellow Pasque on 2008-11-13
```
sudo dpkg --purge wine
```

---

### Post by VTshredder on 2008-11-13
> **Temüjin said:**
> Configuration files will be left over unless you --purge wine (or mark for "complete removal" in Synaptic).

I actually did purge the wine files earlier.  I have searched high and low (yes hidden files) and no trace of wine at all...nothing in the home directory, file system...synaptic....nada.  
Hence me ripping my hair out....

---

### Post by VTshredder on 2008-11-13
> **Temüjin said:**
> ```
sudo dpkg --purge wine
```


```
eightvirtues@eightvirtues-desktop:~$ sudo dpkg --purge wine
[sudo] password for eightvirtues: 
dpkg - warning: ignoring request to remove wine which isn't installed.
```

---

### Post by ciscosurfer on 2008-11-13
Let's try this in a terminal```
sudo rm -r /etc/skel/.wine
```Then re-run the update.

---

### Post by VTshredder on 2008-11-13
> **ciscosurfer said:**
> Let's try this in a terminal```
sudo rm -r /etc/skel/.wine
```Then re-run the update.

Worked like a dream!!!!  
You sir...are the man.  If you ever visit Vermont, drinks are on me.

Thanks a ton....my only curiosity is what caused all the madness?
Nonetheless....you rule!!

Also want to thank everyone else who took the time to look into my issue!!  Gotta love this community!

---

### Post by ciscosurfer on 2008-11-13
I'll be brief: \\:D/=D>

---

### Post by hansdown on 2008-11-13
You do rock ciscosurfer!

---

### Post by ciscosurfer on 2008-11-13
Danke!  Bring it :guitar:
OT: One of the most enjoyable aspects of these forums (for me anyway) is how it truly is a communal effort; everyone can contribute and pitch in--it epitomizes what Ubuntu is all about. :-D

---

### Post by Viranh on 2008-11-13
Edit: seems I was reading furthur back, and what I suggested was already tried.

---

### Post by brento73 on 2008-11-13
Does anyone know what causes/d this? I'm getting the same issue, and I DO use wine, quit a bit, although I had never even heard of this directory before tonight.

---

