---
title: "mysterious USB Drive appears in &quot;places&quot;"
date: 2009-03-31
forum: Hardware
---

### Post by mathtick on 2009-03-31
In the file browser I have a "USB Drive" entry in the places column on the right hand side in addition to the usual entries.  There should be no USB drive (I have only an internal drive).  Right clicking on this gives me only the option to open or "rescan".  Rescanning gives the error:

Unable to poll USB Drive for media changes

Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.UnknownMethod: Method "CheckForMedia" with signature "" on interface "org.freedesktop.Hal.Device.Storage.Removable" doesn't exist 

I'm running Intrepid on an msiwind:

uname -a 

Linux easy 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

I'm not sure if it's related but I'm also having the problem where powertop reports that a USB device is active %100 percent of the time ... other people have reported this and there is some sort of an active thread on this issue.  However, I have not found anything with the USB Drive showing up in the file browswer.

---

### Post by Dark_Stang on 2009-03-31
Can you post the output of "lsusb"?

---

### Post by mathtick on 2009-03-31
~$ lsusb
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 002: ID 5986:0203 Acer, Inc 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



> **Dark_Stang said:**
> Can you post the output of "lsusb"?

---

### Post by Dark_Stang on 2009-04-02
The very first line of that shows a Mass Storage Device hooked up to USB. A quick google search reveals that to be your card reader. So you won't be able to mount that unless you stick an SD (or whatever it supports) card in the slot. Unfortunately, this is about as far as I can take this without throwing out guesses or having the machine in front of me.

---

### Post by 0per4t0r on 2009-04-02
someone probably used a usb drive in your computer. I have the same thing. I use my flash drive, and that thing always stays up there, even when not in use. Just ignore it, it's just from previous use of a usb storage device, but it won't work.

---

