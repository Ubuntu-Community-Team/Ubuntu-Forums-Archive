---
title: "Keyboard Interface error at BIOS"
date: 2011-11-15
forum: Hardware
---

### Post by ask_ on 2011-11-15
Hello,

I am using a HP desktop , with Lubuntu 11.10 installed on it. I had windows XP on it , but recently replaced it with Lubuntu.

I used to have a PS/2 keyboard, but it isn't working now. So I replaced it with USB keyboard. The new keyboard works fine.

But when I turn on the PC , the first thing that happens is that I get a PS/2 keyboard interface error. The PC asks me to press F1, after which BIOS setup appears. I exit the setup by pressing esc,without making any changes , and the PC starts normally . 

Is there a way to suppress this warning. (and can it be done from Ubuntu). I couldn't find anything related to keyboard in the BIOS setup. Though there was something related to PS/2 mouse.

This problem is since my Windows XP days. I understand this issue isn't OS specific ,hence was a bit apprehensive about posting it at ubuntuforums, but since I have Lubuntu now, I was wondering if there is a way to solve this issue via Lubuntu. If not, whether , it can be done from the BIOS.

I am apprehensive about changing anything from BIOS, lest the USB keyboard is not detected.

P.S - My PS/2 mouse was also not working , had to replace it too by USB mouse.

---

### Post by dandnsmith on 2011-11-15
Just from the timing added to the request to press F1 resulting in getting into BIOS, it's apparent that the BIOS settings (current) have a problem with only a USB keyboard - so it's in the BIOS settings you have to find the solution as the OS won't be affecting them.

I also had a problem with using only a USB keyboard (home-built PC with ASUS mobo) - didin't see any error message like that, but couldn't select any bootloader options. I just changed back to PS2 keyboard to avoid the problem.

---

### Post by jjex22 on 2011-11-15
This is a bios issue - it's set to look for the ps/2 keyboard and doesn't find it. have a look around your bios and see if there's anything like default input or such like. If not this may have been addressed in a bios update, have a look on the hp website to see if there's any bios updates for your machine.

---

### Post by ask_ on 2011-11-15
I checked the HP website. I have one query , is it possible to update BIOS , if Windows is not installed on PC. 
And will updating BIOS do any changes to current OS.

Most probably I will have to live with the error. Because mine is a very old HP pc. It is a Pavilion 061 version. I searched for the product .  Perhaps , they have stopped supporting it.

---

### Post by jjex22 on 2011-11-15
you can update bios by using a freedos usb key, but it really does need to be run from a microsoft system, such as dos, windows 9x or nt, do not be tempted to do it through wine or a virtual machine, the latter wont work and the former may go really wrong. I'll have a quick look for a freedos hp bios update tutorial for you. 

But no updating the bios wont change your installed os - the bios is stored on a chip in the motherboard not on the hdd

---

### Post by ask_ on 2011-11-15
> **jjex22 said:**
> you can update bios by using a freedos usb key, but it really does need to be run from a microsoft system, such as dos, windows 9x or nt, do not be tempted to do it through wine or a virtual machine, the latter wont work and the former may go really wrong. I'll have a quick look for a freedos hp bios update tutorial for you. 

But no updating the bios wont change your installed os - the bios is stored on a chip in the motherboard not on the hdd

Thanks for taking the time out. But what if my desktop version isn't supported now by HP. Because when I searched for my product name on their website (both in USA and India) it didn't return any results.

---

### Post by jjex22 on 2011-11-15
found the [guide]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html") I was looking for!

I would suggest googling to find out what motherboard it's using/ posting on a hp forum ... the same computer is frequently sold by different names in different countries after all - We have a studio laptop that is supported by dell, but their own support page doesn't recognise it's service tag!

---

### Post by ask_ on 2011-11-15
```
description: Desktop Computer
    product: PN216AA-ACJ t730i
    vendor: HP Pavilion 061
    version: 04H0211RE101GROUP10
     width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop 
  *-core
       description: Motherboard
       product: Grouper
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.xx
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.06 (08/27/2004)
          size: 64KB
          capacity: 448KB  
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
```


I searched the HP website , for the product PN216AA-ACJ t730i , and I did find one BIOS upgrade. But it doesn't mention anything about PS/2 keyboards . It only mentions that it solves problems related to printers.

Furthermore , it is an exe file which needs Windows XP. Do you think it can be installed via FreeDOS ?

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-40502-1&cc=in&dlc=en&lc=en&os=228&product=435853&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-40502-1&cc=in&dlc=en&lc=en&os=228&product=435853&sw_lang=) 



Thanks for the help so far. :)

---

### Post by jjex22 on 2011-11-15
If HP aren't offering a bios update we're going to need the model number of the motherboard - it looks like the ASUS PTGD1-LA is common, but we need to be sure, so try running

hwinfo

you may have to download it, but it's in the repo's so its just

sudo apt-get install hwinfo 

to get it. 

where did you find the info that the .exe will only run on xp?

---

### Post by ask_ on 2011-11-15
> **jjex22 said:**
> If HP aren't offering a bios update we're going to need the model number of the motherboard - it looks like the ASUS PTGD1-LA is common, but we need to be sure, so try running

hwinfo

you may have to download it, but it's in the repo's so its just

sudo apt-get install hwinfo 

to get it. 

where did you find the info that the .exe will only run on xp?

Well ,HP is offering only 1 BIOS update , and it is from 2006. I am not sure, whether it will provide an option to suppress looking for PS/2 keyboard. 

I thought since they ask to select OS as Windows XP , the file is for .exe only.

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=in&dlc=en&lang=en&lc=en&product=435853&](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=in&dlc=en&lang=en&lc=en&product=435853&) 

This is HP page for my desktop PC. There is 1 BIOS update available there. But they provide it only for XP. Option for DOS isn't there.

hwinfo :-

```

============ start debug info ============
libhd version 16.0u (ia32)
using /var/lib/hardware
kernel version is 3.0
----- /proc/cmdline -----
  BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=ececbda8-912d-4c7c-9065-122f7942b6b0 ro quiet splash vt.handoff=7
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x00138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports -modules.pata -net.eeprom -x86emu -max -lxrc)
shm: attached segment 10616838 at 0xb77da000
>> hal.1: read hal data
  hal: connected to: :1.31
  hal: empty device list
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
  bios: 0 disks
>> bios.2: rom
>> bios.3: smp
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  410  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  420  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  430  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  440  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  450  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  470  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  480  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  490  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
>> bios.4: vbe
VBE: Could not init Int10
>> bios.5: 32
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = -1
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <5>[   10.436926] type=1400 audit(1321379313.914:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
  <5>[   10.455261] type=1400 audit(1321379313.930:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=498 comm="apparmor_parser"
  <5>[   10.709321] intel_rng: FWH not detected
  <6>[   10.709381] lp0: using parport0 (interrupt-driven).
  <6>[   10.805018] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  <7>[   10.805026] i915 0000:00:02.0: setting latency timer to 64
  <6>[   11.161356] usbcore: registered new interface driver uas
  <6>[   11.190525] Initializing USB Mass Storage driver...
  <6>[   11.202287] 8139too 0000:02:02.0: eth0: link down
  <6>[   11.202548] ADDRCONF(NETDEV_UP): eth0: link is not ready
  <6>[   11.205180] scsi4 : usb-storage 5-1:1.0
  <6>[   11.223890] scsi5 : usb-storage 5-2:1.0
  <6>[   11.229689] usbcore: registered new interface driver usb-storage
  <6>[   11.229695] USB Mass Storage support registered.
  <6>[   11.240483] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
  <6>[   11.252923] generic-usb 0003:1C4F:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1d.0-1/input0
  <5>[   11.381877] type=1400 audit(1321379314.858:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=629 comm="apparmor_parser"
  <5>[   11.388648] type=1400 audit(1321379314.866:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=629 comm="apparmor_parser"
  <5>[   11.388992] type=1400 audit(1321379314.866:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=629 comm="apparmor_parser"
  <5>[   11.435679] type=1400 audit(1321379314.910:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=631 comm="apparmor_parser"
  <5>[   11.446817] type=1400 audit(1321379314.922:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=631 comm="apparmor_parser"
  <5>[   11.455419] type=1400 audit(1321379314.930:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=631 comm="apparmor_parser"
  <6>[   11.460094] usb 5-2: USB disconnect, device number 3
  <6>[   11.565329] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
  <6>[   11.565335] [drm] Driver supports precise vblank timestamp query.
  <6>[   11.565926] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
  <6>[   11.700061] usb 5-2: new full speed USB device number 4 using uhci_hcd
  <6>[   11.943459] scsi9 : usb-storage 5-2:1.3
  <4>[   12.019204] init: failsafe main process (732) killed by TERM signal
  <4>[   12.028257] init: apport pre-start process (750) terminated with status 1
  <4>[   12.032548] init: alsa-restore main process (760) terminated with status 19
  <4>[   12.092229] init: apport post-stop process (779) terminated with status 1
  <6>[   12.172624] [drm] initialized overlay support
  <5>[   12.222904] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
  <5>[   12.226042] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
  <5>[   12.228915] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
  <5>[   12.231908] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
  <5>[   12.233136] sd 4:0:0:0: Attached scsi generic sg2 type 0
  <5>[   12.233549] sd 4:0:0:1: Attached scsi generic sg3 type 0
  <5>[   12.233965] sd 4:0:0:2: Attached scsi generic sg4 type 0
  <5>[   12.234388] sd 4:0:0:3: Attached scsi generic sg5 type 0
  <5>[   12.473903] sd 4:0:0:1: [sdc] Attached SCSI removable disk
  <5>[   12.488898] sd 4:0:0:0: [sdb] Attached SCSI removable disk
  <5>[   12.493898] sd 4:0:0:2: [sdd] Attached SCSI removable disk
  <5>[   12.503891] sd 4:0:0:3: [sde] Attached SCSI removable disk
  <6>[   12.608436] ppdev: user-space parallel port driver
  <6>[   12.652670] fbcon: inteldrmfb (fb0) is primary device
  <6>[   12.653750] Console: switching to colour frame buffer device 170x48
  <6>[   12.653787] fb0: inteldrmfb frame buffer device
  <6>[   12.653790] drm: registered panic notifier
  <6>[   12.653840] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
  <6>[   12.653900] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  <7>[   12.653982] HDA Intel 0000:00:1b.0: irq 41 for MSI/MSI-X
  <7>[   12.654021] HDA Intel 0000:00:1b.0: setting latency timer to 64
  <6>[   12.818249] hda_codec: ALC880: BIOS auto-probing.
  <5>[   12.959921] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
  <5>[   12.962917] scsi 9:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
  <4>[   12.978897] sr1: scsi-1 drive
  <7>[   12.979119] sr 9:0:0:0: Attached scsi CD-ROM sr1
  <5>[   12.979249] sr 9:0:0:0: Attached scsi generic sg6 type 5
  <5>[   12.979486] sd 9:0:0:1: Attached scsi generic sg7 type 0
  <5>[   12.989898] sd 9:0:0:1: [sdf] Attached SCSI removable disk
  <6>[   13.461925] Bluetooth: Core ver 2.16
  <6>[   13.462025] NET: Registered protocol family 31
  <6>[   13.462028] Bluetooth: HCI device and connection manager initialized
  <6>[   13.462032] Bluetooth: HCI socket layer initialized
  <6>[   13.462035] Bluetooth: L2CAP socket layer initialized
  <6>[   13.464374] Bluetooth: SCO socket layer initialized
  <6>[   13.487232] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
  <6>[   13.487238] Bluetooth: BNEP filters: protocol multicast
  <4>[   13.853799] init: plymouth-stop pre-start process (1006) terminated with status 1
  <3>[   21.265107] generic-usb 0003:1C4F:0002.0002: usb_submit_urb(ctrl) failed
  <4>[   21.265121] generic-usb 0003:1C4F:0002.0002: timeout initializing reports
  <6>[   21.265287] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
  <6>[   21.265447] generic-usb 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1d.0-1/input1
  <6>[   21.279942] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
  <6>[   21.281360] generic-usb 0003:093A:2510.0003: input,hidraw2: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-2/input0
  <6>[   21.283187] usbcore: registered new interface driver usbhid
  <6>[   21.283192] usbhid: USB HID core driver
  <6>[   21.390315] usbcore: registered new interface driver usbserial
  <6>[   21.390423] USB Serial support registered for generic
  <6>[   21.392932] usbcore: registered new interface driver usbserial_generic
  <6>[   21.392938] usbserial: USB Serial Driver core
  <6>[   21.403577] USB Serial support registered for GSM modem (1-port)
  <6>[   21.404979] option 5-2:1.0: GSM modem (1-port) converter detected
  <6>[   21.407325] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
  <6>[   21.407363] option 5-2:1.1: GSM modem (1-port) converter detected
  <6>[   21.410767] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
  <6>[   21.410800] option 5-2:1.2: GSM modem (1-port) converter detected
  <6>[   21.414087] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
  <6>[   21.414127] option 5-2:1.4: GSM modem (1-port) converter detected
  <6>[   21.415366] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3
  <6>[   21.416980] usbcore: registered new interface driver option
  <6>[   21.416986] option: v0.7.2:USB Driver for GSM modems
  <4>[   21.627289] audit_printk_skb: 12 callbacks suppressed
  <5>[   21.627294] type=1400 audit(1321379325.102:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1092 comm="apparmor_parser"
  <5>[   21.628078] type=1400 audit(1321379325.106:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1092 comm="apparmor_parser"
  <6>[   53.307419] PPP BSD Compression module registered
  <6>[   53.322842] PPP Deflate Compression module registered
  <4>[  627.155170] exe (1532): /proc/1532/oom_adj is deprecated, please use /proc/1532/oom_score_adj instead.
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Module parport_pc is in use
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by ppdev,parport_pc,lp
----- return code: ? -----
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  0000-001f : dma1
  0020-0021 : pic1
  0040-0043 : timer0
  0050-0053 : timer1
  0060-0060 : keyboard
  0064-0064 : keyboard
  0070-0071 : rtc0
  0080-008f : dma page reg
  00a0-00a1 : pic2
  00c0-00df : dma2
  00f0-00ff : fpu
  0170-0177 : 0000:00:1f.1
    0170-0177 : ata_piix
  01f0-01f7 : 0000:00:1f.1
    01f0-01f7 : ata_piix
  0376-0376 : 0000:00:1f.1
    0376-0376 : ata_piix
  0378-037a : parport0
  03f2-03f2 : floppy
  03f4-03f5 : floppy
  03f6-03f6 : 0000:00:1f.1
    03f6-03f6 : ata_piix
  03f7-03f7 : floppy
  0400-041f : 0000:00:1f.3
  0480-04bf : pnp 00:09
  04d0-04d1 : pnp 00:09
  0680-06ff : pnp 00:08
  0778-077a : parport0
  0800-087f : pnp 00:09
    0800-0803 : ACPI PM1a_EVT_BLK
    0804-0805 : ACPI PM1a_CNT_BLK
    0808-080b : ACPI PM_TMR
    0810-0815 : ACPI CPU throttle
    0828-082f : ACPI GPE0_BLK
  0cf8-0cff : PCI conf1
  b800-b80f : 0000:00:1f.2
    b800-b80f : ata_piix
  b880-b883 : 0000:00:1f.2
    b880-b883 : ata_piix
  bc00-bc07 : 0000:00:1f.2
    bc00-bc07 : ata_piix
  c000-c003 : 0000:00:1f.2
    c000-c003 : ata_piix
  c080-c087 : 0000:00:1f.2
    c080-c087 : ata_piix
  c400-c41f : 0000:00:1d.0
    c400-c41f : uhci_hcd
  c480-c49f : 0000:00:1d.1
    c480-c49f : uhci_hcd
  c800-c81f : 0000:00:1d.2
    c800-c81f : uhci_hcd
  c880-c89f : 0000:00:1d.3
    c880-c89f : uhci_hcd
  cc00-cc07 : 0000:00:02.0
  d000-dfff : PCI Bus 0000:01
  e000-efff : PCI Bus 0000:02
    e000-e0ff : 0000:02:05.0
    e480-e487 : 0000:02:05.0
    e800-e8ff : 0000:02:02.0
      e800-e8ff : 8139too
    ec00-ec7f : 0000:02:01.0
  ffa0-ffaf : 0000:00:1f.1
    ffa0-ffaf : ata_piix
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:         57   IO-APIC-edge      timer
    1:          2   IO-APIC-edge      i8042
    6:          3   IO-APIC-edge      floppy
    7:          0   IO-APIC-edge      parport0
    8:          1   IO-APIC-edge      rtc0
    9:          0   IO-APIC-fasteoi   acpi
   12:          4   IO-APIC-edge      i8042
   14:      10386   IO-APIC-edge      ata_piix
   15:          0   IO-APIC-edge      ata_piix
   16:     292981   IO-APIC-fasteoi   uhci_hcd:usb5, i915
   18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
   19:      24092   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
   20:         66   IO-APIC-fasteoi   firewire_ohci
   21:          0   IO-APIC-fasteoi   eth0
   23:      61357   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
   41:      14461   PCI-MSI-edge      hda_intel
  NMI:          0   Non-maskable interrupts
  LOC:     863074   Local timer interrupts
  SPU:          0   Spurious interrupts
  PMI:          0   Performance monitoring interrupts
  IWI:          0   IRQ work interrupts
  RES:          0   Rescheduling interrupts
  CAL:          0   Function call interrupts
  TLB:          0   TLB shootdowns
  TRM:          0   Thermal event interrupts
  THR:          0   Threshold APIC interrupts
  MCE:          0   Machine check exceptions
  MCP:         14   Machine check polls
  ERR:          0
  MIS:          0
----- /proc/interrupts end -----
----- /proc/dma -----
   2: floppy
   3: parport0
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 15
  model		: 3
  model name	: Intel(R) Pentium(R) 4 CPU 2.93GHz
  stepping	: 4
  cpu MHz		: 2932.017
  cache size	: 1024 KB
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
  bogomips	: 5864.03
  clflush size	: 64
  cache_alignment	: 128
  address sizes	: 36 bits physical, 32 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x3f7fe000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0x4dedd000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0x6f09e3cb7bef2a0e) -----
      alarmtimer: /devices/platform/alarmtimer
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
          floppy: /devices/platform/floppy.0
      parport_pc: module = parport_pc
        pcieport: /devices/pci0000:00/0000:00:1c.0
   agpgart-intel: /devices/pci0000:00/0000:00:00.0
        pdc_adma: module = pdc_adma
        ata_piix: /devices/pci0000:00/0000:00:1f.1
        ata_piix: /devices/pci0000:00/0000:00:1f.2
        ata_piix: module = ata_piix
        pata_sis: module = pata_sis
       pata_acpi: module = pata_acpi
     ata_generic: module = ata_generic
        ehci_hcd: /devices/pci0000:00/0000:00:1d.7
        ehci_hcd: module = ehci_hcd
        uhci_hcd: /devices/pci0000:00/0000:00:1d.0
        uhci_hcd: /devices/pci0000:00/0000:00:1d.1
        uhci_hcd: /devices/pci0000:00/0000:00:1d.2
        uhci_hcd: /devices/pci0000:00/0000:00:1d.3
        uhci_hcd: module = uhci_hcd
          8139cp: module = 8139cp
         8139too: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
         8139too: module = 8139too
   firewire_ohci: /devices/pci0000:00/0000:00:1e.0/0000:02:01.0
   firewire_ohci: module = firewire_ohci
      parport_pc: module = parport_pc
            i915: /devices/pci0000:00/0000:00:02.0
            i915: module = drm
       HDA Intel: /devices/pci0000:00/0000:00:1b.0
       HDA Intel: module = snd_hda_intel
        pci_root: /devices/LNXSYSTM:00/device:00/PNP0A08:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
          button: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
       processor: /devices/LNXSYSTM:00/LNXCPU:00
       processor: /devices/LNXSYSTM:00/LNXCPU:01
          system: /devices/pnp0/00:01
          system: /devices/pnp0/00:08
          system: /devices/pnp0/00:09
          system: /devices/pnp0/00:0b
          system: /devices/pnp0/00:0c
          system: /devices/pnp0/00:0d
          system: /devices/pnp0/00:0e
          system: /devices/pnp0/00:0f
        rtc_cmos: /devices/pnp0/00:03
      parport_pc: /devices/pnp0/00:07
              sd: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
              sd: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
              sd: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
              sd: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
              sd: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
              sd: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
              sr: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
              sr: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
             usb: /devices/pci0000:00/0000:00:1d.7/usb1
             usb: /devices/pci0000:00/0000:00:1d.0/usb2
             usb: /devices/pci0000:00/0000:00:1d.1/usb3
             usb: /devices/pci0000:00/0000:00:1d.2/usb4
             usb: /devices/pci0000:00/0000:00:1d.3/usb5
             usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
             usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-2
             usb: /devices/pci0000:00/0000:00:1d.3/usb5/5-1
             usb: /devices/pci0000:00/0000:00:1d.3/usb5/5-2
             uas: module = uas
     usb-storage: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
     usb-storage: module = usb_storage
     usb-storage: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3
          usbhid: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
          usbhid: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
          usbhid: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
          usbhid: module = usbhid
       usbserial: module = usbserial
usbserial_generic: module = usbserial
          option: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
          option: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
          option: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
          option: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
          option: module = option
       serio_raw: module = serio_raw
         psmouse: module = psmouse
     generic-usb: module = usbhid
     generic-usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001
     generic-usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002
     generic-usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003
         generic: module = usbserial
         option1: module = option
         option1: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0
         option1: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1
         option1: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2
         option1: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v00008086d00002580sv0000103Csd00002A08bc06sc00i00"
    class = 0x60000
    vendor = 0x8086
    device = 0x2580
    subvendor = 0x103c
    subdevice = 0x2a08
    irq = 0
    config[64]
  pci device: name = 0000:00:02.0
    path = /devices/pci0000:00/0000:00:02.0
    modalias = "pci:v00008086d00002582sv0000103Csd00002A08bc03sc00i00"
    class = 0x30000
    vendor = 0x8086
    device = 0x2582
    subvendor = 0x103c
    subdevice = 0x2a08
    irq = 16
    res[0] = 0xcfe00000 0xcfe7ffff 0x40200
    res[1] = 0xcc00 0xcc07 0x40101
    res[2] = 0xd0000000 0xdfffffff 0x42208
    res[3] = 0xcfdc0000 0xcfdfffff 0x40200
    config[64]
  pci device: name = 0000:00:02.1
    path = /devices/pci0000:00/0000:00:02.1
    modalias = "pci:v00008086d00002782sv0000103Csd00002A08bc03sc80i00"
    class = 0x38000
    vendor = 0x8086
    device = 0x2782
    subvendor = 0x103c
    subdevice = 0x2a08
    irq = 0
    res[0] = 0xcfe80000 0xcfefffff 0x40200
    config[64]
  pci device: name = 0000:00:1b.0
    path = /devices/pci0000:00/0000:00:1b.0
    modalias = "pci:v00008086d00002668sv0000103Csd00002A09bc04sc03i00"
    class = 0x40300
    vendor = 0x8086
    device = 0x2668
    subvendor = 0x103c
    subdevice = 0x2a09
    irq = 41
    res[0] = 0xcfdb8000 0xcfdbbfff 0x140204
    config[64]
  pci device: name = 0000:00:1c.0
    path = /devices/pci0000:00/0000:00:1c.0
    modalias = "pci:v00008086d00002660sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x2660
    subvendor = 0x0
    subdevice = 0x0
    irq = 40
    config[64]
  pci device: name = 0000:00:1d.0
    path = /devices/pci0000:00/0000:00:1d.0
    modalias = "pci:v00008086d00002658sv0000103Csd00002A0Abc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2658
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 23
    res[4] = 0xc400 0xc41f 0x40101
    config[64]
  pci device: name = 0000:00:1d.1
    path = /devices/pci0000:00/0000:00:1d.1
    modalias = "pci:v00008086d00002659sv0000103Csd00002A0Abc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2659
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 19
    res[4] = 0xc480 0xc49f 0x40101
    config[64]
  pci device: name = 0000:00:1d.2
    path = /devices/pci0000:00/0000:00:1d.2
    modalias = "pci:v00008086d0000265Asv0000103Csd00002A0Abc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x265a
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 18
    res[4] = 0xc800 0xc81f 0x40101
    config[64]
  pci device: name = 0000:00:1d.3
    path = /devices/pci0000:00/0000:00:1d.3
    modalias = "pci:v00008086d0000265Bsv0000103Csd00002A0Abc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x265b
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 16
    res[4] = 0xc880 0xc89f 0x40101
    config[64]
  pci device: name = 0000:00:1d.7
    path = /devices/pci0000:00/0000:00:1d.7
    modalias = "pci:v00008086d0000265Csv0000103Csd00002A0Abc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x265c
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 23
    res[0] = 0xcfdb7c00 0xcfdb7fff 0x40200
    config[64]
  pci device: name = 0000:00:1e.0
    path = /devices/pci0000:00/0000:00:1e.0
    modalias = "pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
    class = 0x60401
    vendor = 0x8086
    device = 0x244e
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.0
    path = /devices/pci0000:00/0000:00:1f.0
    modalias = "pci:v00008086d00002640sv0000103Csd00002A0Abc06sc01i00"
    class = 0x60100
    vendor = 0x8086
    device = 0x2640
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.1
    path = /devices/pci0000:00/0000:00:1f.1
    modalias = "pci:v00008086d0000266Fsv0000103Csd00002A0Abc01sc01i8a"
    class = 0x1018a
    vendor = 0x8086
    device = 0x266f
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 18
    res[0] = 0x1f0 0x1f7 0x110
    res[1] = 0x3f6 0x3f6 0x110
    res[2] = 0x170 0x177 0x110
    res[3] = 0x376 0x376 0x110
    res[4] = 0xffa0 0xffaf 0x40101
    config[64]
  pci device: name = 0000:00:1f.2
    path = /devices/pci0000:00/0000:00:1f.2
    modalias = "pci:v00008086d00002651sv0000103Csd00002A0Abc01sc01i8f"
    class = 0x1018f
    vendor = 0x8086
    device = 0x2651
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 19
    res[0] = 0xc080 0xc087 0x40101
    res[1] = 0xc000 0xc003 0x40101
    res[2] = 0xbc00 0xbc07 0x40101
    res[3] = 0xb880 0xb883 0x40101
    res[4] = 0xb800 0xb80f 0x40101
    config[64]
  pci device: name = 0000:00:1f.3
    path = /devices/pci0000:00/0000:00:1f.3
    modalias = "pci:v00008086d0000266Asv0000103Csd00002A0Abc0Csc05i00"
    class = 0xc0500
    vendor = 0x8086
    device = 0x266a
    subvendor = 0x103c
    subdevice = 0x2a0a
    irq = 10
    res[4] = 0x400 0x41f 0x40101
    config[64]
  pci device: name = 0000:02:01.0
    path = /devices/pci0000:00/0000:00:1e.0/0000:02:01.0
    modalias = "pci:v00001106d00003044sv0000103Csd00002A0Cbc0Csc00i10"
    class = 0xc0010
    vendor = 0x1106
    device = 0x3044
    subvendor = 0x103c
    subdevice = 0x2a0c
    irq = 20
    res[0] = 0xcffff800 0xcfffffff 0x40200
    res[1] = 0xec00 0xec7f 0x40101
    config[64]
  pci device: name = 0000:02:02.0
    path = /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
    modalias = "pci:v000010ECd00008139sv0000103Csd00002A0Bbc02sc00i00"
    class = 0x20000
    vendor = 0x10ec
    device = 0x8139
    subvendor = 0x103c
    subdevice = 0x2a0b
    irq = 21
    res[0] = 0xe800 0xe8ff 0x40101
    res[1] = 0xcffff400 0xcffff4ff 0x40200
    config[64]
  pci device: name = 0000:02:05.0
    path = /devices/pci0000:00/0000:00:1e.0/0000:02:05.0
    modalias = "pci:v000011C1d0000048Csv000011C1sd0000044Cbc07sc80i00"
    class = 0x78000
    vendor = 0x11c1
    device = 0x48c
    subvendor = 0x11c1
    subdevice = 0x44c
    irq = 255
    res[0] = 0xcffff000 0xcffff0ff 0x40200
    res[1] = 0xe480 0xe487 0x40101
    res[2] = 0xe000 0xe0ff 0x40101
    config[64]
---------- PCI raw data ----------
bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 8086:2580:103c:2a08:04
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 80 25 06 00 90 20 04 00 00 06 00 00 00 00  "...%... ........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 08 2a  "............<..*"
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 02, func 0, vend:dev:s_vend:s_dev:rev 8086:2582:103c:2a08:04
class 03, sub_class 00 prog_if 00, hdr 0, flags <>, irq 16
  addr0 cfe00000, size 00080000
  addr1 0000cc00, size 00000008
  addr2 d0000000, size 10000000
  addr3 cfdc0000, size 00040000
  00: 86 80 82 25 07 00 90 00 04 00 00 03 00 00 80 00  "...%............"
  10: 00 00 e0 cf 01 cc 00 00 08 00 00 d0 00 00 dc cf  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 08 2a  "............<..*"
  30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 01 00 00  "................"

bus 00, slot 02, func 1, vend:dev:s_vend:s_dev:rev 8086:2782:103c:2a08:04
class 03, sub_class 80 prog_if 00, hdr 0, flags <>, irq 0
  addr0 cfe80000, size 00080000
  00: 86 80 82 27 07 00 90 00 04 00 80 03 00 00 80 00  "...'............"
  10: 00 00 e8 cf 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 08 2a  "............<..*"
  30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1b, func 0, vend:dev:s_vend:s_dev:rev 8086:2668:103c:2a09:03
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 41
  addr0 cfdb8000, size 00004000
  00: 86 80 68 26 06 04 10 00 03 00 03 04 04 00 00 00  "..h&............"
  10: 04 80 db cf 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 09 2a  "............<..*"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 01 00 00  "....P..........."

bus 00->01, slot 1c, func 0, vend:dev:s_vend:s_dev:rev 8086:2660:0000:0000:03
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 40
  00: 86 80 60 26 07 05 10 00 03 00 04 06 04 00 81 00  "..`&............"
  10: 00 00 00 00 00 00 00 00 00 01 01 00 d0 d0 00 00  "................"
  20: 00 50 10 50 21 50 31 50 00 00 00 00 00 00 00 00  ".P.P!P1P........"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 02 00  "....@..........."

