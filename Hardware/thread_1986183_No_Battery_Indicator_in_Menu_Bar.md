---
title: "No Battery Indicator in Menu Bar"
date: 2012-05-24
forum: Hardware
---

### Post by eclipsechasers2 on 2012-05-24
With 12.04, battery indicator has disappeared from menu bar. Trying "System Settings" "Power", there is a place to indicate "Show battery status in the menu bar"; possibilities are "when battery is present", "when battery is charging", or "never". This option always shows up as blank. When I select any of the options, nothing changes. Furthermore, when I return to this page, the option again shows up as blank. All other options on the power panel are remembered when I change them.

---

### Post by 0110011011 on 2012-05-24
Same thing here.

Not sure what it means, but when I run 
```
sudo gnome-control-center
```
and click on the 'Power' icon I can see the following error message
```
Error getting devices: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.Power' on object at path /org/gnome/SettingsDaemon/Power
```
However, this error is not shown when gnome-control-center is run as a regular user.

Edit 1:
It might also be interesting to note that the log in screen does show a battery indicator and that I'm running GNOME Classic (No effects).

Edit 2:
I added 'Indicator Applet' to the panel and it shows a battery status icon. But it also shows an icon for sound and mail which I would rather not have.

---

### Post by eclipsechasers2 on 2012-05-27
Thank you. Adding the indicator applet works. Like you, I would prefer to get rid of some of the icons, but I would rather have the superfluous data rather than be missing the indicators I want.

---

