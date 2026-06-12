---
title: "Unknown symbols in modules..."
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2008-12-26
Hello...when i try to insert "ehci-hcd" with insmod i am getting this error


[B]root@sharief-desktop:/home/sharief/Desktop/drivers/host# insmod ehci-hcd.ko
insmod: error inserting 'ehci-hcd.ko': -1 Unknown symbol in modul[/B]e


output of  "**dmesg**" is :


[ 196.416023] ehci_hcd: Unknown symbol usb_hcd_pci_suspend
[ 196.416023] ehci_hcd: Unknown symbol usb_free_urb
[ 196.416023] ehci_hcd: Unknown symbol usb_hub_tt_clear_buffer
[ 196.416023] ehci_hcd: Unknown symbol usb_hcd_resume_root_hub
[ 196.416023] ehci_hcd: Unknown symbol usb_hcd_pci_probe
[ 196.416023] ehci_hcd: Unknown symbol usb_hcd_unlink_urb_from_ep
[ 196.428074] ehci_hcd: Unknown symbol usb_hcd_check_unlink_urb
[ 196.428406] ehci_hcd: Unknown symbol usb_calc_bus_time
[ 196.428582] ehci_hcd: Unknown symbol ehci_cf_port_reset_rwsem
[ 196.428761] ehci_hcd: Unknown symbol usb_hcd_pci_shutdown
[ 196.428977] ehci_hcd: Unknown symbol usb_hcd_link_urb_to_ep
[ 196.429151] ehci_hcd: Unknown symbol usb_hcd_pci_resume
[ 196.429340] ehci_hcd: Unknown symbol usb_get_urb
[ 196.429527] ehci_hcd: Unknown symbol usb_hcd_giveback_urb
[ 196.429733] ehci_hcd: Unknown symbol usb_hcd_poll_rh_status
[ 196.429900] ehci_hcd: Unknown symbol usb_hcd_pci_remove
[ 196.430222] ehci_hcd: Unknown symbol usb_root_hub_lost_power

Kindly help me what to do...

---

### Post by PmDematagoda on 2008-12-26
How did this start happening?

---

### Post by shariefbe on 2008-12-26
Thats i dont know...when i try to install this module am getting this error.....can you help me

---

