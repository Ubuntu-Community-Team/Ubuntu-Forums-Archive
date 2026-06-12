---
title: "Scanner no Longer Works"
date: 2009-03-25
forum: Hardware
---

### Post by therian on 2009-03-25
I am running 64 bit Ubuntu (8.10) --

I have an hp psc 1315 all-in-one printer/scanner/copier -- 

It scanned fine before I did the last round of updates about a week or so ago.

Now when I type in xsane, it says "scanning for devices" and goes no further.

I can print to the printer just fine.

Scanner DOES work (dual boot) in Vista, and works if I hook it to my other machine, running 32 Bit SuSE 11.0.  BTW the versions of xsane on both ubuntu and suse are 0.995.

Not a hardware problem, best I can determine.

What is the most likely culprit?

I am documenting all the things I learn about linux here:  

[http://www.pkill-9.com](http://www.pkill-9.com)

The work around (at least for me) is to plug it into my SuSE box, scan there, then scp the images over to my ubuntu box.  Not ideal.

Many Thanks,

Wayno

---

### Post by therian on 2009-04-19
There have been several cups update over the last few weeks but they have had no effect.  hplip is:

  hplip          2.8.7-0ubuntu6 HP Linux Printing and Imaging System (HPLIP)

which best I can tell, is latest.

Scanner is only picking up bottom 6 inches of page, and chops of 2 inches of the left margin.

Used to work on Ubuntu.  Now it doesn't.

Wayno

---

### Post by therian on 2009-06-14
[http://hplipopensource.com/hplip-web/release_notes.html](http://hplipopensource.com/hplip-web/release_notes.html) 

Release Notes

*HPLIP 3.9.4b - This release has the following changes:*


   Detailed Change Log

Fixes for Ubuntu 9.04 and PolicyKit (updated com.hp.hplip.conf to be more precise and made com.hp.hplip.service configurable so that it properly names the location of hp-pkservice).


---------

dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          3.9.2-3ubuntu4 HP Linux Printing and Imaging System (HPLIP)
nwayno@Homer:~$ sudo apt-get install hplip
[sudo] password for nwayno:
Reading package lists... Done
Building dependency tree      Reading state information... Done
hplip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

-----------

Soooo, there's a fix for ubuntu - the repos don't have it - and I have NEVER encountered a ".run" file.....

please advise.

Wayno

---

### Post by david_lynch on 2009-06-15
It looks like the crew is out of the office. 

At any rate, there may be some lag time before the fix gets into the repos. You may have to go into synaptic and enable backports to get anything newer than your current version though.

If you do want to run the run file, then your existing package file get overwritten. Your choice though, it may or may not cause problems. 

To run a run file, just run it. If it's not executable, you can always say "sh file.run" assuming the name of the run file is file.run

---

### Post by therian on 2009-06-15
Thanks for the information.

The rebuild went fine, but the SCANNER STILL DOES NOT WORK!

This is what the scan looks like in Suse:

[http://www.pkill-9.com/wayno/pics/scanner_suse.jpg](http://www.pkill-9.com/wayno/pics/scanner_suse.jpg)  (works)

and this is what it does in ubuntu:

[http://www.pkill-9.com/wayno/pics/scanner_ubuntu.jpg](http://www.pkill-9.com/wayno/pics/scanner_ubuntu.jpg) (chops off)

here the hp-info stuph:

--------

hp-info

HP Linux Imaging and Printing System (ver. 3.9.4b)
Device Information Utility ver. 5.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/psc_1310_series?serial=CN47FB80Q5O2


HP Linux Imaging and Printing System (ver. 3.9.4b)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?

hp:/usb/psc_1310_series?serial=CN47FB80Q5O2

Device Parameters (dynamic data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
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
  agent1-level-trigger          6                                                         
  agent1-sku                    27 (C8727AN)/56 (C6656AN)                                 
  agent1-type                   1                                                         
  agent1-virgin                 False                                                     
  agent2-ack                    False                                                     
  agent2-desc                   Tri-color cartridge                                       
  agent2-dvc                    0                                                         
  agent2-health                 0                                                         
  agent2-health-desc            Good/OK                                                   
  agent2-hp-ink                 False                                                     
  agent2-id                     0                                                         
  agent2-kind                   3                                                         
  agent2-known                  False                                                     
  agent2-level                  94                                                        
  agent2-level-trigger          0                                                         
  agent2-sku                    28 (C8728AN)/57 (C6657AN)                                 
  agent2-type                   2                                                         
  agent2-virgin                 False                                                     
  back-end                      hp                                                        
  cups-printer                  Envelopes,psc-1310-series                                 
  cups-uri                      hp:/usb/psc_1310_series?serial=CN47FB80Q5O2               
  dev-file                                                                                
  device-state                  1                                                         
  device-uri                    hp:/usb/psc_1310_series?serial=CN47FB80Q5O2               
  deviceid                      MFG:hp;MDL:psc 1310 series                                
                                ;CMD:LDL,MLC,PML,DYN;CLS:PRINTER;1284.4DL:4d,4e,1;SN:CN47F
                                B80Q5O2;S:0380008000020020002c14e0000c250005e;Z:007;      
  duplexer                      0                                                         
  error-state                   102                                                       
  host                                                                                    
  in-tray1                      True                                                      
  in-tray2                      False                                                     
  is-hp                         True                                                      
  media-path                    2                                                         
  panel                         0                                                         
  panel-line1                                                                             
  panel-line2                                                                             
  photo-tray                    0                                                         
  port                          1                                                         
  r                             0                                                         
  revision                      3                                                         
  rg                            000                                                       
  rr                            000000                                                    
  rs                            000000000                                                 
  scan-uri                      hpaio:/usb/psc_1310_series?serial=CN47FB80Q5O2            
  serial                        CN47FB80Q5O2                                              
  status-code                   1501                                                      
  status-desc                   Black cartridge is low on ink                             
  supply-door                   0                                                         
  top-door                      1                                                         

Model Parameters (static data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  align-type                    6                                                         
  clean-type                    2                                                         
  color-cal-type                0                                                         
  copy-type                     0                                                         
  embedded-server-type          0                                                         
  fax-type                      0                                                         
  fw-download                   False                                                     
  icon                          psc_1100_series.png                                       
  io-mfp-mode                   6                                                         
  io-mode                       1                                                         
  io-support                    2                                                         
  job-storage                   0                                                         
  linefeed-cal-type             0                                                         
  model                         psc_1310_series                                           
  model-ui                      HP PSC 1310 Series                                        
  model1                        HP PSC 1310 All-in-One Printer                            
  model2                        HP PSC 1311 All-in-One Printer                            
  model3                        HP PSC 1312 All-in-One Printer                            
  model4                        HP PSC 1315 All-in-One Printer                            
  model5                        HP PSC 1315xi All-in-One Printer                          
  model6                        HP PSC 1315v All-in-One Printer                           
  model7                        HP PSC 1315s All-in-One Printer                           
  model8                        HP PSC 1317 All-in-One Printer                            
  model9                        HP PSC 1318 All-in-One Printer                            
  monitor-type                  0                                                         
  panel-check-type              0                                                         
  pcard-type                    0                                                         
  plugin                        0                                                         
  plugin-reason                 0                                                         
  power-settings                0                                                         
  pq-diag-type                  0                                                         
  r-type                        0                                                         
  r0-agent1-kind                3                                                         
  r0-agent1-sku                 27 (C8727AN)/56 (C6656AN)                                 
  r0-agent1-type                1                                                         
  r0-agent2-kind                3                                                         
  r0-agent2-sku                 28 (C8728AN)/57 (C6657AN)                                 
  r0-agent2-type                2                                                         
  r0-agent3-kind                3                                                         
  r0-agent3-sku                 58 (C6658AN)                                              
  r0-agent3-type                3                                                         
  scan-style                    1                                                         
  scan-type                     1                                                         
  status-battery-check          0                                                         
  status-dynamic-counters       0                                                         
  status-type                   2                                                         
  support-released              True                                                      
  support-subtype               15279                                                     
  support-type                  2                                                         
  support-ver                   0.9.5                                                     
  tech-class                    ['DJ3600']                                                
  tech-subclass                 ['Normal']                                                
  tech-type                     2                                                         
  usb-pid                       16145                                                     
  usb-vid                       1008                                                      

Done.

--------

Going to be hard to migrate my server to ubuntu, if I can't get the scanner to work.  BTW when I installed 9.04 -- I did a FRESH install -- NOT an upgrade.

So I am no better/no worse after the rebuild.

---

### Post by Absolom on 2009-08-23
I have the same problem with my epson rx595 and with the cx4800 I had before that the comp works fine with the printer but when it checks for scanner it says no scanner found. Xsane used to find it no problem but now it says none found.

---

### Post by Camilia on 2009-08-27
I had the same problem today. I went into the synaptic manager and downloaded all the programs that had xscan in them. Now it works.

---

### Post by jws957 on 2009-11-14
I'm running the amd64-bit build also.  I have an hp Officejet 6500.  I had been running 9.04 and with that installation the printer was supported by the standard hp libs, but the scanner wasn't.  I could get the scanner to work by loading the hpoj libs in Synaptic, but that library didn't have support for the printer.  I just upgraded to 9.10 and both work.

---

### Post by GrittyBalls on 2010-08-05
Hi, I'm extremely new to Ubuntu and have no clue.  However, I have the same Officejet6500 all-in-one printer as do **JWS957, **and I have a Acer Aspire 5315-2326 which had windows Vista on it.  A friend recommended formatting hard drive and loading UBUNTU, So I did.  Now I'm trying to load CD for my Office jet and nothing is happening, I have no clue and I'm a complete Nube, so If someone can enlighten me step by step to load this printer so I can scan, print and so on. Thanks in advance

---

### Post by 73ckn797 on 2010-08-05
> **GrittyBalls said:**
> Hi, I'm extremely new to Ubuntu and have no clue.  However, I have the same Officejet6500 all-in-one printer as do **JWS957, **and I have a Acer Aspire 5315-2326 which had windows Vista on it.  A friend recommended formatting hard drive and loading UBUNTU, So I did.  Now I'm trying to load CD for my Office jet and nothing is happening, I have no clue and I'm a complete Nube, so If someone can enlighten me step by step to load this printer so I can scan, print and so on. Thanks in advance

Any Windows driver disk will not work in Ubuntu. You will need to go to System/Administration/Synaptic Package Manager. From there look for hplip and install that. Also install hplip-gui.

---

### Post by cybrsaylr on 2010-08-06
> **Camilia said:**
> I had the same problem today. I went into the synaptic manager and downloaded all the programs that had xscan in them. Now it works.

Well you had better luck than me.
Been having a hard time getting my UMAX Astra 1220P scanner to work.

Just tried your solution of installing xscan and mine still won't work. Just get messages saying 'no devices available'.

My scanner runs great with XP on this dual boot setup but 32 bit Lucid can't detect the scanner.

---

### Post by GrittyBalls on 2010-08-13
Thanks 73ckn797

---

### Post by 73ckn797 on 2010-08-21
> **GrittyBalls said:**
> Thanks 73ckn797
I assume your problem was corrected?
Go to Thread Tools and mark this as SOLVED. It could help someone else

---

