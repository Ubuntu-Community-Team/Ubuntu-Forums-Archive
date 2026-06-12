---
title: "Gigabyte H87n-wifi USB 3.0 ports not working with Ubuntu 13.10"
date: 2013-12-20
forum: Hardware
---

### Post by mbourd252 on 2013-12-20
Hi gang, I have a Gigabyte h87n-wifi motherboard which all my USB 3.0 ports do not work, but all the usb 2.0 ports work. Would this be a problem with Ubuntu 13.10 not installing the drivers?

I tried looking in the forum and the internet for similar problems I was able to find old postings of problems with usb 3.0 but they didn't indicate this was fixed.

How can I see if Ubuntu sees these USB 3.0 ports?

Let me know if more information is required.

Thanks.

---

### Post by oldfred on 2013-12-20
I know there is/was this issue.

 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by mbourd252 on 2013-12-20
Hi oldfred, so I enable IOMMU and the USB 3.0 should turn on?

Would you know which section this option is found?

Thanks for your help.

---

### Post by oldfred on 2013-12-20
No idea, it just was what one user posted. Not even sure what IOMMU does, and then if that creates other issues.

---

