---
title: "Restore Partition Boot record"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Lex Luthor on 2009-06-04
Hello all,

I got a Thinkpad T60 at work, and installed Ubuntu.
Before installing it, I generated the CD backups, backed up the master MBR (those that makes the ThinlAdvantage button work) and installed Ubuntu Gutsy 7.10.

I followed the installation guides on the net, and installed with alternate install, and when it asked to install the MBR I chosed to install on partition, not the master. But it never accepted the partitions I choose, since my laptop has SATA disk, it did not accepted any sda entry. In this process, I tried to install on every partition I had, and unfortunately I tried to install on the IBM_SERVICE partition.

I resolved the MBR master problem by rebooting with the Live CD and choose to repair an installation, and the there was an option to reinstall the MBR of the partition.

My situation now is that the ThinkAdvantage button is working, but when it tries to boot on the SERVICE partition, apeers only the word GRUB on the top of the partition.

I'd like to know if there is a way to restore the BR on the IBM_SERVICE partition so I can boot with it.
Thanks a lot.

---

