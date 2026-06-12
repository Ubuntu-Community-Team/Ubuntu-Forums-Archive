---
title: "Acer Revo 80 - Ubuntu 12.04 - Intel 3000 HD"
date: 2013-03-24
forum: Hardware
---

### Post by mrburns2013 on 2013-03-24
Hello

I have an new Acer Revo RL80 Nettop PC with Intel i3 CPU, Intel HD 3000 Graphic with installed Ubuntu 12.04 LTS
After the Grub boot screen the monitor showing a blanc screen or he flicker with different colors on all video outputs (VGA, DVI, HDMI)
The boot option "nomodeset" or "i915.blacklist=1" works, but the hardware acceleration is now disabled. Then the video playback is very slowly.
If i use VNC  remote access, i see the i913 driver is installed correctly. The monitor and the Sony TV is recognized from the display manager (KDE and Ubuntu). XRANDR show possible screen resolution. But the monitor and TV showing no picture.

Same problem with Ubutu 12.10, Ubuntu 13.x Beta and XBMCBuntu.



    
    VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Acer Incorporated [ALI] Device [1025:074c]
        Kernel driver in use: i915
        Kernel modules: i915
     
             
        lshw | grep -i vga -a20
             
    *-display
        Beschreibung: VGA compatible controller
        Produkt: 2nd Generation Core Processor Family Integrated Graphics Controller
        Hersteller: Intel Corporation
        Physische ID: 2
        Bus-Informationen: pci@0000:00:02.0
        Version: 09
        Breite: 64 bits
        Takt: 33MHz
        Fähigkeiten: msi pm vga_controller bus_master cap_list rom
        Konfiguration: driver=i915 latency=0
        Ressourcen: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(Größe=64)
       
       
       
         
    lsmod | grep -i i915
         
        i915                  423451  3 
    drm_kms_helper         45466  1 i915
    drm                   197641  4 i915,drm_kms_helper
    i2c_algo_bit           13199  1 i915
    video                  19115  1 i915
             
             
             
              
     xorg.log
 
     [    16.586] (==) intel(0): Default visual is TrueColor
     [    16.586] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
      

      
On my other pc (Lenovo Notebook with the same Intel HD 3000 graphic) Ubuntu works perfectly       
      
      
Lenovo Ubuntu OK    
Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:[COLOR=#ff0000]0106[/COLOR]] (rev 09)
20.805] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile ([COLOR=#ff0000]GT1[/COLOR])

Acer Ubuntu not OK
Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:[COLOR=#ff0000]0116[/COLOR]] (rev 09)
16.586] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile ([COLOR=#ff0000]GT2[/COLOR])


how can i boot ubuntu without "nomodeset" ??
 
Sorry for bad english

 thanks to all

---

### Post by lasttoknow0 on 2013-03-31
There's another thread about the i915 hardware that the RL80 uses:  check out [http://ubuntuforums.org/showthread.php?t=2099752&page=2&highlight=rl80](http://ubuntuforums.org/showthread.php?t=2099752&page=2&highlight=rl80).

---

