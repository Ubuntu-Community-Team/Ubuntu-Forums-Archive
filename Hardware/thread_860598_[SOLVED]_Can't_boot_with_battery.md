---
title: "[SOLVED] Can't boot with battery"
date: 2008-07-15
forum: Hardware
---

### Post by Sim777 on 2008-07-15
I have 7.10  on Inspiron 1501 and one day I mistakenly left AC cable unplugged which drained battery completely. When I came back, system would not boot up with battery plugged in, it only starts when battery is out or I add "acpi=off" in grab bootup menu. 

here is one lines from /var/log/debug that is constantly reproduced.  

 APIC error on CPU0: 40(40)



I reinstalled acpi with modifications to grub and without battery, but each time I get same result; system just hands. Even caps lock none responsive. 

Help...  I'd like to have battery with acpi running since it tells me how much battery power left and I can change voltage to CPU.

---

### Post by phidia on 2008-07-15
Googling that error turns up [two related bugs]("https://bugs.launchpad.net/ubuntu/+bug/227008") at launchpad.
You may want to look at the [older bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66900") because there are suggestions there on dealing with that. I'm not sure if that fixes the inability to boot when using battery or not though.

---

### Post by dinub1 on 2008-07-15
> **Sim777 said:**
> I have 7.10  on Inspiron 1501 and one day I mistakenly left AC cable unplugged which drained battery completely. When I came back, system would not boot up with battery plugged in, it only starts when battery is out or I add "acpi=off" in grab bootup menu. 

here is one lines from /var/log/debug that is constantly reproduced.  

 APIC error on CPU0: 40(40)



I reinstalled acpi with modifications to grub and without battery, but each time I get same result; system just hands. Even caps lock none responsive. 

Help...  I'd like to have battery with acpi running since it tells me how much battery power left and I can change voltage to CPU.

Have you checked if laptop battery is possibly damaged by deep discharge and possibly in reverse polarity? That smells like a damaged battery in my view.

---

### Post by Sim777 on 2008-07-15
> **dinub1 said:**
> Have you checked if laptop battery is possibly damaged by deep discharge and possibly in reverse polarity? That smells like a damaged battery in my view. 

Battery is fine. Windows runs it properly, and if I run acpi=off in 7.10, I can use it on ubuntu (without knowing how much power left)

---

### Post by dinub1 on 2008-07-15
> **Sim777 said:**
> Battery is fine. Windows runs it properly, and if I run acpi=off in 7.10, I can use it on ubuntu (without knowing how much power left)

I see. There must be other sort of software issue and not hardware. I do not know how to solve this. Now thinking twice,  I think you couldn't have damaged the battery. When battery is drained and no power supply is attached, laptop would automatically shut down.

---

### Post by Sim777 on 2008-07-15
> **phidia said:**
> Googling that error turns up [two related bugs]("https://bugs.launchpad.net/ubuntu/+bug/227008") at launchpad.
You may want to look at the [older bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66900") because there are suggestions there on dealing with that. I'm not sure if that fixes the inability to boot when using battery or not though.

I looked over those, and few others...and nothing is related to battery.

---

### Post by Sim777 on 2008-07-18
Also, system crashes if I plug battery in whiles OS is running.......

---

### Post by Sim777 on 2008-07-18
Here's log when system starts up....with battery it doesn't go any further. 


```
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.420284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_92_24_55_b4'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.436931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4380_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.437519] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_oss_pcm_1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.437942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_oss_pcm_0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.439955] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_alsa_control__1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.440543] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_oss_pcm_0_0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.441068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_oss_mixer__1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.443529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_alsa_capture_0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.444140] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_alsa_playback_0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.446062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_alsa_capture_1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.447134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4383_alsa_playback_1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.447660] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.448081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.448522] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.448938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.449426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.449838] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_0_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.450223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_1_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.450603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_2_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.450982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_3_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.451405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_4_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.451794] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_5_usbraw'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.452226] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_TSSTcorp_DVD_/_RW_TS_L632D'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.452643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_TOSHIBA_MK6034GSX_Y6SSTK8AT'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.561485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_07D7_0106'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.762105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_467860C27860B1FB'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.767575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.774296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_46e05431_2221_4b60_9875_3b625f12bbf9'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.779438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_ce726406_735a_464f_859c_022a086992d1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.787941] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.788440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.788925] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Jul 18 14:41:12 sim-laptop NetworkManager: <debug> [1216410072.789394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_ACAD'). 
```

---

### Post by Sim777 on 2008-07-18
If following services are shutdown "acpid" and "apmd", 

Xorg.0.log gives constantly following error.  

(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused) 

Battery can be attached and system does not crash.

---

### Post by Sim777 on 2008-07-18
I inserted battery.

I turned on "apmd" service. Same error displayed. 

Then I turned on  "acpid" 

Following error started replaying:

APIC error on CPU0: 40(40)


System now can be rebooted without freezes. 

Problem solved.

---

