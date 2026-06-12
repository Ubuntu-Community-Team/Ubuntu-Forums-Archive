---
title: "Attempting to get built-in webcam working again"
date: 2008-09-09
forum: Hardware
---

### Post by stropyboy11 on 2008-09-09
I had my built in webcam working before on my laptop, but I got a new hard drive, and since I have been unable to get the thing working. I know the driver is located here [http://www.arakhne.org/ricoh/index.html]("http://www.arakhne.org/ricoh/index.html"), but I kinda forget how to install drivers like that, as my friend did it for me. If you need any information I have tons of homework left to do, so I'll be happy to oblige :). Thanks a lot!

---

### Post by stropyboy11 on 2008-09-09
Ok, strike that. I've actually just installed the drivers, but still no dice getting the webcam to work. It's a DV6000T laptop. Anyone wanna help a noob out?

---

### Post by IntuitiveNipple on 2008-09-09
I've got the up-to-date r5u870 driver in my PPA. It is a DKMS (Dynamic Kernel Module Support) package so it will be automatically rebuilt if the kernel is updated. Try installing it:

Add my PPA:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
Install the driver:
```

sudo apt-get install r5u870-dkms

```
Remove my PPA:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by HalphaZ on 2008-09-09
I'm going to try your DKMS driver...
However I've some problems with official driver:
[http://ubuntuforums.org/showthread.php?t=914769](http://ubuntuforums.org/showthread.php?t=914769)

See you soon

---

### Post by stropyboy11 on 2008-09-09
Hrm, didn't work. I think adding the PPA didn't work for some reason, but I accidenally already closed out the terminal so I can't show  you specifically what happened. Anyway, I ran everything you said, and it didn't work unfortunately...and now when I try to open the PPA again by running that command, nothing happens. Any suggestions?

---

### Post by HalphaZ on 2008-09-09
I tried, it didn't work... I rebooted:

```
dmesg | grep -i uvc
[   38.727615] uvcvideo: disagrees about version of symbol video_devdata
[   38.727622] uvcvideo: Unknown symbol video_devdata
[   38.727973] uvcvideo: disagrees about version of symbol video_unregister_device
[   38.727975] uvcvideo: Unknown symbol video_unregister_device
[   38.728183] uvcvideo: disagrees about version of symbol video_device_alloc
[   38.728186] uvcvideo: Unknown symbol video_device_alloc
[   38.728261] uvcvideo: disagrees about version of symbol video_register_device
[   38.728264] uvcvideo: Unknown symbol video_register_device
[   38.728481] uvcvideo: disagrees about version of symbol video_device_release
[   38.728483] uvcvideo: Unknown symbol video_device_release

```


```
dmesg | grep -i r5u870
[   39.188396] r5u870: Unknown symbol usbcam_ctrl_add
[   39.188449] r5u870: Unknown symbol usbcam_curframe_get
[   39.188504] r5u870: Unknown symbol usbcam_claim_interface
[   39.188553] r5u870: Unknown symbol usbcam_curframe_testpattern
[   39.188603] r5u870: Unknown symbol usbcam_urbstream_stop
[   39.188652] r5u870: Unknown symbol usbcam_urbstream_start
[   39.188702] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[   39.188751] r5u870: Unknown symbol usbcam_urbstream_cleanup
[   39.188807] r5u870: Unknown symbol usbcam_register_mod
[   39.188991] r5u870: Unknown symbol usbcam_curframe_abortall
[   39.189044] r5u870: Unknown symbol usbcam_curframe_complete_detail
[   39.189094] r5u870: Unknown symbol usbcam_unregister
[   39.189150] r5u870: Unknown symbol usbcam_urbstream_init
[   39.189205] r5u870: Unknown symbol usbcam_choose_altsetting
[   39.189260] r5u870: Unknown symbol usbcam_ctrl_alloc
[   39.189309] r5u870: Unknown symbol usbcam_urbstream_config_iso
```


```
uname -a
Linux MasterChief 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
```

```
lsusb
Bus 002 Device 003: ID 0518:0005 EzKEY Corp. 
Bus 002 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000
```

```
lsmod
http://rafb.net/p/pKmDpx10.html
```

Thanks for your help!

---

### Post by stropyboy11 on 2008-09-09
Yeah, I'm still not working. Can someone PLEASE help? I'm more than willing to provide whatever information you need.

---

### Post by stropyboy11 on 2008-09-09
Ach, I'm really desperate here. Am I not installing the drivers correctly? Is there maybe another way I can uninstall those r5u870 drivers and start from scratch? I think I may have messed up the process....

---

### Post by stropyboy11 on 2008-09-09
Sorry to keep reposting on this old thread, but I really do need some help. If anyone can help me out, it would be greatly appreciated.

---

### Post by IntuitiveNipple on 2008-09-10
It sounds as if you've got conflicts with drivers you've tried to install manually, and kernel updates. The DKMS package is designed to cope with that by rebuilding itself automatically if the kernel is updated.

Remove the products of any manual build/install attempts you made and then try again.

When you are tinkering with the kernel and configuration like this, it is always advisable to make note of all the steps you take and the precise commands you use and their results (Copy/paste to Text Editor) so you can always unpick the steps as well as report precisely what has been done.

---

### Post by stropyboy11 on 2008-09-10
I don't think I've ever done a manual build/install...again, I'm really not that knowledgable about Ubuntu. I mostly try to stay on Synaptic...

---

### Post by IntuitiveNipple on 2008-09-10
Perform the steps I gave in comment #3 again, and if you have problems copy the output into a reply so we can diagnose it.

---

### Post by stropyboy11 on 2008-09-10
Here's the whole output...

> stropko@stropko-laptop:~$ sudo sh -c "echo 'deb [http://ppa.launchpad.net/intuitivenipple/ubuntu](http://ppa.launchpad.net/intuitivenipple/ubuntu) $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
[sudo] password for stropko: 
stropko@stropko-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [57.6kB]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [22.9kB]                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [311kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [13.0kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [29.6kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [4919B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]      
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [88.4kB]        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [90.8kB]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [22.7kB]    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [20.1kB] 
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [2795B]   
Fetched 832kB in 11s (71.8kB/s)                                                
Reading package lists... Done
stropko@stropko-laptop:~$ sudo apt-get install r5u870-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
r5u870-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
stropko@stropko-laptop:~$ sudo rm /etc/apt/sources.list.d/intuitivenipple.list
stropko@stropko-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done


---

### Post by stropyboy11 on 2008-09-11
Can anyone derive anything from that or provide me with another way to activate my webcam?

---

### Post by stropyboy11 on 2008-09-11
Hello? Can anyone help out?

---