bus 00, slot 1d, func 0, vend:dev:s_vend:s_dev:rev 8086:2658:103c:2a0a:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 23
  addr4 0000c400, size 00000020
  00: 86 80 58 26 05 00 80 02 03 00 03 0c 00 00 80 00  "..X&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 c4 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 05 01 00 00  "................"

bus 00, slot 1d, func 1, vend:dev:s_vend:s_dev:rev 8086:2659:103c:2a0a:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 19
  addr4 0000c480, size 00000020
  00: 86 80 59 26 05 00 80 02 03 00 03 0c 00 00 00 00  "..Y&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 81 c4 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 02 00 00  "................"

bus 00, slot 1d, func 2, vend:dev:s_vend:s_dev:rev 8086:265a:103c:2a0a:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 18
  addr4 0000c800, size 00000020
  00: 86 80 5a 26 05 00 80 02 03 00 03 0c 00 00 00 00  "..Z&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 c8 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 03 03 00 00  "................"

bus 00, slot 1d, func 3, vend:dev:s_vend:s_dev:rev 8086:265b:103c:2a0a:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 16
  addr4 0000c880, size 00000020
  00: 86 80 5b 26 05 00 80 02 03 00 03 0c 00 00 00 00  "..[&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 81 c8 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 04 00 00  "................"

bus 00, slot 1d, func 7, vend:dev:s_vend:s_dev:rev 8086:265c:103c:2a0a:03
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 23
  addr0 cfdb7c00, size 00000400
  00: 86 80 5c 26 06 00 90 02 03 20 03 0c 00 00 00 00  "..\&..... ......"
  10: 00 7c db cf 00 00 00 00 00 00 00 00 00 00 00 00  ".|.............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 05 01 00 00  "....P..........."

bus 00->02, slot 1e, func 0, vend:dev:s_vend:s_dev:rev 8086:244e:0000:0000:d3
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 0
  00: 86 80 4e 24 07 01 10 00 d3 01 04 06 00 00 01 00  "..N$............"
  10: 00 00 00 00 00 00 00 00 00 02 02 20 e0 e0 80 a2  "........... ...."
  20: f0 cf f0 cf f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 00 00 02 00  "....P..........."

bus 00, slot 1f, func 0, vend:dev:s_vend:s_dev:rev 8086:2640:103c:2a0a:03
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 40 26 07 00 00 02 03 00 01 06 00 00 80 00  "..@&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1f, func 1, vend:dev:s_vend:s_dev:rev 8086:266f:103c:2a0a:03
class 01, sub_class 01 prog_if 8a, hdr 0, flags <>, irq 18
  addr0 000001f0, size 00000008
  addr1 000003f6, size 00000001
  addr2 00000170, size 00000008
  addr3 00000376, size 00000001
  addr4 0000ffa0, size 00000010
  00: 86 80 6f 26 05 00 80 02 03 8a 01 01 00 00 00 00  "..o&............"
  10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00  "................"
  20: a1 ff 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 01 00 00  "................"

bus 00, slot 1f, func 2, vend:dev:s_vend:s_dev:rev 8086:2651:103c:2a0a:03
class 01, sub_class 01 prog_if 8f, hdr 0, flags <>, irq 19
  addr0 0000c080, size 00000008
  addr1 0000c000, size 00000004
  addr2 0000bc00, size 00000008
  addr3 0000b880, size 00000004
  addr4 0000b800, size 00000010
  00: 86 80 51 26 05 00 b0 02 03 8f 01 01 00 00 00 00  "..Q&............"
  10: 81 c0 00 00 01 c0 00 00 01 bc 00 00 81 b8 00 00  "................"
  20: 01 b8 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 70 00 00 00 00 00 00 00 0b 02 00 00  "....p..........."

bus 00, slot 1f, func 3, vend:dev:s_vend:s_dev:rev 8086:266a:103c:2a0a:03
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 10
  addr4 00000400, size 00000020
  00: 86 80 6a 26 01 00 80 02 03 00 05 0c 00 00 00 00  "..j&............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 04 00 00 00 00 00 00 00 00 00 00 3c 10 0a 2a  "............<..*"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 02 00 00  "................"

bus 02, slot 01, func 0, vend:dev:s_vend:s_dev:rev 1106:3044:103c:2a0c:80
class 0c, sub_class 00 prog_if 10, hdr 0, flags <>, irq 20
  addr0 cffff800, size 00000800
  addr1 0000ec00, size 00000080
  00: 06 11 44 30 17 00 10 02 80 10 00 0c 04 40 00 00  "..D0.........@.."
  10: 00 f8 ff cf 01 ec 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 0c 2a  "............<..*"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 04 01 00 20  "....P.......... "

bus 02, slot 02, func 0, vend:dev:s_vend:s_dev:rev 10ec:8139:103c:2a0b:10
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 21
  addr0 0000e800, size 00000100
  addr1 cffff400, size 00000100
  00: ec 10 39 81 07 00 90 02 10 00 00 02 00 40 00 00  "..9..........@.."
  10: 01 e8 00 00 00 f4 ff cf 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 0b 2a  "............<..*"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 05 01 20 40  "....P......... @"

bus 02, slot 05, func 0, vend:dev:s_vend:s_dev:rev 11c1:048c:11c1:044c:03
class 07, sub_class 80 prog_if 00, hdr 0, flags <>, irq 255
  addr0 cffff000, size 00000100
  addr1 0000e480, size 00000008
  addr2 0000e000, size 00000100
  00: c1 11 8c 04 07 00 90 02 03 00 80 07 00 40 00 00  ".............@.."
  10: 00 f0 ff cf 81 e4 00 00 01 e0 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 40 00 00 00 c1 11 4c 04  "........@.....L."
  30: 00 00 00 00 f8 00 00 00 00 00 00 00 ff 01 fc 0e  "................"
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.4: vio
sysfs: no such bus: vio
>> pci.5: xen
sysfs: no such bus: xen
>> pci.6: ps3
sysfs: no such bus: ps3_system_bus
>> pci.7: platform
  platform device: name = reg-dummy
    path = /devices/platform/reg-dummy
    type = "platform:reg-dummy"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = alarmtimer
    path = /devices/platform/alarmtimer
    type = "platform:alarmtimer"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = eisa.0
    path = /devices/platform/eisa.0
    type = "platform:eisa"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = floppy.0
    path = /devices/platform/floppy.0
    type = "platform:floppy"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> pci.11: ibmebus
sysfs: no such bus: ibmebus
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> isapnp.1: pnp devices
  pnp device: name = 00:00
    path = /devices/pnp0/00:00
    id = PNP 0a08
  pnp device: name = 00:01
    path = /devices/pnp0/00:01
    id = PNP 0c01
  pnp device: name = 00:02
    path = /devices/pnp0/00:02
    id = PNP 0200
  pnp device: name = 00:03
    path = /devices/pnp0/00:03
    id = PNP 0b00
  pnp device: name = 00:04
    path = /devices/pnp0/00:04
    id = PNP 0800
  pnp device: name = 00:05
    path = /devices/pnp0/00:05
    id = PNP 0c04
  pnp device: name = 00:06
    path = /devices/pnp0/00:06
    id = PNP 0700
  pnp device: name = 00:07
    path = /devices/pnp0/00:07
    id = PNP 0401
  pnp device: name = 00:08
    path = /devices/pnp0/00:08
    id = PNP 0c02
  pnp device: name = 00:09
    path = /devices/pnp0/00:09
    id = PNP 0c02
  pnp device: name = 00:0a
    path = /devices/pnp0/00:0a
    id = INT 0800
  pnp device: name = 00:0b
    path = /devices/pnp0/00:0b
    id = PNP 0c02
  pnp device: name = 00:0c
    path = /devices/pnp0/00:0c
    id = PNP 0c02
  pnp device: name = 00:0d
    path = /devices/pnp0/00:0d
    id = PNP 0c02
  pnp device: name = 00:0e
    path = /devices/pnp0/00:0e
    id = PNP 0c02
  pnp device: name = 00:0f
    path = /devices/pnp0/00:0f
    id = PNP 0c01
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:1 0x0000 - 0x001f (0x20) "dma1"
i/o:1 0x0020 - 0x0021 (0x02) "pic1"
i/o:0 0x0040 - 0x0043 (0x04) "timer0"
i/o:0 0x0050 - 0x0053 (0x04) "timer1"
i/o:1 0x0060 - 0x0060 (0x01) "keyboard"
i/o:1 0x0064 - 0x0064 (0x01) "keyboard"
i/o:0 0x0070 - 0x0071 (0x02) "rtc0"
i/o:1 0x0080 - 0x008f (0x10) "dma page reg"
i/o:1 0x00a0 - 0x00a1 (0x02) "pic2"
i/o:1 0x00c0 - 0x00df (0x20) "dma2"
i/o:1 0x00f0 - 0x00ff (0x10) "fpu"
i/o:0 0x0170 - 0x0177 (0x08) "0000:00:1f.1"
i/o:0 0x0170 - 0x0177 (0x08) "ata_piix"
i/o:0 0x01f0 - 0x01f7 (0x08) "0000:00:1f.1"
i/o:0 0x01f0 - 0x01f7 (0x08) "ata_piix"
i/o:0 0x0376 - 0x0376 (0x01) "0000:00:1f.1"
i/o:0 0x0376 - 0x0376 (0x01) "ata_piix"
i/o:1 0x0378 - 0x037a (0x03) "parport0"
i/o:1 0x03f2 - 0x03f2 (0x01) "floppy"
i/o:1 0x03f4 - 0x03f5 (0x02) "floppy"
i/o:0 0x03f6 - 0x03f6 (0x01) "0000:00:1f.1"
i/o:0 0x03f6 - 0x03f6 (0x01) "ata_piix"
i/o:1 0x03f7 - 0x03f7 (0x01) "floppy"
i/o:0 0x0400 - 0x041f (0x20) "0000:00:1f.3"
i/o:0 0x0480 - 0x04bf (0x40) "pnp 00:09"
i/o:0 0x04d0 - 0x04d1 (0x02) "pnp 00:09"
i/o:0 0x0680 - 0x06ff (0x80) "pnp 00:08"
i/o:1 0x0778 - 0x077a (0x03) "parport0"
i/o:0 0x0800 - 0x087f (0x80) "pnp 00:09"
i/o:0 0x0800 - 0x0803 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x0804 - 0x0805 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x0808 - 0x080b (0x04) "ACPI PM_TMR"
i/o:0 0x0810 - 0x0815 (0x06) "ACPI CPU throttle"
i/o:0 0x0828 - 0x082f (0x08) "ACPI GPE0_BLK"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0xb800 - 0xb80f (0x10) "0000:00:1f.2"
i/o:0 0xb800 - 0xb80f (0x10) "ata_piix"
i/o:0 0xb880 - 0xb883 (0x04) "0000:00:1f.2"
i/o:0 0xb880 - 0xb883 (0x04) "ata_piix"
i/o:0 0xbc00 - 0xbc07 (0x08) "0000:00:1f.2"
i/o:0 0xbc00 - 0xbc07 (0x08) "ata_piix"
i/o:0 0xc000 - 0xc003 (0x04) "0000:00:1f.2"
i/o:0 0xc000 - 0xc003 (0x04) "ata_piix"
i/o:0 0xc080 - 0xc087 (0x08) "0000:00:1f.2"
i/o:0 0xc080 - 0xc087 (0x08) "ata_piix"
i/o:0 0xc400 - 0xc41f (0x20) "0000:00:1d.0"
i/o:0 0xc400 - 0xc41f (0x20) "uhci_hcd"
i/o:0 0xc480 - 0xc49f (0x20) "0000:00:1d.1"
i/o:0 0xc480 - 0xc49f (0x20) "uhci_hcd"
i/o:0 0xc800 - 0xc81f (0x20) "0000:00:1d.2"
i/o:0 0xc800 - 0xc81f (0x20) "uhci_hcd"
i/o:0 0xc880 - 0xc89f (0x20) "0000:00:1d.3"
i/o:0 0xc880 - 0xc89f (0x20) "uhci_hcd"
i/o:0 0xcc00 - 0xcc07 (0x08) "0000:00:02.0"
i/o:0 0xd000 - 0xdfff (0x1000) "PCI Bus 0000:01"
i/o:0 0xe000 - 0xefff (0x1000) "PCI Bus 0000:02"
i/o:0 0xe000 - 0xe0ff (0x100) "0000:02:05.0"
i/o:0 0xe480 - 0xe487 (0x08) "0000:02:05.0"
i/o:0 0xe800 - 0xe8ff (0x100) "0000:02:02.0"
i/o:0 0xe800 - 0xe8ff (0x100) "8139too"
i/o:0 0xec00 - 0xec7f (0x80) "0000:02:01.0"
i/o:0 0xffa0 - 0xffaf (0x10) "0000:00:1f.1"
i/o:0 0xffa0 - 0xffaf (0x10) "ata_piix"
irq:1  0 (       57) "timer"
irq:0  1 (        2) "i8042"
irq:1  6 (        3) "floppy"
irq:1  7 (        0) "parport0"
irq:0  8 (        1) "rtc0"
irq:0  9 (        0) "acpi"
irq:0 12 (        4) "i8042"
irq:0 14 (    10386) "ata_piix"
irq:0 15 (        0) "ata_piix"
irq:0 16 (   292981) "uhci_hcd:usb5" "i915"
irq:0 18 (        0) "uhci_hcd:usb4"
irq:0 19 (    24092) "ata_piix" "uhci_hcd:usb3"
irq:0 20 (       66) "firewire_ohci"
irq:0 21 (        0) "eth0"
irq:0 23 (    61357) "ehci_hcd:usb1" "uhci_hcd:usb2"
irq:0 41 (    14461) "hda_intel"
dma:1 2 "floppy"
dma:1 3 "parport0"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Module parport_pc is in use
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
/proc/sys/dev/parport/parport0/base-addr
  888	1912
/proc/sys/dev/parport/parport0/autoprobe
----- parallel info end -----
>> parallel.5: ppa mod
----- exec: "/sbin/modprobe ppa " -----
  FATAL: Error inserting ppa (/lib/modules/3.0.0-12-generic/kernel/drivers/scsi/ppa.ko): Operation not permitted
----- return code: ? -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/3.0.0-12-generic/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:		sr1	sr0
drive speed:		1	94
drive # of slots:	1	1
Can close tray:		1	1
Can open tray:		1	1
Can lock tray:		1	1
Can change speed:	0	1
Can select disk:	0	0
Can read multisession:	1	1
Can read MCN:		1	1
Reports media changed:	1	1
Can play audio:		1	1
Can write CD-R:		0	1
Can write CD-RW:	0	1
Can read DVD:		0	1
Can write DVD-R:	0	1
Can write DVD-RAM:	0	1
Can read MRW:		0	1
Can write MRW:		0	1
Can write RAM:		0	1
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
     8        0   78150744 sda
     8        1   76848128 sda1
     8        2          1 sda2
     8        5    1300480 sda5
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda5
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = sr0, path = /class/block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 0:0:1:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
    vendor = SONY
    model = DVD RW AW-G170A
    rev = 1.75
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 2:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
    vendor = ATA
    model = WDC WD800JD-22JN
    rev = 05.0
    type = 0
>> block.5: /dev/sda
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda5, path = /class/block/sda5
    dev = 8:5
  block: name = fd0, path = /class/block/fd0
    dev = 2:0
    range = 1
    block device: bus = platform, bus_id = floppy.0 driver = floppy
      path = /devices/platform/floppy.0
  block: name = sdb, path = /class/block/sdb
    dev = 8:16
    range = 16
    block device: bus = scsi, bus_id = 4:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
    vendor = Generic
    model = USB SD Reader
    rev = 1.00
    type = 0
