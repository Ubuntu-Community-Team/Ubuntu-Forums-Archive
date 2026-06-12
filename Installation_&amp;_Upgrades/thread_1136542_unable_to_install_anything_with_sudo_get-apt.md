---
title: "unable to install anything with sudo get-apt"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2009-04-25
When try to install anything I receive the following message

abel@ernesto:~$ sudo apt-get install real
[sudo] password for abel:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

this has happened after I tried to install Java6 through the terminal...is there a link between the two events?

thanks in advance for your time
Abel

---

### Post by ninjapirate89 on 2009-04-25
Do you have Add/Remove Programs, Synaptic, or Update Manager going?

---

### Post by gjoellee on 2009-04-25
You can't **install packages** from Add/Remove, Update Manager, Synaptic, GDebi or Terminal at the same time, but you are trying to install from one or more of the programs at the same time.

Wait for the opther program to bu finished and close them before you try to install java again.

---

### Post by abelito8 on 2009-04-25
Also the command "remove" gives the same results

abel@ernesto:~$ sudo aptitude remove java
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
abel@ernesto:~$

---

### Post by abelito8 on 2009-04-25
I have closed exerything, even rebooted the computer but it still says the same thing

---

### Post by Partyboi2 on 2009-04-25
Make sure that there are not package manager processes running you can check by 
```
ps -e
```look down the list and if you see any package manager running like, synaptic, update-manager or apt-get then kill the process with
```
sudo killall name
``` replace 'name' with the name of the process.

If there are no package manager running then try removing the lock file
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by abelito8 on 2009-04-25
Thank you but the ps-e gives no results, am I supposed to type anything else?

abel@ernesto:~$ ps-e
bash: ps-e: command not found

---

### Post by _Purple_ on 2009-04-25
> **abelito8 said:**
> Thank you but the ps-e gives no results, am I supposed to type anything else?

abel@ernesto:~$ ps-e
bash: ps-e: command not found

```
ps -e
```

---

### Post by abelito8 on 2009-04-25
Thank you for ps -e :) 

Tried, no packages running apparently
and the term does not recognize the command 

sudo rm /var/lib/dpkg/lock

