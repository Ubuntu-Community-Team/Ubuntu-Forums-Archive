---
title: "Promise SATA300 TX4"
date: 2009-02-14
forum: Hardware
---

### Post by supersobbie on 2009-02-14
I have searched and searched... I am having trouble replying to message so I decided to start my own.  Am having the same problem in this thread [http://ubuntuforums.org/showthread.php?t=268570&page=3](http://ubuntuforums.org/showthread.php?t=268570&page=3) post number 31.  I just did a fresh install of ubuntu server 8.1.  My goal is to have 2 1TB drives (no raid) mounted with ubuntu running off a ide drive. Here is my information:

**************************  I can see the drives:
sudo cat /proc/scsi/scsi

Attached devices:                                                 
Host: scsi2 Channel: 00 Id: 00 Lun: 00                            
  Vendor: ATA      Model: ST3120026A       Rev: 8.54              
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 01 Lun: 00                            
  Vendor: SONY     Model: DVD RW DRU-720A  Rev: JY01              
  Type:   CD-ROM                           ANSI  SCSI revision: 05
**************************

lsmod|grep -i promise 

sata_promise           19076  0                                                          
libata                176032  5 sata_promise,pata_acpi,ata_piix,pata_pdc2027x,ata_generic

**************************
dmesg | grep sata 

Returns Nothing
**************************

sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes                                 
255 heads, 63 sectors/track, 14593 cylinders                                
Units = cylinders of 16065 * 512 = 8225280 bytes                            
Disk identifier: 0x0009189a                                                 
                                                                            
   Device Boot      Start         End      Blocks   Id  System              
/dev/sda1   *           1       13995   112414806   83  Linux               
/dev/sda2           13996       14593     4803435    5  Extended            
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
**************************

as you can see fdisk does not see the sata drives but they are listed in /proc/scsi/scsi.

What is the next step?  how do I get ubuntu server to recognize these 2 drives?

:)

Kind Regards,
SoBBie

PS why can I not post to some threads like the one mentioned above?



*****************************

OK I made a mistake... the items listed in /proc/scsi/scsi were from my other controller card.... when I unplugged them the drives disappeared from there.  so basically I am not seeing anything from my promise raid SATA300 TX4 card.  is there anyone that has gotten this one to work....  The only reason I picked this card was because it is the one used in unRAID machines so I assumed it would work with any linux.

Regards,
SoBBie

---

### Post by supersobbie on 2009-02-17
ok so I was having problem with this and got around to trying to build the kernel module driver from promise website.  I basically followed the instructions from the website here (for an earlier version of linux).  But I run into a problem.  I download all the tools mentioned (linux-source, ...) and copy the config file to .config in the /usr/src/linux/ dir.  I build the kernel.  I do the make, make install, make modules, and make modules_install.   Then I do into the ut directory where the promis controller is (I did download the 2.6 kernel version) and try to run make clean and I get a error saying config.h not found.  What the hell....  I can not figure it out.  I have looked around the internet and some places mentioned that I needed the kernel headers... so installed them adn I still get that issue.

Has anyone ever install the Promise SATA300 TX4 on a ubuntu 8.1 server successfully?  What am I doing wrong.  I installed ubuntu on an attached IDE drive directly on the mobo.  It boots fine.  but not controller card.  Any help would be GREAT.

Thanks again,
SuPerSoBBie

---

