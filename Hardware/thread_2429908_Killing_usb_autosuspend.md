---
title: "Killing usb autosuspend"
date: 2019-10-24
forum: Hardware
---

### Post by pwabrahams on 2019-10-24
I'm trying to kill **usb autosuspend** with no success so far.  I've also raised this issue in AskUbuntu.  The answer I get is to set /sys/bus/usb/devices/usb*/power/autosuspend to "-1", and to make the effect permanent by embedding the command in the **grub** configuration file by modifying **/etc/default/grub** to include **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"**.  The reason for putting this in the Grub configuration, which might seem a strange place for it, is that the setting has to be made very early, probably before the **/sys** directory is created.  Unfortunately that just does not work for me. The context is a Yamaha electric piano, connected via USB, which cuts out after playing a MIDI file  for about half a minute.  The piano works correctly under Windows 10 on a dual-boot machine.  I'm running Kubuntu 18.04 with the 19.04 backports.

Normally I wouldn't double-post such a subject, but I haven't had any success with the remedies suggested on AskUbuntu. Even with the best physicians, it's often worthwhile getting a second opinion.  It's not clear why turning on **autosuspend** is the default anyway, since it seems to do more harm than good.

---

