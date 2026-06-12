---
title: "Hard drive with xubuntu swap into new computer"
date: 2013-12-07
forum: Hardware
---

### Post by Derringer81 on 2013-12-07
So I have a drive that I pulled from an old pc and threw it into a new pc. Everything seems to function ok except my sound, and network cards.

I still have the install disks, but there is a wiki site I would hate to lose. Is there a way to update these?

I'm sorry if this is a double post, I did a search but didn't find much.

---

### Post by mikewhatever on 2013-12-07
Updating individual drivers on a linux system is hard, especially without knowing exactly which ones. You can backup and reinstall, or upgrade to a supported release - no need to loose anything.

---

### Post by Derringer81 on 2013-12-07
I'm on the latest release already.

Cool thanks!

---

### Post by pbrane on 2013-12-08
If you just have driver issues you *may* be able to just update or re-install the kernel.

Maybe try in a terminal:

[B][FONT=courier new]sudo apt-get update
sudo apt-get dist-upgrade
[/FONT][/B]
reboot and see if that fixed anything, otherwise do a re-install of the kernel

**[FONT=courier new]sudo apt-get --reinstall install linux-image-`uname -r`[/FONT]**

Those are back-ticks around the **[FONT=courier new]uname[/FONT]** command

---

### Post by Yellow Pasque on 2013-12-08
Try deleting pulseaudio's user config files so it generates fresh ones:
```
rm -r ~/.config/pulse*
pulseaudio -k
```

If that still doesn't work give more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

For network give output of:
```
sudo lshw -c network -sanitize
```

---

