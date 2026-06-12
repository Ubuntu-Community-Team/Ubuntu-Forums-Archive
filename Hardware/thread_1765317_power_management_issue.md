---
title: "power management issue"
date: 2011-05-22
forum: Hardware
---

### Post by NERDMAN! on 2011-05-22
i seem to be having issues with power management on a dell inspiron 1525 laptop running xubuntu 11.04 natty, no matter what i do i cannot get the settings to stick when i attempt to increase the brightness of the display while on battery power, it always reverts to 20% and its far too dim to see. is there a config file i can edit to force the settings to stick?

---

### Post by Toz on 2011-05-23
I believe the setting you are looking for is in the XFCE power manager. Open the Settings Manager and select the Power Manager applet. Click on the "On Battery" icon in the left pane and the "Monitor" tab on the right pane. Adjust as required.

---

### Post by NERDMAN! on 2011-05-23
please allow me to clarify my issue a tad more.
the XFCE power manager was completely ineffective at changing anything at all. it did not do anything.
infact when i attempted to change the brightness, not only was there no effect, but when closed the power manager reverted to previous settings. 
as a result of this i wish to know where the file that stores these settings is so i may modify it directly via a text editor and force the changes i require.

---

### Post by Toz on 2011-05-23
Interesting. I just checked now and the brightness level doesn't work for me either (though I don't use thus setting). The file that this setting is saved to is ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml. The new setting is written there, but the Settings Manager ignores it. Perhaps you should report a bug ([https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+filebug](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+filebug)).

---

### Post by NERDMAN! on 2011-05-24
thanks toz. but i feel kinda stupid now as i managed to fix it on my own. i failed to note my laptop has hardwware based brightness controls vis the function key. (i feel really stupid now)
but on the upside thanks for helping me find a bug to report. cheers.
also know anything about multimedia keys in xubuntu? eh spose i should post a thread about it, thanks man

---

