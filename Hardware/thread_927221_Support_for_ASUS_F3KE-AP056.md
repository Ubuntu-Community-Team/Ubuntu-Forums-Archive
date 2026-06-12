---
title: "Support for ASUS F3KE-AP056"
date: 2008-09-22
forum: Hardware
---

### Post by mexus on 2008-09-22
I'm new to ubuntu (kubuntu).
I managed to get wireless working using: 
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780) 
the wireless adapter is (AR5007EG)
Tried to install acpi4asus but no luck.
Disabled acpi_asus and enabled the asus_laptop module.
So far FN + F5 (F6) brightness settings work.
FN+F7 turns on/off LCD illumination
WIFI button stops wireless. (FN+F2 doesn't work).
The multimedia/Splendid/Touchpad/Power profiles/ Internet browser buttons, and multimedia buttons doesn't work.

I need to get the sound controls to work, and also to enable jack sence).
Now even if headphones are plugged the laptop speakers are still playing.
I can mute only the headphones.

~$ sudo lshw   
```
       *-multimedia                                                                     
             description: Audio device                                                   
             product: SBx00 Azalia                                                       
             vendor: ATI Technologies Inc                                                
             physical id: 14.2                                                           
             bus info: pci@0000:00:14.2                                                  
             version: 00                                                                 
             width: 64 bits                                                              
             clock: 33MHz                                                                
             capabilities: pm bus_master cap_list                                        
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel             
        *-isa                                                                            
             description: ISA bridge                                                     
             product: SB600 PCI to LPC Bridge                                            
             vendor: ATI Technologies Inc                                                
             physical id: 14.3                                                           
             bus info: pci@0000:00:14.3                                                  
             version: 00                                                                 
             width: 32 bits                                                              
             clock: 66MHz                                                                
             capabilities: isa bus_master                                                
             configuration: latency=0                                                    
        *-pci:5                                                                          
             description: PCI bridge                                                     
             product: SBx00 PCI to PCI Bridge                                            
             vendor: ATI Technologies Inc                                                
             physical id: 14.4                                                           
             bus info: pci@0000:00:14.4                                                  
             version: 00                                                                 
             width: 32 bits                                                              
             clock: 66MHz                                                                
             capabilities: pci subtractive_decode bus_master                             
```

~$ lspci
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia     
```

Still working on webcam.

Can someone help me get the hotkeys and sound card properly working.

---

