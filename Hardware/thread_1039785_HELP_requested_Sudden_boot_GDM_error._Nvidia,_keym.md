---
title: "HELP requested: Sudden boot GDM error. Nvidia, keymap"
date: 2009-01-14
forum: Hardware
---

### Post by Statik on 2009-01-14
Help! :)

My perfectly running 8.10 setup on an HP DV2310CA laptop has suddenly gone boom. It shows the normal text scroll, then the ubuntu splash with the loading bar. Then the screen goes black and makes the flash it normally makes as it switches to high-res mode for the login screen. It fails. You can see it try several times and then you get the Xserver blue window with the message:
> Failed to start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?
<Yes>   <No>

Selecting yes brings up a window, still in X server, that states:
> Warning:  Failsafe mode was already attempted within 30 seconds.
Warning:  Falling back to gdm to report the issue.
^Y

<OK>

Hitting ok gives another X server window that states:
> The X server is now disabled. Restart GDM
when it is configured correctly.
<OK>

Hitting OK brings up a graphical window on a black background that states:
> Ubuntu is running in low-graphics mode
The following error was encountered. You may need
to update your configuration to solve this.

(EE) Error compiling keymap (server-0)
(EE) XKB: Couldn't compile keymap

<OK>

This also used to mention the nvidia driver but I uninstalled this through booting in recovery-mode directly to command line and apt-get remove nvidia*

Hitting OK brings up another graphical menu on a black background:
> What would you like to do?
* Run Ubuntu in low-graphics mode for just this session
o Reconfigure graphics
o Troubleshoot the error

<Cancel> <OK>

I have tried all options from here. If I run in low-graphics mode I end up back at the same graphical error screen. No reconfiguring is effective. Troubleshooting doesn't give any options.

Can anyone help me get this thing back up and running short of a reinstall?

Assistance appreciated

Statik

---

