---
title: "Ubuntu 9.04 won't boot"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by ABN_Bearcat on 2009-10-10
I am completely new to Linux and Ubuntu.  I just upgraded my Dell Inspiron 2650 laptop to Ubuntu 9.04.  However, when I boot the PC I get to a blank screen that says "Starting Up .." with a blinking cursor.  The system just sits there and doesn't boot.  Can anyone tell me what to do in order to fix this problem?  I have tried:

1. After Ubuntu is installed and you're asked to reboot. You must hit escape before grub loads. Then you must select the first line ( not recovery) and hit e, then goto the second line and hit e again. Delete splash and hit enter, then hit b to boot.
2. Once you're in Ubuntu, open up the terminal and type: 

gksudo gedit /boot/grub/menu.lst

 It is after this step that I get the "Starting Up..." and it hangs there.

 Thanks 
:confused:

---

### Post by Hellishcross on 2009-12-06
I have an inspiron 2650 too. Add this to your boot options **acpi=off**. It should boot then. Also once it does boot go into the terminal and edit your /boot/grub/menu.lst and add the same thing **acpi=off**.

---

### Post by Hellishcross on 2009-12-06
Actually **acpi=ht** seems to work a little better. It gives me more functionality.

---

