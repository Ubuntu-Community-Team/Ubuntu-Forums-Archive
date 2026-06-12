---
title: "upgrading dell inspiron 530 from 7.10 to 8.04 to 8.10"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by danh-a on 2009-04-10
Hi All,

I have a dell inspiron 530 on which ubuntu 7.10 was factory pre-loaded.

I attempted to upgrade it to 8.04 using the web interface.  It could upgrade, but only boots with difficulty, and in fact i don't have a boot sequence i can reliably follow.  (I've managed to boot it twice by stumbling around, but i don't have all the steps written down.)

The symptom of the problem is that if you try to restart in the gui, it just hangs.  If you're fast enough and press F12 in the start up, and then ESC into grub, and boot off of 2.6.24-23-generic (recovery mode), then you get lots of messages with strings like "ata1.00: qc timeout (cmd 0x27)" in them.

(These messages unfortunately are not saved in /var/log/messages or /var/log/dmesg.)

In any event, there is some path through the boot up sequence that you can take to actually get into the machine which i believe involves rebooting twice and inserting an ordinary (non-boot) usb stick some time after the first reboot (i think).

I think this might be related to the usb-sata race condition described in:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)
(However the remedy suggested there does not make my system easily rebooted, which is why my successful reboot count is now 2, and i can't imagine what my unsuccessful reboot count is.)

So i would be interested in anybody's advice on:
(1) how to get or figure out a reliable boot sequence for 8.04
(2) how to upgrade to 8.10.

For item (2), i have an 8.10 disk from Mark Sobell's _A Practical Guide to Ubuntu Linux_ which i might use, or i could burn a different cd if anybody has any recommendations (like maybe if there's something tuned for the Dell Inspiron).

Thanks in advance for any help.

dan

---

### Post by Partyboi2 on 2009-04-10
Hi, try booting using 'all_generic_ide' as a[[COLOR=Blue] boot option [/COLOR]]("https://help.ubuntu.com/community/BootOptions")as well try changing from IDE to to RAID in your cmos.
[http://ubuntuforums.org/showthread.php?t=895721](http://ubuntuforums.org/showthread.php?t=895721)

---

### Post by danh-a on 2009-04-14
Thanks Partyboi2 for taking the time to consider the problem and write out your advice on how to solve it.

For the benefit of anybody who might be searching the archives, what i actually did was just install 8.10 from a cd (from Mark Sobell's book), and wiped out the prior upgrade from 7.10 to 8.04 (including all user data on the machine).

My impression is that working out the software process to upgrade from one version to the next is a very difficult problem and a clean install sidesteps all of those difficulties.  (And in particular [knock on wood] i did not have any boot problems when i shut down the machine and restarted.)

dan

---

