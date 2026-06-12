---
title: "More hd0 questions"
date: 2012-07-29
forum: Hardware
---

### Post by linuxisgreat on 2012-07-29
Hi all.
 
Need to ask something about ubuntu's boot process again because i've had to reinstall the last version of ubuntu several times due to crashes and when I ran the installer one time the sdx letter was different to the second time I ran it.
 
What defines hd0 to grub and the linux kernel? Is it defined by the first boot device or something else? I read somewhere that grub identifies drives with a letter depending on their UUID is that correct?
 
Also I don't boot my linux insalls by changing the USB drive to first boot device but instead because it is a USB drive I use the F12 boot menu to switch to boot from the MBR on my USB drive. Could this affect which drives grub maps letters to? What would the installer and the grub-mbr update packages consider hd0 when they write to it to install the MBR? The drive I originally installed to was seen as sdb2 (hd1,2) which is the second partition of my USB drive.
 
When I ran the installer to reinstall ubuntu after it crashed I realized that the USB drive was seen as sdc2(hd2,2 to grub) second drive second partition, I knew this because my files stored on the first NTFS partition were on the sdc1 drive.
 
EDIT: Sorry should have mentioned that my laptop is an acer aspire 5742 with Intel HDA graphics 128MB, 3GB of RAM and 320GB HDD.

---

### Post by linuxisgreat on 2012-08-03
bump... Anyone? Any idea why the drive letters seemed to be swapping around at different install times? :confused:

This is really strange and quite serious to me as if grub gets confused and updates the wrong drive it could wipe my main drive's windows bootloader.

This was when I was using 11.04 BTW now I have 12.04 but just in case the drive letters swap around again for some reason I have yet to do any kernel or grub updates.

Please let me know any reason this might be happening.

---

