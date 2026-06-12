---
title: "Problem with reconfiguring display/screensaver"
date: 2011-04-20
forum: Hardware
---

### Post by MaxTakeoff on 2011-04-20
Hey, I have been running Xubuntu on my old Toshiba Satellite P4 for a  while now, very happy with it.  Sadly, the cpu fan died so I decided to  transfer the hard drive into my son's old Compaq Presario 700 that had a  dead hard drive.  I intended on re-installing everything but before I  did, I figured I might as well see what happened if I just tried  starting it, I was pretty surprised when it fired up and everything  worked .... or so it seemed!

The display was working but then if I left the laptop for 10 minutes  (when the screensaver kicks in), I suspect that the xserver crashes  because it logs me out and takes me back to the user login screen.  If I  try to start the screensaver setting application, the same thing  happens.
When I try sudo dpkg-reconfigure xserver-xorg, it asks for the password  and then just drops me back to the prompt, same with sudo  dpkg-reconfigure xscreensaver.

Oh, the other thing that may well be relevant is that I now get an SMBus error on start-up to the tune of ...
[   17.846623] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1

Can I salvage the installation ported into the new laptop or do I need to re-install?

Cheers, Stu

---

### Post by MaxTakeoff on 2011-04-22
No-one has any suggestions on fixing the SMBus or a way to configure xserver/xscreensaver?

---

### Post by MaxTakeoff on 2011-04-26
Nevermind, I ended up switching to Zenwalk due to lack of input.

---

