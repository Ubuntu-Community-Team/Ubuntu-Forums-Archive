---
title: "laptop hibernate even if battery not at crutial stage"
date: 2012-03-25
forum: Hardware
---

### Post by eGelor on 2012-03-25
Hello dear friends.
My laptop goes to hibernate mode even if battery is not on crutial stage. So please give me your feedback here. 
Thanks for your time.

---

### Post by eGelor on 2012-03-27
Possible solution
#sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"


run "sudo update-grub" in the terminal.

---

