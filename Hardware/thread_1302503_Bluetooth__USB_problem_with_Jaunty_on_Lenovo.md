---
title: "Bluetooth / USB problem with Jaunty on Lenovo"
date: 2009-10-27
forum: Hardware
---

### Post by Cournot on 2009-10-27
I am a newbie using Jaunty/Gnome on a Lenovo X-Series since a month or so. It comes with an Ultrabase docking station. Yesterday I replaced my old Windows home laptop with the Lenovo and plugged in an external monitor, keyboard, external DVD-writer. Everything worked more or less fine, I booted and rebooted several times, no serious issues.

Today when I booted, after logging in (typing username and password) I got a bunch of apparently bluetooth-related error messages:

 [   18.370594] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
 [   18.370598] Bluetooth: BNEP filters: protocol multicast
 [   18.389289] Bridge firewalling registered
 [   20.064216] usb 1-4.1: device descriptor read/64, error -110
 [   35.240224] usb 1-4.1: device descriptor read/64, error -110
 [   35.416225] usb 1-4.1: new high speed USB device using ehci_hcd and address 7
 [   50.492222] usb 1-4.1: device descriptor read/64, error -110
 [   65.664226] usb 1-4.1: device descriptor read/64, error -110
 [   65.840232] usb 1-4.1: new high speed USB device using ehci_hcd and address 8
 [   70.860218] usb 1-4.1: device descriptor read/8, error -110
 [   75.980225] usb 1-4.1: device descriptor read/8, error -110
 [   76.156230] usb 1-4.1: new high speed USB device using ehci_hcd and address 9
 [   81.176228] usb 1-4.1: device descriptor read/8, error -110
 [   86.296224] usb 1-4.1: device descriptor read/8, error -110
 [   86.400239] hub 1-4:1.0: unable to enumerate USB device on port 1

The laptop gets stuck for a while generating these errors, which is a bother, then works normally. I then disabled Bluetooth (don't use it) through Administration/Services and also Preferences/Startup Applications. On booting again, the error messages are gone (so it is definitely bluetooth-related), but the USB ports of the docking station don't seem to work while booting: actually, they work fine for Grub (checked with the external keyboard), then stop working for the log-in screen, then work again after log-in. To top it, the USB ports in the laptop itself (not the base) have no such problems.

What is going on here? Not a serious problem, I know, but one of the reasons for switching to Linux was to be able to understand what is going on in the computer, and now I am puzzled. Why does Bluetooth give problems after having plugged external monitor and keyboard but not before? Why did it not happen yesterday? Why do the USB ports of the base stop working when Bluetooth is enabled? Is there any elegant solution to all this? I would be grateful for any pointers or suggestions.

---

