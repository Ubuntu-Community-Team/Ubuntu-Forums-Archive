---
title: "Installing Ubuntu on a Sony Vio VGN-C290"
date: 2008-08-02
forum: Hardware
---

### Post by Num1Deluxe on 2008-08-02
Hi,
I am new to linux and I am having problems installing Ubuntu on a Sony VIO VGN-C290 from a live CD. I am able to get to the Ubuntu
Install screen, Then Select Install Ubuntu after that I get this message;

  [ 40.516717] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
  [ 40.516717] ACPI: EC: read timeout, command = 128

While the laptop just hangs there with a flashing cursor. Would I be able to install Ubuntu on this type of laptop.

I also tried to run the live cd as well as trying wubi and wubi gets as far as installing ubuntu but apon reboot I get other errors that I cant recall at this point.

help and thanks,
1

---

### Post by phidia on 2008-08-02
You may need to use a boot option like noapic see the [Ubuntu boot options wiki]("https://help.ubuntu.com/community/BootOptions"). 
From the link above: >  noapic Disable the "Advanced Programmable Interrupt Controller (APIC)".  
Hope that helps.

---

### Post by Num1Deluxe on 2008-08-03
I think that went somewhat well thank you for the tip.
The only thing I am not sure off is the partitioning of my Hard Drive I think the install only let me more than I realy wanted to.
Which was only about 10 gigs. Now I dont think I can go back. I am hoping I am able to get thing working on it with ubuntu.

---