>> block.5: /dev/sdb
  block: name = sdc, path = /class/block/sdc
    dev = 8:32
    range = 16
    block device: bus = scsi, bus_id = 4:0:0:1 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
    vendor = Generic
    model = USB CF Reader
    rev = 1.01
    type = 0
>> block.5: /dev/sdc
  block: name = sdd, path = /class/block/sdd
    dev = 8:48
    range = 16
    block device: bus = scsi, bus_id = 4:0:0:2 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
    vendor = Generic
    model = USB SM Reader
    rev = 1.02
    type = 0
>> block.5: /dev/sdd
  block: name = sde, path = /class/block/sde
    dev = 8:64
    range = 16
    block device: bus = scsi, bus_id = 4:0:0:3 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
    vendor = Generic
    model = USB MS Reader
    rev = 1.03
    type = 0
>> block.5: /dev/sde
  block: name = sr1, path = /class/block/sr1
    dev = 11:1
    range = 1
    block device: bus = scsi, bus_id = 9:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
    vendor = HUAWEI
    model = Mass Storage
    rev = 2.31
    type = 5
>> block.5: /dev/sr1
>> block.5.1: /dev/sr1 cache
  scsi cache: 0x00
  block: name = sdf, path = /class/block/sdf
    dev = 8:80
    range = 16
    block device: bus = scsi, bus_id = 9:0:0:1 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
    vendor = HUAWEI
    model = SD Storage
    rev = 2.31
    type = 0
>> block.5: /dev/sdf
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:1:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 2:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
  scsi: name = sg2, path = /class/scsi_generic/sg2
    dev = 21:2
    scsi device: bus_id = 4:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
  scsi: name = sg3, path = /class/scsi_generic/sg3
    dev = 21:3
    scsi device: bus_id = 4:0:0:1 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
  scsi: name = sg4, path = /class/scsi_generic/sg4
    dev = 21:4
    scsi device: bus_id = 4:0:0:2 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
  scsi: name = sg5, path = /class/scsi_generic/sg5
    dev = 21:5
    scsi device: bus_id = 4:0:0:3 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
  scsi: name = sg6, path = /class/scsi_generic/sg6
    dev = 21:6
    scsi device: bus_id = 9:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
  scsi: name = sg7, path = /class/scsi_generic/sg7
    dev = 21:7
    scsi device: bus_id = 9:0:0:1 driver = sd
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:1d.7/usb1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2
  usb dev: /devices/pci0000:00/0000:00:1d.1/usb3
  usb dev: /devices/pci0000:00/0000:00:1d.2/usb4
  usb dev: /devices/pci0000:00/0000:00:1d.3/usb5
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2/2-2
  usb dev: /devices/pci0000:00/0000:00:1d.3/usb5/5-1
  usb dev: /devices/pci0000:00/0000:00:1d.3/usb5/5-2
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:1d.7/usb1
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:1d.7/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 3.0.0-12-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1d.7"
    bcdDevice = 0300
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:1d.0/usb2
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-12-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.0"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb3
    path = /devices/pci0000:00/0000:00:1d.1/usb3
  usb device: name = 3-0:1.0
    path = /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-0:1.0 @ /devices/pci0000:00/0000:00:1d.1/usb3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-12-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.1"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb4
    path = /devices/pci0000:00/0000:00:1d.2/usb4
  usb device: name = 4-0:1.0
    path = /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-0:1.0 @ /devices/pci0000:00/0000:00:1d.2/usb4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-12-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.2"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb5
    path = /devices/pci0000:00/0000:00:1d.3/usb5
  usb device: name = 5-0:1.0
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-0:1.0 @ /devices/pci0000:00/0000:00:1d.3/usb5
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-12-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.3"
    bcdDevice = 0300
    speed = "12"
  usb device: name = 2-1
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  usb device: name = 2-1:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
    modalias = "usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc01ip01"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 2-1:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1c4f
    idProduct = 0x0002
    manufacturer = "USB"
    product = "USB Keykoard"
    bcdDevice = 0110
    speed = "1.5"
  usb device: name = 2-1:1.1
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
    modalias = "usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 3
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-1:1.1 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1c4f
    idProduct = 0x0002
    manufacturer = "USB"
    product = "USB Keykoard"
    bcdDevice = 0110
    speed = "1.5"
  usb device: name = 2-2
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2
  usb device: name = 2-2:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
    modalias = "usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 2-2:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x093a
    idProduct = 0x2510
    manufacturer = "PIXART"
    product = "USB OPTICAL MOUSE"
    bcdDevice = 0100
    speed = "1.5"
  usb device: name = 5-1
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1
  usb device: name = 5-1:1.0
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
    modalias = "usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50"
    bInterfaceNumber = 0
    bInterfaceClass = 8
    bInterfaceSubClass = 6
    bInterfaceProtocol = 80
    if: 5-1:1.0 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x058f
    idProduct = 0x9360
    manufacturer = ""
    product = "USB Reader"
    serial = "9205291"
    bcdDevice = 0100
    speed = "12"
  usb device: name = 5-2
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2
  usb device: name = 5-2:1.0
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
    modalias = "usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 5-2:1.0 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x12d1
    idProduct = 0x1412
    manufacturer = "HUAÿWEI TECHNOLOGIES"
    product = "HUAWEI Mobile"
    serial = ""
    bcdDevice = 0000
    speed = "12"
  usb device: name = 5-2:1.1
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
    modalias = "usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF"
    bInterfaceNumber = 1
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 5-2:1.1 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x12d1
    idProduct = 0x1412
    manufacturer = "HUAÿWEI TECHNOLOGIES"
    product = "HUAWEI Mobile"
    serial = ""
    bcdDevice = 0000
    speed = "12"
  usb device: name = 5-2:1.2
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
    modalias = "usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF"
    bInterfaceNumber = 2
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 5-2:1.2 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x12d1
    idProduct = 0x1412
    manufacturer = "HUAÿWEI TECHNOLOGIES"
    product = "HUAWEI Mobile"
    serial = ""
    bcdDevice = 0000
    speed = "12"
  usb device: name = 5-2:1.3
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3
    modalias = "usb:v12D1p1412d0000dc00dsc00dp00ic08isc06ip50"
    bInterfaceNumber = 3
    bInterfaceClass = 8
    bInterfaceSubClass = 6
    bInterfaceProtocol = 80
    if: 5-2:1.3 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x12d1
    idProduct = 0x1412
    manufacturer = "HUAÿWEI TECHNOLOGIES"
    product = "HUAWEI Mobile"
    serial = ""
    bcdDevice = 0000
    speed = "12"
  usb device: name = 5-2:1.4
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
    modalias = "usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF"
    bInterfaceNumber = 4
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 5-2:1.4 @ /devices/pci0000:00/0000:00:1d.3/usb5/5-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x12d1
    idProduct = 0x1412
    manufacturer = "HUAÿWEI TECHNOLOGIES"
    product = "HUAWEI Mobile"
    serial = ""
    bcdDevice = 0000
    speed = "12"
removed: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
removed: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
removed: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
>> usb.3.1: joydev mod
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> usb.3.3: input
  input: name = input0, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
    no dev - ignored
  input: name = input1, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
    no dev - ignored
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = event0, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0
    dev = 13:64
    input device: bus = acpi, bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  input: name = event1, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
    dev = 13:65
    input device: bus = acpi, bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
  input: name = input2, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
    no dev - ignored
  input: name = event2, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
    dev = 13:66
    input device: bus = usb, bus_id = 2-1:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  input: name = input3, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
    no dev - ignored
  input: name = event3, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
    dev = 13:67
    input device: bus = usb, bus_id = 2-1:1.1 driver = usbhid
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
  input: name = input4, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
    no dev - ignored
  input: name = mouse0, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/mouse0
    dev = 13:32
    input device: bus = usb, bus_id = 2-2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
  input: name = event4, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/event4
    dev = 13:68
    input device: bus = usb, bus_id = 2-2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
>> usb.3.4: lp
sysfs: no such class: usb
>> usb.3.5: serial
  usb: name = ttyUSB0, path = /class/tty/ttyUSB0
    dev = 188:0
    usb device: bus = (null), bus_id = ttyUSB0 driver = option1
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
  usb: name = ttyUSB1, path = /class/tty/ttyUSB1
    dev = 188:1
    usb device: bus = (null), bus_id = ttyUSB1 driver = option1
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
  usb: name = ttyUSB2, path = /class/tty/ttyUSB2
    dev = 188:2
    usb device: bus = (null), bus_id = ttyUSB2 driver = option1
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
  usb: name = ttyUSB3, path = /class/tty/ttyUSB3
    dev = 188:3
    usb device: bus = (null), bus_id = ttyUSB3 driver = option1
      path = /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
----- return code: ? -----
>> edd.2: edd info
******  started child process 2468 (10s/10s)  ******
>> braille.1.1: alva
>> braille.2.1: alva open
>> braille.1.1: fhp_old
>> braille.2.1: fhp open
>> braille.1.1: fhp_el
>> braille.2.1: fhp open
>> braille.1.1: ht
>> braille.2.1: ht open
>> braille.1.1: baum
>> braille.2.1: baum open
>> braille.1.1: fhp new
>> braille.2.1: fhp2 open
******  stopped child process 2468 (11s)  ******
>> modem.1: serial
******  started child process 2469 (15s/120s)  ******
******  stopped child process 2469 (120s)  ******
>> mouse.2: serial
******  started child process 2470 (20s/20s)  ******
******  stopped child process 2470 (20s)  ******
>> input.1: joydev mod
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
  U: Uniq=
  H: Handlers=kbd event0 
  B: PROP=0
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=LNXPWRBN/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  U: Uniq=
  H: Handlers=kbd event1 
  B: PROP=0
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
  N: Name="USB USB Keykoard"
  P: Phys=usb-0000:00:1d.0-1/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
  U: Uniq=
  H: Handlers=sysrq kbd event2 
  B: PROP=0
  B: EV=120013
  B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
  N: Name="USB USB Keykoard"
  P: Phys=usb-0000:00:1d.0-1/input1
  S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
  U: Uniq=
  H: Handlers=kbd event3 
  B: PROP=0
  B: EV=1f
  B: KEY=4837fff 72ff32d bf544446 0 0 1 20c10 b17c000 267bfa d941dfed 9e1680 4400 0 10000002
  B: REL=40
  B: ABS=1 0
  B: MSC=10
  
  I: Bus=0003 Vendor=093a Product=2510 Version=0110
  N: Name="PIXART USB OPTICAL MOUSE"
  P: Phys=usb-0000:00:1d.0-2/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
  U: Uniq=
  H: Handlers=mouse0 event4 
  B: PROP=0
  B: EV=17
  B: KEY=70000 0 0 0 0 0 0 0 0
  B: REL=103
  B: MSC=10
  
----- /proc/bus/input/devices end -----
bus = 25, name = Power Button
  handlers = kbd event0
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event1
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = USB USB Keykoard
  handlers = sysrq kbd event2
  key = 0001000000000007ff800000000007fffebeffdff3cffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = USB USB Keykoard
  handlers = kbd event3
  key = 04837fff072ff32dbf54444600000000000000000000000100020c100b17c00000267bfad941dfed009e1680000044000000000010000002
  rel = 00000040
  abs = 0000000100000000
  mouse buttons = 0
  mouse wheels = 1
bus = 3, name = PIXART USB OPTICAL MOUSE
  handlers = mouse0 event4
  key = 000700000000000000000000000000000000000000000000000000000000000000000000
  rel = 00000103
  mouse buttons = 3
  mouse wheels = 1
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 15
  model		: 3
  model name	: Intel(R) Pentium(R) 4 CPU 2.93GHz
  stepping	: 4
  cpu MHz		: 2932.017
  cache size	: 1024 KB
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
  bogomips	: 5864.03
  clflush size	: 64
  cache_alignment	: 128
  address sizes	: 36 bits physical, 32 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 0
    hw_addr = 00:11:2f:a6:54:ae
    net device: path = /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
    net driver: name = 8139too, path = /bus/pci/drivers/8139too
  net interface: name = ppp0, path = /class/net/ppp0
    type = 512
    carrier = 1
    hw_addr = 
    GDRVINFO ethtool error: Operation not supported
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4.2: /dev/sdb
  read_block0: open(/dev/sdb) failed
>> int.4.3: /dev/sdc
  read_block0: open(/dev/sdc) failed
>> int.4.4: /dev/sdd
  read_block0: open(/dev/sdd) failed
>> int.4.5: /dev/sde
  read_block0: open(/dev/sde) failed
>> int.4.6: /dev/sdf
  read_block0: open(/dev/sdf) failed
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 25
  bios ctrl 1: 20
  bios ctrl 2: 61
