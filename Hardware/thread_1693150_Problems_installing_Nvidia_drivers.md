---
title: "Problems installing Nvidia drivers"
date: 2011-02-22
forum: Hardware
---

### Post by Acheron3 on 2011-02-22
Hi,
I deleted some files by error and I broke Nvidia (current version) drivers on my Ubuntu 10.10. :sad:
After installing all the packages again I'm unable to install again the  driver (I have to use nv instead). When I try to install it I get this  log on jockey.log:
```

2011-02-22 18:48:51,761 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:48:51,728 DEBUG: got handler  xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA  accelerated graphics driver)
2011-02-22 18:48:51,762 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,762 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:device:')
2011-02-22 18:48:51,763 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-02-22 18:48:51,763 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-02-22 18:48:51,763 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-02-22 18:48:51,763 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-02-22 18:48:51,764 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d0000283Esv000014C0sd00000023bc0Csc05i00')
2011-02-22 18:48:51,769 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,769 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-02-22 18:48:51,770 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d00002836sv000014C0sd00000023bc0Csc03i20')
2011-02-22 18:48:51,774 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-02-22 18:48:51,774 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,775 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0003v0461p4D64e0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2011-02-22 18:48:51,775 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,775 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v04F2pB018d0460dcEFdsc02dp01ic0Eisc02ip00')
2011-02-22 18:48:51,777 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,2,3,k110,111,112,145,14A,14D,14E,r0,1,a0,1,mlsfw')
2011-02-22 18:48:51,777 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,777 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,778 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:CPL0002:')
2011-02-22 18:48:51,778 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'dmi:bvnCOMPAL:bvr1.12:bd08/29/2007:svn-:pnN/A:pvrN/A:rvn-:rnIFT00:rvrIFT00:cvnNoEnclosure:ct10:cvrN/A:')
2011-02-22 18:48:51,797 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'compal_laptop',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,797 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-02-22 18:48:51,797 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-02-22 18:48:51,798 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,798 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icE0isc01ip01')
2011-02-22 18:48:51,800 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'btusb',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,800 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icFFiscFFipFF')
2011-02-22 18:48:51,801 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'btusb',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,801 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-02-22 18:48:51,801 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-02-22 18:48:51,801 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d00002832sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,807 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v04F2pB018d0460dcEFdsc02dp01ic0Eisc01ip00')
2011-02-22 18:48:51,807 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,808 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d0000283Asv000014C0sd00000023bc0Csc03i20')
2011-02-22 18:48:51,812 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d00002831sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,817 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d0000284Bsv000014C0sd00000023bc04sc03i00')
2011-02-22 18:48:51,821 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,822 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'platform:pcspkr')
2011-02-22 18:48:51,822 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,822 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,823 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-02-22 18:48:51,823 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,823 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-02-22 18:48:51,823 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icFEisc01ip00')
2011-02-22 18:48:51,824 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'btusb',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,824 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v000014E4d00001693sv000014C0sd00000023bc02sc00i00')
2011-02-22 18:48:51,893 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'tg3',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,893 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'platform:eisa')
2011-02-22 18:48:51,893 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d00002829sv000014C0sd00000023bc01sc06i01')
2011-02-22 18:48:51,898 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'ahci',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,899 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'ahci',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,899 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-02-22 18:48:51,913 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,913 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,913 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'pci:v00008086d00002830sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,918 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-02-22 18:48:51,918 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2011-02-22 18:48:51,918 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x95cdfcc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-02-22 18:48:51,918 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002834sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,918 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0003v04F2pB018e0460-e0,1,kD4,ramlsfw')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00001180d00000822sv000014C0sd00000023bc08sc05i00')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:INT0800:')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0C02:')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002835sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,919 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'platform:regulatory')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00001180d00000592sv000014C0sd00000023bc08sc80i00')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002815sv00000000sd00000000bc06sc01i00')
2011-02-22 18:48:51,920 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-02-22 18:48:51,921 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00004229sv00008086sd00001101bc02sc80i00')
2011-02-22 18:48:51,921 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'platform:compal-laptop')
2011-02-22 18:48:51,921 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00001180d00000832sv000014C0sd00000023bc0Csc00i10')
2011-02-22 18:48:51,921 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002A00sv000014C0sd00000023bc06sc00i00')
2011-02-22 18:48:51,921 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v0461p4D64d0200dc00dsc00dp00ic03isc01ip02')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0303:')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0000:')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v000010DEd00000427sv000014C0sd00000023bc03sc00i00')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:device:')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0F13:')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-02-22 18:48:51,922 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0B00:')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d0000283Esv000014C0sd00000023bc0Csc05i00')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002836sv000014C0sd00000023bc0Csc03i20')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-02-22 18:48:51,923 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0003v0461p4D64e0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v04F2pB018d0460dcEFdsc02dp01ic0Eisc02ip00')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,2,3,k110,111,112,145,14A,14D,14E,r0,1,a0,1,mlsfw')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:CPL0002:')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'dmi:bvnCOMPAL:bvr1.12:bd08/29/2007:svn-:pnN/A:pvrN/A:rvn-:rnIFT00:rvrIFT00:cvnNoEnclosure:ct10:cvrN/A:')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-02-22 18:48:51,924 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icE0isc01ip01')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icFFiscFFipFF')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0100:')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0C04:')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002832sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v04F2pB018d0460dcEFdsc02dp01ic0Eisc01ip00')
2011-02-22 18:48:51,925 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d0000283Asv000014C0sd00000023bc0Csc03i20')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002831sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d0000284Bsv000014C0sd00000023bc04sc03i00')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'platform:pcspkr')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-02-22 18:48:51,926 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'usb:v0A5Cp2101d0100dcE0dsc01dp01icFEisc01ip00')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v000014E4d00001693sv000014C0sd00000023bc02sc00i00')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'platform:eisa')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002829sv000014C0sd00000023bc01sc06i01')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'pci:v00008086d00002830sv000014C0sd00000023bc0Csc03i00')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-02-22 18:48:51,927 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97fa9ec>  about HardwareID('modalias', 'acpi:PNP0200:')
2011-02-22 18:48:52,053 DEBUG: nvidia_173 is not the alternative in use
2011-02-22 18:48:53,458 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:48:54,195 DEBUG: nvidia_173 is not the alternative in use
2011-02-22 18:48:54,497 DEBUG: nvidia_173 is not the alternative in use
2011-02-22 18:49:00,232 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:49:05,782 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:49:13,016 DEBUG: Installing package: linux-headers-2.6.32-23-generic
2011-02-22 18:49:13,413 DEBUG: Package linux-headers-2.6.32-23-generic does not exist, aborting
2011-02-22 18:49:13,985 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-02-22 18:49:13,986 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-02-22 18:49:54,401 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:49:54,432 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-02-22 18:49:57,187 DEBUG: nvidia_173 is not the alternative in use

```My kernel is 2.6.32-23-generic but the log keeps telling me that  "Package linux-headers-2.6.32-23-generic does not exist, aborting"

