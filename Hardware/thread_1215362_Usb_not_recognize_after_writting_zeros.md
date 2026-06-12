---
title: "Usb not recognize after writting zeros"
date: 2009-07-17
forum: Hardware
---

### Post by gordo151091 on 2009-07-17
So I have Ubuntu 8.10 running in aspire one, and i got a 4gb PQI usb thumb. I wanted to create a bootable usb drive, so first i wanted to format it. I format it writing zeros to the usb with this command dd if=/dev/zero/ of=/dev/sdb1, then i wanted to format it using cfdisk, but i saw no usb. So I runned fdisk -l and it didnt showed the usb, I also runned mount to see if it was there but no luck. If anyone knows a solution or a suggestion please post thanks.

---

### Post by gordo151091 on 2009-07-17
> **gordo151091 said:**
> So I have Ubuntu 8.10 running in aspire one, and i got a 4gb PQI usb thumb. I wanted to create a bootable usb drive, so first i wanted to format it. I format it writing zeros to the usb with this command dd if=/dev/zero/ of=/dev/sdb1, then i wanted to format it using cfdisk, but i saw no usb. So I runned fdisk -l and it didnt showed the usb, I also runned mount to see if it was there but no luck. If anyone knows a solution or a suggestion please post thanks.

using the command dsmeg i get 

"device descriptor read/64, error -110"

---