>> int.6: mouse
>> int.15: system info
  system type:
  acpi: 1
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /devices/LNXSYSTM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00
  E: MODALIAS=acpi:LNXSYSTM:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
  E: DRIVER=button
  E: MODALIAS=acpi:LNXPWRBN:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="LNXPWRBN/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-LNXPWRBN:00
  E: ID_PATH_TAG=acpi-LNXPWRBN_00
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  N: input/event1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  E: MAJOR=13
  E: MINOR=65
  E: DEVNAME=/dev/input/event1
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-LNXPWRBN:00
  E: ID_PATH_TAG=acpi-LNXPWRBN_00
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us,in
  E: XKBVARIANT=,eng
  E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll
  E: DMI_VENDOR=HP Pavilion 061
  
  P: /devices/LNXSYSTM:00/device:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00
  E: DRIVER=pci_root
  E: MODALIAS=acpi:PNP0A08:PNP0A03:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C01:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C01:00
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:04
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/INT0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/INT0800:00
  E: MODALIAS=acpi:INT0800:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0000:00
  E: MODALIAS=acpi:PNP0000:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0100:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0100:00
  E: MODALIAS=acpi:PNP0100:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0200:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0200:00
  E: MODALIAS=acpi:PNP0200:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0401:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0401:00
  E: MODALIAS=acpi:PNP0401:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0700:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0700:00
  E: MODALIAS=acpi:PNP0700:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0800:00
  E: MODALIAS=acpi:PNP0800:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0B00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0B00:00
  E: MODALIAS=acpi:PNP0B00:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:00
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:01
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:02
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:03
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C04:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C04:00
  E: MODALIAS=acpi:PNP0C04:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:12
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C01:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C01:01
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C02:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C02:05
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0C:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="PNP0C0C/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0C:00
  E: ID_PATH_TAG=acpi-PNP0C0C_00
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0
  N: input/event0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0
  E: MAJOR=13
  E: MINOR=64
  E: DEVNAME=/dev/input/event0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0C:00
  E: ID_PATH_TAG=acpi-PNP0C0C_00
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us,in
  E: XKBVARIANT=,eng
  E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll
  E: DMI_VENDOR=HP Pavilion 061
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:00
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:01
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:02
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:03
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:04
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:05
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:06
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:07
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:17
  E: SUBSYSTEM=acpi
  
  P: /devices/breakpoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/breakpoint
  E: SUBSYSTEM=event_source
  
  P: /devices/cpu
  E: UDEV_LOG=3
  E: DEVPATH=/devices/cpu
  E: SUBSYSTEM=event_source
  
  P: /devices/pci0000:00/0000:00:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:00.0
  E: DRIVER=agpgart-intel
  E: PCI_CLASS=60000
  E: PCI_ID=8086:2580
  E: PCI_SUBSYS_ID=103C:2A08
  E: PCI_SLOT_NAME=0000:00:00.0
  E: MODALIAS=pci:v00008086d00002580sv0000103Csd00002A08bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0
  E: DRIVER=i915
  E: PCI_CLASS=30000
  E: PCI_ID=8086:2582
  E: PCI_SUBSYS_ID=103C:2A08
  E: PCI_SLOT_NAME=0000:00:02.0
  E: MODALIAS=pci:v00008086d00002582sv0000103Csd00002A08bc03sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0
  N: dri/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
  E: MAJOR=226
  E: MINOR=0
  E: DEVNAME=/dev/dri/card0
  E: DEVTYPE=drm_minor
  E: SUBSYSTEM=drm
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/controlD64
  N: dri/controlD64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/controlD64
  E: MAJOR=226
  E: MINOR=64
  E: DEVNAME=/dev/dri/controlD64
  E: DEVTYPE=drm_minor
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/graphics/fb0
  N: fb0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/graphics/fb0
  E: MAJOR=29
  E: MINOR=0
  E: DEVNAME=/dev/fb0
  E: SUBSYSTEM=graphics
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-0
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-1
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-10
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-11
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-12
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-13
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-2
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-3
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-4
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-5
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-6
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-7
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-8
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-9
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1
  E: PCI_CLASS=38000
  E: PCI_ID=8086:2782
  E: PCI_SUBSYS_ID=103C:2A08
  E: PCI_SLOT_NAME=0000:00:02.1
  E: MODALIAS=pci:v00008086d00002782sv0000103Csd00002A08bc03sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
  E: DRIVER=HDA Intel
  E: PCI_CLASS=40300
  E: PCI_ID=8086:2668
  E: PCI_SUBSYS_ID=103C:2A09
  E: PCI_SLOT_NAME=0000:00:1b.0
  E: MODALIAS=pci:v00008086d00002668sv0000103Csd00002A09bc04sc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x2668
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: SOUND_FORM_FACTOR=internal
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  N: snd/hwC0D0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  E: MAJOR=116
  E: MINOR=6
  E: DEVNAME=/dev/snd/hwC0D0
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  E: MAJOR=116
  E: MINOR=5
  E: DEVNAME=/dev/snd/pcmC0D0c
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  E: MAJOR=116
  E: MINOR=4
  E: DEVNAME=/dev/snd/pcmC0D0p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
  N: snd/pcmC0D1p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
  E: MAJOR=116
  E: MINOR=3
  E: DEVNAME=/dev/snd/pcmC0D1p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D2c
  N: snd/pcmC0D2c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D2c
  E: MAJOR=116
  E: MINOR=2
  E: DEVNAME=/dev/snd/pcmC0D2c
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  N: snd/controlC0
  S: snd/by-path/pci-0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  E: MAJOR=116
  E: MINOR=7
  E: DEVNAME=/dev/snd/controlC0
  E: SUBSYSTEM=sound
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/snd/by-path/pci-0000:00:1b.0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1c.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:2660
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1c.0
  E: MODALIAS=pci:v00008086d00002660sv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1d.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2658
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1d.0
  E: MODALIAS=pci:v00008086d00002658sv0000103Csd00002A0Abc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2
  N: bus/usb/002/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2
  E: MAJOR=189
  E: MINOR=128
  E: DEVNAME=/dev/bus/usb/002/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=002
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-12-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-12-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-12-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.0
  E: ID_SERIAL_SHORT=0000:00:1d.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  N: bus/usb/002/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1
  E: MAJOR=189
  E: MINOR=129
  E: DEVNAME=/dev/bus/usb/002/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1c4f/2/110
  E: TYPE=0/0/0
  E: BUSNUM=002
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=USB
  E: ID_VENDOR_ENC=USB
  E: ID_VENDOR_ID=1c4f
  E: ID_MODEL=USB_Keykoard
  E: ID_MODEL_ENC=USB\x20Keykoard
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0110
  E: ID_SERIAL=USB_USB_Keykoard
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=1c4f/2/110
  E: TYPE=0/0/0
  E: INTERFACE=3/1/1
  E: MODALIAS=usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc01ip01
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001
  E: DRIVER=generic-usb
  E: HID_ID=0003:00001C4F:00000002
  E: HID_NAME=USB USB Keykoard
  E: HID_PHYS=usb-0000:00:1d.0-1/input0
  E: SUBSYSTEM=hid
  E: MODALIAS=hid:b0003v00001C4Fp00000002
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001/hidraw/hidraw0
  N: hidraw0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001/hidraw/hidraw0
  E: MAJOR=250
  E: MINOR=0
  E: DEVNAME=/dev/hidraw0
  E: SUBSYSTEM=hidraw
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
  E: PRODUCT=3/1c4f/2/110
  E: NAME="USB USB Keykoard"
  E: PHYS="usb-0000:00:1d.0-1/input0"
  E: UNIQ=""
  E: PROP=0
  E: EV=120013
  E: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
  E: MSC=10
  E: LED=7
  E: MODALIAS=input:b0003v1C4Fp0002e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=USB
  E: ID_VENDOR_ENC=USB
  E: ID_VENDOR_ID=1c4f
  E: ID_MODEL=USB_Keykoard
  E: ID_MODEL_ENC=USB\x20Keykoard
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0110
  E: ID_SERIAL=USB_USB_Keykoard
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_1_0
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
  N: input/event2
  S: input/by-id/usb-USB_USB_Keykoard-event-kbd
  S: input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
  E: MAJOR=13
  E: MINOR=66
  E: DEVNAME=/dev/input/event2
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=USB
  E: ID_VENDOR_ENC=USB
  E: ID_VENDOR_ID=1c4f
  E: ID_MODEL=USB_Keykoard
  E: ID_MODEL_ENC=USB\x20Keykoard
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0110
  E: ID_SERIAL=USB_USB_Keykoard
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_1_0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us,in
  E: XKBVARIANT=,eng
  E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll
  E: DEVLINKS=/dev/input/by-id/usb-USB_USB_Keykoard-event-kbd /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=1c4f/2/110
  E: TYPE=0/0/0
  E: INTERFACE=3/0/0
  E: MODALIAS=usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002
  E: DRIVER=generic-usb
  E: HID_ID=0003:00001C4F:00000002
  E: HID_NAME=USB USB Keykoard
  E: HID_PHYS=usb-0000:00:1d.0-1/input1
  E: SUBSYSTEM=hid
  E: MODALIAS=hid:b0003v00001C4Fp00000002
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002/hidraw/hidraw1
  N: hidraw1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002/hidraw/hidraw1
  E: MAJOR=250
  E: MINOR=1
  E: DEVNAME=/dev/hidraw1
  E: SUBSYSTEM=hidraw
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
  E: PRODUCT=3/1c4f/2/110
  E: NAME="USB USB Keykoard"
  E: PHYS="usb-0000:00:1d.0-1/input1"
  E: UNIQ=""
  E: PROP=0
  E: EV=1f
  E: KEY=4837fff 72ff32d bf544446 0 0 1 20c10 b17c000 267bfa d941dfed 9e1680 4400 0 10000002
  E: REL=40
  E: ABS=1 0
  E: MSC=10
  E: MODALIAS=input:b0003v1C4Fp0002e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D4,D8,D9,DB,E4,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=USB
  E: ID_VENDOR_ENC=USB
  E: ID_VENDOR_ID=1c4f
  E: ID_MODEL=USB_Keykoard
  E: ID_MODEL_ENC=USB\x20Keykoard
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0110
  E: ID_SERIAL=USB_USB_Keykoard
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=01
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.1
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_1_1
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
  N: input/event3
  S: input/by-id/usb-USB_USB_Keykoard-event-if01
  S: input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
  E: MAJOR=13
  E: MINOR=67
  E: DEVNAME=/dev/input/event3
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=USB
  E: ID_VENDOR_ENC=USB
  E: ID_VENDOR_ID=1c4f
  E: ID_MODEL=USB_Keykoard
  E: ID_MODEL_ENC=USB\x20Keykoard
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0110
  E: ID_SERIAL=USB_USB_Keykoard
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=01
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.1
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_1_1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us,in
  E: XKBVARIANT=,eng
  E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll
  E: DEVLINKS=/dev/input/by-id/usb-USB_USB_Keykoard-event-if01 /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2
  N: bus/usb/002/003
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2
  E: MAJOR=189
  E: MINOR=130
  E: DEVNAME=/dev/bus/usb/002/003
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=93a/2510/100
  E: TYPE=0/0/0
  E: BUSNUM=002
  E: DEVNUM=003
  E: SUBSYSTEM=usb
  E: ID_VENDOR=PIXART
  E: ID_VENDOR_ENC=PIXART
  E: ID_VENDOR_ID=093a
  E: ID_MODEL=USB_OPTICAL_MOUSE
  E: ID_MODEL_ENC=USB\x20OPTICAL\x20MOUSE
  E: ID_MODEL_ID=2510
  E: ID_REVISION=0100
  E: ID_SERIAL=PIXART_USB_OPTICAL_MOUSE
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=93a/2510/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/2
  E: MODALIAS=usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000093A:00002510
  E: HID_NAME=PIXART USB OPTICAL MOUSE
  E: HID_PHYS=usb-0000:00:1d.0-2/input0
  E: SUBSYSTEM=hid
  E: MODALIAS=hid:b0003v0000093Ap00002510
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003/hidraw/hidraw2
  N: hidraw2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003/hidraw/hidraw2
  E: MAJOR=250
  E: MINOR=2
  E: DEVNAME=/dev/hidraw2
  E: SUBSYSTEM=hidraw
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
  E: PRODUCT=3/93a/2510/110
  E: NAME="PIXART USB OPTICAL MOUSE"
  E: PHYS="usb-0000:00:1d.0-2/input0"
  E: UNIQ=""
  E: PROP=0
  E: EV=17
  E: KEY=70000 0 0 0 0 0 0 0 0
  E: REL=103
  E: MSC=10
  E: MODALIAS=input:b0003v093Ap2510e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=PIXART
  E: ID_VENDOR_ENC=PIXART
  E: ID_VENDOR_ID=093a
  E: ID_MODEL=USB_OPTICAL_MOUSE
  E: ID_MODEL_ENC=USB\x20OPTICAL\x20MOUSE
  E: ID_MODEL_ID=2510
  E: ID_REVISION=0100
  E: ID_SERIAL=PIXART_USB_OPTICAL_MOUSE
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:2:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_2_1_0
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/event4
  N: input/event4
  S: input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-event-mouse
  S: input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/event4
  E: MAJOR=13
  E: MINOR=68
  E: DEVNAME=/dev/input/event4
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=PIXART
  E: ID_VENDOR_ENC=PIXART
  E: ID_VENDOR_ID=093a
  E: ID_MODEL=USB_OPTICAL_MOUSE
  E: ID_MODEL_ENC=USB\x20OPTICAL\x20MOUSE
  E: ID_MODEL_ID=2510
  E: ID_REVISION=0100
  E: ID_SERIAL=PIXART_USB_OPTICAL_MOUSE
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:2:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_2_1_0
  E: DEVLINKS=/dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-event-mouse /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/mouse0
  N: input/mouse0
  S: input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-mouse
  S: input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/mouse0
  E: MAJOR=13
  E: MINOR=32
  E: DEVNAME=/dev/input/mouse0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=PIXART
  E: ID_VENDOR_ENC=PIXART
  E: ID_VENDOR_ID=093a
  E: ID_MODEL=USB_OPTICAL_MOUSE
  E: ID_MODEL_ENC=USB\x20OPTICAL\x20MOUSE
  E: ID_MODEL_ID=2510
  E: ID_REVISION=0100
  E: ID_SERIAL=PIXART_USB_OPTICAL_MOUSE
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1d.0-usb-0:2:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_2_1_0
  E: DEVLINKS=/dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-mouse /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-mouse
  
  P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  N: usbmon2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  E: MAJOR=252
  E: MINOR=2
  E: DEVNAME=/dev/usbmon2
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2659
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1d.1
  E: MODALIAS=pci:v00008086d00002659sv0000103Csd00002A0Abc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.1/usb3
  N: bus/usb/003/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb3
  E: MAJOR=189
  E: MINOR=256
  E: DEVNAME=/dev/bus/usb/003/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=003
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-12-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-12-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-12-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.1
  E: ID_SERIAL_SHORT=0000:00:1d.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  N: usbmon3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  E: MAJOR=252
  E: MINOR=3
  E: DEVNAME=/dev/usbmon3
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:265A
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1d.2
  E: MODALIAS=pci:v00008086d0000265Asv0000103Csd00002A0Abc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.2/usb4
  N: bus/usb/004/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb4
  E: MAJOR=189
  E: MINOR=384
  E: DEVNAME=/dev/bus/usb/004/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=004
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-12-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-12-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-12-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.2
  E: ID_SERIAL_SHORT=0000:00:1d.2
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  N: usbmon4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  E: MAJOR=252
  E: MINOR=4
  E: DEVNAME=/dev/usbmon4
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:265B
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1d.3
  E: MODALIAS=pci:v00008086d0000265Bsv0000103Csd00002A0Abc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5
  N: bus/usb/005/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5
  E: MAJOR=189
  E: MINOR=512
  E: DEVNAME=/dev/bus/usb/005/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=005
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-12-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-12-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-12-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.3
  E: ID_SERIAL_SHORT=0000:00:1d.3
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1
  N: bus/usb/005/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1
  E: MAJOR=189
  E: MINOR=513
  E: DEVNAME=/dev/bus/usb/005/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=58f/9360/100
  E: TYPE=0/0/0
  E: BUSNUM=005
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR_ENC=\x20
  E: ID_VENDOR_ID=058f
  E: ID_MODEL=USB_Reader
  E: ID_MODEL_ENC=USB\x20Reader
  E: ID_MODEL_ID=9360
  E: ID_REVISION=0100
  E: ID_SERIAL=_USB_Reader_9205291
  E: ID_SERIAL_SHORT=9205291
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usb-storage
  E: PRODUCT=58f/9360/100
  E: TYPE=0/0/0
  E: INTERFACE=8/6/80
  E: MODALIAS=usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/scsi_host/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/scsi_host/host4
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/block/sdb
  N: sdb
  S: disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0
  S: disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/block/sdb
  E: MAJOR=8
  E: MINOR=16
  E: DEVNAME=/dev/sdb
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_VENDOR=Generic
  E: ID_VENDOR_ENC=Generic\x20
  E: ID_VENDOR_ID=058f
  E: ID_MODEL=USB_SD_Reader
  E: ID_MODEL_ENC=USB\x20SD\x20Reader\x20\x20\x20
  E: ID_MODEL_ID=9360
  E: ID_REVISION=1.00
  E: ID_SERIAL=Generic_USB_SD_Reader_9205291-0:0
  E: ID_SERIAL_SHORT=9205291
  E: ID_TYPE=disk
  E: ID_INSTANCE=0:0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_1_1_0-scsi-0_0_0_0
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: ID_DRIVE_FLASH_SD=1
  E: DEVLINKS=/dev/disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0
  N: bsg/4:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0
  E: MAJOR=253
  E: MINOR=2
  E: DEVNAME=/dev/bsg/4:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2
  N: sg2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2
  E: MAJOR=21
  E: MINOR=2
  E: DEVNAME=/dev/sg2
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/block/sdc
  N: sdc
  S: disk/by-id/usb-Generic_USB_CF_Reader_9205291-0:1
  S: disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/block/sdc
  E: MAJOR=8
  E: MINOR=32
  E: DEVNAME=/dev/sdc
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_VENDOR=Generic
  E: ID_VENDOR_ENC=Generic\x20
  E: ID_VENDOR_ID=058f
  E: ID_MODEL=USB_CF_Reader
  E: ID_MODEL_ENC=USB\x20CF\x20Reader\x20\x20\x20
  E: ID_MODEL_ID=9360
  E: ID_REVISION=1.01
  E: ID_SERIAL=Generic_USB_CF_Reader_9205291-0:1
  E: ID_SERIAL_SHORT=9205291
  E: ID_TYPE=disk
  E: ID_INSTANCE=0:1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_1_1_0-scsi-0_0_0_1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: ID_DRIVE_FLASH_CF=1
  E: DEVLINKS=/dev/disk/by-id/usb-Generic_USB_CF_Reader_9205291-0:1 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/bsg/4:0:0:1
  N: bsg/4:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/bsg/4:0:0:1
  E: MAJOR=253
  E: MINOR=3
  E: DEVNAME=/dev/bsg/4:0:0:1
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_device/4:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_device/4:0:0:1
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_disk/4:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_disk/4:0:0:1
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_generic/sg3
  N: sg3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_generic/sg3
  E: MAJOR=21
  E: MINOR=3
  E: DEVNAME=/dev/sg3
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/block/sdd
  N: sdd
  S: disk/by-id/usb-Generic_USB_SM_Reader_9205291-0:2
  S: disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/block/sdd
  E: MAJOR=8
  E: MINOR=48
  E: DEVNAME=/dev/sdd
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_VENDOR=Generic
  E: ID_VENDOR_ENC=Generic\x20
  E: ID_VENDOR_ID=058f
  E: ID_MODEL=USB_SM_Reader
  E: ID_MODEL_ENC=USB\x20SM\x20Reader\x20\x20\x20
  E: ID_MODEL_ID=9360
  E: ID_REVISION=1.02
  E: ID_SERIAL=Generic_USB_SM_Reader_9205291-0:2
  E: ID_SERIAL_SHORT=9205291
  E: ID_TYPE=disk
  E: ID_INSTANCE=0:2
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_1_1_0-scsi-0_0_0_2
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: ID_DRIVE_FLASH_SM=1
  E: DEVLINKS=/dev/disk/by-id/usb-Generic_USB_SM_Reader_9205291-0:2 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/bsg/4:0:0:2
  N: bsg/4:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/bsg/4:0:0:2
  E: MAJOR=253
  E: MINOR=4
  E: DEVNAME=/dev/bsg/4:0:0:2
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_device/4:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_device/4:0:0:2
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_disk/4:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_disk/4:0:0:2
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_generic/sg4
  N: sg4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_generic/sg4
  E: MAJOR=21
  E: MINOR=4
  E: DEVNAME=/dev/sg4
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/block/sde
  N: sde
  S: disk/by-id/usb-Generic_USB_MS_Reader_9205291-0:3
  S: disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/block/sde
  E: MAJOR=8
  E: MINOR=64
  E: DEVNAME=/dev/sde
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_VENDOR=Generic
  E: ID_VENDOR_ENC=Generic\x20
  E: ID_VENDOR_ID=058f
  E: ID_MODEL=USB_MS_Reader
  E: ID_MODEL_ENC=USB\x20MS\x20Reader\x20\x20\x20
  E: ID_MODEL_ID=9360
  E: ID_REVISION=1.03
  E: ID_SERIAL=Generic_USB_MS_Reader_9205291-0:3
  E: ID_SERIAL_SHORT=9205291
  E: ID_TYPE=disk
  E: ID_INSTANCE=0:3
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_1_1_0-scsi-0_0_0_3
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: ID_DRIVE_FLASH_MS=1
  E: DEVLINKS=/dev/disk/by-id/usb-Generic_USB_MS_Reader_9205291-0:3 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/bsg/4:0:0:3
  N: bsg/4:0:0:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/bsg/4:0:0:3
  E: MAJOR=253
  E: MINOR=5
  E: DEVNAME=/dev/bsg/4:0:0:3
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_device/4:0:0:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_device/4:0:0:3
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_disk/4:0:0:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_disk/4:0:0:3
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_generic/sg5
  N: sg5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_generic/sg5
  E: MAJOR=21
  E: MINOR=5
  E: DEVNAME=/dev/sg5
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2
  N: bus/usb/005/004
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2
  E: MAJOR=189
  E: MINOR=515
  E: DEVNAME=/dev/bus/usb/005/004
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: BUSNUM=005
  E: DEVNUM=004
  E: SUBSYSTEM=usb
  E: ID_VENDOR=HUAÿWEI_TECHNOLOGIES
  E: ID_VENDOR_ENC=HUAÿWEI\x20TECHNOLOGIES
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=HUAWEI_Mobile
  E: ID_MODEL_ENC=HUAWEI\x20Mobile
  E: ID_MODEL_ID=1412
  E: ID_REVISION=0000
  E: ID_SERIAL=HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=option
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0
  E: DRIVER=option1
  E: SUBSYSTEM=usb-serial
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0/tty/ttyUSB0
  N: ttyUSB0
  S: serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0
  S: serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0/tty/ttyUSB0
  E: MAJOR=188
  E: MINOR=0
  E: DEVNAME=/dev/ttyUSB0
  E: SUBSYSTEM=tty
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.0
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_0
  E: ID_VENDOR=HUAÿWEI_TECHNOLOGIES
  E: ID_VENDOR_ENC=HUAÿWEI\x20TECHNOLOGIES
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=HUAWEI_Mobile
  E: ID_MODEL_ENC=HUAWEI\x20Mobile
  E: ID_MODEL_ID=1412
  E: ID_REVISION=0000
  E: ID_SERIAL=HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=generic
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=option
  E: ID_VENDOR_FROM_DATABASE=Huawei Technologies Co., Ltd.
  E: ID_MM_CANDIDATE=1
  E: DEVLINKS=/dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=option
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1
  E: DRIVER=option1
  E: SUBSYSTEM=usb-serial
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1/tty/ttyUSB1
  N: ttyUSB1
  S: serial/by-path/pci-0000:00:1d.3-usb-0:2:1.1-port0
  S: serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1/tty/ttyUSB1
  E: MAJOR=188
  E: MINOR=1
  E: DEVNAME=/dev/ttyUSB1
  E: SUBSYSTEM=tty
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.1
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_1
  E: ID_VENDOR=HUAÿWEI_TECHNOLOGIES
  E: ID_VENDOR_ENC=HUAÿWEI\x20TECHNOLOGIES
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=HUAWEI_Mobile
  E: ID_MODEL_ENC=HUAWEI\x20Mobile
  E: ID_MODEL_ID=1412
  E: ID_REVISION=0000
  E: ID_SERIAL=HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=generic
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=01
  E: ID_USB_DRIVER=option
  E: ID_VENDOR_FROM_DATABASE=Huawei Technologies Co., Ltd.
  E: ID_MM_CANDIDATE=1
  E: DEVLINKS=/dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.1-port0 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
  E: DEVTYPE=usb_interface
  E: DRIVER=option
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2
  E: DRIVER=option1
  E: SUBSYSTEM=usb-serial
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2/tty/ttyUSB2
  N: ttyUSB2
  S: serial/by-path/pci-0000:00:1d.3-usb-0:2:1.2-port0
  S: serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2/tty/ttyUSB2
  E: MAJOR=188
  E: MINOR=2
  E: DEVNAME=/dev/ttyUSB2
  E: SUBSYSTEM=tty
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.2
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_2
  E: ID_VENDOR=HUAÿWEI_TECHNOLOGIES
  E: ID_VENDOR_ENC=HUAÿWEI\x20TECHNOLOGIES
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=HUAWEI_Mobile
  E: ID_MODEL_ENC=HUAWEI\x20Mobile
  E: ID_MODEL_ID=1412
  E: ID_REVISION=0000
  E: ID_SERIAL=HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=generic
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=02
  E: ID_USB_DRIVER=option
  E: ID_VENDOR_FROM_DATABASE=Huawei Technologies Co., Ltd.
  E: ID_MM_CANDIDATE=1
  E: DEVLINKS=/dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.2-port0 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3
  E: DEVTYPE=usb_interface
  E: DRIVER=usb-storage
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: INTERFACE=8/6/80
  E: MODALIAS=usb:v12D1p1412d0000dc00dsc00dp00ic08isc06ip50
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/scsi_host/host9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/scsi_host/host9
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/block/sr1
  N: sr1
  S: scd1
  S: disk/by-id/usb-HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:0
  S: disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:0
  S: cdrom1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/block/sr1
  E: MAJOR=11
  E: MINOR=1
  E: DEVNAME=/dev/sr1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_MEDIA=1
  E: ID_VENDOR=HUAWEI
  E: ID_VENDOR_ENC=HUAWEI\x20\x20
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=Mass_Storage
  E: ID_MODEL_ENC=Mass\x20Storage\x20\x20\x20\x20
  E: ID_MODEL_ID=1412
  E: ID_REVISION=2.31
  E: ID_SERIAL=HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:0
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=cd
  E: ID_INSTANCE=0:0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=03
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_3-scsi-0_0_0_0
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/scd1 /dev/disk/by-id/usb-HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:0 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:0 /dev/cdrom1
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/bsg/9:0:0:0
  N: bsg/9:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/bsg/9:0:0:0
  E: MAJOR=253
  E: MINOR=6
  E: DEVNAME=/dev/bsg/9:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_device/9:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_device/9:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_generic/sg6
  N: sg6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_generic/sg6
  E: MAJOR=21
  E: MINOR=6
  E: DEVNAME=/dev/sg6
  E: SUBSYSTEM=scsi_generic
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/block/sdf
  N: sdf
  S: disk/by-id/usb-HUAWEI_SD_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:1
  S: disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/block/sdf
  E: MAJOR=8
  E: MINOR=80
  E: DEVNAME=/dev/sdf
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_VENDOR=HUAWEI
  E: ID_VENDOR_ENC=HUAWEI\x20\x20
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=SD_Storage
  E: ID_MODEL_ENC=SD\x20Storage\x20\x20\x20\x20\x20\x20
  E: ID_MODEL_ID=1412
  E: ID_REVISION=2.31
  E: ID_SERIAL=HUAWEI_SD_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:1
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=disk
  E: ID_INSTANCE=0:1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=03
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:1
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_3-scsi-0_0_0_1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/disk/by-id/usb-HUAWEI_SD_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:1 /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:1
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/bsg/9:0:0:1
  N: bsg/9:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/bsg/9:0:0:1
  E: MAJOR=253
  E: MINOR=7
  E: DEVNAME=/dev/bsg/9:0:0:1
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_device/9:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_device/9:0:0:1
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_disk/9:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_disk/9:0:0:1
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_generic/sg7
  N: sg7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_generic/sg7
  E: MAJOR=21
  E: MINOR=7
  E: DEVNAME=/dev/sg7
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
  E: DEVTYPE=usb_interface
  E: DRIVER=option
  E: PRODUCT=12d1/1412/0
  E: TYPE=0/0/0
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3
  E: DRIVER=option1
  E: SUBSYSTEM=usb-serial
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3/tty/ttyUSB3
  N: ttyUSB3
  S: serial/by-path/pci-0000:00:1d.3-usb-0:2:1.4-port0
  S: serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if04-port0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3/tty/ttyUSB3
  E: MAJOR=188
  E: MINOR=3
  E: DEVNAME=/dev/ttyUSB3
  E: SUBSYSTEM=tty
  E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.4
  E: ID_PATH_TAG=pci-0000_00_1d_3-usb-0_2_1_4
  E: ID_VENDOR=HUAÿWEI_TECHNOLOGIES
  E: ID_VENDOR_ENC=HUAÿWEI\x20TECHNOLOGIES
  E: ID_VENDOR_ID=12d1
  E: ID_MODEL=HUAWEI_Mobile
  E: ID_MODEL_ENC=HUAWEI\x20Mobile
  E: ID_MODEL_ID=1412
  E: ID_REVISION=0000
  E: ID_SERIAL=HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_SERIAL_SHORT=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
  E: ID_TYPE=generic
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:080650:
  E: ID_USB_INTERFACE_NUM=04
  E: ID_USB_DRIVER=option
  E: ID_VENDOR_FROM_DATABASE=Huawei Technologies Co., Ltd.
  E: ID_MM_CANDIDATE=1
  E: DEVLINKS=/dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.4-port0 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if04-port0
  
  P: /devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  N: usbmon5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  E: MAJOR=252
  E: MINOR=5
  E: DEVNAME=/dev/usbmon5
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:265C
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1d.7
  E: MODALIAS=pci:v00008086d0000265Csv0000103Csd00002A0Abc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1
  N: bus/usb/001/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1
  E: MAJOR=189
  E: MINOR=0
  E: DEVNAME=/dev/bus/usb/001/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: BUSNUM=001
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-12-generic_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-12-generic\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-12-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1d.7
  E: ID_SERIAL_SHORT=0000:00:1d.7
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  N: usbmon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  E: MAJOR=252
  E: MINOR=1
  E: DEVNAME=/dev/usbmon1
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1e.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0
  E: PCI_CLASS=60401
  E: PCI_ID=8086:244E
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1e.0
  E: MODALIAS=pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:02:01.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:02:01.0
  E: DRIVER=firewire_ohci
  E: PCI_CLASS=C0010
  E: PCI_ID=1106:3044
  E: PCI_SUBSYS_ID=103C:2A0C
  E: PCI_SLOT_NAME=0000:02:01.0
  E: MODALIAS=pci:v00001106d00003044sv0000103Csd00002A0Cbc0Csc00i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/fw0
  N: fw0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/fw0
  E: MAJOR=251
  E: MINOR=0
  E: DEVNAME=/dev/fw0
  E: SUBSYSTEM=firewire
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:02:02.0
  E: DRIVER=8139too
  E: PCI_CLASS=20000
  E: PCI_ID=10EC:8139
  E: PCI_SUBSYS_ID=103C:2A0B
  E: PCI_SLOT_NAME=0000:02:02.0
  E: MODALIAS=pci:v000010ECd00008139sv0000103Csd00002A0Bbc02sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth0
  E: INTERFACE=eth0
  E: IFINDEX=2
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Realtek Semiconductor Co., Ltd.
  E: ID_MODEL_FROM_DATABASE=RTL-8139/8139C/8139C+
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x10ec
  E: ID_MODEL_ID=0x8139
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:02:05.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:02:05.0
  E: PCI_CLASS=78000
  E: PCI_ID=11C1:048C
  E: PCI_SUBSYS_ID=11C1:044C
  E: PCI_SLOT_NAME=0000:02:05.0
  E: MODALIAS=pci:v000011C1d0000048Csv000011C1sd0000044Cbc07sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/pci_bus/0000:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:02
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1f.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
  E: PCI_CLASS=60100
  E: PCI_ID=8086:2640
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1f.0
  E: MODALIAS=pci:v00008086d00002640sv0000103Csd00002A0Abc06sc01i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1f.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1
  E: DRIVER=ata_piix
  E: PCI_CLASS=1018A
  E: PCI_ID=8086:266F
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1f.1
  E: MODALIAS=pci:v00008086d0000266Fsv0000103Csd00002A0Abc01sc01i8a
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
  
  P: /devices/pci0000:00/0000:00:1f.1/ata1/ata_port/ata1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata1/ata_port/ata1
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.1/ata1/link1/ata_link/link1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata1/link1/ata_link/link1
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.0/ata_device/dev1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.0/ata_device/dev1.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.1/ata_device/dev1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.1/ata_device/dev1.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.1/ata2/ata_port/ata2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata2/ata_port/ata2
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.1/ata2/link2/ata_link/link2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata2/link2/ata_link/link2
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.0/ata_device/dev2.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.0/ata_device/dev2.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.1/ata_device/dev2.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.1/ata_device/dev2.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.1/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/scsi_host/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/scsi_host/host0
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/block/sr0
  N: sr0
  S: scd0
  S: disk/by-id/ata-SONY_DVD_RW_AW-G170A
  S: disk/by-path/pci-0000:00:1f.1-scsi-0:0:1:0
  S: cdrom
  S: cdrw
  S: dvd
  S: dvdrw
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/block/sr0
  E: MAJOR=11
  E: MINOR=0
  E: DEVNAME=/dev/sr0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_CD=1
  E: ID_CDROM_CD_R=1
  E: ID_CDROM_CD_RW=1
  E: ID_CDROM_DVD=1
  E: ID_CDROM_DVD_R=1
  E: ID_CDROM_DVD_RW=1
  E: ID_CDROM_DVD_RAM=1
  E: ID_CDROM_DVD_PLUS_R=1
  E: ID_CDROM_DVD_PLUS_RW=1
  E: ID_CDROM_DVD_PLUS_R_DL=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_ATA=1
  E: ID_TYPE=cd
  E: ID_BUS=ata
  E: ID_MODEL=SONY_DVD_RW_AW-G170A
  E: ID_MODEL_ENC=SONY\x20\x20\x20\x20DVD\x20RW\x20AW-G170A\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=1.75
  E: ID_SERIAL=SONY_DVD_RW_AW-G170A
  E: ID_PATH=pci-0000:00:1f.1-scsi-0:0:1:0
  E: ID_PATH_TAG=pci-0000_00_1f_1-scsi-0_0_1_0
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/scd0 /dev/disk/by-id/ata-SONY_DVD_RW_AW-G170A /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:1:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/bsg/0:0:1:0
  N: bsg/0:0:1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/bsg/0:0:1:0
  E: MAJOR=253
  E: MINOR=0
  E: DEVNAME=/dev/bsg/0:0:1:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_device/0:0:1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_device/0:0:1:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_generic/sg0
  N: sg0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_generic/sg0
  E: MAJOR=21
  E: MINOR=0
  E: DEVNAME=/dev/sg0
  E: SUBSYSTEM=scsi_generic
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1f.1/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host1
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.1/host1/scsi_host/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.1/host1/scsi_host/host1
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
  E: DRIVER=ata_piix
  E: PCI_CLASS=1018F
  E: PCI_ID=8086:2651
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1f.2
  E: MODALIAS=pci:v00008086d00002651sv0000103Csd00002A0Abc01sc01i8f
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=82801FB/FW (ICH6/ICH6W) SATA Controller
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.1/ata_device/dev3.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.1/ata_device/dev3.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.1/ata_device/dev4.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.1/ata_device/dev4.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  N: sda
  S: disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835
  S: disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  E: MAJOR=8
  E: MINOR=0
  E: DEVNAME=/dev/sda
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD800JD-22JNA0
  E: ID_MODEL_ENC=WDC\x20WD800JD-22JNA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=05.01C50
  E: ID_SERIAL=WDC_WD800JD-22JNA0_WD-WMAM91950835
  E: ID_SERIAL_SHORT=WD-WMAM91950835
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=0
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_SCSI_COMPAT=SATA_WDC_WD800JD-22JWD-WMAM91950835
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=3
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835 /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda1
  N: sda1
  S: disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part1
  S: disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part1
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
  S: disk/by-uuid/ececbda8-912d-4c7c-9065-122f7942b6b0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda1
  E: MAJOR=8
  E: MINOR=1
  E: DEVNAME=/dev/sda1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD800JD-22JNA0
  E: ID_MODEL_ENC=WDC\x20WD800JD-22JNA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=05.01C50
  E: ID_SERIAL=WDC_WD800JD-22JNA0_WD-WMAM91950835
  E: ID_SERIAL_SHORT=WD-WMAM91950835
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=0
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_SCSI_COMPAT=SATA_WDC_WD800JD-22JWD-WMAM91950835
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=ececbda8-912d-4c7c-9065-122f7942b6b0
  E: ID_FS_UUID_ENC=ececbda8-912d-4c7c-9065-122f7942b6b0
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext4
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x83
  E: ID_PART_ENTRY_FLAGS=0x80
  E: ID_PART_ENTRY_NUMBER=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=78692483072
  E: UDISKS_PARTITION_FLAGS=boot
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part1 /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 /dev/disk/by-uuid/ececbda8-912d-4c7c-9065-122f7942b6b0
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda2
  N: sda2
  S: disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part2
  S: disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part2
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda2
  E: MAJOR=8
  E: MINOR=2
  E: DEVNAME=/dev/sda2
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD800JD-22JNA0
  E: ID_MODEL_ENC=WDC\x20WD800JD-22JNA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=05.01C50
  E: ID_SERIAL=WDC_WD800JD-22JNA0_WD-WMAM91950835
  E: ID_SERIAL_SHORT=WD-WMAM91950835
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=0
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_SCSI_COMPAT=SATA_WDC_WD800JD-22JWD-WMAM91950835
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x5
  E: ID_PART_ENTRY_NUMBER=2
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=2
  E: UDISKS_PARTITION_TYPE=0x05
  E: UDISKS_PARTITION_SIZE=1331692544
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=78694579200
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part2 /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda5
  N: sda5
  S: disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part5
  S: disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part5
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
  S: disk/by-uuid/cd20ec63-2c4c-48b5-beeb-8f441259208a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda5
  E: MAJOR=8
  E: MINOR=5
  E: DEVNAME=/dev/sda5
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD800JD-22JNA0
  E: ID_MODEL_ENC=WDC\x20WD800JD-22JNA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=05.01C50
  E: ID_SERIAL=WDC_WD800JD-22JNA0_WD-WMAM91950835
  E: ID_SERIAL_SHORT=WD-WMAM91950835
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=0
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_SCSI_COMPAT=SATA_WDC_WD800JD-22JWD-WMAM91950835
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=cd20ec63-2c4c-48b5-beeb-8f441259208a
  E: ID_FS_UUID_ENC=cd20ec63-2c4c-48b5-beeb-8f441259208a
  E: ID_FS_VERSION=2
  E: ID_FS_TYPE=swap
  E: ID_FS_USAGE=other
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x82
  E: ID_PART_ENTRY_NUMBER=5
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=5
  E: UDISKS_PARTITION_TYPE=0x82
  E: UDISKS_PARTITION_SIZE=1331691520
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=78694580224
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part5 /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5 /dev/disk/by-uuid/cd20ec63-2c4c-48b5-beeb-8f441259208a
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  N: bsg/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  E: MAJOR=253
  E: MINOR=1
  E: DEVNAME=/dev/bsg/2:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  N: sg1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  E: MAJOR=21
  E: MINOR=1
  E: DEVNAME=/dev/sg1
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1f.2/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
  E: PCI_CLASS=C0500
  E: PCI_ID=8086:266A
  E: PCI_SUBSYS_ID=103C:2A0A
  E: PCI_SLOT_NAME=0000:00:1f.3
  E: MODALIAS=pci:v00008086d0000266Asv0000103Csd00002A0Abc0Csc05i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/pci_bus/0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
  E: SUBSYSTEM=pci_bus
  
  P: /devices/platform/Fixed MDIO bus.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0
  E: MODALIAS=platform:Fixed MDIO bus
  E: SUBSYSTEM=platform
  
  P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: SUBSYSTEM=mdio_bus
  
  P: /devices/platform/alarmtimer
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/alarmtimer
  E: DRIVER=alarmtimer
  E: MODALIAS=platform:alarmtimer
  E: SUBSYSTEM=platform
  
  P: /devices/platform/eisa.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/eisa.0
  E: MODALIAS=platform:eisa
  E: SUBSYSTEM=platform
  
  P: /devices/platform/floppy.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/floppy.0
  E: DRIVER=floppy
  E: MODALIAS=platform:floppy
  E: SUBSYSTEM=platform
  
  P: /devices/platform/floppy.0/block/fd0
  N: fd0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/floppy.0/block/fd0
  E: MAJOR=2
  E: MINOR=0
  E: DEVNAME=/dev/fd0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: ID_DRIVE_FLOPPY=1
  
  P: /devices/platform/i8042
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042
  E: DRIVER=i8042
  E: MODALIAS=platform:i8042
  E: SUBSYSTEM=platform
  
  P: /devices/platform/i8042/serio0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0
  E: SERIO_TYPE=06
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty06pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/i8042/serio1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1
  E: SERIO_TYPE=01
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty01pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/pcspkr
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/pcspkr
  E: MODALIAS=platform:pcspkr
  E: SUBSYSTEM=platform
  
  P: /devices/platform/reg-dummy
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/reg-dummy
  E: MODALIAS=platform:reg-dummy
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250
  E: DRIVER=serial8250
  E: MODALIAS=platform:serial8250
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250/tty/ttyS0
  N: ttyS0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
  E: MAJOR=4
  E: MINOR=64
  E: DEVNAME=/dev/ttyS0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS1
  N: ttyS1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
  E: MAJOR=4
  E: MINOR=65
  E: DEVNAME=/dev/ttyS1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS10
  N: ttyS10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS10
  E: MAJOR=4
  E: MINOR=74
  E: DEVNAME=/dev/ttyS10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS11
  N: ttyS11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS11
  E: MAJOR=4
  E: MINOR=75
  E: DEVNAME=/dev/ttyS11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS12
  N: ttyS12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS12
  E: MAJOR=4
  E: MINOR=76
  E: DEVNAME=/dev/ttyS12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS13
  N: ttyS13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS13
  E: MAJOR=4
  E: MINOR=77
  E: DEVNAME=/dev/ttyS13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS14
  N: ttyS14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS14
  E: MAJOR=4
  E: MINOR=78
  E: DEVNAME=/dev/ttyS14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS15
  N: ttyS15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS15
  E: MAJOR=4
  E: MINOR=79
  E: DEVNAME=/dev/ttyS15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS16
  N: ttyS16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS16
  E: MAJOR=4
  E: MINOR=80
  E: DEVNAME=/dev/ttyS16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS17
  N: ttyS17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS17
  E: MAJOR=4
  E: MINOR=81
  E: DEVNAME=/dev/ttyS17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS18
  N: ttyS18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS18
  E: MAJOR=4
  E: MINOR=82
  E: DEVNAME=/dev/ttyS18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS19
  N: ttyS19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS19
  E: MAJOR=4
  E: MINOR=83
  E: DEVNAME=/dev/ttyS19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS2
  N: ttyS2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
  E: MAJOR=4
  E: MINOR=66
  E: DEVNAME=/dev/ttyS2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS20
  N: ttyS20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS20
  E: MAJOR=4
  E: MINOR=84
  E: DEVNAME=/dev/ttyS20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS21
  N: ttyS21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS21
  E: MAJOR=4
  E: MINOR=85
  E: DEVNAME=/dev/ttyS21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS22
  N: ttyS22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS22
  E: MAJOR=4
  E: MINOR=86
  E: DEVNAME=/dev/ttyS22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS23
  N: ttyS23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS23
  E: MAJOR=4
  E: MINOR=87
  E: DEVNAME=/dev/ttyS23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS24
  N: ttyS24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS24
  E: MAJOR=4
  E: MINOR=88
  E: DEVNAME=/dev/ttyS24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS25
  N: ttyS25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS25
  E: MAJOR=4
  E: MINOR=89
  E: DEVNAME=/dev/ttyS25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS26
  N: ttyS26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS26
  E: MAJOR=4
  E: MINOR=90
  E: DEVNAME=/dev/ttyS26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS27
  N: ttyS27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS27
  E: MAJOR=4
  E: MINOR=91
  E: DEVNAME=/dev/ttyS27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS28
  N: ttyS28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS28
  E: MAJOR=4
  E: MINOR=92
  E: DEVNAME=/dev/ttyS28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS29
  N: ttyS29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS29
  E: MAJOR=4
  E: MINOR=93
  E: DEVNAME=/dev/ttyS29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS3
  N: ttyS3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
  E: MAJOR=4
  E: MINOR=67
  E: DEVNAME=/dev/ttyS3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS30
  N: ttyS30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS30
  E: MAJOR=4
  E: MINOR=94
  E: DEVNAME=/dev/ttyS30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS31
  N: ttyS31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS31
  E: MAJOR=4
  E: MINOR=95
  E: DEVNAME=/dev/ttyS31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS4
  N: ttyS4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS4
  E: MAJOR=4
  E: MINOR=68
  E: DEVNAME=/dev/ttyS4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS5
  N: ttyS5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS5
  E: MAJOR=4
  E: MINOR=69
  E: DEVNAME=/dev/ttyS5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS6
  N: ttyS6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS6
  E: MAJOR=4
  E: MINOR=70
  E: DEVNAME=/dev/ttyS6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS7
  N: ttyS7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS7
  E: MAJOR=4
  E: MINOR=71
  E: DEVNAME=/dev/ttyS7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS8
  N: ttyS8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS8
  E: MAJOR=4
  E: MINOR=72
  E: DEVNAME=/dev/ttyS8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS9
  N: ttyS9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS9
  E: MAJOR=4
  E: MINOR=73
  E: DEVNAME=/dev/ttyS9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pnp0/00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:00
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:01
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:02
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03
  E: DRIVER=rtc_cmos
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03/rtc/rtc0
  N: rtc0
  S: rtc
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03/rtc/rtc0
  E: MAJOR=254
  E: MINOR=0
  E: DEVNAME=/dev/rtc0
  E: SUBSYSTEM=rtc
  E: DEVLINKS=/dev/rtc
  
  P: /devices/pnp0/00:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:04
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:06
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07
  E: DRIVER=parport_pc
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07/ppdev/parport0
  N: parport0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07/ppdev/parport0
  E: MAJOR=99
  E: MINOR=0
  E: DEVNAME=/dev/parport0
  E: SUBSYSTEM=ppdev
  
  P: /devices/pnp0/00:07/printer/lp0
  N: lp0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07/printer/lp0
  E: MAJOR=6
  E: MINOR=0
  E: DEVNAME=/dev/lp0
  E: SUBSYSTEM=printer
  E: TAGS=:udev-configure-printer:
  
  P: /devices/pnp0/00:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:08
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:09
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0b
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0c
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0d
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0e
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0f
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/software
  E: UDEV_LOG=3
  E: DEVPATH=/devices/software
  E: SUBSYSTEM=event_source
  
  P: /devices/tracepoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/tracepoint
  E: SUBSYSTEM=event_source
  
  P: /devices/virtual/bdi/0:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:19
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:10
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:11
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:12
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:13
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:14
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:15
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:8
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:9
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/2:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/2:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:16
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:32
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:48
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:64
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:80
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:80
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/default
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/default
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/block/loop0
  N: loop0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop0
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/loop0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop1
  N: loop1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/loop1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop2
  N: loop2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/loop2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop3
  N: loop3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/loop3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop4
  N: loop4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/loop4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop5
  N: loop5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/loop5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop6
  N: loop6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/loop6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop7
  N: loop7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop7
  E: MAJOR=7
  E: MINOR=7
  E: DEVNAME=/dev/loop7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/ram0
  N: ram0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram0
  E: MAJOR=1
  E: MINOR=0
  E: DEVNAME=/dev/ram0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram1
  N: ram1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram1
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/ram1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram10
  N: ram10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram10
  E: MAJOR=1
  E: MINOR=10
  E: DEVNAME=/dev/ram10
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram11
  N: ram11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram11
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/ram11
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram12
  N: ram12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram12
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/ram12
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram13
  N: ram13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram13
  E: MAJOR=1
  E: MINOR=13
  E: DEVNAME=/dev/ram13
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram14
  N: ram14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram14
  E: MAJOR=1
  E: MINOR=14
  E: DEVNAME=/dev/ram14
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram15
  N: ram15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram15
  E: MAJOR=1
  E: MINOR=15
  E: DEVNAME=/dev/ram15
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram2
  N: ram2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram2
  E: MAJOR=1
  E: MINOR=2
  E: DEVNAME=/dev/ram2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram3
  N: ram3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram3
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/ram3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram4
  N: ram4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram4
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/ram4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram5
  N: ram5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram5
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/ram5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram6
  N: ram6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram6
  E: MAJOR=1
  E: MINOR=6
  E: DEVNAME=/dev/ram6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram7
  N: ram7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram7
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/ram7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram8
  N: ram8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram8
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/ram8
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram9
  N: ram9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram9
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/ram9
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/dmi/id
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/dmi/id
  E: MODALIAS=dmi:bvnAmericanMegatrendsInc.:bvr3.06:bd08/27/2004:svnHPPavilion061:pnPN216AA-ACJt730i:pvr04H0211RE101GROUP10:rvnASUSTeKComputerINC.:rnGrouper:rvr1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:
  E: SUBSYSTEM=dmi
  
  P: /devices/virtual/graphics/fbcon
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/graphics/fbcon
  E: SUBSYSTEM=graphics
  
  P: /devices/virtual/input/mice
  N: input/mice
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/mice
  E: MAJOR=13
  E: MINOR=63
  E: DEVNAME=/dev/input/mice
  E: SUBSYSTEM=input
  
  P: /devices/virtual/mem/full
  N: full
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/full
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/full
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/kmsg
  N: kmsg
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/kmsg
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/kmsg
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/mem
  N: mem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/mem
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/mem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/null
  N: null
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/null
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/null
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/oldmem
  N: oldmem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/oldmem
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/oldmem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/port
  N: port
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/port
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/port
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/random
  N: random
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/random
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/random
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/urandom
  N: urandom
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/urandom
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/urandom
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/zero
  N: zero
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/zero
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/zero
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/misc/agpgart
  N: agpgart
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/agpgart
  E: MAJOR=10
  E: MINOR=175
  E: DEVNAME=/dev/agpgart
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/cpu_dma_latency
  N: cpu_dma_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
  E: MAJOR=10
  E: MINOR=60
  E: DEVNAME=/dev/cpu_dma_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/device-mapper
  N: mapper/control
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/device-mapper
  E: MAJOR=10
  E: MINOR=236
  E: DEVNAME=/dev/mapper/control
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/ecryptfs
  N: ecryptfs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/ecryptfs
  E: MAJOR=10
  E: MINOR=61
  E: DEVNAME=/dev/ecryptfs
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/fuse
  N: fuse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/fuse
  E: MAJOR=10
  E: MINOR=229
  E: DEVNAME=/dev/fuse
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/hpet
  N: hpet
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/hpet
  E: MAJOR=10
  E: MINOR=228
  E: DEVNAME=/dev/hpet
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/mcelog
  N: mcelog
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/mcelog
  E: MAJOR=10
  E: MINOR=227
  E: DEVNAME=/dev/mcelog
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_latency
  N: network_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_latency
  E: MAJOR=10
  E: MINOR=59
  E: DEVNAME=/dev/network_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_throughput
  N: network_throughput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_throughput
  E: MAJOR=10
  E: MINOR=58
  E: DEVNAME=/dev/network_throughput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/psaux
  N: psaux
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/psaux
  E: MAJOR=10
  E: MINOR=1
  E: DEVNAME=/dev/psaux
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/rfkill
  N: rfkill
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/rfkill
  E: MAJOR=10
  E: MINOR=62
  E: DEVNAME=/dev/rfkill
  E: SUBSYSTEM=misc
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/misc/snapshot
  N: snapshot
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/snapshot
  E: MAJOR=10
  E: MINOR=231
  E: DEVNAME=/dev/snapshot
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/tun
  N: net/tun
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/tun
  E: MAJOR=10
  E: MINOR=200
  E: DEVNAME=/dev/net/tun
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/uinput
  N: uinput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/uinput
  E: MAJOR=10
  E: MINOR=223
  E: DEVNAME=/dev/uinput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/vga_arbiter
  N: vga_arbiter
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vga_arbiter
  E: MAJOR=10
  E: MINOR=63
  E: DEVNAME=/dev/vga_arbiter
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/net/lo
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/lo
  E: INTERFACE=lo
  E: IFINDEX=1
  E: SUBSYSTEM=net
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/net/ppp0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/ppp0
  E: INTERFACE=ppp0
  E: IFINDEX=3
  E: SUBSYSTEM=net
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/ppp/ppp
  N: ppp
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/ppp/ppp
  E: MAJOR=108
  E: MINOR=0
  E: DEVNAME=/dev/ppp
  E: SUBSYSTEM=ppp
  
  P: /devices/virtual/regulator/regulator.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/regulator/regulator.0
  E: SUBSYSTEM=regulator
  
  P: /devices/virtual/sound/seq
  N: snd/seq
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/seq
  E: MAJOR=116
  E: MINOR=1
  E: DEVNAME=/dev/snd/seq
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/sound/timer
  N: snd/timer
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/timer
  E: MAJOR=116
  E: MINOR=33
  E: DEVNAME=/dev/snd/timer
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/thermal/cooling_device0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/tty/console
  N: console
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/console
  E: MAJOR=5
  E: MINOR=1
  E: DEVNAME=/dev/console
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ptmx
  N: ptmx
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ptmx
  E: MAJOR=5
  E: MINOR=2
  E: DEVNAME=/dev/ptmx
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty
  N: tty
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty
  E: MAJOR=5
  E: MINOR=0
  E: DEVNAME=/dev/tty
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty0
  N: tty0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty0
  E: MAJOR=4
  E: MINOR=0
  E: DEVNAME=/dev/tty0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty1
  N: tty1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty1
  E: MAJOR=4
  E: MINOR=1
  E: DEVNAME=/dev/tty1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty10
  N: tty10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty10
  E: MAJOR=4
  E: MINOR=10
  E: DEVNAME=/dev/tty10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty11
  N: tty11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty11
  E: MAJOR=4
  E: MINOR=11
  E: DEVNAME=/dev/tty11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty12
  N: tty12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty12
  E: MAJOR=4
  E: MINOR=12
  E: DEVNAME=/dev/tty12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty13
  N: tty13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty13
  E: MAJOR=4
  E: MINOR=13
  E: DEVNAME=/dev/tty13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty14
  N: tty14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty14
  E: MAJOR=4
  E: MINOR=14
  E: DEVNAME=/dev/tty14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty15
  N: tty15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty15
  E: MAJOR=4
  E: MINOR=15
  E: DEVNAME=/dev/tty15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty16
  N: tty16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty16
  E: MAJOR=4
  E: MINOR=16
  E: DEVNAME=/dev/tty16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty17
  N: tty17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty17
  E: MAJOR=4
  E: MINOR=17
  E: DEVNAME=/dev/tty17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty18
  N: tty18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty18
  E: MAJOR=4
  E: MINOR=18
  E: DEVNAME=/dev/tty18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty19
  N: tty19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty19
  E: MAJOR=4
  E: MINOR=19
  E: DEVNAME=/dev/tty19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty2
  N: tty2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty2
  E: MAJOR=4
  E: MINOR=2
  E: DEVNAME=/dev/tty2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty20
  N: tty20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty20
  E: MAJOR=4
  E: MINOR=20
  E: DEVNAME=/dev/tty20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty21
  N: tty21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty21
  E: MAJOR=4
  E: MINOR=21
  E: DEVNAME=/dev/tty21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty22
  N: tty22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty22
  E: MAJOR=4
  E: MINOR=22
  E: DEVNAME=/dev/tty22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty23
  N: tty23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty23
  E: MAJOR=4
  E: MINOR=23
  E: DEVNAME=/dev/tty23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty24
  N: tty24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty24
  E: MAJOR=4
  E: MINOR=24
  E: DEVNAME=/dev/tty24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty25
  N: tty25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty25
  E: MAJOR=4
  E: MINOR=25
  E: DEVNAME=/dev/tty25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty26
  N: tty26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty26
  E: MAJOR=4
  E: MINOR=26
  E: DEVNAME=/dev/tty26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty27
  N: tty27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty27
  E: MAJOR=4
  E: MINOR=27
  E: DEVNAME=/dev/tty27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty28
  N: tty28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty28
  E: MAJOR=4
  E: MINOR=28
  E: DEVNAME=/dev/tty28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty29
  N: tty29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty29
  E: MAJOR=4
  E: MINOR=29
  E: DEVNAME=/dev/tty29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty3
  N: tty3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty3
  E: MAJOR=4
  E: MINOR=3
  E: DEVNAME=/dev/tty3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty30
  N: tty30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty30
  E: MAJOR=4
  E: MINOR=30
  E: DEVNAME=/dev/tty30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty31
  N: tty31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty31
  E: MAJOR=4
  E: MINOR=31
  E: DEVNAME=/dev/tty31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty32
  N: tty32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty32
  E: MAJOR=4
  E: MINOR=32
  E: DEVNAME=/dev/tty32
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty33
  N: tty33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty33
  E: MAJOR=4
  E: MINOR=33
  E: DEVNAME=/dev/tty33
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty34
  N: tty34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty34
  E: MAJOR=4
  E: MINOR=34
  E: DEVNAME=/dev/tty34
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty35
  N: tty35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty35
  E: MAJOR=4
  E: MINOR=35
  E: DEVNAME=/dev/tty35
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty36
  N: tty36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty36
  E: MAJOR=4
  E: MINOR=36
  E: DEVNAME=/dev/tty36
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty37
  N: tty37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty37
  E: MAJOR=4
  E: MINOR=37
  E: DEVNAME=/dev/tty37
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty38
  N: tty38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty38
  E: MAJOR=4
  E: MINOR=38
  E: DEVNAME=/dev/tty38
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty39
  N: tty39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty39
  E: MAJOR=4
  E: MINOR=39
  E: DEVNAME=/dev/tty39
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty4
  N: tty4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty4
  E: MAJOR=4
  E: MINOR=4
  E: DEVNAME=/dev/tty4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty40
  N: tty40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty40
  E: MAJOR=4
  E: MINOR=40
  E: DEVNAME=/dev/tty40
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty41
  N: tty41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty41
  E: MAJOR=4
  E: MINOR=41
  E: DEVNAME=/dev/tty41
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty42
  N: tty42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty42
  E: MAJOR=4
  E: MINOR=42
  E: DEVNAME=/dev/tty42
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty43
  N: tty43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty43
  E: MAJOR=4
  E: MINOR=43
  E: DEVNAME=/dev/tty43
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty44
  N: tty44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty44
  E: MAJOR=4
  E: MINOR=44
  E: DEVNAME=/dev/tty44
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty45
  N: tty45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty45
  E: MAJOR=4
  E: MINOR=45
  E: DEVNAME=/dev/tty45
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty46
  N: tty46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty46
  E: MAJOR=4
  E: MINOR=46
  E: DEVNAME=/dev/tty46
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty47
  N: tty47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty47
  E: MAJOR=4
  E: MINOR=47
  E: DEVNAME=/dev/tty47
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty48
  N: tty48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty48
  E: MAJOR=4
  E: MINOR=48
  E: DEVNAME=/dev/tty48
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty49
  N: tty49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty49
  E: MAJOR=4
  E: MINOR=49
  E: DEVNAME=/dev/tty49
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty5
  N: tty5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty5
  E: MAJOR=4
  E: MINOR=5
  E: DEVNAME=/dev/tty5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty50
  N: tty50
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty50
  E: MAJOR=4
  E: MINOR=50
  E: DEVNAME=/dev/tty50
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty51
  N: tty51
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty51
  E: MAJOR=4
  E: MINOR=51
  E: DEVNAME=/dev/tty51
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty52
  N: tty52
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty52
  E: MAJOR=4
  E: MINOR=52
  E: DEVNAME=/dev/tty52
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty53
  N: tty53
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty53
  E: MAJOR=4
  E: MINOR=53
  E: DEVNAME=/dev/tty53
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty54
  N: tty54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty54
  E: MAJOR=4
  E: MINOR=54
  E: DEVNAME=/dev/tty54
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty55
  N: tty55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty55
  E: MAJOR=4
  E: MINOR=55
  E: DEVNAME=/dev/tty55
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty56
  N: tty56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty56
  E: MAJOR=4
  E: MINOR=56
  E: DEVNAME=/dev/tty56
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty57
  N: tty57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty57
  E: MAJOR=4
  E: MINOR=57
  E: DEVNAME=/dev/tty57
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty58
  N: tty58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty58
  E: MAJOR=4
  E: MINOR=58
  E: DEVNAME=/dev/tty58
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty59
  N: tty59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty59
  E: MAJOR=4
  E: MINOR=59
  E: DEVNAME=/dev/tty59
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty6
  N: tty6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty6
  E: MAJOR=4
  E: MINOR=6
  E: DEVNAME=/dev/tty6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty60
  N: tty60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty60
  E: MAJOR=4
  E: MINOR=60
  E: DEVNAME=/dev/tty60
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty61
  N: tty61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty61
  E: MAJOR=4
  E: MINOR=61
  E: DEVNAME=/dev/tty61
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty62
  N: tty62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty62
  E: MAJOR=4
  E: MINOR=62
  E: DEVNAME=/dev/tty62
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty63
  N: tty63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty63
  E: MAJOR=4
  E: MINOR=63
  E: DEVNAME=/dev/tty63
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty7
  N: tty7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty7
  E: MAJOR=4
  E: MINOR=7
  E: DEVNAME=/dev/tty7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty8
  N: tty8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty8
  E: MAJOR=4
  E: MINOR=8
  E: DEVNAME=/dev/tty8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty9
  N: tty9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty9
  E: MAJOR=4
  E: MINOR=9
  E: DEVNAME=/dev/tty9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ttyprintk
  N: ttyprintk
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ttyprintk
  E: MAJOR=5
  E: MINOR=3
  E: DEVNAME=/dev/ttyprintk
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/usbmon/usbmon0
  N: usbmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/usbmon/usbmon0
  E: MAJOR=252
  E: MINOR=0
  E: DEVNAME=/dev/usbmon0
  E: SUBSYSTEM=usbmon
  
  P: /devices/virtual/vc/vcs
  N: vcs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/vcs
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs1
  N: vcs1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/vcs1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs2
  N: vcs2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/vcs2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs3
  N: vcs3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/vcs3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs4
  N: vcs4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/vcs4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs5
  N: vcs5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/vcs5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs6
  N: vcs6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/vcs6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa
  N: vcsa
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa
  E: MAJOR=7
  E: MINOR=128
  E: DEVNAME=/dev/vcsa
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa1
  N: vcsa1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa1
  E: MAJOR=7
  E: MINOR=129
  E: DEVNAME=/dev/vcsa1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa2
  N: vcsa2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa2
  E: MAJOR=7
  E: MINOR=130
  E: DEVNAME=/dev/vcsa2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa3
  N: vcsa3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa3
  E: MAJOR=7
  E: MINOR=131
  E: DEVNAME=/dev/vcsa3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa4
  N: vcsa4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa4
  E: MAJOR=7
  E: MINOR=132
  E: DEVNAME=/dev/vcsa4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa5
  N: vcsa5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa5
  E: MAJOR=7
  E: MINOR=133
  E: DEVNAME=/dev/vcsa5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa6
  N: vcsa6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa6
  E: MAJOR=7
  E: MINOR=134
  E: DEVNAME=/dev/vcsa6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vtconsole/vtcon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon0
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/vtconsole/vtcon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon1
  E: SUBSYSTEM=vtconsole
  
