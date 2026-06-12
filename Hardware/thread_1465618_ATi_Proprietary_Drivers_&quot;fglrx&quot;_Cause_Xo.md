---
title: "ATi Proprietary Drivers &quot;fglrx&quot; Cause Xorg to Hang During Boot"
date: 2010-04-29
forum: Hardware
---

### Post by partymetroid on 2010-04-29
Hello.  I installed the full version of Ubuntu 10.04 LTS, codenamed Lucid Lynx earlier today.  Soon after booting into the operating system for the first time, I installed the ATi proprietary drivers, called "fglrx", from the official Ubuntu repository.  The system boots through the kernel, but hangs during the start of Xorg.  The lights on my keyboard flash, and the Ubuntu chime repeats indefinitely.  I have to hard shutdown (hold the power button for several seconds) to turn off my computer. :confused:

I am using an ATi Radeon HD 4670 graphics card, and Ubuntu 10.04 LTS with the proprietary "fglrx" drivers. :-\"

Any help would be greatly appreciated. :KS

[SIZE=3] [edit] The solution to the problem is typing into the console this command:```
dpkg-reconfigure -phigh xserver-xorg
```Hope this helps someone! :popcorn:[/SIZE]

---

### Post by tgalati4 on 2010-04-29
Revert to the open drivers for the time being.  Boot into the rescue kernel and remove the fglrx driver:

apt-get remove xorg-driver-fglrx
dpkg-reconfigure -phigh xserver-xorg

Reboot.

---

### Post by mcoleman44 on 2010-04-29
> Revert to the open drivers for the time being.  Boot into the rescue  kernel and remove the fglrx driver:
I agree. The open source driver is working better than I expected so far. I haven't had any problems from it yet.

---

### Post by partymetroid on 2010-04-29
Thanks for the workaround guys!

... But don't let that stop any of you other guys from coming up with a solution! :KS

---

### Post by tgalati4 on 2010-04-29
Send an email to AMD/ATI and describe your experience.

---

### Post by partymetroid on 2010-04-29
I actually think that this might be an Ubuntu problem, for when I typed  apt-get remove xorg-driver-fglrx into the console, there was nothing to remove... maybe the restricted drivers installer broke the installation? :confused:

I'll try to install them from Synaptic and give a response. :KS

---

### Post by partymetroid on 2010-04-29
Huh... I type in fglrxinfo into the console, and I get back information stating that I'm using the driver:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series
OpenGL version string: 3.2.9756 Compatibility Profile Context

```I suppose this means that I've been using the driver all along since installing it... and that the "dpkg-reconfigure -phigh xserver-xorg" line fixed the driver?  I hope this is the case! :KS

If it is, then problem solved!  If anyone else has this problem, then I recommend typing "dpkg-reconfigure -phigh xserver-xorg" into the console after entering the recovery root shell. :popcorn:

... assuming that this is confirmed to be a viable solution, that is. :)

---

### Post by partymetroid on 2010-04-30
Yes, that is what resolved the issue.  I'll edit my original post to include the console command which fixed the issue. :KS```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by partymetroid on 2010-05-05
> **partymetroid said:**
> Yes, that is what resolved the issue.  I'll edit my original post to include the console command which fixed the issue. :KS```
dpkg-reconfigure -phigh xserver-xorg
```Never mind... the problem still persists.  With the fglrx drivers, on one hand, the system hangs when normally booting.  On the other hand, when booting into recovery mode, the screen just has a row of 1:2 height/width-ratio rectangles, which all look the same.  They change a little bit when I press the up and down arrow keys, as if they are just teeny tiny versions of the true recovery mode screen.  Very strange and frustrating.

I have to boot into the LiveCD to change the xorg.conf so that X will use the open source "radeon" drivers.

I tried reactivating the fglrx drivers for kicks, booted normally without problems; however, after restarting, the problem started all over again.

I want to use Ubuntu for digital painting and open source game programming (using game frameworks that utilize OpenGL on *nix systems, including Linux (for example, LOVE))... but I can't really do digital painting with Krita without OpenGL (with decent framerate, at least), and of course I can't do 2D/3D acceleration without the fglrx drivers.

I'm quite between a rock and a hard place.:(

---

