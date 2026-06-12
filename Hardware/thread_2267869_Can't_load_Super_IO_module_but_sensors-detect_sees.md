---
title: "Can't load Super I/O module but sensors-detect sees it"
date: 2015-03-04
forum: Hardware
---

### Post by mrJTparadise on 2015-03-04
Hey all,

Not sure if this belongs in hardware or software, but since we are talking more low level I will assume hardware.  Anyways..

I have a Winbond (previously Nuvoton) W83627DHG Super I/O chip that I can't seem to communicate with. I am also running kernel 3.13.11.

My goal is to have access to the devices I have connected to it - in my case, it is 3 voltage readings and a UART.  Under the BIOS options > Advanced > Super IO Configuration, I see Serial Port 0 Configuration as well as the same for Serial Port 1 and a Parallel Port.  I have enabled these.

There is no w83627 entry under the /sys/devices/platform directory.

According to the Linux Kernel Config, under Device Drivers > Hardware Monitoring support, they say this - 

```
CONFIG_SENSORS_W83627EHF:                                               
  &#9474;                                                                          
  &#9474; If you say yes here you get support for the hardware                     
  &#9474; monitoring functionality of the Winbond W83627EHF Super-I/O chip.        
  &#9474;                                                                          
  &#9474; This driver also supports the W83627EHG, which is the lead-free           
  &#9474; version of the W83627EHF, and the W83627DHG, which is a similar          
  &#9474; chip suited for specific Intel processors that use PECI such as          
  &#9474; the Core 2 Duo. And also the W83627UHG, which is a stripped down         
  &#9474; version of the W83627DHG (as far as hardware monitoring goes.)            
  &#9474;                                                                         
  &#9474; This driver also supports Nuvoton W83667HG, W83667HG-B, NCT6775F         
  &#9474; (also known as W83667HG-I), and NCT6776F.                                 
  &#9474;                                                                          
  &#9474; This driver can also be built as a module.  If so, the module            
  &#9474; will be called w83627ehf.                                                
  &#9474;                                                                         
  &#9474; Symbol: SENSORS_W83627EHF [=m]                                          
  &#9474; Type  : tristate                                                        
  &#9474; Prompt: Winbond W83627EHF/EHG/DHG/UHG, W83667HG, NCT6775F, NCT6776F     
  &#9474;   Location:                                                              
  &#9474;     -> Device Drivers                                                   
  &#9474;       -> Hardware Monitoring support (HWMON [=y])                       
  &#9474;   Defined at drivers/hwmon/Kconfig:1478                                   
  &#9474;   Depends on: HWMON [=y] && !PPC                                        
  &#9474;   Selects: HWMON_VID [=m] 
```

Below is my attempt to load the module.  I've also tried insmod as well (just for kicks) - same results (obviously).  

```

root@x:~# moprobe w83627ehf
modprobe: ERROR: could not insert 'w83627ehf' : No such device

```

Trying a variant of w83627 such as w83627hf_wdt returns no error, but there is nothing in the /sys/devices/platform directory.

sensors-detect gets the following output.  I will not show the entire output of all the questions sensors-detect asks unless someone thinks it would be useful in a solution.
```

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
**Found `Winbond W83627HF/F/HG/G Super IO Sensors'            **
**    (but not activated)**
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

```  

How do I "activate" the chip?

I have tried inserting GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax" inside grub, but no help.

If anyone out there has any experience with this your help would be greatly appreciated.

Thanks all,
JT

---

