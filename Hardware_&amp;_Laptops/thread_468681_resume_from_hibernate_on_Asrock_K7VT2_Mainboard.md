---
title: "resume from hibernate on Asrock K7VT2 Mainboard"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by ernstkl on 2007-06-09
Hello!

with the above mainboard, and kubuntu feisty, I can suspend or hibernate, this seems to work fine. But when I press the power button to awaken the machine, it always does a normal reboot. The Bios seems to be configured correctly (in windows it works).

Is this a configuration problem? Has anybody experienced similar problems?

Ernst

---

### Post by neptho on 2007-06-09
Check your BIOS settings; see if ACPI is set for S1 or S3.

---

### Post by ernstkl on 2007-06-12
in the bios, there is only one option w.r.t S3: disable or enable it. It is enabled. In the BIOS, I see nothing else that would seem related.

---

### Post by prensing on 2007-06-12
I just solved this "exact" problem on my Sony.  It started happening a few days ago, and now I realize it was caused by the upgrade to the 2.6.20-16 kernel.

My problem was that the RESUME disk in the initrd is listed by UUID and the UUID of my swap partition was getting changed every time I tried resuming but failed.

So, start by doing "ls -l /dev/disks/by-uuid/" and noting the UUID of your swap partition. Check in /etc/fstab to see if they agree. The place that really matters for resuming, however, is /etc/initramfs-tools/conf.d/resume. 

I chose to change both /etc/fstab and the initramfs file to use old-fashion /dev names, in my cause /dev/sda6. I edited both files. 

You then need to rebuild the initrd file for your kernel. Save a copy of your current /boot/initrd-XXX, just in case.  Then do mkinitramfs -o /boot/initrd-XXX (where XXX is your current kernel version). 

That solved it for me. I am not sure about the logic of using UUIDs for disk; in this case, it was way too fragile.

---

### Post by ernstkl on 2007-06-13
prensing, these were very interesting hints. I followed them, but unfortunately the problem remains.

From the symptoms I would guess I have a problem with the way the mainboard interprets the press of the power button: immediately after pressing the power button (to trigger the resume) the CD LEDs blink like during a reboot.

---

### Post by ernstkl on 2007-06-13
well, I did not distinguish between 'suspend to disk" and "suspend to ram" clearly
for suspend to disk (hibernate) the hints of prensing were the solution
for suspend to ram the problem of "reboot instead of resume" remains

---

### Post by neptho on 2007-06-15
There should be another means to awaken your machine from sleep when you 'suspend to RAM.'  Have you tried pressing the 'soft power' power button on your keyboard?  (Many keyboards have had this for years; most USB keyboards do.)

---