-----  udevinfo end -----
/devices/LNXSYSTM:00
/devices/LNXSYSTM:00/LNXCPU:00
/devices/LNXSYSTM:00/LNXCPU:01
/devices/LNXSYSTM:00/LNXPWRBN:00
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  name: /dev/input/event1
/devices/LNXSYSTM:00/device:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C01:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:04
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/INT0800:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0000:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0100:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0200:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0401:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0700:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0800:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0B00:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:01
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:02
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C02:03
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C04:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0b
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a/device:0c
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0e
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0d/device:0f
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:12
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16
/devices/LNXSYSTM:00/device:00/PNP0C01:01
/devices/LNXSYSTM:00/device:00/PNP0C02:05
/devices/LNXSYSTM:00/device:00/PNP0C0C:00
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0
  name: /dev/input/event0
/devices/LNXSYSTM:00/device:00/PNP0C0F:00
/devices/LNXSYSTM:00/device:00/PNP0C0F:01
/devices/LNXSYSTM:00/device:00/PNP0C0F:02
/devices/LNXSYSTM:00/device:00/PNP0C0F:03
/devices/LNXSYSTM:00/device:00/PNP0C0F:04
/devices/LNXSYSTM:00/device:00/PNP0C0F:05
/devices/LNXSYSTM:00/device:00/PNP0C0F:06
/devices/LNXSYSTM:00/device:00/PNP0C0F:07
/devices/LNXSYSTM:00/device:17
/devices/breakpoint
/devices/cpu
/devices/pci0000:00/0000:00:00.0
/devices/pci0000:00/0000:00:02.0
/devices/pci0000:00/0000:00:02.0/drm/card0
  name: /dev/dri/card0
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
/devices/pci0000:00/0000:00:02.0/drm/controlD64
  name: /dev/dri/controlD64
