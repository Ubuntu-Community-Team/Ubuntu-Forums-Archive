---
title: "Error: IO APIC resources could be not be allocated"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by neon100 on 2009-09-04
except from the fact that there is a blatant grammatical mistake in this error statement,

i cannot install jaunty due to this error on my Dell Latitude D600 Laptop. I use USB to install ubuntu by the method given on [pendrivelinux.com 's USB tutorial for 9.04]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/"). By this method i neatly installed on my Dell XPS Gen 2 Laptop. But D600 is problematic.

any suggestions?

---

### Post by ronparent on 2009-09-04
When installing try hitting F6 at the first menu screen after menu selection and X'ing out the apic and maybe the lapic options. I had to do this to run or install 9.04 on three computers (pre 2005 amd boxes). If this does'nt work try posting here and we'll see if we can come up with other suggestions.

---

### Post by presence1960 on 2009-09-04
> **ronparent said:**
> When installing try hitting F6 at the first menu screen after menu selection and X'ing out the apic and maybe the lapic options. I had to do this to run or install 9.04 on three computers (pre 2005 amd boxes). If this does'nt work try posting here and we'll see if we can come up with other suggestions.

+1 ron

in case the OP needs a graphical look at what you are asking to be done see [here]("https://help.ubuntu.com/community/BootOptions")

---

### Post by neon100 on 2009-09-05
> **ronparent said:**
> When installing try hitting F6 at the first menu screen after menu selection and X'ing out the apic and maybe the lapic options. I had to do this to run or install 9.04 on three computers (pre 2005 amd boxes). If this does'nt work try posting here and we'll see if we can come up with other suggestions.

in the initial menu, i went in help, then pressed F6 and then used the following command

live-install noapic nolapic

It loads for a while and then gives following message

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell  (ash)
Enter 'help' for a list of built-in commands


Still stuck.

---

### Post by neon100 on 2009-09-05
i have also tried with the acpi=off parameter, but same problem persists.
Every single option results in error

in the end, it just displays following

(initramfs) with a cursor blinking in front of it.

---

### Post by ronparent on 2009-09-05
In the initial menu, do not go in help. Just press the F6 and use the spacebar to X out apic and/or lapic. If I have explained it poorly, see the screen shot reference provided you in the post by presence1960.

---

### Post by neon100 on 2009-09-06
as i mentioned before, i am using the usb version. Now i understand the boot parameters and i have tried them but they are not working. I've used nolapic noapic and acpi=off individually and with various combinations. They are giving the same errors.

---