abel@ernesto:~$ ps -e                                          
  PID TTY          TIME CMD                                    
    1 ?        00:00:02 init                                   
    2 ?        00:00:00 kthreadd                               
    3 ?        00:00:00 migration/0                            
    4 ?        00:00:00 ksoftirqd/0                            
    5 ?        00:00:00 watchdog/0                             
    6 ?        00:00:00 migration/1                            
    7 ?        00:00:00 ksoftirqd/1                            
    8 ?        00:00:00 watchdog/1                             
    9 ?        00:00:00 events/0                               
   10 ?        00:00:00 events/1                               
   11 ?        00:00:00 khelper                                
   51 ?        00:00:00 kintegrityd/0                          
   52 ?        00:00:00 kintegrityd/1                          
   54 ?        00:00:00 kblockd/0                              
   55 ?        00:00:00 kblockd/1                              
   57 ?        00:00:00 kacpid                                 
   58 ?        00:00:00 kacpi_notify                           
  139 ?        00:00:00 cqueue                                 
  143 ?        00:00:00 kseriod                                
  188 ?        00:00:00 pdflush                                
  189 ?        00:00:00 pdflush                                
  190 ?        00:00:00 kswapd0                                
  232 ?        00:00:00 aio/0                                  
  233 ?        00:00:00 aio/1                                  
 1213 ?        00:00:00 ksuspend_usbd                          
 1219 ?        00:00:00 khubd                                  
 1386 ?        00:00:00 ata/0                                  
 1397 ?        00:00:00 ata/1                                  
 1402 ?        00:00:00 khpsbpkt                               
 1408 ?        00:00:00 ata_aux                                
 1476 ?        00:00:00 scsi_eh_0                              
 1477 ?        00:00:00 scsi_eh_1                              
 1478 ?        00:00:00 scsi_eh_2                              
 1870 ?        00:00:00 knodemgrd_0                            
 1888 ?        00:00:01 scsi_eh_3                              
 1890 ?        00:00:00 scsi_eh_4                              
 2277 ?        00:00:00 kjournald                              
 2451 ?        00:00:00 udevd                                  
 2678 ?        00:00:00 sony-laptop                            
 2743 ?        00:00:00 tifm                                   
 2787 ?        00:00:00 pccardd                                
 2846 ?        00:00:00 kpsmoused                              
 4349 tty4     00:00:00 getty                                  
 4350 tty5     00:00:00 getty                                  
 4357 tty2     00:00:00 getty                                  
 4358 tty3     00:00:00 getty                                  
 4359 tty6     00:00:00 getty                                  
 4551 ?        00:00:00 acpid                                  
 4609 ?        00:00:00 kondemand/0                            
 4611 ?        00:00:00 kondemand/1                            
 4675 ?        00:00:00 syslogd                                
 4724 ?        00:00:00 dd                                     
 4726 ?        00:00:00 klogd                                  
 4749 ?        00:00:07 dbus-daemon                            
 4771 ?        00:00:00 avahi-daemon                           
 4772 ?        00:00:00 avahi-daemon                           
 4819 ?        00:00:00 cupsd                                  
 4910 ?        00:00:04 hald                                   
 4913 ?        00:00:01 console-kit-dae                        
 4914 ?        00:00:00 hald-runner                            
 5003 ?        00:00:00 hald-addon-inpu                        
 5005 ?        00:00:00 hald-addon-cpuf                        
 5006 ?        00:00:00 hald-addon-acpi                        
 5022 ?        00:00:01 hald-addon-stor                        
 5069 ?        00:00:00 bluetoothd                             
 5076 ?        00:00:00 btaddconn                              
 5077 ?        00:00:00 btdelconn                              
 5107 ?        00:00:00 krfcommd                               
 5127 ?        00:00:00 NetworkManager                         
 5137 ?        00:00:00 wpa_supplicant                         
 5139 ?        00:00:00 nm-system-setti                        
 5143 ?        00:00:00 kdm                                    
 5178 ?        00:00:00 atd                                    
 5206 ?        00:00:00 cron                                   
 5336 tty1     00:00:00 getty                                  
 5464 tty7     00:06:10 Xorg                                   
 5495 ?        00:00:00 kdm                                    
 5508 ?        00:00:00 dbus-launch                            
 5509 ?        00:00:00 dbus-daemon                            
 5516 ?        00:00:00 ck-launch-sessi                        
 5557 ?        00:00:00 ssh-agent                              
 5571 ?        00:00:00 x-session-manag                        
 5574 ?        00:00:00 dbus-launch                            
 5575 ?        00:00:00 dbus-daemon                            
 5637 ?        00:00:00 kdeinit4                               
 5638 ?        00:00:00 klauncher                              
 5640 ?        00:00:02 kded4                                  
 5645 ?        00:00:00 kwrapper4                              
 5646 ?        00:00:00 ksmserver                              
 5648 ?        00:01:25 kwin                                   
 5704 ?        00:00:19 plasma
 5705 ?        00:00:10 knotify4
 5711 ?        00:00:00 kio_file
 5712 ?        00:00:04 krunner
 5714 ?        00:00:00 nepomukserver
 5722 ?        00:00:00 kxkb
 5727 ?        00:00:00 kaccess
 5729 ?        00:00:00 nepomukservices
 5734 ?        00:00:00 nepomukservices
 5735 ?        00:00:00 nepomukservices
 5737 ?        00:00:00 kmix
 5739 ?        00:00:08 skype
 5774 ?        00:00:06 guidance-power-
 5798 ?        00:00:01 python
 5806 ?        00:00:00 klipper
 5807 ?        00:00:00 kblueplugd
 5860 ?        00:00:39 knetworkmanager
 5894 ?        00:00:00 kdeinit
 5897 ?        00:00:00 dcopserver
 5900 ?        00:00:00 klauncher
 5902 ?        00:00:00 kded
 5912 ?        00:00:00 knotify
 5915 ?        00:00:00 pppd
 5919 ?        00:00:03 artsd
 6027 ?        00:19:30 firefox
 6030 ?        00:00:00 gconfd-2
 6227 ?        00:00:02 apt-get
 6255 pts/2    00:00:00 dpkg
 6294 pts/2    00:00:01 frontend
 6300 pts/2    00:00:00 preinst
 6304 pts/2    00:00:01 whiptail
 7514 ?        00:00:00 dbus-daemon
 7515 ?        00:00:00 dbus-launch
 7767 ?        00:00:02 konsole
 7769 pts/3    00:00:00 bash
 8320 pts/3    00:00:00 ps
abel@ernesto:~$ sudo rm /var/lib/dpkg/lock
abel@ernesto:~$ sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory

---

### Post by Partyboi2 on 2009-04-25
According to the output you have dpkg and apt-get process running so you will need to kill them.
```
sudo killall dpkg
sudo killall apt-get
```

---

