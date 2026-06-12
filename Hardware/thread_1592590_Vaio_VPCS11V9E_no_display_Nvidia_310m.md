---
title: "Vaio VPCS11V9E no display Nvidia 310m"
date: 2010-10-10
forum: Hardware
---

### Post by tungmeister on 2010-10-10
Hi guys, having trouble getting 10.10 up and running on on vaio - Initially i was being presented with no display at all from the installer - overcame this by starting up with nomodeset. Once i'd got into gnome i installed the nvidia drivers, rebooted to be presented with the black display with the backlight fluctuating from 100% - 0 about 5 times then nothing,  i'm pretty new to linux so any help would be appreciated. Thanks

edit: setting nomodeset at boot no longer has any effect either - it appears that once the nvidia drivers initialise they override the nomodeset and produce the same issue.

---

### Post by bikrus on 2010-10-11
Hi. Have same issue with Vaio VPCS11M9R NVidia 310m.

1. At boot select "recovery", press "e" and add nomodeset to "linux ..." line. This option works for me. Ctrl-x to boot.
2. After boot finished you can see terminal without prompt or text menu. If you see terminal - try press "down arrow" button - text menu should appear.
3. In menu select last option - root.
4. In prompt:
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
startx
This starts gnome by root in my case. Then check Settings->Additional drivers(Hardware drivers). If necessary - activate nvidia. Reboot as usually.

These steps helped me to have 1280x720 instead of native 1368x768 as workaround awaiting normal nvidia support. Main key is to remove /etc/X11/xorg.conf and activate nvidia-current driver.

Hope this will help.

---

### Post by bikrus on 2010-10-11
With 1280x720 working (see previous post):

1. Go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
2. Download driver for your configuration.
3. Do like [http://www.nvnews.net/vbulletin/showthread.php?t=79966](http://www.nvnews.net/vbulletin/showthread.php?t=79966). Take into account next step before startx.
4. Before startx restore backuped xorg.conf with few options added:

...
Section "Screen"
...
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/IGPU/LCD0/EDID"
...
EndSection
...

EDID place could be different. "cat" EDID before place it to xorg.conf. If "cat" show something like "<not supported>" - this is wrong choise. "cat" should print few lines of garbage (binary data) - this is correct choise.

Have now NVidia driver 256.53 with 1366x768 but **a little slow**.

Hope this will help.

---

### Post by tungmeister on 2010-10-11
i'll give it a shot and post back

---

### Post by bikrus on 2010-10-12
So. Have you any progress?

---

### Post by tungmeister on 2010-10-22
sorry for the delay. sadly it's not working for me, if I specify the default monitor and custom EDID it results in the back light being activated but no picture :(

---

