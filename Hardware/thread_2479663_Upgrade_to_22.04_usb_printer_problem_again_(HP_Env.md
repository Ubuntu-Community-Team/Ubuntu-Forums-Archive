---
title: "Upgrade to 22.04: usb printer problem again (HP Envy 5640)"
date: 2022-10-02
forum: Hardware
---

### Post by gja on 2022-10-02
Hi,
After the previous 20.04 upgrade my system had serious printer problems. They were fixed as explained here: 
[https://ubuntuforums.org/showthread.php?t=2442142]("https://ubuntuforums.org/showthread.php?t=2442142")

Now after the 22.04 upgrade problems pop up again.
Printer: HP Envy 5640 connected via USB

Multiple printer instances pop up, none of them seem to be working.
The old fix of removing ippusbxd does not work anymore.

Tried removing avahi auto detection and cups auto detection, still no use.
>> from syslog: during a print attempt:
Oct  2 16:11:05 gja-desktop systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Process 6997 died: No such process; trying to remove PID file. (/run/avahi-daemon//pid)
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Found user 'avahi' (UID 116) and group 'avahi' (GID 122).
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Successfully dropped root privileges.
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: avahi-daemon 0.8 starting up.
Oct  2 16:11:05 gja-desktop dbus-daemon[451]: [system] Successfully activated service 'org.freedesktop.Avahi'
Oct  2 16:11:05 gja-desktop systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Successfully called chroot().
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Successfully dropped remaining capabilities.
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: No service file found in /etc/avahi/services.
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: Failed to create server: No suitable network protocol available
Oct  2 16:11:05 gja-desktop avahi-daemon[6999]: avahi-daemon 0.8 exiting.
Oct  2 16:11:05 gja-desktop systemd[1]: avahi-daemon.service: Main process exited, code=exited, status=255/EXCEPTION
Oct  2 16:11:05 gja-desktop systemd[1]: avahi-daemon.service: Failed with result 'exit-code'.
>>

All ideas and suggestions welcome.

---

### Post by csae2608 on 2022-10-05
what i have to do on my epson ecotank is to remove package "ipp-usb" for 22.04 and "ippusbxd" or similar for 20.04, afterwards manually add the printer to the printer list (i would manually download and install the linux drivers from epson homepage for my model to get best results)
maybe you can achieve similar with your HP printer; remember the package for Linux hplip that you maybe can find on HP Website , Good Luck.

---

### Post by ajgreeny on 2022-10-05
Do you have the possibility of connecting the printer by wireless?

I have never had a problem using any HP printer using wireless, even though one desktop machine uses ethernet only.
Normally there is no need to even search for the printer, in my case currently an Envy 4257 as it is detected immediately following installation of any recent version of Ubuntu.

USB connection seems to present more difficulties in recent times so try wireless if you can; it may be much simpler.

---

### Post by gja on 2022-10-06
> **csae2608 said:**
> what i have to do on my epson ecotank is to remove package "ipp-usb" for 22.04 and "ippusbxd" or similar for 20.04, afterwards manually add the printer to the printer list (i would manually download and install the linux drivers from epson homepage for my model to get best results)
maybe you can achieve similar with your HP printer; remember the package for Linux hplip that you maybe can find on HP Website , Good Luck.

I had already tried removing the "ippusbxd" package but as you mention it has now been renamed to "ipp-usb".
Removing "ipp-usb" did the trick. Printer is working again.

Thank you!

---

