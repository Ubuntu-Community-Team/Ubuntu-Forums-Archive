---
title: "&quot;On Battery&quot; Tab Disappeared from g-p-m"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by Tristam Green on 2007-11-15
Today, in an effort to get Hibernate/Suspend working, an associate and I noticed that I had two services running to handle power, acpid and apmd.  I disabled one then restarted, and noticed that I was still unable to hibernate/suspend.  I re-enabled it, then disabled the other, and restarted with the same outcome.

I re-enabled both as they were initially, and restarted.  After this restart, the "on battery" tab has disappeared from the g-p-m interface.

Gutsy 7.10 on a Dell 1501, stats on the computer in my signature.

Relevant Outputs, on Batt Power:

tristam@DDBF6QD1:~$ cat /proc/acpi/battery/*/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1219 mA
remaining capacity:      3387 mAh
present voltage:         11447 mV

tristam@DDBF6QD1:~$ cat /proc/acpi/ac_adapter/*/state
state:                   off-line

When I plug in, I get the same outputs.  However, the panel icon in GNOME indicates "you are running on AC Power".

Restarting dbus helps, but only while the laptop is booted.  Upon restart of the system, the problem comes right back.


Any help would be greatly appreciated.  I'd hate to have to reinstall Gutsy because of this.

---

### Post by ffchaves on 2007-11-21
A very similar issue happened to me last night. Only my circumstances were different as I was following an orientation from ubuntuguide.org to speed-up my system.

The text listed some services that could be disabled as the Bluetooth Manager which I dont use.

As I was unchecking the listed services in System > Services (namely: alsa-utils, bluetooth, brltty, hdparm, acpid, apmd, screen), I realized acpid and apmd were power management services and, as I am using a laptop, I just turned those two back on (like, 10s later, before even closing the window).

From the first reboot on, my system's been behaving just like Tristam described:

- "On Battery" not visible in Power Management window;
- the notification always displays "Computer running on AC power", even if running on battery (in fact, no change of behavior at all when unplugged from AC);
- upon login, display dims to half brightness although gpm accuses 100%;

- only, in my case, I get the correct outputs from "cat /proc/acpi/ac_adapter/*/state" and "cat /proc/acpi/battery/*/state":

I am running Gutsy in a Toshiba Satellite A50.

No clue on where to start. And I also thought about reinstalling...

---

### Post by ffchaves on 2007-12-04
For the sake of documentation, this worked for me:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413/comments/21](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413/comments/21)

Regards

---