/devices/pci0000:00/0000:00:02.0/graphics/fb0
  name: /dev/fb0
/devices/pci0000:00/0000:00:02.0/i2c-0
/devices/pci0000:00/0000:00:02.0/i2c-1
/devices/pci0000:00/0000:00:02.0/i2c-10
/devices/pci0000:00/0000:00:02.0/i2c-11
/devices/pci0000:00/0000:00:02.0/i2c-12
/devices/pci0000:00/0000:00:02.0/i2c-13
/devices/pci0000:00/0000:00:02.0/i2c-2
/devices/pci0000:00/0000:00:02.0/i2c-3
/devices/pci0000:00/0000:00:02.0/i2c-4
/devices/pci0000:00/0000:00:02.0/i2c-5
/devices/pci0000:00/0000:00:02.0/i2c-6
/devices/pci0000:00/0000:00:02.0/i2c-7
/devices/pci0000:00/0000:00:02.0/i2c-8
/devices/pci0000:00/0000:00:02.0/i2c-9
/devices/pci0000:00/0000:00:02.1
/devices/pci0000:00/0000:00:1b.0
/devices/pci0000:00/0000:00:1b.0/sound/card0
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  name: /dev/snd/hwC0D0
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  name: /dev/snd/pcmC0D0c
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  name: /dev/snd/pcmC0D0p
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
  name: /dev/snd/pcmC0D1p
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D2c
  name: /dev/snd/pcmC0D2c
/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  name: /dev/snd/controlC0
  links: /dev/snd/by-path/pci-0000:00:1b.0
/devices/pci0000:00/0000:00:1c.0
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
/devices/pci0000:00/0000:00:1d.0
/devices/pci0000:00/0000:00:1d.0/usb2
  name: /dev/bus/usb/002/001
/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1
  name: /dev/bus/usb/002/002
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1C4F:0002.0001/hidraw/hidraw0
  name: /dev/hidraw0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
  name: /dev/input/event2
  links: /dev/input/by-id/usb-USB_USB_Keykoard-event-kbd, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1C4F:0002.0002/hidraw/hidraw1
  name: /dev/hidraw1
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
  name: /dev/input/event3
  links: /dev/input/by-id/usb-USB_USB_Keykoard-event-if01, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event
/devices/pci0000:00/0000:00:1d.0/usb2/2-2
  name: /dev/bus/usb/002/003
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/0003:093A:2510.0003/hidraw/hidraw2
  name: /dev/hidraw2
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/event4
  name: /dev/input/event4
  links: /dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-event-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse
/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4/mouse0
  name: /dev/input/mouse0
  links: /dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-mouse
/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  name: /dev/usbmon2
/devices/pci0000:00/0000:00:1d.1
/devices/pci0000:00/0000:00:1d.1/usb3
  name: /dev/bus/usb/003/001
/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  name: /dev/usbmon3
/devices/pci0000:00/0000:00:1d.2
/devices/pci0000:00/0000:00:1d.2/usb4
  name: /dev/bus/usb/004/001
/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  name: /dev/usbmon4
/devices/pci0000:00/0000:00:1d.3
/devices/pci0000:00/0000:00:1d.3/usb5
  name: /dev/bus/usb/005/001
/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1
  name: /dev/bus/usb/005/002
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/scsi_host/host4
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/block/sdb
  name: /dev/sdb
  links: /dev/disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0
  name: /dev/bsg/4:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2
  name: /dev/sg2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/block/sdc
  name: /dev/sdc
  links: /dev/disk/by-id/usb-Generic_USB_CF_Reader_9205291-0:1, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/bsg/4:0:0:1
  name: /dev/bsg/4:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_device/4:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_disk/4:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1/scsi_generic/sg3
  name: /dev/sg3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/block/sdd
  name: /dev/sdd
  links: /dev/disk/by-id/usb-Generic_USB_SM_Reader_9205291-0:2, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/bsg/4:0:0:2
  name: /dev/bsg/4:0:0:2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_device/4:0:0:2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_disk/4:0:0:2
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2/scsi_generic/sg4
  name: /dev/sg4
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/block/sde
  name: /dev/sde
  links: /dev/disk/by-id/usb-Generic_USB_MS_Reader_9205291-0:3, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/bsg/4:0:0:3
  name: /dev/bsg/4:0:0:3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_device/4:0:0:3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_disk/4:0:0:3
/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3/scsi_generic/sg5
  name: /dev/sg5
/devices/pci0000:00/0000:00:1d.3/usb5/5-2
  name: /dev/bus/usb/005/004
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0/tty/ttyUSB0
  name: /dev/ttyUSB0
  links: /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0, /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/ttyUSB1/tty/ttyUSB1
  name: /dev/ttyUSB1
  links: /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.1-port0, /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/ttyUSB2/tty/ttyUSB2
  name: /dev/ttyUSB2
  links: /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.2-port0, /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/scsi_host/host9
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/block/sr1
  name: /dev/sr1
  links: /dev/scd1, /dev/disk/by-id/usb-HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:0, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:0, /dev/cdrom1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/bsg/9:0:0:0
  name: /dev/bsg/9:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_device/9:0:0:0
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0/scsi_generic/sg6
  name: /dev/sg6
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/block/sdf
  name: /dev/sdf
  links: /dev/disk/by-id/usb-HUAWEI_SD_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:1, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/bsg/9:0:0:1
  name: /dev/bsg/9:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_device/9:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_disk/9:0:0:1
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1/scsi_generic/sg7
  name: /dev/sg7
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3
/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.4/ttyUSB3/tty/ttyUSB3
  name: /dev/ttyUSB3
  links: /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.4-port0, /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if04-port0
/devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  name: /dev/usbmon5
/devices/pci0000:00/0000:00:1d.7
/devices/pci0000:00/0000:00:1d.7/usb1
  name: /dev/bus/usb/001/001
/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  name: /dev/usbmon1
/devices/pci0000:00/0000:00:1e.0
/devices/pci0000:00/0000:00:1e.0/0000:02:01.0
/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/fw0
  name: /dev/fw0
/devices/pci0000:00/0000:00:1e.0/0000:02:02.0
/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth0
/devices/pci0000:00/0000:00:1e.0/0000:02:05.0
/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:02
/devices/pci0000:00/0000:00:1f.0
/devices/pci0000:00/0000:00:1f.1
/devices/pci0000:00/0000:00:1f.1/ata1/ata_port/ata1
/devices/pci0000:00/0000:00:1f.1/ata1/link1/ata_link/link1
/devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.0/ata_device/dev1.0
/devices/pci0000:00/0000:00:1f.1/ata1/link1/dev1.1/ata_device/dev1.1
/devices/pci0000:00/0000:00:1f.1/ata2/ata_port/ata2
/devices/pci0000:00/0000:00:1f.1/ata2/link2/ata_link/link2
/devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.0/ata_device/dev2.0
/devices/pci0000:00/0000:00:1f.1/ata2/link2/dev2.1/ata_device/dev2.1
/devices/pci0000:00/0000:00:1f.1/host0
/devices/pci0000:00/0000:00:1f.1/host0/scsi_host/host0
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/block/sr0
  name: /dev/sr0
  links: /dev/scd0, /dev/disk/by-id/ata-SONY_DVD_RW_AW-G170A, /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:1:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/bsg/0:0:1:0
  name: /dev/bsg/0:0:1:0
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_device/0:0:1:0
/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/scsi_generic/sg0
  name: /dev/sg0
/devices/pci0000:00/0000:00:1f.1/host1
/devices/pci0000:00/0000:00:1f.1/host1/scsi_host/host1
/devices/pci0000:00/0000:00:1f.2
/devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
/devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.1/ata_device/dev3.1
/devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
/devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.1/ata_device/dev4.1
/devices/pci0000:00/0000:00:1f.2/host2
/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda
  name: /dev/sda
  links: /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda1
  name: /dev/sda1
  links: /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part1, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/ececbda8-912d-4c7c-9065-122f7942b6b0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda2
  name: /dev/sda2
  links: /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part2, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda5
  name: /dev/sda5
  links: /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part5, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5, /dev/disk/by-uuid/cd20ec63-2c4c-48b5-beeb-8f441259208a
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  name: /dev/bsg/2:0:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  name: /dev/sg1
/devices/pci0000:00/0000:00:1f.2/host3
/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
/devices/pci0000:00/0000:00:1f.3
/devices/pci0000:00/pci_bus/0000:00
/devices/platform/Fixed
/devices/platform/Fixed
/devices/platform/alarmtimer
/devices/platform/eisa.0
/devices/platform/floppy.0
/devices/platform/floppy.0/block/fd0
  name: /dev/fd0
/devices/platform/i8042
/devices/platform/i8042/serio0
/devices/platform/i8042/serio1
/devices/platform/pcspkr
/devices/platform/reg-dummy
/devices/platform/serial8250
/devices/platform/serial8250/tty/ttyS0
  name: /dev/ttyS0
/devices/platform/serial8250/tty/ttyS1
  name: /dev/ttyS1
/devices/platform/serial8250/tty/ttyS10
  name: /dev/ttyS10
/devices/platform/serial8250/tty/ttyS11
  name: /dev/ttyS11
/devices/platform/serial8250/tty/ttyS12
  name: /dev/ttyS12
/devices/platform/serial8250/tty/ttyS13
  name: /dev/ttyS13
/devices/platform/serial8250/tty/ttyS14
  name: /dev/ttyS14
/devices/platform/serial8250/tty/ttyS15
  name: /dev/ttyS15
/devices/platform/serial8250/tty/ttyS16
  name: /dev/ttyS16
/devices/platform/serial8250/tty/ttyS17
  name: /dev/ttyS17
/devices/platform/serial8250/tty/ttyS18
  name: /dev/ttyS18
/devices/platform/serial8250/tty/ttyS19
  name: /dev/ttyS19
/devices/platform/serial8250/tty/ttyS2
  name: /dev/ttyS2
/devices/platform/serial8250/tty/ttyS20
  name: /dev/ttyS20
/devices/platform/serial8250/tty/ttyS21
  name: /dev/ttyS21
/devices/platform/serial8250/tty/ttyS22
  name: /dev/ttyS22
/devices/platform/serial8250/tty/ttyS23
  name: /dev/ttyS23
/devices/platform/serial8250/tty/ttyS24
  name: /dev/ttyS24
/devices/platform/serial8250/tty/ttyS25
  name: /dev/ttyS25
/devices/platform/serial8250/tty/ttyS26
  name: /dev/ttyS26
/devices/platform/serial8250/tty/ttyS27
  name: /dev/ttyS27
/devices/platform/serial8250/tty/ttyS28
  name: /dev/ttyS28
/devices/platform/serial8250/tty/ttyS29
  name: /dev/ttyS29
/devices/platform/serial8250/tty/ttyS3
  name: /dev/ttyS3
/devices/platform/serial8250/tty/ttyS30
  name: /dev/ttyS30
/devices/platform/serial8250/tty/ttyS31
  name: /dev/ttyS31
/devices/platform/serial8250/tty/ttyS4
  name: /dev/ttyS4
/devices/platform/serial8250/tty/ttyS5
  name: /dev/ttyS5
/devices/platform/serial8250/tty/ttyS6
  name: /dev/ttyS6
/devices/platform/serial8250/tty/ttyS7
  name: /dev/ttyS7
/devices/platform/serial8250/tty/ttyS8
  name: /dev/ttyS8
/devices/platform/serial8250/tty/ttyS9
  name: /dev/ttyS9
/devices/pnp0/00:00
/devices/pnp0/00:01
/devices/pnp0/00:02
/devices/pnp0/00:03
/devices/pnp0/00:03/rtc/rtc0
  name: /dev/rtc0
  links: /dev/rtc
/devices/pnp0/00:04
/devices/pnp0/00:05
/devices/pnp0/00:06
/devices/pnp0/00:07
/devices/pnp0/00:07/ppdev/parport0
  name: /dev/parport0