Any ideas?

Cheers

---

### Post by Acheron3 on 2011-02-23
After some reseacrh I've realized that I need to update my kernel headers in order to install Nvidia drivers:
My kernel (what I get from uname -r) is 2.6.32-23-generic.
So my kernel keaders should be linux-headers-2.6.23-23-generic 2.6.23-23 or something like this. I am right?
When I search in Synaptic I don't find any package like this and when I try to update them in terminal 
```

sudo apt-get install linux-headers

```I just get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.35-25-virtual 2.6.35-25.44
  linux-headers-2.6.35-25-generic-pae 2.6.35-25.44
  linux-headers-2.6.35-25-generic 2.6.35-25.44
  linux-headers-2.6.35-25 2.6.35-25.44
  linux-headers-2.6.35-24-virtual 2.6.35-24.42
  linux-headers-2.6.35-24-generic-pae 2.6.35-24.42
  linux-headers-2.6.35-24-generic 2.6.35-24.42
  linux-headers-2.6.35-24 2.6.35-24.42
  linux-headers-2.6.35-23-virtual 2.6.35-23.41
  linux-headers-2.6.35-23-generic-pae 2.6.35-23.41
  linux-headers-2.6.35-23-generic 2.6.35-23.41
  linux-headers-2.6.35-23 2.6.35-23.41
  linux-headers-2.6.35-22-virtual 2.6.35-22.35
  linux-headers-2.6.35-22-generic-pae 2.6.35-22.35
  linux-headers-2.6.35-22-generic 2.6.35-22.35
  linux-headers-2.6.35-22 2.6.35-22.35
You should explicitly select one to install.


```Any ideas?

Cheers

---

