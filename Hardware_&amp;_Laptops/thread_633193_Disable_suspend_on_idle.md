---
title: "Disable suspend on idle"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by gautehk on 2007-12-06
I've got an aging "Compaq Presario 5686" desktop computer which enters suspend mode (or is it "sleep"?) after 30 minutes or so of inactivity. How can I prevent that?

This was never a problem with earlier Ubuntu versions, but started after a fresh Gutsy install.

All suspend settings are set to "never" in Gnome's power manager. The ACPI_SLEEP and ACPI_HIBERNATE lines in /etc/default/acpi-support are commented out, as suggested in [another post]("http://ubuntuforums.org/showpost.php?p=1151390&postcount=2"). I have also run gconf-editor and turned off everything that seemed relevant under apps/gnome-powermanager. Nothing helps, the computer still goes to sleep.


I had another problem that might be related: Before upgrading to Ubuntu Gutsy, I used the acpi=force boot option to make the computer switch off at halt instead of just hanging. After the upgrade, acpi=force doesn't work anymore. (With acpi=force, it now hangs at boot, after displaying the bios date 1999 fails cutoff message.) I solved that shutdown issue [like this]("http://ubuntuforums.org/showpost.php?p=2260791&postcount=10").

Here's another maybe-unrelated/maybe-informative observation: When I wake up the computer after suspend, I cannot get the network to work again until I reboot. "/etc/init.d/networking restart" and other attempts fail. I haven't put much effort into solving this issue, since the computer shouldn't suspend anyway...

This last piece of info is probably unrelated: Before the Gutsy upgrade, I installed a S-ATA controller, two S-ATA hard drives, and a new ATI video card. I just mention this to inform that the hardware configuration that used to work is not quite the same as what I've got now.


The output from dmesg is attached.

---

### Post by SpacePilot on 2007-12-06
system --> preferences --> powermanagement

Where is says:

Actions
-- put computer to sleep when inactive for ..

Drag it all the way up so it says never.




Do the same thing with all the others if you want to be sure. Then every such thing as suspend/hibernate and so on is off.

---

### Post by gautehk on 2007-12-06
I already tried that: "All suspend settings are set to "never" in Gnome's power manager. " The computer doesn't seem to care...

---

### Post by SpacePilot on 2007-12-06
Have you tried acpi=off or pci=noacpi on your kernel line?

---

### Post by gautehk on 2007-12-06
Thanks for the suggestions. pci=noacpi did not help. I'm now trying acpi=off, but I'd have thought acpi was off anyway, when it says:
```
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
```

This sure takes time to debug, waiting for the computer to eventually suspend... :-/

Edit: No luck with the acpi=off option, either.

---

### Post by gautehk on 2008-01-06
(Long break, then some last attempts before I downgrade to a version that works.)

I tried removing all packages related to apm and acpi, as I noticed there was an 'apmd' process running. This changed nothing.

I then found the 'apm' kernel module and disabled that as well. The computer now finally stays on - the problem is solved :) To make it stick across reboots, I added this line to /etc/modprobe.d/blacklist:

```
blacklist apm
```

---

