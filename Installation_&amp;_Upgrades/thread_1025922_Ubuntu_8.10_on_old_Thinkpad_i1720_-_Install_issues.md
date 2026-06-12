---
title: "Ubuntu 8.10 on old Thinkpad i1720 - Install issues/disk partitions?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by rrkrr on 2008-12-30
I've installed Ubuntu 8.10 on an old Thinkpad i Series laptop with a pre-2000 BIOS.  It boots and runs, but there are dependency issues which prevent the install from completing.

Preface items are: (1) I have installed a new 250GB hard drive, which the native BIOS apparently cannot handle all at once, so I partitioned it with a 100MB assigned to /boot; 512MB assigned to swap, and the remaining space assigned to / (2) This machine has a SATA drive bus for the HD and CDROM, with SATA to PATA interfaces at the drives - the drives are PATA.  Since Feisty, the disk drivers supplied on the Ubuntu install CDs cannot handle suspend and resume for the CDROM, so the install always fails when the installer can't wake up the CDROM at some critical stage.  The way I installed this was to use a Dapper install CD, which worked with no problems, then upgraded to the lastest Dapper, dist-upgraded by network to Hardy 8.04.  Everything worked fine to this point.

After doing a net upgrade to 8.10, there are dependency problems with the kernel install.  The vmlinuz, config, initrd.img, &etc. files are generated and installed in /boot , but I had to manually run update-grub to get the new kernel added to menu.lst in /boot/grub. -  This is apparently complete enough to boot the system with the new kernel.  However, there are error messages that show that installation of all new kernel related files is not complete.  These messages show up everytime I try to install or remove anything using Synaptic or apt-get.  Here's an example of a run of apt-get autoremove:

rrkrr@Thinkpadi1720:/$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
7 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic 
Could not find postinst hook script [usr/sbin/update-grub]. 
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin' 
dpkg: error processing linux-image-2.6.27-9-generic (--configure): 
 subprocess post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.27-9-generic; however: 
  Package linux-image-2.6.27-9-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image: 
 linux-image depends on linux-image-generic (= 2.6.27.9.13); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-image (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic: 
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however: 
  Package linux-image-2.6.27-9-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration No apport report written because the error message indicates its a followup error from a previous failure. 
                                                                          No apport report written because the error message indicates its a followup error from a previous failure. 
                    No apport report written because MaxReports is reached already 
  No apport report written because MaxReports is reached already 
                                                                No apport report written because MaxReports is reached already 
                                              No apport report written because MaxReports is reached already 
                            of linux-restricted-modules-generic: 
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-9-generic; however: 
  Package linux-restricted-modules-2.6.27-9-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules: 
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.27.9.13); however: 
  Package linux-restricted-modules-generic is not configured yet. 
dpkg: error processing linux-restricted-modules (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux: 
 linux depends on linux-image (= 2.6.27.9.13); however: 
  Package linux-image is not configured yet. 
 linux depends on linux-restricted-modules (= 2.6.27.9.13); however: 
  Package linux-restricted-modules is not configured yet. 
dpkg: error processing linux (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 linux-image-2.6.27-9-generic 
 linux-image-generic 
 linux-image 
 linux-restricted-modules-2.6.27-9-generic 
 linux-restricted-modules-generic 
 linux-restricted-modules 
 linux 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

***********************************************
In the above, I particularly notice the line:

"Could not find postinst hook script [usr/sbin/update-grub]."

This is strange, because update-grub is indeed installed in the /usr/sbin directory.

I've tried removing all the above kernel related files except "linux-image-2.6.27-9-generic" to appease the dependency gods, but I still get the bit about the "postinst hook script" and the routine ends in an error.

The fact that I had to run update-grub manually to get /boot/grub/menu.lst to update with the new kernel information makes me suspect that there is something wrong with the way the apt-get routines see the disk partitions.

Is it possible the the old BIOS in this machine combined with the disk partitioning scheme prevents apt-get from seeing files located outside of /boot?  I've not had this problem with Ubuntu versions prior to 8.10.

I would appreciate any ideas.

  

Does anyone have any ideas?

---

### Post by rrkrr on 2008-12-30
Problem solved.  Not a disk partition issue at all.  The issue is described here:

[http://ubuntuforums.org/showthread.php?t=975190](http://ubuntuforums.org/showthread.php?t=975190)

---

