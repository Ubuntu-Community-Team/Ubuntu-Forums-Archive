---
title: "Minimal Intrepid Installation"
date: 2008-11-12
forum: General Help
---

### Post by Xyem on 2008-11-12
I'm going to make a topic here about the minimal installation of Intrepid I am trying to configure on my laptop. The reason is two-fold. First and foremost, others may find the information here useful and solve their issues. Secondly, someone may be able to help solve the issues I am having :) So please post any suggestions or questions!

At first it will be just some quick notes, I'll flesh it out if needs be. Comments are about the minimal install unless otherwise specified.

**Initial notes**
The installation was done from the Alternative CD, using the entire disk as Encrypted/LVM.
After installation, I installed 'xorg' and 'fluxbox' as my window manager.

**Touchpad**
Desktop : Works
Minimal : Works

Didn't work initially, had to install the 'hal' package so Xorg could find it as a pointer device ( Xorg.log told me it couldn't find any ).
Alternatively, I may have been able to add it to xorg.conf..

**Wired ethernet**
Desktop : Works
Minimal : Works

Was there ever any doubt? I've never come across a wired network adapter Linux couldn't use immediately!

**Wireless**
Desktop : Works
Minimal : Works

Installed 'network-manager' and started the service ( 'sudo /etc/init.d/NetworkManager start' ).
Using 'nm-applet' I can easily connect to the network. Would like to get rid of the request to add the password to the keyring though..

**Suspend**
Desktop : Works
Minimal : Broken

Installed 'gnome-power-manager' and ran it. Forced the tray icon to always be visible using 'gnome-power-preferences'. Trying to suspend did absolutely nothing though. I used one of the PolicyKit tools to grant my user permission to suspend. Suspend works but Wakeup(?) does not. The screen remains completely blank. Switching terminals doesn't work but I can reset with Ctrl-Alt-Del so it is responsive.
Possible problem: May be the root partition encryption is interfering

**nVidia driver**
Desktop : Works
Minimal : Broken

In the desktop installation, I just used the Restricted Driver Manager ( jockey? ) to install and it works nicely.
If I install 'nvidia-glx-177' it doesn't work. Not sure what other steps the RDM takes to install it.
Alternatively, I could install 'jockey' and get that to install the driver..

**Camera**
Desktop : Works
Minimal : Not tested

Installed 'xawtv' to get it to work in Desktop, although I think it was actually a dependency that fixed the issue ( v4l2? )

**SD card reader**
Desktop : Broken
Minimal : Not tested

Putting in an SD card on the desktop did nothing at all. The controller doesn't seem to show in 'lspci' or anything.

**Bluetooth**
Desktop : Untested
Minimal : Untested

I don't use Bluetooth :)

---

