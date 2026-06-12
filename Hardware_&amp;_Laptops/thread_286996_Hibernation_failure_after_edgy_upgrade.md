---
title: "Hibernation failure after edgy upgrade"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by tiggerntatie on 2006-10-28
**This issue turned out to result from issues with the swap partition. Follow the resolution described [here]("https://launchpad.net/distros/ubuntu/+bug/66637"). You must run mkswap and edit fstab with the new UUID for the swap partition, then add that UUID to the end of "RESUME=" found in /etc/initramfs-tools/conf.d/resume**

My Asus Z7100 could always hibernate happily on Dapper. Today, after the edgy upgrade hibernate works no more.

When I click on hibernate, the laptop seems to go through all the motions of hibernating: screen fades to black, hard drive activity, audio clicks off, etc. except that final step of shutting power seems to be lacking. It then sits there for 30 seconds or so until it decides that it's time to wake up again and presents me with the password dialog as if it has just resumed and everything is completely normal. 

No error messages on screen.. 

I have the following from /var/log/messages (is there a better place to look for troubles?):

[INDENT][SIZE="1"]Oct 28 11:00:06 localhost gnome-power-manager: (ericd) Hibernating computer because user clicked hibernate from tray menu
Oct 28 11:00:19 localhost kernel: [17180913.696000] skge eth0: disabling interface
Oct 28 11:00:27 localhost kernel: [17180922.152000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Oct 28 11:00:30 localhost kernel: [17180925.008000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
Oct 28 11:01:01 localhost kernel: [17180928.988000] Freezing cpus ...
Oct 28 11:01:01 localhost kernel: [17180928.988000] Stopping tasks: ==============================================================================================|
Oct 28 11:01:01 localhost kernel: [17180929.120000] Shrinking memory...  ^H-^Hdone (0 pages freed)
Oct 28 11:01:01 localhost kernel: [17180929.160000] ACPI: PCI interrupt for device 0000:03:01.1 disabled
Oct 28 11:01:01 localhost kernel: [17180929.160000] ACPI: PCI interrupt for device 0000:03:01.0 disabled
Oct 28 11:01:01 localhost kernel: [17180929.160000] NVRM: RmPowerManagement: 3
Oct 28 11:01:01 localhost kernel: [17180930.956000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Oct 28 11:01:01 localhost kernel: [17180932.520000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Oct 28 11:01:01 localhost kernel: [17180932.520000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 28 11:01:01 localhost kernel: [17180932.520000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 28 11:01:01 localhost kernel: [17180932.520000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 28 11:01:01 localhost kernel: [17180935.516000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Oct 28 11:01:01 localhost kernel: [17180935.516000] ....
Oct 28 11:01:01 localhost kernel: [17180935.516000] swsusp: Need to copy 98330 pages
Oct 28 11:01:01 localhost kernel: [17180935.516000] swsusp: critical section/: done (98330 pages copied)
Oct 28 11:01:01 localhost kernel: [17180935.516000] swsusp: Restoring Highmem
Oct 28 11:01:01 localhost kernel: [17180936.524000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Oct 28 11:01:01 localhost kernel: [17180936.524000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
Oct 28 11:01:01 localhost kernel: [17180948.632000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
Oct 28 11:01:01 localhost kernel: [17180948.632000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
Oct 28 11:01:01 localhost kernel: [17180948.632000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
Oct 28 11:01:01 localhost kernel: [17180948.632000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
Oct 28 11:01:01 localhost kernel: [17180948.632000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Oct 28 11:01:01 localhost kernel: [17180950.132000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 28 11:01:01 localhost kernel: [17180950.132000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
Oct 28 11:01:01 localhost kernel: [17180950.132000] usb usb5: root hub lost power or was reset
Oct 28 11:01:01 localhost kernel: [17180950.132000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 28 11:01:01 localhost kernel: [17180950.136000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 28 11:01:01 localhost kernel: [17180950.136000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
Oct 28 11:01:01 localhost kernel: [17180950.140000] NVRM: RmPowerManagement: 4
Oct 28 11:01:01 localhost kernel: [17180950.780000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 177
Oct 28 11:01:01 localhost kernel: [17180950.780000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 185
Oct 28 11:01:01 localhost kernel: [17180950.780000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 19 (level, low) -> IRQ 225
Oct 28 11:01:01 localhost kernel: [17180955.508000] Restarting tasks... done
Oct 28 11:01:01 localhost kernel: [17180955.520000] Thawing cpus ...
Oct 28 11:01:01 localhost gnome-power-manager: (ericd) Resuming computer
[/SIZE][/INDENT]

---

