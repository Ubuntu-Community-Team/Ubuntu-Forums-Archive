---
title: "System freeze with Logitech G29 after launching various racing games"
date: 2018-07-21
forum: Hardware
---

### Post by ahood on 2018-07-21
Hi All,

I am getting complete system freeze in xubuntu (18.04) after I (a) connect a Logitech G29 device, (b) launch SuperTux Kart (installed via software center), and (c) launch the race from within SuperTux Kart. This issue occurs with racing game installed via steam (Dirt Rally and F1 2017). When the freeze occurs, the system is unresponsive to all keyboard inputs and I have to shut down by holding the power button for 5 seconds.

The Logitech G29 device is recognized by the system because it (a) autocalibrates upon connecting with the machine (via USB) and (b) jstest-gtk and evtest list the device and interact with the G29 normally. This issue started recently after an update that included a message about Logitech devices and something about security. Below is the lastest apt history update. I have looked in the syslog and kernlog and I do not see an error message that coincides with the issue.

> Start-Date: 2018-07-20  22:14:13
Commandline: apt autoremove
Requested-By: steam (1001)
Remove: python-gdata:amd64 (2.0.18+dfsg1-2), python-crypto:amd64 (2.6.1-8ubuntu2)
End-Date: 2018-07-20  22:14:14

Start-Date: 2018-07-20  23:19:21
Commandline: apt upgrade
Requested-By: steam (1001)
Install: linux-image-4.15.0-29-generic:amd64 (4.15.0-29.31, automatic), linux-headers-4.15.0-29:amd64 (4.15.0-29.31, automatic), linux-modules-extra-4.15.0-29-generic:amd64 (4.15.0-29.31, automatic), linux-modules-4.15.0-29-generic:amd64 (4.15.0-29.31, automatic), linux-headers-4.15.0-29-generic:amd64 (4.15.0-29.31, automatic)
Upgrade: language-pack-gnome-en:amd64 (1:18.04+20180423, 1:18.04+20180712), linux-headers-generic:amd64 (4.15.0.23.25, 4.15.0.29.31), linux-libc-dev:amd64 (4.15.0-24.26, 4.15.0-29.31), libapt-inst2.0:amd64 (1.6.2, 1.6.3), libsystemd0:amd64 (237-3ubuntu10, 237-3ubuntu10.2), libsystemd0:i386 (237-3ubuntu10, 237-3ubuntu10.2), linux-image-generic:amd64 (4.15.0.23.25, 4.15.0.29.31), apt:amd64 (1.6.2, 1.6.3), snapd:amd64 (2.32.9+18.04, 2.33.1+18.04ubuntu2), squashfs-tools:amd64 (1:4.3-6, 1:4.3-6ubuntu0.18.04.1), xfce4-settings:amd64 (4.12.3-0ubuntu1, 4.12.4-0ubuntu0.18.04.1), python-apt-common:amd64 (1.6.1, 1.6.2), udev:amd64 (237-3ubuntu10, 237-3ubuntu10.2), language-pack-en:amd64 (1:18.04+20180423, 1:18.04+20180712), libapt-pkg5.0:amd64 (1.6.2, 1.6.3), libudev1:amd64 (237-3ubuntu10, 237-3ubuntu10.2), libudev1:i386 (237-3ubuntu10, 237-3ubuntu10.2), python3-distupgrade:amd64 (1:18.04.19, 1:18.04.21), ubuntu-release-upgrader-core:amd64 (1:18.04.19, 1:18.04.21), language-pack-gnome-en-base:amd64 (1:18.04+20180423, 1:18.04+20180712), systemd-sysv:amd64 (237-3ubuntu10, 237-3ubuntu10.2), libpam-systemd:amd64 (237-3ubuntu10, 237-3ubuntu10.2), systemd:amd64 (237-3ubuntu10, 237-3ubuntu10.2), apt-utils:amd64 (1.6.2, 1.6.3), libnss-systemd:amd64 (237-3ubuntu10, 237-3ubuntu10.2), language-pack-en-base:amd64 (1:18.04+20180423, 1:18.04+20180712), ubuntu-release-upgrader-gtk:amd64 (1:18.04.19, 1:18.04.21), libnss-resolve:amd64 (237-3ubuntu10, 237-3ubuntu10.2), unattended-upgrades:amd64 (1.1ubuntu1, 1.1ubuntu1.18.04.4), apt-transport-https:amd64 (1.6.2, 1.6.3), linux-tools-common:amd64 (4.15.0-24.26, 4.15.0-29.31), linux-generic:amd64 (4.15.0.23.25, 4.15.0.29.31), python3-apt:amd64 (1.6.1, 1.6.2)
End-Date: 2018-07-20  23:20:25

Start-Date: 2018-07-21  06:29:56
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-extra-4.15.0-22-generic:amd64 (4.15.0-22.24), linux-modules-4.15.0-22-generic:amd64 (4.15.0-22.24), linux-image-4.15.0-22-generic:amd64 (4.15.0-22.24)
End-Date: 2018-07-21  06:29:59

Start-Date: 2018-07-21  06:30:02
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-4.15.0-22:amd64 (4.15.0-22.24), linux-headers-4.15.0-22-generic:amd64 (4.15.0-22.24)
End-Date: 2018-07-21  06:30:04

How might I obtain more information that would clue me in on the problem? Any assistance will be greatly appreciated.

Thanks

---

### Post by #&amp;thj^% on 2018-07-21
When ever I run into suspected bugs on mouse related hardware.
Open a terminal and enter the following commands:
This is when the mouse is responsive though.
```

xmodmap -pp > ~/xmodmap-pp
xev | grep -i button 
```

Put the mouse cursor into the rectangle and push all your mouse buttons. Mention in the bug report which button number is reported, e.g. left = 1, scrollwheel up = 4, horizontal scrollwheel left = 6, thumb button = 8, pinkie button = 9, ...

Attach as separate attachments to your bug report /var/log/Xorg.0.log and ~/xmodmap-pp. 
I wish i could be more helpful here though. :(
BTW Try UN-plugging the mouse and re-plug it. (On the off chance you haven't yet)

---

### Post by ahood on 2018-07-22
Thank you for the reply. I should clarify that the G29 is a steering wheel. After more investigation, I was experiencing freezing in almost all of my games that I had installed, even with the Logitech G29 not connected to the pc. The freezing in the games stopped after I disconnected my Logitech wireless k400r keyboard with integrated mouse. I don't know why this keyboard appears to be incompatible with my system, but I am happy I have no more freezes. I am now using a generic USB keyboard and mouse and the freezing has gone away.

---

