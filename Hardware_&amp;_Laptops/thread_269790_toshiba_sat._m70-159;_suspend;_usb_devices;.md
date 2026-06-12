---
title: "toshiba sat. m70-159; suspend; usb devices;"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by p_kolya on 2006-10-02
Hello, All!
I have installed Ubuntu Linux 6.06 TLS on my laptop toshiba satellite m70-159. All works fine. The exceptions is "suspend-to-disk": 
1) I plug my usb-mouse (logitech). It just works.
2) Then I ask Ubuntu to suspend (mouse is plugged). No problems there.
3) But after resuming Ubuntu (mouse is plugged) my mouse don't work! If I unplug and plug mouse again it works again.
So I have read something and decided that some usb-modules must be unloaded while suspending and loaded at resuming again. Then I add MODULES (/etc/default/acpi-support) ehci_hcd, uhci_hcd, ohci_hcd, pcmouse, button (as in hibernate script in suspend2). 
Now when I resume Ubuntu mouse works! But "hotpluggin" doesn't works! I.e. if I reattach mouse it will not work, or if I plug another device it will not work too until reboot.
Can anybody help me? In Slackware I have no problems with suspend, so, I think, solution exists :)
Thanks.
PS: Sorry for my english :)

---

