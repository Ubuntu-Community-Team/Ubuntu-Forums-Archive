---
title: "HP PSC 2175 Scanner"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by DistroTech on 2007-08-23
Hello there UbuntuForums!

I'm trying to get the scanning functionality of an HP PSC 2175 All-In-One to work.

Printing works fine, and the HP Toolbox seems to detect everything alright.

When I try to scan, I get the same problem described here[http://ubuntuforums.org/showthread.php?t=486113&page=2]("http://ubuntuforums.org/showthread.php?t=486113&page=2")

The solution to that seemed to be a fresh install, but this IS a fresh install of Feisty.

Here's some helpful data, I'd love to get some help with this...:)

The exact error I get is this...

Kooka says that no scanner is found, and that I have to install and configure sane.

XSane returns this error: Failed to open device 'hpaio:/usb/PSC_2170_Series?serial=MY44RF427Q73':Error during device I/O

> 
joanne@main:~$ scanimage -L
device `hpaio:/usb/PSC_2170_Series?serial=MY44RF427Q73' is a Hewlett-Packard PSC_2170_Series all-in-one

j> oanne@main:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2b11 [PSC 2170 Series]) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

> joanne@main:~$ hp-info

HP Linux Imaging and Printing System (ver. 1.7.3)
Device Information Utility ver. 3.4

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/PSC_2170_Series?serial=MY44RF427Q73

hp:/usb/PSC_2170_Series?serial=MY44RF427Q73

Device Parameters (dynamic data):
  Parameter                     Value(s)                                        
  ----------------------------  ----------------------------------------------------------
  3bit-status-code              24                                              
  3bit-status-name              NoFault                                         
  agent1-ack                    False                                           
  agent1-desc                   Black cartridge                                 
  agent1-dvc                    0                                               
  agent1-health                 0                                               
  agent1-health-desc            Very low                                        
  agent1-hp-ink                 False                                           
  agent1-id                     9                                               
  agent1-kind                   3                                               
  agent1-known                  False                                           
  agent1-level                  0                                               
  agent1-level-trigger          7                                               
  agent1-sku                    56 (C6656A) / 27 (C8727A)                       
  agent1-type                   1                                               
  agent1-virgin                 False                                           
  agent2-ack                    False                                           
  agent2-desc                   Tri-color cartridge                             
  agent2-dvc                    0                                               
  agent2-health                 0                                               
  agent2-health-desc            Good/OK                                         
  agent2-hp-ink                 False                                           
  agent2-id                     10                                              
  agent2-kind                   3                                               
  agent2-known                  False                                           
  agent2-level                  33                                              
  agent2-level-trigger          0                                               
  agent2-sku                    57 (C6657A) / 28 (C8728A)                       
  agent2-type                   2                                               
  agent2-virgin                 False                                           
  agent3-ack                    False                                           
  agent3-desc                   Photo cartridge                                 
  agent3-dvc                    0                                               
  agent3-health                 1                                               
  agent3-health-desc            Not installed                                   
  agent3-hp-ink                 False                                           
  agent3-id                     0                                               
  agent3-kind                   3                                               
  agent3-known                  False                                           
  agent3-level                  0                                               
  agent3-level-trigger          7                                               
  agent3-sku                    58 (C6658A)                                     
  agent3-type                   3                                               
  agent3-virgin                 False                                           
  back-end                      hp                                              
  cups-printer                  PSC_2170                                        
  cups-uri                      hp:/usb/PSC_2170_Series?serial=MY44RF427Q73     
  dev-file                                                                      
  device-state                  1                                               
  device-uri                    hp:/usb/PSC_2170_Series?serial=MY44RF427Q73     
  deviceid                      MFG:Hewlett-Packard;MDL:PSC 2170                
                                Series;CMD:MLC,PCL,PML,DW-PCL,DYN;CLS:PRINTER;1284.4DL:4d,
                                4e,1;SN:MY44RF427Q73;S:0380008084021000002c14f0000c2500021
                                ;AiO:0;                                         
  duplexer                      0                                               
  error-state                   102                                             
  host                                                                          
  in-tray1                      True                                            
  in-tray2                      False                                           
  is-hp                         True                                            
  media-path                    3                                               
  panel                         1                                               
  panel-line1                   Power Save On.                                  
  panel-line2                                                                   
  photo-tray                    0                                               
  port                          1                                               
  r                             0                                               
  revision                      3                                               
  rg                            000                                             
  rr                            000000                                          
  rs                            000000000                                       
  scan-uri                      hpaio:/usb/PSC_2170_Series?serial=MY44RF427Q73  
  serial                        MY44RF427Q73                                    
  status-code                   1501                                            
  status-desc                   Black cartridge is low on ink                   
  supply-door                   0                                               
  top-door                      1                                               

Model Parameters (static data):
  Parameter                     Value(s)                                        
  ----------------------------  ----------------------------------------------------------
  align-type                    1                                               
  clean-type                    1                                               
  color-cal-type                0                                               
  copy-type                     0                                               
  embedded-server-type          0                                               
  fax-type                      0                                               
  fw-download                   0                                               
  icon                          default_psc.png                                 
  io-control                    0                                               
  io-mfp-mode                   2                                               
  io-mode                       1                                               
  io-scan-port                  0                                               
  io-support                    2                                               
  linefeed-cal-type             0                                               
  model                         PSC_2170_Series                                 
  model-ui                      HP PSC 2170 series                              
  model1                        PSC 2170                                        
  model2                        PSC 2171                                        
  model3                        PSC 2175                                        
  model4                        PSC 2175v                                       
  model5                        PSC 2175xi                                      
  model6                        PSC 2179                                        
  panel-check-type              1                                               
  pcard-type                    1                                               
  pq-diag-type                  0                                               
  r-type                        0                                               
  r0-agent1-kind                3                                               
  r0-agent1-sku                 56 (C6656A) / 27 (C8727A)                       
  r0-agent1-type                1                                               
  r0-agent2-kind                3                                               
  r0-agent2-sku                 57 (C6657A) / 28 (C8728A)                       
  r0-agent2-type                2                                               
  r0-agent3-kind                3                                               
  r0-agent3-sku                 58 (C6658A)                                     
  r0-agent3-type                3                                               
  scan-style                    1                                               
  scan-type                     1                                               
  status-battery-check          0                                               
  status-dynamic-counters       0                                               
  status-type                   2                                               
  support-released              1                                               
  support-type                  2                                               
  support-ver                   0.9.5                                           
  tech-class                    DJ9xxVIP                                        
  tech-type                     2                                               


Thanks in advance guys!
-DT

---

### Post by nadamsieee on 2007-08-25
I'm having the same problem with my HP PSC-1210xi. :confused:

---

### Post by Sebastral on 2007-09-09
Try the hplip automatic install script; [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Worked wonders for me :)

---

### Post by nadamsieee on 2007-09-22
> **Sebastral said:**
> Try the hplip automatic install script; [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

This printer used to 'just work'. I'm not sure what happened to cause it to fail.

---

### Post by Martin C Baumann on 2007-09-28
Thanks. Had the same problem with a Photosmart 2575a. Sebastal's hint resolved it, working like a treat now.:KS

---

### Post by FXFman1209 on 2007-10-22
This has not helped me at all. I am currently running a new installation of Gutsy, and I simply cannot get my PSC-2175 to scan. Please help.

---

### Post by hardawayd on 2007-10-29
I can not get mine to work either.  This should have been fixed before release.

---

### Post by sadohert on 2008-05-06
Anyone have any luck with this?  I have a fairly fresh Gutsy install and the printing works fine, but XSane errors out when I try to scan.  I'm looking at installing the latest hplip, but when I go to uninstall the current (packaged) version (2.7.12) it says some packages have unmet dependencies and need to be installed.  The packages are hpijs, and ubuntu-desktop.  The thought of uninstalling the 2nd one kinda scares me... like I"ll end up rebooting to nothing but a terminal... 1980 style.

---

