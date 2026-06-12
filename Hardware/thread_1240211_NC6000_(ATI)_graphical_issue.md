---
title: "NC6000 (ATI) graphical issue"
date: 2009-08-14
forum: Hardware
---

### Post by CFury on 2009-08-14
I have an HP Compaq nc6000 notebook which was running Jaunty just fine, however I stumbled across a thread somewhere here which got me thinking my system was a bit slow due to improper graphic drivers.  I went ahead and installed EnvyNG and selected the ATI drivers, as it was marked compatible.  Upon reboot the system freezes at a screen with colourful garbage at the bottom, black in the middle to top bit, and more colourful garbage at the very top- perhaps 4 or so pixels tall.  I know there's a way to correnct this issue in recovery mode, however now I'm lost.  Any help would be greatly appreciated.

---

### Post by vedek on 2009-08-14
if you can enter the recovery mode fine, then go to
 
System > Administration > and the hardware drivers
 
select the recommended one then reboot and you should be good to go.

---

### Post by CFury on 2009-08-14
I must be missing something here as when I enter recovery mode via pressing esc upon startup I only have options to go to the CLI.  There's also an option to correct graphic issues which I attempted however nothing has come of it.

---

### Post by CFury on 2009-08-14
envyng --uninstall-all
reboot

Hey thanks!  That did the trick!

---

### Post by EricKruse on 2009-08-29
This was more or less resolved, but i think it's important to note something.  It looks like EnvyNG is installing the latest ATI driver no matter which ATI card you have.  I have the x1950pro and EnvyNG lists the latest ATI driver as being compatible.  The newer ATI drivers will not support R5xx or earlier cards.   I guess EnvyNG is doing a number of things automatically, but the changes in driver support by ATI are not being accounted for through Envy.  Im a noob to this stuff, but i'm pretty sure i'm right on this one.

---

