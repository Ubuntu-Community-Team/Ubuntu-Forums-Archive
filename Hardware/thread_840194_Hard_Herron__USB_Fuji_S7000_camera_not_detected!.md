---
title: "Hard Herron : USB Fuji S7000 camera not detected!"
date: 2008-06-25
forum: Hardware
---

### Post by reisrocks on 2008-06-25
Hi,

Fujifilm s7000 camera would automount on Gusty Gibbon.

Now on Hardy Herron it doesn't automount.. I've tried fixing the problem with fstab but it was a bit over me.

I've tried this on my workstations using Hardy Herron, it was the case on all of them.

Could someone kindly help me out with this issue?

Thanks in advance.

Reis.

---

### Post by reisrocks on 2008-06-25
Progress:

Running lsusb gives me:

Bus 002 Device 004: ID 04cb:012d Fuji Photo Film Co., Ltd FinePix S7000 Zoom (PC-Cam mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

also running dmesg:

[187324.342380] usb 2-6: new high speed USB device using ehci_hcd and address 5
[187324.475946] usb 2-6: configuration #1 chosen from 1 choice

running lspci, the only relevant parts are:

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)


So the camera is clearly detected.. but still I'm not too sure where to go from here.. it's definitely not in /media/ and /mnt/ is empty.

---

### Post by reisrocks on 2008-06-25
Also please note I am posting here partly to help out other owners of this camera who might encounter this problem in the future..

I'll post the solution (or a link to this thread) on the hardware wiki 

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaDigitalCamerasFujifilm](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaDigitalCamerasFujifilm)

---

### Post by starcannon on 2008-06-25
I have 1 fuji film digital camera, it never got along nice with linux, the fast solution was to just use a usb card reader and take the camera out of the equation when getting the pictures off of it.

---

### Post by timcredible on 2008-06-25
it's just that the system doesn't know what the camera is, you need to tell it it's a camera, that's done simply by adding the make/model from the lscpi command into a text file.  try using [this link]("http://ubuntuforums.org/showthread.php?t=323196"), it worked for me.  if that doesn't work, try setting the camera to the other usb mode (there's 2 modes, dsc and ptp) mode and see if digikam or fspot sees it then.  if not, then you're going to be stuck with buying a card reader - fuji's newer cameras are moving to sd cards, so i would suggest you buy a reader that at least does xd and sd.

edit: i just checked hardy, and that file doesn't exist anymore, so maybe create it, reboot, and see if it works?  if not, then hopefully someone else knows where the new files are.

---

### Post by reisrocks on 2008-06-26
OK the problem was coming from the camera rather than the OS:

To fix this:

Twist the camera preset knob to 'SET', the main power knob to camera (the red camera image, rather than the playblack image), then in the settings hit 'reset'.

The usb transfer mode was set to 'PC' now it seems to be set to 'Memory card + CF + DSC'.

I hope this will help people in the future, this sure did give me some hardache.

---

