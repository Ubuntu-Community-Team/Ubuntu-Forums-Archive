---
title: "Sound broken after this morning's wily update"
date: 2016-03-18
forum: Hardware
---

### Post by drdrnewman on 2016-03-18
This morning I did a wily-update. It broke my sound system and scanner access.

The update was:

[FONT=monospace][COLOR=#000000]Start-Date: 2016-03-18  09:52:52[/COLOR]
Upgrade: libpam-systemd:amd64 (225-1ubuntu9, 225-1ubuntu9.1), udev:amd64 (225-1ubuntu9, 225-1ubu
ntu9.1), libudev1:amd64 (225-1ubuntu9, 225-1ubuntu9.1), libudev1:i386 (225-1ubuntu9, 225-1ubuntu
9.1), systemd-sysv:amd64 (225-1ubuntu9, 225-1ubuntu9.1), systemd:amd64 (225-1ubuntu9, 225-1ubunt
u9.1), libsystemd0:amd64 (225-1ubuntu9, 225-1ubuntu9.1), libsystemd0:i386 (225-1ubuntu9, 225-1ub
untu9.1)
End-Date: 2016-03-18  09:53:34

Now the only sound output (sink) available is the dummy one. Neither alsamixer nor pavucontrol list my Intel and Nvidia sound cards.

aplay -l gives 'no soundcards found'. But sudo aplay -l finds them all.

I have manually forced pulseaudio to use the Intel card, as it isn't getting it from udev, and am running it as a daemon from root. But that doesn't let me choose sinks and sources, as I was able to do from the KDE system settings.

Another udev change is that it can no longer find my scanner (part of my Canon Pixma multi-function printer scanner). That is disappointing, as it was only in an update last week that for the first time in a year allowed software to access the scanner without being blocked because usb-storage was using another subchannel over the same usb connection.

I also see that /etc/init.d/sound and /etc/init.d/pulseaudio scripts have disappered. I know they are only there for init compatability, but it looks like a systemd update has removed them. That may be why some of the new versions have changelog entries to wily-proposed, rather than wily or wily-updates. But they were released as wily-updates. I don't have wily-proposed as a source.

Has anyone had similar problems, or found a fix? How can I revert?[/FONT]

---

### Post by drdrnewman on 2016-03-18
I should add I am using the lowlatency kernel, and the Kubuntu desktop environment.

---

### Post by drdrnewman on 2016-03-19
I've managed to revert to the previous versions, and got my sound back (but not the scanner). But I still don't know what went wrong.

---

