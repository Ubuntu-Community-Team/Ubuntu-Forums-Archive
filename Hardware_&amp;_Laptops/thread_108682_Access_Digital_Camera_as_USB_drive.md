---
title: "Access Digital Camera as USB drive"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by kingmonkey on 2005-12-26
My kodak dx7440 works like a charm when importing photographs using gThumb. I recently wanted to use my camera as a usb drive but I could not find the mount point. 

Can someone please enlighten me on this issue?

KM

---

### Post by kingmonkey on 2005-12-27
I figured out that there is PTP protocol and USB mass storage type cameras. On windows you need a driver to see the camera as a USB mass storage type drive.

I used "gphoto --upload-file" and I still couldnt upload files even though the --summary said I could.

Does anyone else have any idea where I should go from here? Would anybody be intreseted in the debug error messages from gphoto when I try to upload?

---

### Post by stuporglue on 2005-12-27
Check your camera's settings first. Mine (Old Sony Cybershot) has options for both types of transfer. When it's in USB storage mode it mounts as a USB thumb drive would, otherwise it doesn't. 

I'm afraid I don't have any experience getting PTP mode to work under Linux.

---

