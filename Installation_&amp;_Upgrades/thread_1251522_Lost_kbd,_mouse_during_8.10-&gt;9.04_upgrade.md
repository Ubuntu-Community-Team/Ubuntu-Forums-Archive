---
title: "Lost kbd, mouse during 8.10-&gt;9.04 upgrade"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by kenryan on 2009-08-27
Hello!

I seem to be rather stuck, and I'm hoping someone can help unstick me.

I had an 8.10 installation (32bit, it itself was a dist-upgrade for the last two releases).  I made sure all outstanding updates were installed, did a backup, then started the distro upgrade to 9.04.

It launched and seemed to be happily downloading the needed packages.  I wandered off while it was doing its thing.

When I returned to check on it, I found the following had happened:

- The screensaver and/or power saver had kicked in, placing my monitor into standby.

- Mouse and keyboard no longer caused activity in X (or at least neither would deactivate the screensaver/power management).

- According to apt-term.log, the upgrade is asking a question (says /etc/gnome/defaults.list was modified, wants to know what it should do).

I am able to ssh in.  I ran "gnome-screensaver-command --exit" (after setting DISPLAY), and "xset dpms force off" (the latter returnd a message that I don't have the Generic Event Extention).

I tried unplugging and replugging the mouse/keyboard (it's a USB combo wireless, with a common dongle).  I tried plugging in a separate mouse.  I tried plugging in a PS2 keyboard.  None seems to work.  (lsusb does list the USB keyboard and mice).  The usbhid and [ue]hci-hid kernel modules are loaded.

Below is the dmesg log from the last plug-in of the kbd/mouse combo and the standalone mouse (both Logitech devices):

---------------------------------------
[25792.300011] usb 7-6: new high speed USB device using ehci_hcd and address 21
[25792.432534] usb 7-6: configuration #1 chosen from 1 choice
[25792.432611] hub 7-6:1.0: USB hub found
[25792.432746] hub 7-6:1.0: 4 ports detected
[25792.728087] usb 7-6.2: new low speed USB device using ehci_hcd and address 22
[25792.842017] usb 7-6.2: configuration #1 chosen from 1 choice
[25792.845161] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6.2/7-6.2:1.0/input/input24
[25792.856090] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-6.2
[25792.860964] Fixing up Logitech keyboard report descriptor
[25792.861587] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6.2/7-6.2:1.1/input/input25
[25792.865466] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-6.2
[27852.440211] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input26
[27938.912010] usb 4-2: new low speed USB device using uhci_hcd and address 3
[27939.086284] usb 4-2: configuration #1 chosen from 1 choice
[27939.107277] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input27
[27939.112343] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
-------------------------------------------

Obviously with the upgrade only partially completed I'm real reluctant to do anything that would kill the X server or cause a reboot - it doesn't seem like that could possibly go well.  I do have a backup but would like to avoid resorting to that if at all possible.

I don't recall the exact menu choice I selected to start the upgrade.  It's the usual GUI that pops up whenever updates are pending - Update Manager?  I can't check without the console, but I think it's this line from ps:

gksu --desktop /usr/share/applications/update-manager.desktop /tmp/tmpGuE2XB/jaunty

If it matters, the machine is a Core 2 Duo on a DG35EC mainboard, only a PCHDTV 5500 card in the slots.  It's running software RAID-1.

I'm out of ideas.  Can anyone suggest anything?  Is there some way to "take over" the upgrade process from the GUI?

Thanks in advance!

---

### Post by stlsaint on 2009-08-27
this is when learning computers gets fun...yes it might not be a good idea for the OS for you to reboot considering that it installed halfway...so can you still use the system as is...meaning can u start the update again but this time remove all external input devices after you start the update? if not you may be looking at a restore...and the upgrade from 8 to 9 has cause many a issues and as of right now you may want to look at just doing a fresh install!!

---

### Post by kenryan on 2009-08-28
Well, since X seems to be permanently in screensave/powersave mode I can't use the console.  Your comment does make me think that I might be able to kill the GUI update (so it unlocks the configuration databases) and try running the upgrade from command line.  I wonder if the apt databases have any sort of checkpointing where it'll know that the process was aborted and can figure out what still needs to be done.  I guess if nobody else comes up with a better idea before tomorrow evening I'll find out.

> this is when learning computers gets fun

Yah, and it seems to be a never-ending process.  I've been hacking Linux since roughly kernel 0.99.something (anyone remember the distro "Linux from Nascent"?)  I've written device drivers, hand-configured servers (i.e. config files for sendmail, bind, apache, etc), all sorts of stuff.  However the big modern distros have a whole layer of stuff - HAL, dbus, pulseaudio, etc to manage devices and configurations.  This new (as in last 8 years or so) stuff has simply left me in the dust!  I'm a hardware weenie, I simply haven't been able to wrap my brain around the layers of abstraction under the hood of distros like Ubuntu or Fedora.  As a result, when something goes wrong I end up a n00b in the woods ...

---

### Post by kenryan on 2009-08-28
Well that was interesting.

I was all prepared to kill the machine and head for my backups.  Just for fun I decided to see if I could switch to a text console.

Ctl-Alt-F1

Bam!  Mouse and keyboard are back, everything working fine!
Question dialogs answered, upgrade completed without a hitch.
I'm posting from the upgraded machine now. :-)

Weird ... I wonder how to switch to a text console now?  Never mind, different thread for a different day...

---

