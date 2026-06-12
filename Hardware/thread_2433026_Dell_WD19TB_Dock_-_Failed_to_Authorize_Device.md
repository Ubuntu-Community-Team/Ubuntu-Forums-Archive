---
title: "Dell WD19TB Dock - Failed to Authorize Device"
date: 2019-12-12
forum: Hardware
---

### Post by aj-johnson-sflo on 2019-12-12
I have a Dell XPS 13 7390 "Developer Edition" that came from Dell installed with 18.04.3 LTS. We ordered a WD19TB Thunderbolt dock to connect peripherals and I can't get it working right. When I first plugged in the dock, an external HDMI monitor connection worked correctly, but none of the USB 3 ports worked, nor did the gigabit ethernet. When I looked in devices -> Thunderbolt, I saw that the system had detected the dock, but that it was in a "pending" state, screenshot: [https://i.stack.imgur.com/9wdc1.png](https://i.stack.imgur.com/9wdc1.png)

[COLOR=#242729][FONT=Arial]I clicked on the dock name in that screen and this dialog popped up, asking me to "authorize and connect" to the dock: [/FONT][/COLOR][https://i.stack.imgur.com/aD7dN.png](https://i.stack.imgur.com/aD7dN.png)

[COLOR=#242729][FONT=Arial]I click the "authorize and connect" button, and after typing in my sudo password, I got another dialog stating "Failed to authorize device: kernel error." [/FONT][/COLOR][https://i.stack.imgur.com/GAWHE.png](https://i.stack.imgur.com/GAWHE.png)

[COLOR=#242729][FONT=Arial]After this, back on the devices->Thunderbolt screen, the dock shows with an error: [/FONT][/COLOR][https://i.stack.imgur.com/vAo9M.png](https://i.stack.imgur.com/vAo9M.png)

Dell support directed me to this forum for assistance. Are there any special drivers that I have to install? What do I have to do to get this WD19TB dock working?

---

### Post by oldfred on 2019-12-12
Please attach screen shots. Do not post in line, not everyone has high speed Internet.
       If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

       [SOLVED] dock Dell TB16 does not work with XPS 13  - needed Firmware updates
[https://ubuntuforums.org/showthread.php?t=2431141](https://ubuntuforums.org/showthread.php?t=2431141)

---

### Post by aj-johnson-sflo on 2019-12-13
Thanks, oldfred. I edited the original post to remove the inline images.

Following instructions in the other thread, I ran "sudo fwupdmgr get-devices" with the dock connected to the Thunderbolt+AC power port. This laptop has two Thunderbolt ports, one with AC power, one without. The result was:

```
XPS 7390 Thunderbolt Controller
  DeviceId:             e667ec18c6305bca374892c95779060cef5d1827
  Guid:                 7d538854-204d-51b2-8f9d-1fe881c70200 <- TBT-00d40962-native
  Summary:              Unmatched performance for high-speed I/O
  Plugin:               thunderbolt
  Flags:                internal|updatable|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              41.02
  Icon:                 computer
  Created:              2019-12-13


Thunderbolt controller in Dell dock
  DeviceId:             bb66369405142c1ad19448e90645678ec74cbd08
  Guid:                 c94770ca-1773-592c-b20a-e87243bc7cd0 <- TBT-00d4b070
  Summary:              Thunderbolt controller
  Plugin:               thunderbolt
  Flags:                updatable|require-ac|supported|registered
  Vendor:               Dell Inc
  VendorId:             TBT:0x00D4
  Version:              40.00
  Icon:                 audio-card
  InstallDuration:      22
  Created:              2019-12-13


XPS 13 7390 System Firmware
  DeviceId:             b6c08fb9e5384d9d101853cc1ca20cf0ce2df2e2
  Guid:                 cbe49cca-492b-93e8-b0f4-f693501f271b
  Plugin:               uefi
  Flags:                internal|updatable|require-ac|supported|registered|needs-reboot
  Version:              0.1.3.1
  VersionLowest:        0.1.3.1
  Icon:                 computer
  Created:              2019-12-13
  UpdateState:          success


CAZ-82512-Q11 NVMe LITEON 512GB
  DeviceId:             c6a0cfba7c7d81e253fce571e1d1e9f6003ae1c7
  Guid:                 d4f01c0f-f1b4-50af-9438-b22bfdd16205 <- STORAGE-DELL-108035
  Guid:                 edb7c4c7-2e42-4aa3-b10c-8e5a4c99d2ed
  Serial:               TW0K64PGLOH009AF08ZW
  Summary:              NVM Express Solid State Drive
  Plugin:               nvme
  Flags:                internal|updatable|require-ac|registered|needs-reboot|no-auto-instance-ids
  Vendor:               Lite-On Technology Corporation
  VendorId:             NVME:0x14A4
  Version:              23201111
  Icon:                 drive-harddisk
  Created:              2019-12-13



```

Then, running "sudo fwupdmgr get-updates" returned this:

```

No upgrades for Thunderbolt controller in Dell dock, current is 40.00: 40.00=same
No upgrades for XPS 13 7390 System Firmware, current is 0.1.3.1: 0.1.3.1=same, 0.1.2.0=older, 0.1.1.3=older

```

I held the power button down until the system rebooted, leaving the dock plugged in to the AC power+Thunderbolt port. When it came back up, I tried one of the USB 3 ports on the dock and it still does not work. Thinking I needed to remove the dock from AC power, as you said in the other thread, I shut down the system, switched the dock so it plugged in to the Thunderbolt-only port, booted it, then held the power button down and restarted it without a connection to AC power, with the dock on the Thunderbolt only port. Still does not work. If I run "sudo fwupdmgr get-devices," the output is the same as above.

I find it curious that both the dock Thunderbolt controller and the 7390 Thunderbolt controller show "updatable" in their flags, as well as being concerned that I can't seem to clear the "needs-reboot" flag for the firmware and SSD devices. But that may not be relevant.

At [https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/), I see an entry for "WD19/WD19DC/WDTB Device Update." This dock is a WD19TB. Should the "get-updates" command resolve the correct device update from LVFS? Should I attempt to update the device manually and if so, how?

Thank you again for your assistance.

---

### Post by oldfred on 2019-12-13
Dell was one of the first to use fwupd, so UEFI could be updated from Linux.

I would expect that the version of Dock should be exactly correct. 
But sometimes same firmware is used for more than one model. My Asus motherboard has several versions, mostly port differences. And same UEFI is used for all of them.

I would go out to Dell and see if they have an update in their support area. It should show what firmware is correct for your Dock. And see if they have more instructions on how to clear needs reboot. There is a Dell forum where you can also ask about it.

My old Dell is not in the updates available, so I just go to Dell support for my model, download update file and save into my ESP as UEFI only reads FAT32 (I change fstab to allow read/write). And then from within UEFI can install update. Not then sure how it would work with a Dock.

---

### Post by aj-johnson-sflo on 2019-12-13
Yeah, the Dell support area for the WD19TB does not have any downloads/drivers available, nor any information on firmware. I've already posted on the Dell forum but will update and try again. Thanks for your help. 

I'm also wondering if the kernel write error from the Devices -> Thunderbolt screen has anything to do with it. On suggestion from my question on askubuntu.com ([https://askubuntu.com/q/1195666/254743](https://askubuntu.com/q/1195666/254743)), I "unlocked" that dialog and tried to "connect," but got the same results. Seems strange that it's getting a write error when it seems I'm essentially sudo'ing the command.... :confused:

---

### Post by oldfred on 2019-12-13
I wonder if you need newer version of Ubuntu.

I suggest installing 19.10 or if willing to just totally test, install 20.04 daily live. And see if with newer kernel it works better. Do not know if just trying live installer will work or you need install to be able to do updates as you cannot update live installer.

I have multiple Ubuntu installs, and hassle is that second install will take over default boot. But I always keep my 18.04 as main working install. 
So I have to backup /EFI/Boot & /EFI/ubuntu folders but normally just edit /EFI/ubuntu/grub.cfg back to 18.04 from new install's version and then add new install to 40_custom to boot it.

       Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)

---

### Post by aj-johnson-sflo on 2019-12-16
I stumbled upon the answer to this today when looking at BIOS settings for a different Dell laptop. In the BIOS, there is a series of settings related to Thunderbolt under System Configuration. I changed the "Thunderbolt Security Level" setting to "No Security" and now everything works perfectly. USB 3 and Ethernet ports both picked up right away. And the dock now shows up as "Authorized" in the Thunderbolt dialog for Devices.

Additional details and screenshots found here: [https://askubuntu.com/a/1196574/254743](https://askubuntu.com/a/1196574/254743)

Thanks again for your help, oldfred!

---

