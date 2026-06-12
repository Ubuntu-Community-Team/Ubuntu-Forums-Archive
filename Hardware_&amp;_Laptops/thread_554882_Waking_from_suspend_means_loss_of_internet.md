---
title: "Waking from suspend means loss of internet"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by Robbyx on 2007-09-19
Fiesty

If I use either hibernate or sleep to save electricity, I find that upon awaking the internet connection is lost and can only be recovered by a reboot. The internet connection is via Ethernet. Has anyone else had the same problem and cured it?

---

### Post by Robbyx on 2007-09-28
Any chance of a reply, please?

---

### Post by peabody on 2007-09-28
Are you using network manager or manually configuring the connection?

---

### Post by tgalati4 on 2007-09-28
Check the advanced settings of your BIOS.  You may have a setting that keeps power to the ethernet chip so it will stay up.

Of course, you posted your hardware specifications so that we can see what you are running.

---

### Post by Robbyx on 2007-09-29
> **tgalati4 said:**
> Check the advanced settings of your BIOS.  You may have a setting that keeps power to the ethernet chip so it will stay up.

Of course, you posted your hardware specifications so that we can see what you are running.

I had assumed it was a bug not a bios setting and so did not post details of the MB.

I am using 32bit fiesty.

The board is a MSI P6N SLI which runs on  a pentium lga 775.

The manual does not make it clear to me if the bios has the setting to keep power to the ethernet chip, but it does have a wakeup event setup in the power management which includes resume by onboard lan. Is that in effect the same thing?


Looking through the Bios Manual some other questions arise:

Should  Apic mode be on?


Do you know what version of MPS table Fiesty supports?


Should I enable HPET?


I hope you do not mind the extra questions.

Robin

---

### Post by Robbyx on 2007-09-30
This is an extract from my syslog. I am hoping that someone can tell me why the suspend is not working. I am hoping my loss of adsl connection is due to this problem and that it is possible to sort it out.

```
Sep 30 10:43:55 robin-desktop gnome-power-manager: (robin) Suspending computer because the DBUS method Suspend() was invoked
Sep 30 10:43:57 robin-desktop NetworkManager: <information>^IGoing to sleep. 
Sep 30 10:44:00 robin-desktop kernel: [  960.787458] bridge-eth1: disabling the bridge
Sep 30 10:44:00 robin-desktop kernel: [  960.797915] bridge-eth1: down
Sep 30 10:44:00 robin-desktop NetworkManager: <debug info>^I[1191145440.532861] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_19_db_4c_ef_fd'). 
Sep 30 10:44:00 robin-desktop kernel: [  960.832737] ACPI: PCI interrupt for device 0000:00:14.0 disabled
Sep 30 10:44:01 robin-desktop NetworkManager: <debug info>^I[1191145441.047272] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Sep 30 10:44:01 robin-desktop NetworkManager: <debug info>^I[1191145441.052080] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Sep 30 10:44:01 robin-desktop kernel: [  961.798815] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Sep 30 10:44:01 robin-desktop kernel: [  961.801535] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 19
Sep 30 10:44:01 robin-desktop kernel: [  961.801548] PCI: Setting latency timer of device 0000:00:14.0 to 64
Sep 30 10:44:01 robin-desktop kernel: [  961.802952] forcedeth: using HIGHDMA
Sep 30 10:44:02 robin-desktop kernel: [  962.324504] eth0: forcedeth.c: subsystem: 01462:7350 bound to 0000:00:14.0
Sep 30 10:44:02 robin-desktop kernel: [  962.347812] input: Power Button (FF) as /class/input/input8
Sep 30 10:44:02 robin-desktop kernel: [  962.348149] ACPI: Power Button (FF) [PWRF]
Sep 30 10:44:02 robin-desktop kernel: [  962.348660] input: Power Button (CM) as /class/input/input9
Sep 30 10:44:02 robin-desktop kernel: [  962.348958] ACPI: Power Button (CM) [PWRB]
Sep 30 10:44:02 robin-desktop NetworkManager: <debug info>^I[1191145442.135170] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_19_db_4c_ef_fd'). 
Sep 30 10:44:02 robin-desktop kernel: [  962.435367] eth1: no link during initialization.
Sep 30 10:44:02 robin-desktop kernel: [  962.435505] bridge-eth1: enabling the bridge
Sep 30 10:44:02 robin-desktop kernel: [  962.435509] bridge-eth1: up
Sep 30 10:44:02 robin-desktop NetworkManager: <debug info>^I[1191145442.192740] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Sep 30 10:44:02 robin-desktop NetworkManager: <debug info>^I[1191145442.239986] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Sep 30 10:44:03 robin-desktop kernel: [  963.499019] eth1: link up.
Sep 30 10:44:12 robin-desktop gnome-power-manager: (robin) select() to /dev/rtc to wait for clock tick timed out   select() to /dev/rtc to wait for clock tick timed out code='32' quark='g-exec-error-quark'
Sep 30 10:44:12 robin-desktop gnome-power-manager: (robin) Resuming computer
Sep 30 10:44:12 robin-desktop gnome-power-manager: (robin) suspend failed
Sep 30 10:44:12 robin-desktop NetworkManager: <information>^IWaking up from sleep. 
```

---

### Post by peabody on 2007-09-30
You never answered my original question as to whether you were using network manager.  If you're not, it might be able to help.  I know that it'll attempt to reconfigure the wired network on resume from sleep.

---

### Post by Robbyx on 2007-09-30
> **peabody said:**
> You never answered my original question as to whether you were using network manager.  If you're not, it might be able to help.  I know that it'll attempt to reconfigure the wired network on resume from sleep.

I apologise for over-looking your reply. I do not know how to invoke the network manager. I have one installed because I checked in synaptec. Ubuntu found my adsl connection without any help from me.

---

### Post by peabody on 2007-09-30
If you're running feisty then it will have been installed per default and should show up as an icon in the system tray (pair of computer monitors or a wireless signal graph).  If you're running an earlier Ubuntu, network manager can be installed with sudo apt-get install network-manager.

---

### Post by Robbyx on 2007-09-30
> **peabody said:**
> If you're running feisty then it will have been installed per default and should show up as an icon in the system tray (pair of computer monitors or a wireless signal graph).  If you're running an earlier Ubuntu, network manager can be installed with sudo apt-get install network-manager.

I am using fiesty and it is in the system tray.  There is not much to do with it but enable networking is clicked.

In a recent posting to this topic I mentioned that there is an error messaage on starting up after suspend. That is why I posted the sys log. I wonder if that is causing the state of the machine not to be suspended properly so that upon waking up the network does not connect properly. Does that make sense to you?

Robin

---

