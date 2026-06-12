---
title: "dell feisty laptop Fn stand by / suspend key broken"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by r343l on 2007-05-02
I've been on feisty for a while (only it had the proper support for my 64 bit laptop). I recently updated (via update manager) to current which should be about what the official release was. Very few configurations have been hacked on by me. The major one is a few lines to get suspend working (see the laptop testing page for the D620 [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620")). Now that I've updated, suspend works BUT I can't use the Fn+escape (stand by) key to do it -- going thru the logout dialog and choosing suspend does. When I checked the acpi log (/var/log/acpid) I saw this:

[Wed May  2 14:49:42 2007] received event "button/sleep SBTN 00000080 00000002"
[Wed May  2 14:49:42 2007] notifying client 5112[106:110]
[Wed May  2 14:49:42 2007] notifying client 17099[0:0]
[Wed May  2 14:49:42 2007] executing action "/etc/acpi/sleep.sh"
[Wed May  2 14:49:42 2007] BEGIN HANDLER MESSAGES
[Wed May  2 14:49:42 2007] END HANDLER MESSAGES
[Wed May  2 14:49:42 2007] action exited with status 0
[Wed May  2 14:49:42 2007] completed event "button/sleep SBTN 00000080 00000002"

When I added set -x sleep.sh, it exited on a condition whose comment in the script said that gnome-power-manager would handle the event. Checking syslog after this I find:

May  2 14:49:20 <myhost> gnome-power-manager: (<myname>) Doing nothing because the s
uspend button has been pressed

What do I do to fix this? The only power management GUI I know about talks about what to do when the lid closes or when the power is low, not whether to disable the Fn+Suspend key.

---