/devices/pnp0/00:07/printer/lp0
  name: /dev/lp0
/devices/pnp0/00:08
/devices/pnp0/00:09
/devices/pnp0/00:0a
/devices/pnp0/00:0b
/devices/pnp0/00:0c
/devices/pnp0/00:0d
/devices/pnp0/00:0e
/devices/pnp0/00:0f
/devices/software
/devices/tracepoint
/devices/virtual/bdi/0:19
/devices/virtual/bdi/11:0
/devices/virtual/bdi/11:1
/devices/virtual/bdi/1:0
/devices/virtual/bdi/1:1
/devices/virtual/bdi/1:10
/devices/virtual/bdi/1:11
/devices/virtual/bdi/1:12
/devices/virtual/bdi/1:13
/devices/virtual/bdi/1:14
/devices/virtual/bdi/1:15
/devices/virtual/bdi/1:2
/devices/virtual/bdi/1:3
/devices/virtual/bdi/1:4
/devices/virtual/bdi/1:5
/devices/virtual/bdi/1:6
/devices/virtual/bdi/1:7
/devices/virtual/bdi/1:8
/devices/virtual/bdi/1:9
/devices/virtual/bdi/2:0
/devices/virtual/bdi/7:0
/devices/virtual/bdi/7:1
/devices/virtual/bdi/7:2
/devices/virtual/bdi/7:3
/devices/virtual/bdi/7:4
/devices/virtual/bdi/7:5
/devices/virtual/bdi/7:6
/devices/virtual/bdi/7:7
/devices/virtual/bdi/8:0
/devices/virtual/bdi/8:16
/devices/virtual/bdi/8:32
/devices/virtual/bdi/8:48
/devices/virtual/bdi/8:64
/devices/virtual/bdi/8:80
/devices/virtual/bdi/default
/devices/virtual/block/loop0
  name: /dev/loop0
/devices/virtual/block/loop1
  name: /dev/loop1
/devices/virtual/block/loop2
  name: /dev/loop2
/devices/virtual/block/loop3
  name: /dev/loop3
/devices/virtual/block/loop4
  name: /dev/loop4
/devices/virtual/block/loop5
  name: /dev/loop5
/devices/virtual/block/loop6
  name: /dev/loop6
/devices/virtual/block/loop7
  name: /dev/loop7
/devices/virtual/block/ram0
  name: /dev/ram0
/devices/virtual/block/ram1
  name: /dev/ram1
/devices/virtual/block/ram10
  name: /dev/ram10
/devices/virtual/block/ram11
  name: /dev/ram11
/devices/virtual/block/ram12
  name: /dev/ram12
/devices/virtual/block/ram13
  name: /dev/ram13
/devices/virtual/block/ram14
  name: /dev/ram14
/devices/virtual/block/ram15
  name: /dev/ram15
/devices/virtual/block/ram2
  name: /dev/ram2
/devices/virtual/block/ram3
  name: /dev/ram3
/devices/virtual/block/ram4
  name: /dev/ram4
/devices/virtual/block/ram5
  name: /dev/ram5
/devices/virtual/block/ram6
  name: /dev/ram6
/devices/virtual/block/ram7
  name: /dev/ram7
/devices/virtual/block/ram8
  name: /dev/ram8
/devices/virtual/block/ram9
  name: /dev/ram9
/devices/virtual/dmi/id
/devices/virtual/graphics/fbcon
/devices/virtual/input/mice
  name: /dev/input/mice
/devices/virtual/mem/full
  name: /dev/full
/devices/virtual/mem/kmsg
  name: /dev/kmsg
/devices/virtual/mem/mem
  name: /dev/mem
/devices/virtual/mem/null
  name: /dev/null
/devices/virtual/mem/oldmem
  name: /dev/oldmem
/devices/virtual/mem/port
  name: /dev/port
/devices/virtual/mem/random
  name: /dev/random
/devices/virtual/mem/urandom
  name: /dev/urandom
/devices/virtual/mem/zero
  name: /dev/zero
/devices/virtual/misc/agpgart
  name: /dev/agpgart
/devices/virtual/misc/cpu_dma_latency
  name: /dev/cpu_dma_latency
/devices/virtual/misc/device-mapper
  name: /dev/mapper/control
/devices/virtual/misc/ecryptfs
  name: /dev/ecryptfs
/devices/virtual/misc/fuse
  name: /dev/fuse
/devices/virtual/misc/hpet
  name: /dev/hpet
/devices/virtual/misc/mcelog
  name: /dev/mcelog
/devices/virtual/misc/network_latency
  name: /dev/network_latency
/devices/virtual/misc/network_throughput
  name: /dev/network_throughput
/devices/virtual/misc/psaux
  name: /dev/psaux
/devices/virtual/misc/rfkill
  name: /dev/rfkill
/devices/virtual/misc/snapshot
  name: /dev/snapshot
/devices/virtual/misc/tun
  name: /dev/net/tun
/devices/virtual/misc/uinput
  name: /dev/uinput
/devices/virtual/misc/vga_arbiter
  name: /dev/vga_arbiter
/devices/virtual/net/lo
/devices/virtual/net/ppp0
/devices/virtual/ppp/ppp
  name: /dev/ppp
/devices/virtual/regulator/regulator.0
/devices/virtual/sound/seq
  name: /dev/snd/seq
/devices/virtual/sound/timer
  name: /dev/snd/timer
/devices/virtual/thermal/cooling_device0
/devices/virtual/tty/console
  name: /dev/console
/devices/virtual/tty/ptmx
  name: /dev/ptmx
/devices/virtual/tty/tty
  name: /dev/tty
/devices/virtual/tty/tty0
  name: /dev/tty0
/devices/virtual/tty/tty1
  name: /dev/tty1
/devices/virtual/tty/tty10
  name: /dev/tty10
/devices/virtual/tty/tty11
  name: /dev/tty11
/devices/virtual/tty/tty12
  name: /dev/tty12
/devices/virtual/tty/tty13
  name: /dev/tty13
/devices/virtual/tty/tty14
  name: /dev/tty14
/devices/virtual/tty/tty15
  name: /dev/tty15
/devices/virtual/tty/tty16
  name: /dev/tty16
/devices/virtual/tty/tty17
  name: /dev/tty17
/devices/virtual/tty/tty18
  name: /dev/tty18
/devices/virtual/tty/tty19
  name: /dev/tty19
/devices/virtual/tty/tty2
  name: /dev/tty2
/devices/virtual/tty/tty20
  name: /dev/tty20
/devices/virtual/tty/tty21
  name: /dev/tty21
/devices/virtual/tty/tty22
  name: /dev/tty22
/devices/virtual/tty/tty23
  name: /dev/tty23
/devices/virtual/tty/tty24
  name: /dev/tty24
/devices/virtual/tty/tty25
  name: /dev/tty25
/devices/virtual/tty/tty26
  name: /dev/tty26
/devices/virtual/tty/tty27
  name: /dev/tty27
/devices/virtual/tty/tty28
  name: /dev/tty28
/devices/virtual/tty/tty29
  name: /dev/tty29
/devices/virtual/tty/tty3
  name: /dev/tty3
/devices/virtual/tty/tty30
  name: /dev/tty30
/devices/virtual/tty/tty31
  name: /dev/tty31
/devices/virtual/tty/tty32
  name: /dev/tty32
/devices/virtual/tty/tty33
  name: /dev/tty33
/devices/virtual/tty/tty34
  name: /dev/tty34
/devices/virtual/tty/tty35
  name: /dev/tty35
/devices/virtual/tty/tty36
  name: /dev/tty36
/devices/virtual/tty/tty37
  name: /dev/tty37
/devices/virtual/tty/tty38
  name: /dev/tty38
/devices/virtual/tty/tty39
  name: /dev/tty39
/devices/virtual/tty/tty4
  name: /dev/tty4
/devices/virtual/tty/tty40
  name: /dev/tty40
/devices/virtual/tty/tty41
  name: /dev/tty41
/devices/virtual/tty/tty42
  name: /dev/tty42
/devices/virtual/tty/tty43
  name: /dev/tty43
/devices/virtual/tty/tty44
  name: /dev/tty44
/devices/virtual/tty/tty45
  name: /dev/tty45
/devices/virtual/tty/tty46
  name: /dev/tty46
/devices/virtual/tty/tty47
  name: /dev/tty47
/devices/virtual/tty/tty48
  name: /dev/tty48
/devices/virtual/tty/tty49
  name: /dev/tty49
/devices/virtual/tty/tty5
  name: /dev/tty5
/devices/virtual/tty/tty50
  name: /dev/tty50
/devices/virtual/tty/tty51
  name: /dev/tty51
/devices/virtual/tty/tty52
  name: /dev/tty52
/devices/virtual/tty/tty53
  name: /dev/tty53
/devices/virtual/tty/tty54
  name: /dev/tty54
/devices/virtual/tty/tty55
  name: /dev/tty55
/devices/virtual/tty/tty56
  name: /dev/tty56
/devices/virtual/tty/tty57
  name: /dev/tty57
/devices/virtual/tty/tty58
  name: /dev/tty58
/devices/virtual/tty/tty59
  name: /dev/tty59
/devices/virtual/tty/tty6
  name: /dev/tty6
/devices/virtual/tty/tty60
  name: /dev/tty60
/devices/virtual/tty/tty61
  name: /dev/tty61
/devices/virtual/tty/tty62
  name: /dev/tty62
/devices/virtual/tty/tty63
  name: /dev/tty63
/devices/virtual/tty/tty7
  name: /dev/tty7
/devices/virtual/tty/tty8
  name: /dev/tty8
/devices/virtual/tty/tty9
  name: /dev/tty9
/devices/virtual/tty/ttyprintk
  name: /dev/ttyprintk
/devices/virtual/usbmon/usbmon0
  name: /dev/usbmon0
/devices/virtual/vc/vcs
  name: /dev/vcs
/devices/virtual/vc/vcs1
  name: /dev/vcs1
/devices/virtual/vc/vcs2
  name: /dev/vcs2
/devices/virtual/vc/vcs3
  name: /dev/vcs3
/devices/virtual/vc/vcs4
  name: /dev/vcs4
/devices/virtual/vc/vcs5
  name: /dev/vcs5
/devices/virtual/vc/vcs6
  name: /dev/vcs6
/devices/virtual/vc/vcsa
  name: /dev/vcsa
/devices/virtual/vc/vcsa1
  name: /dev/vcsa1
/devices/virtual/vc/vcsa2
  name: /dev/vcsa2
/devices/virtual/vc/vcsa3
  name: /dev/vcsa3
/devices/virtual/vc/vcsa4
  name: /dev/vcsa4
/devices/virtual/vc/vcsa5
  name: /dev/vcsa5
/devices/virtual/vc/vcsa6
  name: /dev/vcsa6
