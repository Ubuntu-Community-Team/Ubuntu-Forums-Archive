---
title: "PC Camera problem"
date: 2009-05-04
forum: Hardware
---

### Post by me4oslav on 2009-05-04
Hi,I've just bought a **PC Camera-USB PC CAMERA 211V**.
I use Jaunty(upgraded form Intrepid).
Skype recognizes it as **"USB2.0 JPEG WebCam (/dev/video0/)"**,but it is not working.
To fix this I've installed gspca-source.It started,but after a reboot it stopped working,after a session reboot still doesn't want to work,the only way to make it work is changing the USB's in which the camera cable is plugged.
I tried wxcam,but the only effect was that Skype crashed.
Canoramo is also not working.
GPhoto had the same effect as gspca-source.
KInfoCenter says that there is camera plugged.
For now it works but i have to change the USB's ports very often,which is quite annoying.
Looking forward for your help.
Thanks in advance.

---

### Post by ahbart on 2009-05-04
just installing gspca-source will not actually help you. This just installs a source package under /usr/src. 
```
This package provides the source code for the gspca kernel modules.
Kernel source or headers are required to compile these modules. For
basic install steps see /usr/share/doc/gspca-source/README.Debian.gz
```

It seems your cam is already working but it is not stable. Can you give some more info about the chip in this cam? 
lsusb -vv. (you'd better make a selection then ;) )

---

### Post by me4oslav on 2009-05-04
Here is the exit from lsusb -vv (as normal user):

[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               2.00                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0002 2.0 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3                                   
  iProduct                2                                   
  iSerial                 1                                   
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0004  1x 4 bytes                 
        bInterval              12                             
can't get hub descriptor: Operation not permitted             
can't get device qualifier: Operation not permitted           
can't get debug descriptor: Operation not permitted           
cannot read device status, Operation not permitted (1)        

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3                                   
  iProduct                2                                   
  iSerial                 1                                   
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
can't get hub descriptor: Operation not permitted             
cannot read device status, Operation not permitted (1)        

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3                                   
  iProduct                2                                   
  iSerial                 1                                   
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
can't get hub descriptor: Operation not permitted             
cannot read device status, Operation not permitted (1)        

Bus 003 Device 002: ID 17a1:0128  
Device Descriptor:                
  bLength                18       
  bDescriptorType         1       
  bcdUSB               1.10       
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0        64                             
  idVendor           0x17a1                             
  idProduct          0x0128                             
  bcdDevice            1.00                             
  iManufacturer          32                             
  iProduct               38                             
  iSerial                 0                             
  bNumConfigurations      1                             
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength           57                           
    bNumInterfaces          1                           
    bConfigurationValue     1                           
    iConfiguration          0                           
    bmAttributes         0xc0                           
      Self Powered                                      
    MaxPower              224mA                         
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       0                         
      bNumEndpoints           1                         
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x0000  1x 0 bytes               
        bInterval               1                           
    Interface Descriptor:                                   
      bLength                 9                             
      bDescriptorType         4                             
      bInterfaceNumber        0                             
      bAlternateSetting       1                             
      bNumEndpoints           1                             
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x0200  1x 512 bytes             
        bInterval               1                           
    Interface Descriptor:                                   
      bLength                 9                             
      bDescriptorType         4                             
      bInterfaceNumber        0                             
      bAlternateSetting       2                             
      bNumEndpoints           1                             
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x03c0  1x 960 bytes             
        bInterval               1                           
cannot read device status, Operation not permitted (1)      

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3                                   
  iProduct                2                                   
  iSerial                 1                                   
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
can't get hub descriptor: Operation not permitted             
cannot read device status, Operation not permitted (1)        

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3                                   
  iProduct                2                                   
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)[/B]

Here is the exit from m-a prepare (as root):

[B]Getting source for kernel version: 2.6.28-11-generic
Kernel headers available in /usr/src/linux-headers-2.6.28-11-generic
Creating symlink...
apt-get install build-essential
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1089;&#1087;&#1080;&#1089;&#1098;&#1094;&#1080;&#1090;&#1077; &#1089; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1048;&#1079;&#1075;&#1088;&#1072;&#1078;&#1076;&#1072;&#1085;&#1077; &#1085;&#1072; &#1076;&#1098;&#1088;&#1074;&#1086;&#1090;&#1086; &#1089;&#1098;&#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1089;&#1098;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;&#1090;&#1086;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
build-essential &#1074;&#1077;&#1095;&#1077; &#1077; &#1085;&#1072;&#1081;-&#1085;&#1086;&#1074;&#1072;&#1090;&#1072; &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;.
build-essential &#1077; &#1086;&#1090;&#1073;&#1077;&#1083;&#1103;&#1079;&#1072;&#1085; &#1082;&#1072;&#1090;&#1086; &#1088;&#1098;&#1095;&#1085;&#1086; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;.
0 &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1085;&#1086;&#1074;&#1080; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1079;&#1072; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1080; 0 &#1073;&#1077;&#1079; &#1087;&#1088;&#1086;&#1084;&#1103;&#1085;&#1072;.[/B]

The exit from m-a a-i gspca (as root)(it gives *error can not build*):

[B]Updated infos about 1 packages
Getting source for kernel version: 2.6.28-11-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1089;&#1087;&#1080;&#1089;&#1098;&#1094;&#1080;&#1090;&#1077; &#1089; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1048;&#1079;&#1075;&#1088;&#1072;&#1078;&#1076;&#1072;&#1085;&#1077; &#1085;&#1072; &#1076;&#1098;&#1088;&#1074;&#1086;&#1090;&#1086; &#1089;&#1098;&#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1089;&#1098;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;&#1090;&#1086;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
build-essential &#1074;&#1077;&#1095;&#1077; &#1077; &#1085;&#1072;&#1081;-&#1085;&#1086;&#1074;&#1072;&#1090;&#1072; &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;.
0 &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1085;&#1086;&#1074;&#1080; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1079;&#1072; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1080; 0 &#1073;&#1077;&#1079; &#1087;&#1088;&#1086;&#1084;&#1103;&#1085;&#1072;.

Done!
unpack
Extracting the package tarball, /usr/src/gspca.tar.bz2, please wait...
"/usr/share/modass/overrides/gspca-source" build KVERS=2.6.28-11-generic KSRC=/usr/src/linux-headers-2.6.28-11-generic KDREV=2.6.28-11.42 kdist_image[/B]

And finally the exit from lsusb -vv (as root):

[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               2.00                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0002 2.0 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3 Linux 2.6.28-11-generic ehci_hcd  
  iProduct                2 EHCI Host Controller              
  iSerial                 1 0000:00:1d.7                      
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0004  1x 4 bytes                 
        bInterval              12                             
Hub Descriptor:                                               
  bLength              11                                     
  bDescriptorType      41                                     
  nNbrPorts             8                                     
  wHubCharacteristic 0x000a                                   
    No power switching (usb 1.0)                              
    Per-port overcurrent protection                           
  bPwrOn2PwrGood       10 * 2 milli seconds                   
  bHubContrCurrent      0 milli Ampere                        
  DeviceRemovable    0x00 0x00                                
  PortPwrCtrlMask    0xff 0xff                                
 Hub Port Status:                                             
   Port 1: 0000.0100 power                                    
   Port 2: 0000.0100 power                                    
   Port 3: 0000.0100 power                                    
   Port 4: 0000.0100 power                                    
   Port 5: 0000.0100 power                                    
   Port 6: 0000.0100 power                                    
   Port 7: 0000.0100 power                                    
   Port 8: 0000.0100 power                                    
Device Status:     0x0003                                     
  Self Powered                                                
  Remote Wakeup Enabled                                       

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd  
  iProduct                2 UHCI Host Controller              
  iSerial                 1 0000:00:1d.3                      
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
Hub Descriptor:                                               
  bLength               9                                     
  bDescriptorType      41                                     
  nNbrPorts             2                                     
  wHubCharacteristic 0x000a                                   
    No power switching (usb 1.0)                              
    Per-port overcurrent protection                           
  bPwrOn2PwrGood        1 * 2 milli seconds                   
  bHubContrCurrent      0 milli Ampere                        
  DeviceRemovable    0x00                                     
  PortPwrCtrlMask    0xff                                     
 Hub Port Status:                                             
   Port 1: 0000.0100 power                                    
   Port 2: 0000.0100 power                                    
Device Status:     0x0003                                     
  Self Powered                                                
  Remote Wakeup Enabled                                       

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd  
  iProduct                2 UHCI Host Controller              
  iSerial                 1 0000:00:1d.2                      
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
Hub Descriptor:                                               
  bLength               9                                     
  bDescriptorType      41                                     
  nNbrPorts             2                                     
  wHubCharacteristic 0x000a                                   
    No power switching (usb 1.0)                              
    Per-port overcurrent protection                           
  bPwrOn2PwrGood        1 * 2 milli seconds                   
  bHubContrCurrent      0 milli Ampere                        
  DeviceRemovable    0x00                                     
  PortPwrCtrlMask    0xff                                     
 Hub Port Status:                                             
   Port 1: 0000.0100 power                                    
   Port 2: 0000.0100 power                                    
Device Status:     0x0003                                     
  Self Powered                                                
  Remote Wakeup Enabled                                       

Bus 003 Device 002: ID 17a1:0128  
Device Descriptor:                
  bLength                18       
  bDescriptorType         1       
  bcdUSB               1.10       
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0        64                             
  idVendor           0x17a1                             
  idProduct          0x0128                             
  bcdDevice            1.00                             
  iManufacturer          32                             
  iProduct               38                             
  iSerial                 0                             
  bNumConfigurations      1                             
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength           57                           
    bNumInterfaces          1                           
    bConfigurationValue     1                           
    iConfiguration          0                           
    bmAttributes         0xc0                           
      Self Powered                                      
    MaxPower              224mA                         
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       0                         
      bNumEndpoints           1                         
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x0000  1x 0 bytes               
        bInterval               1                           
    Interface Descriptor:                                   
      bLength                 9                             
      bDescriptorType         4                             
      bInterfaceNumber        0                             
      bAlternateSetting       1                             
      bNumEndpoints           1                             
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x0200  1x 512 bytes             
        bInterval               1                           
    Interface Descriptor:                                   
      bLength                 9                             
      bDescriptorType         4                             
      bInterfaceNumber        0                             
      bAlternateSetting       2                             
      bNumEndpoints           1                             
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0                             
      bInterfaceProtocol      0                             
      iInterface              0                             
      Endpoint Descriptor:                                  
        bLength                 7                           
        bDescriptorType         5                           
        bEndpointAddress     0x81  EP 1 IN                  
        bmAttributes            1                           
          Transfer Type            Isochronous              
          Synch Type               None                     
          Usage Type               Data                     
        wMaxPacketSize     0x03c0  1x 960 bytes             
        bInterval               1                           
Device Status:     0xffff                                   
  Self Powered                                              
  Remote Wakeup Enabled                                     
  Test Mode                                                 
  Debug Mode                                                

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd  
  iProduct                2 UHCI Host Controller              
  iSerial                 1 0000:00:1d.1                      
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4                               
      bInterfaceNumber        0                               
      bAlternateSetting       0                               
      bNumEndpoints           1                               
      bInterfaceClass         9 Hub                           
      bInterfaceSubClass      0 Unused                        
      bInterfaceProtocol      0 Full speed (or root) hub      
      iInterface              0                               
      Endpoint Descriptor:                                    
        bLength                 7                             
        bDescriptorType         5                             
        bEndpointAddress     0x81  EP 1 IN                    
        bmAttributes            3                             
          Transfer Type            Interrupt                  
          Synch Type               None                       
          Usage Type               Data                       
        wMaxPacketSize     0x0002  1x 2 bytes                 
        bInterval             255                             
Hub Descriptor:                                               
  bLength               9                                     
  bDescriptorType      41                                     
  nNbrPorts             2                                     
  wHubCharacteristic 0x000a                                   
    No power switching (usb 1.0)                              
    Per-port overcurrent protection                           
  bPwrOn2PwrGood        1 * 2 milli seconds                   
  bHubContrCurrent      0 milli Ampere                        
  DeviceRemovable    0x00                                     
  PortPwrCtrlMask    0xff                                     
 Hub Port Status:                                             
   Port 1: 0000.0100 power                                    
   Port 2: 0000.0103 power enable connect                     
Device Status:     0x0003                                     
  Self Powered                                                
  Remote Wakeup Enabled                                       

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:                                            
  bLength                18                                   
  bDescriptorType         1                                   
  bcdUSB               1.10                                   
  bDeviceClass            9 Hub                               
  bDeviceSubClass         0 Unused                            
  bDeviceProtocol         0 Full speed (or root) hub          
  bMaxPacketSize0        64                                   
  idVendor           0x1d6b Linux Foundation                  
  idProduct          0x0001 1.1 root hub                      
  bcdDevice            2.06                                   
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd  
  iProduct                2 UHCI Host Controller              
  iSerial                 1 0000:00:1d.0                      
  bNumConfigurations      1                                   
  Configuration Descriptor:                                   
    bLength                 9                                 
    bDescriptorType         2                                 
    wTotalLength           25                                 
    bNumInterfaces          1                                 
    bConfigurationValue     1                                 
    iConfiguration          0                                 
    bmAttributes         0xe0                                 
      Self Powered                                            
      Remote Wakeup                                           
    MaxPower                0mA                               
    Interface Descriptor:                                     
      bLength                 9                               
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled[/B]

---

### Post by ahbart on 2009-05-04
are you sure your cam is plugged in? Can you give a simple 
lsusb
without the -v

---

### Post by me4oslav on 2009-05-05
absolutely sure

chichovoto6@tototo6:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 17a1:0128  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chichovoto6@tototo6:~$

---

### Post by ahbart on 2009-05-05
I'm not sure in what state the development of this driver is. It sounds like it is still in heavy development and not stable at all. Have a look at this threat: [link](http://ubuntuforums.org/showthread.php?t=832805)
Especially the last entry: #6.

If you get it working it will still be a pretty worse picture. Well that is what I read about the chip in this cam.

---

### Post by me4oslav on 2009-05-05
Well,the quality is pretty nice(640x480 resolution),but if it is a driver problem that's bad.I was thinking that it was problem from USB or Skype.
Anyway thanks for the help,but if the driver is in heavy devolopment period,there is nothing to be done.I guess i should wait for the developers to make the driver more stable.Thanks.

---

