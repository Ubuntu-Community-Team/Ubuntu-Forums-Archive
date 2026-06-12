---
title: "over-current condition"
date: 2013-06-28
forum: Hardware
---

### Post by neoTheCat on 2013-06-28
hello.

i just installed 13.04 amd64 on a Dell Vostro 3750, and i keep getting:
[FONT=Fixedsys]hub 2-1:1.0 over-current condition on port [3|4][/FONT]

i tried including the instructions in:
[http://askubuntu.com/questions/147555/over-current-condition-on-port-7-or-8](http://askubuntu.com/questions/147555/over-current-condition-on-port-7-or-8)

in summary:
ehci_hcd.ignore_OC=1

Edit GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to include this option and run sudo update-grub

but still did not work.  I have the same exact option added in the Arch installation on the same laptop, and it did work.  Any suggestions of what i could try, or what more information would help?

thank you.

---

### Post by Keith_Beef on 2013-12-04
That line "ehci_hcd.ignore_OC=1" should be "ehci_hcd.ignore_oc=1" (note that it is all in lower case).

Check it after rebooting by reading back the parameter from the /sys/module/ehci_hcd/parameters/ignore_oc file.

If you get "N", then the parameter was not set at boot time; if you get "Y", then it was set.

Changing this parameter did not fix my problem with a USB device that generates error codes -32 or -71.

---