/devices/virtual/vtconsole/vtcon0
/devices/virtual/vtconsole/vtcon1
>> int.13: device names
>> int.14: soft raid
----- soft raid devices -----
----- soft raid devices end -----
>> int.15: geo
>> int.16: parent
  prop read: rdCR.lZF+r4EgHp4 (failed)
  old prop read: rdCR.lZF+r4EgHp4 (failed)
  prop read: rdCR.n_7QNeEnh23 (failed)
  old prop read: rdCR.n_7QNeEnh23 (failed)
  prop read: rdCR.EMpH5pjcahD (failed)
  old prop read: rdCR.EMpH5pjcahD (failed)
  prop read: rdCR.f5u1ucRm+H9 (failed)
  old prop read: rdCR.f5u1ucRm+H9 (failed)
  prop read: rdCR.8uRK7LxiIA2 (failed)
  old prop read: rdCR.8uRK7LxiIA2 (failed)
  prop read: rdCR.AJKleuxpiP0 (failed)
  old prop read: rdCR.AJKleuxpiP0 (failed)
  prop read: rdCR.9N+EecqykME (failed)
  old prop read: rdCR.9N+EecqykME (failed)
  prop read: YMnp.ecK7NLYWZ5D (failed)
  old prop read: YMnp.ecK7NLYWZ5D (failed)
  prop read: rdCR.3wRL2_g4d2B (failed)
  old prop read: rdCR.3wRL2_g4d2B (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: qLht.Fo0h7LoGZYE (failed)
  old prop read: qLht.Fo0h7LoGZYE (failed)
  prop read: _Znp.EAFRYfLxHkA (failed)
  old prop read: _Znp.EAFRYfLxHkA (failed)
  prop read: ruGf.WzkqjRbwQ0D (failed)
  old prop read: ruGf.WzkqjRbwQ0D (failed)
  prop read: u1Nb.1iKcnAwVcq9 (failed)
  old prop read: u1Nb.1iKcnAwVcq9 (failed)
  prop read: z8Q3.hdHR1LU2D6A (failed)
  old prop read: z8Q3.hdHR1LU2D6A (failed)
  prop read: 1GTX.QZFNJ4APbs8 (failed)
  old prop read: 1GTX.QZFNJ4APbs8 (failed)
  prop read: vayM.xzB7oeH67F9 (failed)
  old prop read: vayM.xzB7oeH67F9 (failed)
  prop read: mvRC.SO8tGDPped9 (failed)
  old prop read: mvRC.SO8tGDPped9 (failed)
  prop read: eEx1.zo4dlnWWA0A (failed)
  old prop read: eEx1.zo4dlnWWA0A (failed)
  prop read: 5YuN._DdYWQ7_DEF (failed)
  old prop read: 5YuN._DdYWQ7_DEF (failed)
  prop read: 6NW+.OG+Sv+NxnRB (failed)
  old prop read: 6NW+.OG+Sv+NxnRB (failed)
  prop read: BUZT.wHOUAGcfug9 (failed)
  old prop read: BUZT.wHOUAGcfug9 (failed)
  prop read: 3p2J.EF_Wvc6p_p7 (failed)
  old prop read: 3p2J.EF_Wvc6p_p7 (failed)
  prop read: w7Y8.rlTunxHRvK1 (failed)
  old prop read: w7Y8.rlTunxHRvK1 (failed)
  prop read: nS1_.kR7HUuICU+D (failed)
  old prop read: nS1_.kR7HUuICU+D (failed)
  prop read: GA8e.5SJ3KMVAAgD (failed)
  old prop read: GA8e.5SJ3KMVAAgD (failed)
  prop read: rBUF.5xS4GrwfJ67 (failed)
  old prop read: rBUF.5xS4GrwfJ67 (failed)
  prop read: ZcKW.2OImT7beh+4 (failed)
  old prop read: ZcKW.2OImT7beh+4 (failed)
  prop read: z9pp.+GmdJItMGB9 (failed)
  old prop read: z9pp.+GmdJItMGB9 (failed)
  prop read: QL3u.gNN83gfynbD (failed)
  old prop read: QL3u.gNN83gfynbD (failed)
  prop read: tWJy.ld94kxNGZf5 (failed)
  old prop read: tWJy.ld94kxNGZf5 (failed)
  prop read: KiZ0.WYwRElrJa93 (failed)
  old prop read: KiZ0.WYwRElrJa93 (failed)
  prop read: ntp4.bvKf3UMzZfE (failed)
  old prop read: ntp4.bvKf3UMzZfE (failed)
  prop read: E349.DE8RM9cWQQ8 (failed)
  old prop read: E349.DE8RM9cWQQ8 (failed)
  prop read: hEKD.yhTOLOXWEq7 (failed)
  old prop read: hEKD.yhTOLOXWEq7 (failed)
  prop read: NhVi.YgT1Hy0M6x6 (failed)
  old prop read: NhVi.YgT1Hy0M6x6 (failed)
  prop read: qslm.B+yZ9Ve8gC1 (failed)
  old prop read: qslm.B+yZ9Ve8gC1 (failed)
  prop read: H20r.B+yZ9Ve8gC1 (failed)
  old prop read: H20r.B+yZ9Ve8gC1 (failed)
  prop read: iT2w.jDhFyyFrbg5 (failed)
  old prop read: iT2w.jDhFyyFrbg5 (failed)
  prop read: 9fI_.B+yZ9Ve8gC1 (failed)
  old prop read: 9fI_.B+yZ9Ve8gC1 (failed)
  prop read: cqY2.B+yZ9Ve8gC1 (failed)
  old prop read: cqY2.B+yZ9Ve8gC1 (failed)
  prop read: 30p6.B+yZ9Ve8gC1 (failed)
  old prop read: 30p6.B+yZ9Ve8gC1 (failed)
  prop read: XB3B.B+yZ9Ve8gC1 (failed)
  old prop read: XB3B.B+yZ9Ve8gC1 (failed)
  prop read: _MJF.gNN83gfynbD (failed)
  old prop read: _MJF.gNN83gfynbD (failed)
  prop read: KD9E.6choFOip+U0 (failed)
  old prop read: KD9E.6choFOip+U0 (failed)
  prop read: 3OOL.dcNp6AS8L+9 (failed)
  old prop read: 3OOL.dcNp6AS8L+9 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: QLVZ.SE1wIdpsiiC (failed)
  old prop read: QLVZ.SE1wIdpsiiC (failed)
  prop read: UfPf.8lRxanoJw62 (failed)
  old prop read: UfPf.8lRxanoJw62 (failed)
  prop read: LUEV.y5lbdhZ_1SF (failed)
  old prop read: LUEV.y5lbdhZ_1SF (failed)
  prop read: ofUZ.y5lbdhZ_1SF (failed)
  old prop read: ofUZ.y5lbdhZ_1SF (failed)
  prop read: Frkd.y5lbdhZ_1SF (failed)
  old prop read: Frkd.y5lbdhZ_1SF (failed)
  prop read: HKo0.UCahF2cUSn2 (failed)
  old prop read: HKo0.UCahF2cUSn2 (failed)
  prop read: i0+h.ESVs1s9RhT7 (failed)
  old prop read: i0+h.ESVs1s9RhT7 (failed)
  prop read: k4bc.9T1GDCLyFd9 (failed)
  old prop read: k4bc.9T1GDCLyFd9 (failed)
  prop read: pBe4.v+N+B0xY+P6 (failed)
  old prop read: pBe4.v+N+B0xY+P6 (failed)
  prop read: uIhY.gkSaZmjGyhD (failed)
  old prop read: uIhY.gkSaZmjGyhD (failed)
  prop read: zPk0.RTX9xWW_uz4 (failed)
  old prop read: zPk0.RTX9xWW_uz4 (failed)
  prop read: 2XnU.CCckIHJirFC (failed)
  old prop read: 2XnU.CCckIHJirFC (failed)
  prop read: FKGF.a0ve4Q0u1MD (failed)
  old prop read: FKGF.a0ve4Q0u1MD (failed)
  prop read: iVWJ.J7_oRypTyO7 (failed)
  old prop read: iVWJ.J7_oRypTyO7 (failed)
  prop read: hSuP.ywu2euu9AfE (failed)
  old prop read: hSuP.ywu2euu9AfE (failed)
  prop read: wn1q.Mr_0UuZRYy3 (failed)
  old prop read: wn1q.Mr_0UuZRYy3 (failed)
  prop read: rdCR.j8NaKXDZtZ6 (failed)
  old prop read: rdCR.j8NaKXDZtZ6 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: RRvF.GSopYcFr9cF (failed)
  old prop read: RRvF.GSopYcFr9cF (failed)
----- /proc/modules -----
  ppp_deflate 12878 0 - Live 0x00000000
  zlib_deflate 26622 1 ppp_deflate, Live 0x00000000
  bsd_comp 12842 0 - Live 0x00000000
  ppp_async 17307 1 - Live 0x00000000
  crc_ccitt 12595 1 ppp_async, Live 0x00000000
  option 21205 3 - Live 0x00000000
  usb_wwan 19779 1 option, Live 0x00000000
  usbserial 37203 9 option,usb_wwan, Live 0x00000000
  joydev 17393 0 - Live 0x00000000
  bnep 17923 2 - Live 0x00000000
  bluetooth 148839 7 bnep, Live 0x00000000
  snd_hda_codec_realtek 254125 1 - Live 0x00000000
  ppdev 12849 0 - Live 0x00000000
  snd_hda_intel 24262 0 - Live 0x00000000
  snd_hda_codec 91754 2 snd_hda_codec_realtek,snd_hda_intel, Live 0x00000000
  snd_hwdep 13276 1 snd_hda_codec, Live 0x00000000
  snd_pcm 80468 2 snd_hda_intel,snd_hda_codec, Live 0x00000000
  snd_seq_midi 13132 0 - Live 0x00000000
  snd_rawmidi 25241 1 snd_seq_midi, Live 0x00000000
  snd_seq_midi_event 14475 1 snd_seq_midi, Live 0x00000000
  usbhid 41905 0 - Live 0x00000000
  hid 77367 1 usbhid, Live 0x00000000
  usb_storage 44173 0 - Live 0x00000000
  snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event, Live 0x00000000
  uas 17699 0 - Live 0x00000000
  psmouse 73673 0 - Live 0x00000000
  snd_timer 28932 2 snd_pcm,snd_seq, Live 0x00000000
  serio_raw 12990 0 - Live 0x00000000
  snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x00000000
  i915 505108 2 - Live 0x00000000
  snd 55902 9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x00000000
  soundcore 12600 1 snd, Live 0x00000000
  drm_kms_helper 32889 1 i915, Live 0x00000000
  parport_pc 32114 1 - Live 0x00000000
  snd_page_alloc 14115 2 snd_hda_intel,snd_pcm, Live 0x00000000
  drm 192226 3 i915,drm_kms_helper, Live 0x00000000
  i2c_algo_bit 13199 1 i915, Live 0x00000000
  video 18908 1 i915, Live 0x00000000
  lp 17455 0 - Live 0x00000000
  parport 40930 3 ppdev,parport_pc,lp, Live 0x00000000
  firewire_ohci 35854 0 - Live 0x00000000
  firewire_core 56937 1 firewire_ohci, Live 0x00000000
  crc_itu_t 12627 1 firewire_core, Live 0x00000000
  8139too 23283 0 - Live 0x00000000
  8139cp 22636 0 - Live 0x00000000
  floppy 60310 0 - Live 0x00000000
----- /proc/modules end -----
  used irqs: 0,1,6,7,8,9,10,12,14,15,16,18,19,20,21,23,40,41,63
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0x1f (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (57 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

08: None 00.0: 0701 Parallel controller (SPP)
  [Created at misc.262]
  Unique ID: YMnp.ecK7NLYWZ5D
  Hardware Class: unknown
  Model: "Parallel controller"
  Device File: /dev/lp0
  I/O Ports: 0x378-0x37a (rw)
  I/O Ports: 0x778-0x77a (rw)
  DMA: 3
  IRQ: 7 (no events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

09: None 00.0: 0102 Floppy disk controller
  [Created at misc.282]
  Unique ID: rdCR.3wRL2_g4d2B
  Hardware Class: storage
  Model: "Floppy disk controller"
  I/O Port: 0x3f2 (rw)
  I/O Ports: 0x3f4-0x3f5 (rw)
  I/O Port: 0x3f7 (rw)
  DMA: 2
  IRQ: 6 (3 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0x4dedcfff (rw)
  Memory Size: 1 GB + 256 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.0: 0600 Host bridge
  [Created at pci.318]
  Unique ID: qLht.Fo0h7LoGZYE
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "Intel 82915G/P/GV/GL/PL/910GL Memory Controller Hub"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2580 "82915G/P/GV/GL/PL/910GL Memory Controller Hub"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a08 
  Revision: 0x04
  Driver: "agpgart-intel"
  Module Alias: "pci:v00008086d00002580sv0000103Csd00002A08bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _Znp.EAFRYfLxHkA
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 915 G"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2582 "915 G"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a08 
  Revision: 0x04
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xcfe00000-0xcfe7ffff (rw,non-prefetchable)
  I/O Ports: 0xcc00-0xcc07 (rw)
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xcfdc0000-0xcfdfffff (rw,non-prefetchable)
  IRQ: 16 (292981 events)
  Module Alias: "pci:v00008086d00002582sv0000103Csd00002A08bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  Unique ID: ruGf.WzkqjRbwQ0D
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel 82915G Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2782 "82915G Integrated Graphics Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a08 
  Revision: 0x04
  Memory Range: 0xcfe80000-0xcfefffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d00002782sv0000103Csd00002A08bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: u1Nb.1iKcnAwVcq9
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Hewlett-Packard Company PufferM-UL8E"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2668 "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a09 "PufferM-UL8E"
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xcfdb8000-0xcfdbbfff (rw,non-prefetchable)
  IRQ: 41 (14461 events)
  Module Alias: "pci:v00008086d00002668sv0000103Csd00002A09bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 1c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: z8Q3.hdHR1LU2D6A
  SysFS ID: /devices/pci0000:00/0000:00:1c.0
  SysFS BusID: 0000:00:1c.0
  Hardware Class: bridge
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2660 "82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 40 (no events)
  Module Alias: "pci:v00008086d00002660sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 1d.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: 1GTX.QZFNJ4APbs8
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: usb controller
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2658 "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0xc400-0xc41f (rw)
  IRQ: 23 (61357 events)
  Module Alias: "pci:v00008086d00002658sv0000103Csd00002A0Abc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 1d.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: vayM.xzB7oeH67F9
  SysFS ID: /devices/pci0000:00/0000:00:1d.1
  SysFS BusID: 0000:00:1d.1
  Hardware Class: usb controller
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2659 "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0xc480-0xc49f (rw)
  IRQ: 19 (24092 events)
  Module Alias: "pci:v00008086d00002659sv0000103Csd00002A0Abc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 1d.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: mvRC.SO8tGDPped9
  SysFS ID: /devices/pci0000:00/0000:00:1d.2
  SysFS BusID: 0000:00:1d.2
  Hardware Class: usb controller
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x265a "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0xc800-0xc81f (rw)
  IRQ: 18 (no events)
  Module Alias: "pci:v00008086d0000265Asv0000103Csd00002A0Abc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 1d.3: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: eEx1.zo4dlnWWA0A
  SysFS ID: /devices/pci0000:00/0000:00:1d.3
  SysFS BusID: 0000:00:1d.3
  Hardware Class: usb controller
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x265b "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0xc880-0xc89f (rw)
  IRQ: 16 (292981 events)
  Module Alias: "pci:v00008086d0000265Bsv0000103Csd00002A0Abc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 1d.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  Unique ID: 5YuN._DdYWQ7_DEF
  SysFS ID: /devices/pci0000:00/0000:00:1d.7
  SysFS BusID: 0000:00:1d.7
  Hardware Class: usb controller
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x265c "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xcfdb7c00-0xcfdb7fff (rw,non-prefetchable)
  IRQ: 23 (61357 events)
  Module Alias: "pci:v00008086d0000265Csv0000103Csd00002A0Abc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 1e.0: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  Unique ID: 6NW+.OG+Sv+NxnRB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0
  SysFS BusID: 0000:00:1e.0
  Hardware Class: bridge
  Model: "Intel 82801 PCI Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x244e "82801 PCI Bridge"
  Revision: 0xd3
  Module Alias: "pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 1f.0: 0601 ISA bridge
  [Created at pci.318]
  Unique ID: BUZT.wHOUAGcfug9
  SysFS ID: /devices/pci0000:00/0000:00:1f.0
  SysFS BusID: 0000:00:1f.0
  Hardware Class: bridge
  Model: "Intel 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2640 "82801FB/FR (ICH6/ICH6R) LPC Interface Bridge"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Module Alias: "pci:v00008086d00002640sv0000103Csd00002A0Abc06sc01i00"
  Driver Info #0:
    Driver Status: intel_rng is not active
    Driver Activation Cmd: "modprobe intel_rng"
  Driver Info #1:
    Driver Status: iTCO_wdt is not active
    Driver Activation Cmd: "modprobe iTCO_wdt"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 1f.1: 0101 IDE interface
  [Created at pci.318]
  Unique ID: 3p2J.EF_Wvc6p_p7
  SysFS ID: /devices/pci0000:00/0000:00:1f.1
  SysFS BusID: 0000:00:1f.1
  Hardware Class: storage
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x266f "82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "ata_piix"
  Driver Modules: "ata_piix"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0xffa0-0xffaf (rw)
  IRQ: 18 (no events)
  Module Alias: "pci:v00008086d0000266Fsv0000103Csd00002A0Abc01sc01i8a"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 1f.2: 0101 IDE interface
  [Created at pci.318]
  Unique ID: w7Y8.rlTunxHRvK1
  SysFS ID: /devices/pci0000:00/0000:00:1f.2
  SysFS BusID: 0000:00:1f.2
  Hardware Class: storage
  Model: "Intel 82801FB/FW (ICH6/ICH6W) SATA Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2651 "82801FB/FW (ICH6/ICH6W) SATA Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  Driver: "ata_piix"
  Driver Modules: "ata_piix"
  I/O Ports: 0xc080-0xc087 (rw)
  I/O Ports: 0xc000-0xc003 (rw)
  I/O Ports: 0xbc00-0xbc07 (rw)
  I/O Ports: 0xb880-0xb883 (rw)
  I/O Ports: 0xb800-0xb80f (rw)
  IRQ: 19 (24092 events)
  Module Alias: "pci:v00008086d00002651sv0000103Csd00002A0Abc01sc01i8f"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 1f.3: 0c05 SMBus
  [Created at pci.318]
  Unique ID: nS1_.kR7HUuICU+D
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: unknown
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x266a "82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0a 
  Revision: 0x03
  I/O Ports: 0x400-0x41f (rw)
  IRQ: 10 (no events)
  Module Alias: "pci:v00008086d0000266Asv0000103Csd00002A0Abc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_i801 is not active
    Driver Activation Cmd: "modprobe i2c_i801"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 201.0: 0c00 FireWire (IEEE 1394) (OHCI)
  [Created at pci.318]
  Unique ID: GA8e.5SJ3KMVAAgD
  Parent ID: 6NW+.OG+Sv+NxnRB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:01.0
  SysFS BusID: 0000:02:01.0
  Hardware Class: firewire controller
  Model: "VIA VT6306 Fire II IEEE 1394 OHCI Link Layer Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3044 "VT6306 Fire II IEEE 1394 OHCI Link Layer Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0c 
  Revision: 0x80
  Driver: "firewire_ohci"
  Driver Modules: "firewire_ohci"
  Memory Range: 0xcffff800-0xcfffffff (rw,non-prefetchable)
  I/O Ports: 0xec00-0xec7f (rw)
  IRQ: 20 (66 events)
  Module Alias: "pci:v00001106d00003044sv0000103Csd00002A0Cbc0Csc00i10"
  Driver Info #0:
    Driver Status: ohci1394 is not active
    Driver Activation Cmd: "modprobe ohci1394"
  Driver Info #1:
    Driver Status: firewire_ohci is active
    Driver Activation Cmd: "modprobe firewire_ohci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

28: PCI 202.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.5xS4GrwfJ67
  Parent ID: 6NW+.OG+Sv+NxnRB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
  SysFS BusID: 0000:02:02.0
  Hardware Class: network
  Model: "Realtek RTL-8139/8139C/8139C+"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8139 "RTL-8139/8139C/8139C+"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a0b 
  Revision: 0x10
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth0
  I/O Ports: 0xe800-0xe8ff (rw)
  Memory Range: 0xcffff400-0xcffff4ff (rw,non-prefetchable)
  IRQ: 21 (no events)
  HW Address: 00:11:2f:a6:54:ae
  Link detected: no
  Module Alias: "pci:v000010ECd00008139sv0000103Csd00002A0Bbc02sc00i00"
  Driver Info #0:
    Driver Status: 8139too is active
    Driver Activation Cmd: "modprobe 8139too"
  Driver Info #1:
    Driver Status: 8139cp is active
    Driver Activation Cmd: "modprobe 8139cp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

29: PCI 205.0: 0780 Communication controller
  [Created at pci.318]
  Unique ID: ZcKW.2OImT7beh+4
  Parent ID: 6NW+.OG+Sv+NxnRB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:05.0
  SysFS BusID: 0000:02:05.0
  Hardware Class: unknown
  Model: "Agere V.92 56K WinModem"
  Vendor: pci 0x11c1 "Agere Systems"
  Device: pci 0x048c "V.92 56K WinModem"
  SubVendor: pci 0x11c1 "Agere Systems"
  SubDevice: pci 0x044c 
  Revision: 0x03
  Memory Range: 0xcffff000-0xcffff0ff (rw,non-prefetchable)
  I/O Ports: 0xe480-0xe487 (rw)
  I/O Ports: 0xe000-0xefff (rw)
  IRQ: 255 (no events)
  Module Alias: "pci:v000011C1d0000048Csv000011C1sd0000044Cbc07sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

30: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: QL3u.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: tWJy.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: KiZ0.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: ntp4.bvKf3UMzZfE
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: E349.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: hEKD.yhTOLOXWEq7
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0700 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: NhVi.YgT1Hy0M6x6
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0401 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: qslm.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: H20r.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: iT2w.jDhFyyFrbg5
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: INT 
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: 9fI_.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: cqY2.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0c
  SysFS BusID: 00:0c
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: 30p6.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0d
  SysFS BusID: 00:0d
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: XB3B.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0e
  SysFS BusID: 00:0e
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: _MJF.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:0f
  SysFS BusID: 00:0f
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

46: SCSI 01.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  Unique ID: KD9E.6choFOip+U0
  Parent ID: 3p2J.EF_Wvc6p_p7
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:1:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  Hardware Class: cdrom
  Model: "SONY DVD RW AW-G170A"
  Vendor: "SONY"
  Device: "DVD RW AW-G170A"
  Revision: "1.75"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-SONY_DVD_RW_AW-G170A, /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:1:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (IDE interface)
  Drive Speed: 94

47: IDE 200.0: 10600 Disk
  [Created at block.243]
  Unique ID: 3OOL.dcNp6AS8L+9
  Parent ID: w7Y8.rlTunxHRvK1
  SysFS ID: /class/block/sda
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0
  Hardware Class: disk
  Model: "WDC WD800JD-22JN"
  Vendor: "WDC"
  Device: "WD800JD-22JN"
  Revision: "05.0"
  Driver: "ata_piix", "sd"
  Driver Modules: "ata_piix"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  Device Number: block 8:0-8:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (IDE interface)

48: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.dcNp6AS8L+9
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part1, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/ececbda8-912d-4c7c-9065-122f7942b6b0
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

49: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.dcNp6AS8L+9
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part2, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

50: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.dcNp6AS8L+9
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-WDC_WD800JD-22JNA0_WD-WMAM91950835-part5, /dev/disk/by-id/scsi-SATA_WDC_WD800JD-22JWD-WMAM91950835-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5, /dev/disk/by-uuid/cd20ec63-2c4c-48b5-beeb-8f441259208a
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

51: SCSI 400.0: 10600 Disk
  [Created at block.254]
  Unique ID: UfPf.8lRxanoJw62
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sdb
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:0
  Hardware Class: disk
  Model: "Generic USB SD Reader"
  Vendor: usb 0x058f "Generic"
  Device: usb 0x9360 "USB SD Reader"
  Revision: "1.00"
  Serial ID: "9205291"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdb (/dev/sg2)
  Device Files: /dev/sdb, /dev/disk/by-id/usb-Generic_USB_SD_Reader_9205291-0:0, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0
  Device Number: block 8:16-8:31 (char 21:2)
  Speed: 12 Mbps
  Module Alias: "usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: uas is active
    Driver Activation Cmd: "modprobe uas"
  Driver Info #1:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

52: SCSI 400.1: 10600 Disk
  [Created at block.254]
  Unique ID: LUEV.y5lbdhZ_1SF
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sdc
  SysFS BusID: 4:0:0:1
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:1
  Hardware Class: disk
  Model: "Generic USB CF Reader"
  Vendor: usb 0x058f "Generic"
  Device: usb 0x9360 "USB CF Reader"
  Revision: "1.01"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdc (/dev/sg3)
  Device Files: /dev/sdc, /dev/disk/by-id/usb-Generic_USB_CF_Reader_9205291-0:1, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1
  Device Number: block 8:32-8:47 (char 21:3)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

53: SCSI 400.2: 10600 Disk
  [Created at block.254]
  Unique ID: ofUZ.y5lbdhZ_1SF
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sdd
  SysFS BusID: 4:0:0:2
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:2
  Hardware Class: disk
  Model: "Generic USB SM Reader"
  Vendor: usb 0x058f "Generic"
  Device: usb 0x9360 "USB SM Reader"
  Revision: "1.02"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdd (/dev/sg4)
  Device Files: /dev/sdd, /dev/disk/by-id/usb-Generic_USB_SM_Reader_9205291-0:2, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2
  Device Number: block 8:48-8:63 (char 21:4)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

54: SCSI 400.3: 10600 Disk
  [Created at block.254]
  Unique ID: Frkd.y5lbdhZ_1SF
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sde
  SysFS BusID: 4:0:0:3
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/host4/target4:0:0/4:0:0:3
  Hardware Class: disk
  Model: "Generic USB MS Reader"
  Vendor: usb 0x058f "Generic"
  Device: usb 0x9360 "USB MS Reader"
  Revision: "1.03"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sde (/dev/sg5)
  Device Files: /dev/sde, /dev/disk/by-id/usb-Generic_USB_MS_Reader_9205291-0:3, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3
  Device Number: block 8:64-8:79 (char 21:5)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

55: SCSI 900.0: 10602 CD-ROM
  [Created at block.247]
  Unique ID: HKo0.UCahF2cUSn2
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sr1
  SysFS BusID: 9:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:0
  Hardware Class: cdrom
  Model: "HUAWEI Mass Storage"
  Vendor: usb 0x12d1 "HUAWEI"
  Device: usb 0x1412 "Mass Storage"
  Revision: "2.31"
  Serial ID: ""
  Driver: "usb-storage", "sr"
  Driver Modules: "usb_storage"
  Device File: /dev/sr1 (/dev/sg6)
  Device Files: /dev/sr1, /dev/scd1, /dev/disk/by-id/usb-HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:0, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:0, /dev/cdrom1
  Device Number: block 11:1 (char 21:6)
  Speed: 12 Mbps
  Module Alias: "usb:v12D1p1412d0000dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Driver Info #1:
    Driver Status: uas is active
    Driver Activation Cmd: "modprobe uas"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)
  Drive Speed: 1
  Volume ID: "RELIANCE"
  Creation date: "2009012401000000"

56: SCSI 900.1: 10600 Disk
  [Created at block.254]
  Unique ID: i0+h.ESVs1s9RhT7
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /class/block/sdf
  SysFS BusID: 9:0:0:1
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.3/host9/target9:0:0/9:0:0:1
  Hardware Class: disk
  Model: "HUAWEI SD Storage"
  Vendor: usb 0x12d1 "HUAWEI"
  Device: usb 0x1412 "SD Storage"
  Revision: "2.31"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdf (/dev/sg7)
  Device Files: /dev/sdf, /dev/disk/by-id/usb-HUAWEI_SD_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0:1, /dev/disk/by-path/pci-0000:00:1d.3-usb-0:2:1.3-scsi-0:0:0:1
  Device Number: block 8:80-8:95 (char 21:7)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: k4bc.9T1GDCLyFd9
  Parent ID: 5YuN._DdYWQ7_DEF
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-12-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-12-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (USB Controller)

58: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.v+N+B0xY+P6
  Parent ID: 1GTX.QZFNJ4APbs8
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-12-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-12-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

59: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: uIhY.gkSaZmjGyhD
  Parent ID: vayM.xzB7oeH67F9
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-12-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-12-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

60: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: zPk0.RTX9xWW_uz4
  Parent ID: mvRC.SO8tGDPped9
  SysFS ID: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-12-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-12-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

61: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 2XnU.CCckIHJirFC
  Parent ID: eEx1.zo4dlnWWA0A
  SysFS ID: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-12-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-12-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.3"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

62: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  Unique ID: FKGF.a0ve4Q0u1MD
  Parent ID: pBe4.v+N+B0xY+P6
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  SysFS BusID: 2-1:1.0
  Hardware Class: keyboard
  Model: "USB Keykoard"
  Hotplug: USB
  Vendor: usb 0x1c4f "USB"
  Device: usb 0x0002 "USB Keykoard"
  Revision: "1.10"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event2
  Device Files: /dev/input/event2, /dev/input/by-id/usb-USB_USB_Keykoard-event-kbd, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd
  Device Number: char 13:66
  Speed: 1.5 Mbps
  Module Alias: "usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

63: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: iVWJ.J7_oRypTyO7
  Parent ID: pBe4.v+N+B0xY+P6
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
  SysFS BusID: 2-1:1.1
  Hardware Class: unknown
  Model: "USB Keykoard"
  Hotplug: USB
  Vendor: usb 0x1c4f "USB"
  Device: usb 0x0002 "USB Keykoard"
  Revision: "1.10"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-id/usb-USB_USB_Keykoard-event-if01, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event
  Device Number: char 13:67
  Speed: 1.5 Mbps
  Module Alias: "usb:v1C4Fp0002d0110dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

64: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: hSuP.ywu2euu9AfE
  Parent ID: pBe4.v+N+B0xY+P6
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
  SysFS BusID: 2-2:1.0
  Hardware Class: mouse
  Model: "Pixart Imaging USB OPTICAL MOUSE"
  Hotplug: USB
  Vendor: usb 0x093a "Pixart Imaging, Inc."
  Device: usb 0x2510 "USB OPTICAL MOUSE"
  Revision: "1.00"
  Compatible to: int 0x0210 0x0013
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-event-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse, /dev/input/by-id/usb-PIXART_USB_OPTICAL_MOUSE-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 1.5 Mbps
  Module Alias: "usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

66: USB 00.0: 0700 Serial controller
  [Created at usb.122]
  Unique ID: wn1q.Mr_0UuZRYy3
  Parent ID: 2XnU.CCckIHJirFC
  SysFS ID: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0
  SysFS BusID: 5-2:1.0
  Hardware Class: unknown
  Model: "HUAÿWEI HUAWEI Mobile"
  Hotplug: USB
  Vendor: usb 0x12d1 "HUAÿWEI TECHNOLOGIES"
  Device: usb 0x1412 "HUAWEI Mobile"
  Serial ID: ""
  Driver: "option"
  Driver Modules: "option"
  Device File: /dev/ttyUSB0
  Device Files: /dev/ttyUSB0, /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0, /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0
  Device Number: char 188:0
  Speed: 12 Mbps
  Module Alias: "usb:v12D1p1412d0000dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Driver Info #1:
    Driver Status: option is active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #61 (Hub)

71: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.3.4 "Intel(R) Pentium(R) 4 CPU 2.93GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,constant_tsc,up,pebs,bts,pni,dtes64,monitor,ds_cpl,cid,xtpr
  Clock: 2933 MHz
  BogoMips: 5864.03
  Cache: 1024 kb
  Units/Processor: 1
  Config Status: cfg=new, avail=yes, need=no, active=unknown

72: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

73: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.5xS4GrwfJ67
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth0
  HW Address: 00:11:2f:a6:54:ae
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (Ethernet controller)

74: None 00.0: 10780 Network Interface
  [Created at net.124]
  Unique ID: RRvF.GSopYcFr9cF
  SysFS ID: /class/net/ppp0
  Hardware Class: network interface
  Model: "Network Interface"
  Device File: ppp0
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by jjex22 on 2011-11-15
ah right, well that'll be the most recent version of it then, that's version 3.28, so first things first make sure you have an older version of the bios (pre 3.28 )

Edit: I can't see why the .exe wouldn't run from dos, I've had no problem using this method for dell, samsung and asus pc's, but if you do want to be really safe, you can always install a copy of xp temporarily in some free space - you don't need to activate it as you'll be deleting it straight after? Bios updates can go wrong and it is only an hour install, so it's up to you, just remember you'll need to be an administrator to do it

---

### Post by ask_ on 2011-11-15
Yeah. That's why I was worried and apprehensive.
I do have an older version. Mine is 3.06(released in 2004) and the one they are providing is 3.28(released in 2006).


I wish I hadn't deleted Windows XP in such a hurry. :|


I will mostly install Windows XP and then do the BIOS upgrade (just to be very safe). I think I have a set of recovery disks of HP.

But anyways , thanks so much for the help you have given in this thread.(& congrats for getting a new profile picture. If I am not wrong you just got 50 beans ;) )
I will mark the thread as solved now.

Mischief Managed!

---

### Post by jjex22 on 2011-11-15
You're welcome, and thanks - finally got to the stage where I can start putting some knowledge back in!

---

### Post by ask_ on 2013-04-26
Sorry for bumping into an old solved thread. 

I finally updated my BIOS after 1.5 years since I posted this thread. :) 

I was hesitant to do so from a non Windows XP environment. I finally installed Windows XP after so many days. I wanted to format my PC to install Lubuntu 13.04 , so I thought this would be a good time to put in Windows XP.

But , sadly the keyboard interface error issue has not been resolved as even the new Bios does not have that option. So have to live with it I guess. They have not released any updates since 2006 thus this issue was never addressed.

Is it possible to install some other BIOS ? I mean one of a different HP product ? (I guess this may be too risky.)

---

### Post by mörgæs on 2013-04-26
Yes, it is indeed risky to try a different BIOS, and hopefully the process will not run at all. Don't go there.

You can try to reset the BIOS to factory settings if you have been playing around too much in there, but else I guess you are right: You have to live with it.

---

### Post by ask_ on 2013-04-26
> **mörgæs said:**
> Yes, it is indeed risky to try a different BIOS, and hopefully the process will not run at all. Don't go there.

You can try to reset the BIOS to factory settings if you have been playing around too much in there, but else I guess you are right: You have to live with it.

Thanks for the warning.

No , I did not do anything after updating the BIOS. The update is working normally so no worries over there.

Ya I will not venture into that area now. 

Thanks.

---

