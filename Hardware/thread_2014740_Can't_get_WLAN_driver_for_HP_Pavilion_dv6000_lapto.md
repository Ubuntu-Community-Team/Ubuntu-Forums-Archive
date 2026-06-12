---
title: "Can't get WLAN driver for HP Pavilion dv6000 laptop in Ubuntu 10.10"
date: 2012-07-02
forum: Hardware
---

### Post by Keavon on 2012-07-02
I'm new to Linux, and installing Ubuntu 10.10 on my laptop. I'm  liking Ubuntu, but I can't get a WLAN driver, so I'm stuck without an  easy connection to the internet. I've been searching around the web for a  while, and can't find anything that works.


  The laptop is an HP Pavilion dv6408nr. Here is a link to the specs [http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01061065&lang=en&cc=us&taskId=101&prodSeriesId=3308890&prodTypeId=321957](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01061065&lang=en&cc=us&taskId=101&prodSeriesId=3308890&prodTypeId=321957)


I may be mistaken, but I believe the WLAN card is Broadcom BCM94311MCG


My output from ```
lspci
``` is:
```
    00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
    00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
    00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
    00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
    00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
    00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
    00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
    00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
    00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
    00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
    00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
    07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```I don't see the driver available in System > Administration > Additional Drivers.
  Again, I'm totally new to Linux, so please help me fix the problem/find the driver in an easy-to-understand way.


  Thank you!

---

### Post by Dlambert on 2012-07-02
WHy not use Ubuntu 12.04?

---

### Post by Dlambert on 2012-07-02
Have you tried this? From: [http://ubuntuforums.org/showthread.php?t=889395](http://ubuntuforums.org/showthread.php?t=889395)


> open the terminal and give
     Code:
     sudo apt-get remove ndiswrapper 
then open synaptic and apply these 
     Code:
     ndisgtk 0.83-1 ndiswrapper-common 1.50 ndiswrapper-utils-1.9 b43-fwcutter 1:011-1 
then command at terminal
     Code:
     echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
then take the driver from [here]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html")

now you have to unzip the file
so do right click to the file and chose "unzip here" 
you will see a file "WLANBroadcom"
in there is a file "bcmwl5.inf"
that is what you need , so open ndiswrapper and apply it.
then command 
     Code:
     ndiswrapper -l 
if the answer is something like this
     Code:
     Installed ndis drivers: {name of driver}* driver present, hardware present 
command
      Code:
     sudo depmod -a sudo modprobe ndiswrapper 
     Code:
     gksu gedit /etc/modules 
add at the end of the text the word
     Code:
     ndiswrapper 
save and exit.

Then follow these steps:
Open the Networking Admin tool (System | Administration | Networking),  select the Wireless connection and click Properties, ensure the Enable  roaming mode checkbox is ticked.
1.Click the Network Manager icon (computers icon in the top right corner  of system tray), your network ESSID should be shown in the drop-down  list. Select your network by clicking on it.
2.If the Network requires any further configuration (eg WEP key), a  dialog should appear, select the correct settings and paste in your key.
Now you reboot and you are ready...
good luck

---

### Post by ahallubuntu on 2012-07-02
Ubuntu 10.10 is no longer supported.  You are strongly encouraged to use a newer version.  12.04 LTS is preferred (as it may support your wireless card automatically), but 11.04 is at least a little newer and still supported for a few more months, if you simply are trying to avoid Unity desktop.

---

