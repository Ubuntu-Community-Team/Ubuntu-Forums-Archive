---
title: "after 5.10 installation neither USB nor floppy working"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by evaristegalois on 2006-02-19
I just got the CD in the mail and installed Ubuntu 5.10. on my laptop (an older Thinkpad i Series 1412 model). Everything's working fine (although I had to disable pnp os in the bios and write on boot: ``linux acpi=off no acpi'' before it installed properly) but ** I can't find a way to see my floppy drive or my USB port**. The floppy drive is displayed in Nautilus (as opposed to the USB drive -- no sign of that [worked fine under Windows]) but when I click on it I get the message: ``Unable to mount the selected volume -- mount: I could not determine the filesystem type, and none was specified''). I've searched Forums and Documentation Files for a long time but now I'd really like to get some help on this.

evaristegalois

---

### Post by Heike on 2006-02-22
Hi :) 
I have exactly the same problem :confused: . Have you found a solution so far?

Heike

---

### Post by evaristegalois on 2006-02-23
Heike,

let me know how you do. No solution yet. I am going to check out a linux book at the library to see how hardware problems like this can be hunted down. There is apparently a log file which tells you what your computer sees when it starts up and how it does with driver installation (/var/log/something or other)

Evariste

---

### Post by schatz on 2006-02-26
Can you post the result of 
sudo fdisk -l
and
cat /etc/fstab

They are problably not being mounted correctly

---

### Post by evaristegalois on 2006-03-08
the problem was that I disabled PnP OS in my BIOS -- a step which seemed to be necessary because my installation process would get stuck if I didn't do it. I solved that problem by writing ``linux acpi=off no acpi'' on the boot line before installing Ubuntu which took care of the installation problem. Then I forgot to enable PnP OS in my BIOS, almost gave up on Linux until a colleague pointed out the obvious to me. Re-enable PnP OS: everything's working fine now. Thanks.

---

