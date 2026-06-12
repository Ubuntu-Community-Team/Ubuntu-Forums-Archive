---
title: "Unable to mount USB 3.0 sticks"
date: 2014-12-11
forum: Hardware
---

### Post by Peter_Kirsner on 2014-12-11
Hello guys,

I would like to ask you if can help me to find where is a problem with USB 3.0 memory sticks on my older Lenovo Think-center M78 computer.
When I connect USB 3.0 stick it is recognized with a system (based on dmesg output) but I am not able to mount it. There in no /dev/sdc device :( Is it a hardware problem or something with SW?

Ubuntu is in version 12.04.LTS
Linux XXX 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Here is an output from dmesg
```
[602639.761795] usb 1-2: new high-speed USB device number 5 using ehci-pci
[602639.910077] usb 1-2: New USB device found, idVendor=0951, idProduct=1666
[602639.910085] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[602639.910091] usb 1-2: Product: DataTraveler 3.0
[602639.910095] usb 1-2: Manufacturer: Kingston
[602639.910099] usb 1-2: SerialNumber: 60A44C3FACD3BE91996F039C
[602639.910691] scsi9 : usb-storage 1-2:1.0
[602641.009401] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 3.0 PMAP PQ: 0 ANSI: 6
[602641.010324] sd 9:0:0:0: Attached scsi generic sg2 type 0
[602641.469896] sd 9:0:0:0: [sdc] 30244864 512-byte logical blocks: (15.4 GB/14.4 GiB)
[602641.472012] sd 9:0:0:0: [sdc] Write Protect is off
[602641.472017] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[602641.474152] sd 9:0:0:0: [sdc] No Caching mode page present
[602641.474159] sd 9:0:0:0: [sdc] Assuming drive cache: write through
```

dmesg output from another USB 3.0 stick (also not working)
```
[602736.679752] usb 1-2: new high-speed USB device number 6 using ehci-pci
[602736.903303] usb 1-2: New USB device found, idVendor=0951, idProduct=16a2
[602736.903312] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[602736.903317] usb 1-2: Product: DTR30G2
[602736.903321] usb 1-2: Manufacturer: Kingston
[602736.903325] usb 1-2: SerialNumber: 0018F30BFEC4BE8151EB1E24
[602736.903915] scsi10 : usb-storage 1-2:1.0
[602737.968836] scsi 10:0:0:0: Direct-Access     Kingston DTR30G2          PMAP PQ: 0 ANSI: 6
[602737.969810] sd 10:0:0:0: Attached scsi generic sg2 type 0
[602738.675338] sd 10:0:0:0: [sdc] 61472768 512-byte logical blocks: (31.4 GB/29.3 GiB)
[602738.676956] sd 10:0:0:0: [sdc] Write Protect is off
[602738.676964] sd 10:0:0:0: [sdc] Mode Sense: 23 00 00 00
[602738.678578] sd 10:0:0:0: [sdc] No Caching mode page present
[602738.678586] sd 10:0:0:0: [sdc] Assuming drive cache: write through
```

And dmesg output from working USB 2.0 stick (I can see /dev/sdc device and mount it correctly):
```
[603009.645290] usb 1-2: new high-speed USB device number 7 using ehci-pci
[603009.780695] usb 1-2: New USB device found, idVendor=0951, idProduct=1643
[603009.780704] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[603009.780709] usb 1-2: Product: DataTraveler G3
[603009.780714] usb 1-2: Manufacturer: Kingston
[603009.780718] usb 1-2: SerialNumber: 001CC0EC34F1FC11271723D0
[603009.781492] scsi11 : usb-storage 1-2:1.0
[603010.834586] scsi 11:0:0:0: Direct-Access     Kingston DataTraveler G3  1.00 PQ: 0 ANSI: 4
[603010.835128] sd 11:0:0:0: Attached scsi generic sg2 type 0
[603010.838211] sd 11:0:0:0: [sdc] 7820360 512-byte logical blocks: (4.00 GB/3.72 GiB)
[603010.838810] sd 11:0:0:0: [sdc] Write Protect is off
[603010.838815] sd 11:0:0:0: [sdc] Mode Sense: 45 00 00 00
[603010.839427] sd 11:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[603010.846046]  sdc: sdc1
[603010.850649] sd 11:0:0:0: [sdc] Attached SCSI removable disk
```

I will try to boot from Ubuntu 14.10 to see if it is a hardware problem. What else would you recommend me to try?

thaaanks a lot for any advice!!!

Peter

---

### Post by sudodus on 2014-12-11
If the pendrive is good (works in some other computer), it could be bad cooperation between the pendrive and the motherboard or BIOS system. Kingston is a well-known brand name, and I have a similar (Kingston Datatraveller Ultimate G3 32 GB) USB 3 pendrive, that works in several computers (including an old IBM Thinkpad T41, which can even boot from it).

Have you tried all USB ports of the computer?

***Edit***: Try with ***gparted*** - check that gparted can recognize each of the pendrives.

---

### Post by Peter_Kirsner on 2014-12-11
Pendrives work fine on other computers (windows and SLES11 also). I've tried all usb ports on the front panel and also from behind directly connected to the MB. I will check BIOS settings if there are some USB settings as well.

THX

---

### Post by sudodus on 2014-12-11
Then I suspect bad cooperation between the pendrive and the motherboard or BIOS system. It is a good idea to check and maybe tweak the BIOS settings.

I have a pendrive (Transcend Jetflash 500 8GB USB 2) which was not recognized by the BIOS in a Thinkpad T42, so it  could not be selected. It failed several times. It was recognized by the  BIOS when connected via a USB hub*, and then it could boot.

See this link for more details [http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
[HR][/HR]* hub alias extension box

---

### Post by mörgæs on 2014-12-11
> **Peter_Kirsner said:**
> I will try to boot from Ubuntu 14.10 to see if it is a hardware problem.

Yes, please do and post the results.

---

### Post by Peter_Kirsner on 2014-12-12
I checked BIOS and everything is set correctly so I booted Ubuntu 14.10 from USB (Kingstone, USB 3.0) and when I plugged another USB 3.0 pendrive everything was fine. So there is no HW problem.

output from dmesg:
```
[   62.512210] usb 1-2: new high-speed USB device number 3 using ehci-pci 
[   62.660678] usb 1-2: New USB device found, idVendor=0951, idProduct=1666 
[   62.660682] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[   62.660685] usb 1-2: Product: DataTraveler 3.0 
[   62.660686] usb 1-2: Manufacturer: Kingston 
[   62.660688] usb 1-2: SerialNumber: 60A44C3D7ECDBE919974038C 
[   62.660969] usb-storage 1-2:1.0: USB Mass Storage device detected 
[   62.661083] scsi7 : usb-storage 1-2:1.0 
[   63.764135] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 3.0 PMAP PQ: 0 ANSI: 6 
[   63.764446] sd 7:0:0:0: Attached scsi generic sg3 type 0 
[   64.218941] sd 7:0:0:0: [sdc] 30244864 512-byte logical blocks: (15.4 GB/14.4 GiB) 
[   64.221066] sd 7:0:0:0: [sdc] Write Protect is off 
[   64.221071] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00 
[   64.223194] sd 7:0:0:0: [sdc] No Caching mode page found 
[   64.223199] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[   64.307181]  sdc: sdc1 
[   64.313259] sd 7:0:0:0: [sdc] Attached SCSI removable disk 
[   64.610020] ipmi_si: There appears to be no BMC at this location

```

The only difference is in this line:
```
[   64.307181]  sdc: sdc1
```
What can I do in order to be able to use USB 3.0 pendrives on Ubuntu 12.04 instalation? What else to check? This computer is not connected to the Internet...

---

### Post by mörgæs on 2014-12-12
Wouldn't it be best to forget about the old stuff and do a fresh install of 14.10, now that you know it supports your hardware better?

---

### Post by Peter_Kirsner on 2014-12-12
Unfortunately, it is not that easy :) This computer is used as AV scanner. There were installed and configured several AV scanner engines and reporting tools that were not compatible with newer versions of Ubuntu. There were problem with missing dependencies if I remember when my colleague tried to use 14.04 LTS.

Maybe I will try one more time by myself but I am not as experienced as was my colleague with Linux / Ubuntu.

But anyway I am still open to any advice from your side :)

Thanks a lot in advance...

---

### Post by mörgæs on 2014-12-12
Sounds like a setup which must be stable for long periods of time, so maybe 14.04.1 is a better option. Did you try this one in a live boot? 

If you have some free space on the hard disk you could install 14.* in a dual boot for experimenting without erasing 12.04.

---

