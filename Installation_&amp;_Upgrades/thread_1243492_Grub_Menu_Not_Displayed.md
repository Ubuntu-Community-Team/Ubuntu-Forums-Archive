---
title: "Grub Menu Not Displayed"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by hlewagastir on 2009-08-18
Now, I recently came into possession of a new acer 5530g laptop. It came preinstalled with Vista, and with the hard drive pre-partitioned into 4 blocks : a 10g restore partition, 2 large partitions (one for system, one for data), and a 3.5g partition for "Instant On Arcade", for which there is a button, to boot directly to that partition.
 
I decided to install Ubuntu (9.04) on this laptop, as I have it on all my existing machines. I cleared the final 3.5g part. and shrank the data partition to provide around 30g of total space. I reparted this as a primary, and installed ubuntu into the remaining space, after a bit of trouble, everything seemed to work.
 
The problem is, I had tried to be a tad clever: Knowing that the 'arcade button' booted from the fourth partition on the drive automatically, I was trying to keep the linux and the windows installs completely seperate - thus being able to boot ubuntu from the arcade button, and windows as normal via the power button. So, I installed grub onto that fourth partition for that purpose.
Now Vista continues to boot perfectly normally, as expected, but when I use the alternate button to boot to ubuntu, grub loads but goes straight to a prompt, and does not provide me a boot menu.
 
Any ideas on how I could resolve this, or should I just give up, and reinstall with a normal dual boot?
 
Thanks

---

