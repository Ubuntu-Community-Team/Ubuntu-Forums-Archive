---
title: "External Hard disk problem"
date: 2008-05-14
forum: Hardware
---

### Post by coool on 2008-05-14
Hi

I have an iomega 250 gb external hard disk. I have got some serious problem. I am not able to use the drive in windows.In windows, as i soon as i plugin the external hard disk, the system hangs. I checked it in another windows system also.

In linux, when i plugin the hard disk, it recognises it as i can see the icon IOMEGA_HDD in the Places menu. But an error comes up saying "Cannot mount volume". When i click details, this is what it says:
"ntfs_attr_pread: ntfs_pread failed: Input/Output error Failed to read NTFS $Bitmap: Input/Output error NTFS is either inconsistent or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (eg /dev/mapper/nvidia_eahaabc_1). Please see the 'dmraid' documentation for the details."

The hard disk was working perfectly 3 days ago in ubuntu and windows. I dont know why this problem occured. 
I had deleted some stray exe files in the hard disk when i was using it under linux. (I plugged in another Iomega hard drive into linux and saw an autorun.inf file in the drive). I may have deleted this autorun.inf file in the hard disk and that may be the cause of the problem. 

Can someone help me with this? I dont want to format this disk as it contains lot of data i dont want to lose. Thanks.

---

