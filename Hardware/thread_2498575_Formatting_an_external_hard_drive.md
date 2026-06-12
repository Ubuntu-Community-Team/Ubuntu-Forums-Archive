---
title: "Formatting an external hard drive"
date: 2024-06-20
forum: Hardware
---

### Post by apassi on 2024-06-20
Hi
I tried to format the external nwme ssd with Ubuntu's gparted, but I got the message shown in the picture and the format was not successful.
Is there any help?

[IMG][[IMG]https://i.ibb.co/dQ7p0mv/alustus1.jpg[/IMG]]("https://ibb.co/2j5M7Zr")[/IMG]

---

### Post by ajgreeny on 2024-06-20
I suspect that the disk was still mounted when you attempted for format it but it's difficult to see much detail in your image.

Also please do not add large images inline as you have done here; use the attachment system, the paperclip icon, in the toolbar which will show a small icon image below the post which is then expanded by clicking it.

---

### Post by yancek on 2024-06-20
The image you posted shows an error unmount /dev/sda1 but you indicate it is an nvme SSD so that probably isn't the right device.  Use parted or fdisk to get the correct device information.  Do you have any partitions on the device or were you planning to format the entire device?

---

