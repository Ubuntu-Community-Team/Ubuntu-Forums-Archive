---
title: "Bionic only boots in recovery mode"
date: 2018-06-19
forum: Hardware
---

### Post by Qd64erK on 2018-06-19
Hi everyone,  I've been having problems starting Xubuntu Bionic since the day I installed it and every time I tried to reboot it. (It worked fine if I choose "Shutdown" and turned it on)   The PC would boot to BIOS and then I get this error: 
 ```
[Firmware Bug]: AMD-Vi: IOAPIC[0] not in IVRS table [Firmware Bug]:  AMD-Vi: No southbridge IOAPC found AMD-Vi: Disabling interrupt remapping
```  and rebooted again. It looped like this, maybe 3 times or so, but it would eventually start.  This was until 2 or 3 days ago. Now I can only boot from recovery mode (using reboot, shutdown, reset, power button, whatever). I get the same error as before and sometimes even the BIOS gets stuck (see attached image_2)  The only thing that seems to make it work is if I edit grub and add the **nomodeset **parameter. The problem is if I use nomedeset I get an error when Xubuntu needs xrandr. The settings on the display are just generic and redshift doesn't work. I can't even find what video driver it's using.  I'm almost certain this is a graphics card issue. Here are some outputs to identify the kernel and my hardware: 
```
**uname -a** Linux Linux 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux  [B]

sudo lshw -c video[/B] 
*-display DISPONÍVEL
              descrição: VGA compatible controller
              produto: Richland [Radeon HD 8370D] 
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 1
             informações do barramento: pci@0000:00:01.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pm pciexpress msi vga_controller bus_master cap_list
             configuração: latency=0
             recursos: memória:c0000000-cfffffff porta de E/S:f000(tamanho=256) memória:feb00000-feb3ffff memória:c0000-dffff  [B]

sudo dmidecode -t 2[/B] 
# dmidecode 3.1 
Getting SMBIOS data from sysfs. 
SMBIOS 2.8 present.  
Handle 0x0002, DMI type 2, 15 bytes
 Base Board Information
     Manufacturer: MSI
     Product Name: A68HM-E33 (MS-7721)
     Version: 9.0
     Serial Number: To be filled by O.E.M.
     Asset Tag: To be filled by O.E.M.
     Features:
                 Board is a hosting board
                 Board is replaceable
     Location In Chassis: To be filled by O.E.M.
     Chassis Handle: 0x0003
     Type: Motherboard
     Contained Object Handles: 0
```
  (I also attached some pictures)  

Hope someone can help. 
Thanks in advance.

---

### Post by Qd64erK on 2018-07-02
I solved it by flashing my BIOS. I don't know where the error was coming from, BIOS, OS or graphics driver but, for now, it's working fine.

---

### Post by Qd64erK on 2018-07-05
No, it's not solved. Was working fine until now. I have again the same error and have to use the **nomodeset** parameter at boot. The only thing different that I've done in this 3 days was a restart just now using the xfce4-session-logout. 

 Any help?
Thanks

---

