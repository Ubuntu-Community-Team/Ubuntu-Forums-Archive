---
title: "Aiptek tablet appears as a mouse in /dev/input"
date: 2009-04-14
forum: Hardware
---

### Post by Ubuntiac on 2009-04-14
Hey all,

I'm trying to get my Aiptek tablet going using the only guide that seems to exist at [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) .This hasn't been updated for Jaunty, but I followed the Intrepid instructions.  I have xserver-xorg-input-aiptek and wacom-tools installed. Trouble is, the tablet still shows up under /dev/input/mouseX rather than under /dev/input/aiptektablet

My /dev/input just shows:
```
by-id  by-path  event0  event1  event2  event3  event4  event5  event6  mice  mouse0  mouse1  mouse2
```
I only have one mouse by the way.

```
udevadm info -a -p /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input6
```

Gives:
```
looking at device '/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input6':
    KERNEL=="input6"                                                                 
    SUBSYSTEM=="input"                                                               
    DRIVER==""                                                                       
    ATTR{name}=="Aiptek"                                                             
    ATTR{phys}=="usb-0000:00:12.0-2/input0"                                          
    ATTR{uniq}==""                                                                   
    ATTR{modalias}=="input:b0003v08CAp0010e0105-e0,1,2,3,4,k80,81,82,83,84,85,86,87,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,110,111,112,140,141,142,143,144,146,147,14A,14B,14C,r0,1,8,a0,1,8,18,1A,1B,28,m0,lsfw"

  looking at parent device '/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0':
    KERNELS=="3-2:1.0"                                                         
    SUBSYSTEMS=="usb"                                                          
    DRIVERS=="aiptek"                                                          
    ATTRS{bInterfaceNumber}=="00"                                              
    ATTRS{bAlternateSetting}==" 0"                                             
    ATTRS{bNumEndpoints}=="01"                                                 
    ATTRS{bInterfaceClass}=="03"                                               
    ATTRS{bInterfaceSubClass}=="00"                                            
    ATTRS{bInterfaceProtocol}=="00"                                            
    ATTRS{modalias}=="usb:v08CAp0010d0105dc00dsc00dp00ic03isc00ip00"           
    ATTRS{supports_autosuspend}=="0"                                           
    ATTRS{size}=="6000x4500"                                                   
    ATTRS{pointer_mode}=="either"                                              
    ATTRS{coordinate_mode}=="absolute"                                         
    ATTRS{tool_mode}=="pen"                                                    
    ATTRS{xtilt}=="disable"                                                    
    ATTRS{ytilt}=="disable"                                                    
    ATTRS{jitter}=="50"                                                        
    ATTRS{delay}=="400"                                                        
    ATTRS{event_count}=="1"                                                    
    ATTRS{diagnostic}=="no errors"                                             
    ATTRS{odm_code}=="0x0200"                                                  
    ATTRS{model_code}=="0x00c9"                                                                                                                                                                                                              
    ATTRS{firmware_code}=="0105"                                                                                                                                                                                                             
    ATTRS{stylus_lower}=="lower"                                                                                                                                                                                                             
    ATTRS{stylus_upper}=="upper"                                                                                                                                                                                                             
    ATTRS{mouse_left}=="left"                                                                                                                                                                                                                
    ATTRS{mouse_middle}=="middle"                                                                                                                                                                                                            
    ATTRS{mouse_right}=="right"                                                                                                                                                                                                              
    ATTRS{wheel}=="0"                                                                                                                                                                                                                        
    ATTRS{execute}=="Write anything to this file to program your tablet."                                                                                                                                                                    
                                                                                                                                                                                                                                             
  looking at parent device '/devices/pci0000:00/0000:00:12.0/usb3/3-2':                                                                                                                                                                      
    KERNELS=="3-2"                                                                                                                                                                                                                           
    SUBSYSTEMS=="usb"                                                                                                                                                                                                                        
    DRIVERS=="usb"                                                                                                                                                                                                                           
    ATTRS{configuration}==""                                                                                                                                                                                                                 
    ATTRS{bNumInterfaces}==" 1"                                                                                                                                                                                                              
    ATTRS{bConfigurationValue}=="1"                                                                                                                                                                                                          
    ATTRS{bmAttributes}=="80"                                                                                                                                                                                                                
    ATTRS{bMaxPower}==" 26mA"                                                                                                                                                                                                                
    ATTRS{urbnum}=="27"                                                                                                                                                                                                                      
    ATTRS{idVendor}=="08ca"                                                                                                                                                                                                                  
    ATTRS{idProduct}=="0010"                                                                                                                                                                                                                 
    ATTRS{bcdDevice}=="0105"                                                                                                                                                                                                                 
    ATTRS{bDeviceClass}=="00"                                                                                                                                                                                                                
    ATTRS{bDeviceSubClass}=="00"                                                                                                                                                                                                             
    ATTRS{bDeviceProtocol}=="00"                                                                                                                                                                                                             
    ATTRS{bNumConfigurations}=="1"                                                                                                                                                                                                           
    ATTRS{bMaxPacketSize0}=="8"                                                                                                                                                                                                              
    ATTRS{speed}=="1.5"                                                                                                                                                                                                                      
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="AIPTEK International Inc."
    ATTRS{product}=="USB Tablet Series Version 1.05"

  looking at parent device '/devices/pci0000:00/0000:00:12.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="39"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="3"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.28-11-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:12.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:12.0':
    KERNELS=="0000:00:12.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x1002"
    ATTRS{device}=="0x4397"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x834e"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00001002d00004397sv00001043sd0000834Ebc0Csc03i10"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```


and my /etc/udev/rules.d/61-aiptek.rules includes:
```
DRIVERS=="aiptek",ATTRS{size}=="6000x4500",ATTRS{model_code}=="0x00c9", SYMLINK+="input/aiptektablet"
```

although I even tried making it just:
```
DRIVERS=="aiptek"
```
with the same result.


ANy help greatfully appreciated as there seems next to nothing on tha interwebs.

---

