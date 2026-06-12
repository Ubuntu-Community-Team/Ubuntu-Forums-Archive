---
title: "how to (temporarily) disable the bluetooth module?"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by GordonFreeman on 2008-03-28
Hi,
how can I temporarily disable my bluetooth module? I don't want to disable it for real, just a little command which I can execute when I'm running my laptop on battery without using any bluetooth device, to safe a little energy.


Thanks.



P.S. and how can I do the same with the wireless network card?

---

### Post by oliveroms on 2008-03-28
I know on my ibm, there's a file called /proc/acpi/ibm/bluetooth where i can echo enable/disable into it. As for wireless, I use the network manager to 'disable' wireless. That _should_ in therory put it into a power saving mode.

If not, then network-manager is bugged :p


I was actually thinking of writing a little app to enable/disable them both. the IBM's at the least have a fn-(f5) keycombo that lets you normally enable/disable wifi/bluetooth. Since that key combo fires off an acpi event it might trigger network-manager to show a enable/disable pop up. This would require a hook in hal to send an event over dbus to the network manager. I'll think about it :)

---

### Post by GordonFreeman on 2008-03-28
I don't have such an entry in my /proc/acpi folder.

I'm using a Dell laptop and I have a switch with which I can disable wlan/bluetooth and I can configure it in the bios if it should deactivate only bluetooth, wlan or both, but as you can see I would need two switches to enable/disable only one of them (and to have the possibility to disable both).



I think a have kind of a solution: the smbios lib ships (at least for me) with a tool called dellWirelessCtl which allows me to configure some wireless options of the bios from linux and I can control with this tool the behaviour of the wireless switch, so I can configure it to what module(s) I want to disable and then by pressing it the module(s) get(s) disabled. So I can write some scripts which use this tool, call the script and then press the button, not the best solution but it should work.

---

