---
title: "How to use bluetooth with my Nokia 7370?"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by Turin Turambar on 2006-08-23
I cannot access my Nokia phone in Ubuntu! I installed gnome bluetooth and in 3rd try it found the phone. However, I cannot do anything with it. No file sharing, nothing.

Also when I try "sudo hidd --search", nothing happens... It just says "searching..." and that's it.

---

### Post by Turin Turambar on 2006-08-24
So nobody knows?:confused:

---

### Post by lemmy999 on 2006-08-25
TT try this as a starter. It works for me.

Question  HOWTO: Use GNOME's bluetooth tools
I've been playing around trying to use the GNOME bluetooth tools to transfer files to and from my mobile phone (a Nokia 6680). Somebody's already posted a message here about using KDE bits and pieces to do this, but I wanted to explore the more elegant GNOME tools. So here's how it's done.

INSTALLING GNOME-BLUETOOTH
- assuming your system is configured to use the online software repositories, open Synaptic Package Manager and search for gnome-bluetooth.
- choose to install gnome-bluetooth. There's no need to search for and install the bluez utilities because, under Ubuntu 5.10, they're installed by default

SENDING FILES TO ANOTHER DEVICE
You'll need to create a desktop shortcut for this to work:
- right-click on the desktop and click Create Launcher
- in the Name field, type something like "Send file via bluetooth".
- in the command field, type gnome-obex-send
- give it a cool icon if you wish (I like the road icon near the top of the list)
- Click OK to create the shortcut.
- from now on, just drag and drop a file onto the shortcut to send it via bluetooth. You'll then be able to choose your device in the dialog that comes up (assuming that your phone is set to be "visible" so it can be detected by other bluetooth devices)

RECEIVING FILES VIA BLUETOOTH
- click the Applications - System Tools menu and click Bluetooth File Sharing
- nothing will seem to happen but a new icon will appear top right of the screen in the system tray
- on the device you're sending the file from, choose to send the file and search for your computer. It should be called something like ubuntu-0.
- send the file
- a dialog will appear on your PC asking if you want to receive the file. Click Yes
- the file will be saved to your Home folder
- you can add this program to your startup by clicking System - Preferences - Sessions, and clicking the Startup tab. The program's called gnome-obex-server

And that's all there is to it. There's another component installed along with gnome-bluetooth called Bluetooth Manager. I don't know what this does. It can see my phone after searching for some time but when I click on Properties it just doesn't do anything. Similarly, if I try and pair my phone to Ubuntu, I'm asked for a PIN code, yet I haven't been supplied with any by the Gnome-Bluetooth tools. If anybody knows of any documentation for Gnome-Bluetooth (the official website has none), post it below.

---

### Post by DC@DR on 2006-10-21
Thanks lemmy999 for this useful instruction :)

---

