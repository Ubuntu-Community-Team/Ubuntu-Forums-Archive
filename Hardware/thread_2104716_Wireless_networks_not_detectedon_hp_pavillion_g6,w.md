---
title: "Wireless networks not detectedon hp pavillion g6,wifi light off"
date: 2013-01-14
forum: Hardware
---

### Post by yamil on 2013-01-14
I just removed windows 8 from my new HP becouse i couldnt stand the metro UI and just intalled the newest ubuntu distribution i believe 12.10, on windows 8 my wireless worked fine but when i made the switch the wireless togle button on f12 only turns off bluetooth and when i chwck for connections it never finds anny, the only way i can connect to the internet is through a wired connnection, i have waded through forums that say it has somethin to do with drivers but im completely new at all this and am in dire need of help. is there anyway to get my wifi working or should i go back to windows?

---

### Post by adityamagadi on 2013-01-14
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter

do this it shud work in ur terminal :)  n reboot ...

---

### Post by adityamagadi on 2013-01-14
n do it while you are hooked to the ethernet

---

### Post by yamil on 2013-01-14
so i did all you said heres what i got

  	 	 	 	 	 	   camell@camell-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get remove bcmwl-kernel-source  
 [sudo] password for camell:  
 Sorry, try again.  
 [sudo] password for camell:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Package 'bcmwl-kernel-source' is not installed, so not removed  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 camell@camell-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install firmware-b43-installer b43-fwcutter  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following NEW packages will be installed:  
   b43-fwcutter firmware-b43-installer  
 0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 22.5 kB of archives.  
 After this operation, 111 kB of additional disk space will be used.  
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main b43-fwcutter i386 1:015-14 [18.9 kB]  
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/multiverse firmware-b43-installer all 1:015-14 [3,532 B]  
 Fetched 22.5 kB in 0s (43.9 kB/s)             
 Selecting previously unselected package b43-fwcutter.  
 (Reading database ... 180187 files and directories currently installed.)  
 Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-14_i386.deb) ...  
 Selecting previously unselected package firmware-b43-installer.  
 Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-14_all.deb) ...  
 Processing triggers for man-db ...  
 Setting up b43-fwcutter (1:015-14) ...  
 Setting up firmware-b43-installer (1:015-14) ...  
 No chroot environment found. Starting normal installation  
  
i restarted and its still not detecting wifi and the ligh is still off. is there anything els i can do?

---

### Post by adityamagadi on 2013-01-14
hmmmm  could you pls post the output of lscpi ?

---

### Post by yamil on 2013-01-14
> **adityamagadi said:**
> hmmmm  could you pls post the output of lscpi ?

No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lscp' from package 'nilfs-tools' (universe)
 Command 'lspci' from package 'pciutils' (main)
lscpi: command not foun

---

### Post by adityamagadi on 2013-01-14
sorry thats lspci :(

---

### Post by yamil on 2013-01-14
> **adityamagadi said:**
> sorry thats lspci :(

oh for that i got

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9992
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
02:00.0 Network controller: Ralink corp. Device 3290
02:00.1 Bluetooth: Ralink corp. Device 3298
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by adityamagadi on 2013-01-14
[http://ubuntuforums.org/showthread.php?t=1850267](http://ubuntuforums.org/showthread.php?t=1850267)


follow this...

---

