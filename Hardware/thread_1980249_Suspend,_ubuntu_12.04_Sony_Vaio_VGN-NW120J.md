---
title: "Suspend, ubuntu 12.04 Sony Vaio VGN-NW120J"
date: 2012-05-14
forum: Hardware
---

### Post by Abadonna on 2012-05-14
I've install 12.04 on my Vaio as a second OS.  I created 2 new partitions for swap and /.


  When the lid is closed, system fails in suspend mode. The indicator  blinks like it does in Windows (by powered on it is green, on suspend  links orange). 
  But when I start the system again by pressing any key, it looks like normal boot. No changes are saved.


  What can be the problem? P.S all updates are installed.

---

### Post by Abadonna on 2012-05-16
Nobody knows?)

---

### Post by super.niels on 2012-05-18
Hey, I have the same problem with my sony. I have been searching on google, but cant seem to find any solution. 

Hope that there is anybody how has a solution.
Niels

---

### Post by kevin2849 on 2012-05-18
I will offer the solution I found to this issue, but I make no claims it will work on all systems.

Open */etc/default/grub* with text editor and look for 
this line *GRUB_CMDLINE_LINUX=""*

Change it to be :*GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"*

Then *upgrade-grub*2.

Run all commands as root.

On reboot, my system will now resume from suspend, and has done so over the last couple releases of Ubuntu.

---

### Post by super.niels on 2012-05-23
changing the grub does not seem to work... :-(

---

### Post by sandwormblues on 2012-05-26
same problem with Sony Vaio, VGN-CS110E, Ubuntu 12.04.  Resuming from suspend (closed laptop lid) causes keyboard to go non-responsive. acpi_sleep=nonvs grub paramater has no effect.

syslog is attached.


here's what's on board (lspci)
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
06:02.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:02.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:02.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Ada```

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
06:02.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:02.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:02.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by rizzy on 2012-06-06
I am having the same issue with my Sony Vaio Laptop it is model VGN-FW465J.

It is not just shutting the laptop lid either. If I let my computer sit there idle and it goes into suspend mode on waking it all the programs I was working on before are gone.

I have been researching this for several days now and can not find a solution. 

Hopefully someone figures something out sooner than later for this.

---

### Post by Willynux on 2012-06-14
I have a Vaio VGN and at first the *acpi_sleep=nonvs* didn't work either.

Then I did both: sudo update-grub and sudo update-grub2

Now suspend is working :p

---

### Post by Zomby Woof on 2012-06-17
> **kevin2849 said:**
> I will offer the solution I found to this issue, but I make no claims it will work on all systems.

Open */etc/default/grub* with text editor and look for 
this line *GRUB_CMDLINE_LINUX=""*

Change it to be :*GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"*

Then *upgrade-grub*2.

Run all commands as root.

On reboot, my system will now resume from suspend, and has done so over the last couple releases of Ubuntu.

Bravo for whoever came up with this. It fixed the suspend issue on my desktop 12.04.

---

### Post by mcopelli on 2012-08-08
Just for the record, neither of the two tricks worked on my Sony Vaio VGN-SZN770AN...

---

### Post by ariwe on 2012-08-14
> **kevin2849 said:**
> I will offer the solution I found to this issue, but I make no claims it will work on all systems.

Open */etc/default/grub* with text editor and look for 
this line *GRUB_CMDLINE_LINUX=""*

Change it to be :*GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"*

Then *upgrade-grub*2.

Run all commands as root.

On reboot, my system will now resume from suspend, and has done so over the last couple releases of Ubuntu.

It worked out perfectly on a sony vaio FW140e
Thanks!

---

### Post by BrunoMartin on 2012-10-16
> **kevin2849 said:**
> I will offer the solution I found to this issue, but I make no claims it will work on all systems.

Open */etc/default/grub* with text editor and look for 
this line *GRUB_CMDLINE_LINUX=""*

Change it to be :*GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"*

Then *upgrade-grub*2.

Run all commands as root.

On reboot, my system will now resume from suspend, and has done so over the last couple releases of Ubuntu.

Just works! You need to restart once to work.

Thanks!

---

### Post by Ja55 on 2012-10-20
THANK YOU!!!!
it works for **vaio vgn-nw21ef**.
for other facing the same problem what you should do :

> 
_1- add "acpi_sleep=nonvs" to grub file :_
***gksu gedit /etc/default/grub***
in this line *GRUB_CMDLINE_LINUX=""*
Change it to be :[B][I]GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"

[/I][/B]_2 - update grub with the new parameters :_[I]
[B]sudo update-grub && sudo update-grub2
[/B]
[/I]_3- Reboot your system :_[I]
**sudo reboot **
[/I]
and that's all :)


---

### Post by oaxacamatt1 on 2012-10-20
Success...
This works form Gateway NV51B08u with the AMD Dual-core C50 and Radeon HD 6250 video card using Xubuntu 12.10.

sudo leafpad /etc/default/grub
Find: GRUB_CMDLINE_LINUX=""
Change it to be :GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
sudo update-grub
sudo update-grub2

I did not need to reboot after this set of commands and Suspend now works! 
Probably do not need one of the updates but what the heck...
Thanks All,
M

---

### Post by pgfreire on 2013-02-15
> **Willynux said:**
> I have a Vaio VGN and at first the *acpi_sleep=nonvs* didn't work either.

Then I did both: sudo update-grub and sudo update-grub2

Now suspend is working :p

**update-grub** did it for me on a Vaio VGN-NS11Z with 12.04 where **update-grub2** had failed to solve the problem.
:D

---

### Post by golanyoni on 2013-05-13
Worked for me too. 
Did both "sudo update-grub" and "sudo update-grub2" as suggested.
Sony Vaio VGN-SR19XN
Ubuntu 12.04
Thanks a lot!

---

