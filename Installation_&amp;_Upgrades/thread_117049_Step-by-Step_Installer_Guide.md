---
title: "Step-by-Step Installer Guide?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by Joshatdot on 2006-01-14
Asus A7N8X-X Rev 2.xx, BIOS v1.009
AMD XP 3200+ Barton Core 400MHz FSB
1.5GB PC3200 RAM
Master: Maxtor 120GB UltraATA133
Slave: Maxtor 20GB UltraATA100
ATI Radeon 9800 Pro 128MB
SB Live! 5.1 PCI
MS Intellimouse Optical 1.1
amu CF1997PF 19" PureFlat CRT

I am trying to install Ubuntu Breezy Badger 5.10.  I am trying to dual boot on 2 HDD's.  Do I really need a bootloader? cause I'll just pick what HDD I want to boot from in BIOS.

1st attempt it seemed to go fine, I installed grub just to go with the install, upon reboot it loaded grub, and thats it.  It had a very limited sh shell, and nothing else.

I rebooted, and reinstalled in 'expert mode'. I got thru that fine, this time I tried LILO. Rebooted, lilo was loading linux, but my BIOS Anti-Virus screen popped up!  I never seen this before and I was shocked.  Rebooted, disabled the BIOS AV, and reinstalled, but this time in normal mode.

I tried in all these installs/re-installs to only have 1 partition and no SWAP, cause I have 1.5GB of ram.  I formated all of /dev/hdb1 in ext3fs, and had it mount as root (/), thats it.  This woked before with Fedora Core 4...I tried that cause at college that is what they used.

Anywho...on this last re-install everyting was fine, finished, rebooted, lilo loaded linux-386, normal big list of hardware detected and mounted..etc.  Then I saw this:

====================================================


/scripts/local-top/evms: 31: /sbin/evms_activate: not found
Done.
Begin: Running /scripts/local-premount ...
Done.
FATAL: Module unknown not found.
mount: Mounting /dev/root on /root failed: No such device
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

/bin/sh: can't access tty; job control turned off


=====================================================

Do I need to make seperate mount/partition points for different directories?

I would love to read thru a step-by-step walkthru of install in 'expert' mode.

---

### Post by Joshatdot on 2006-01-14
OH MAN IMA DORK

Ok for somereason the LILO mod'd the SLAVE HDD, and my BIOS was set to boot from that 1st.

I changed BIOS to boot: CDROM, HDD-0, HDD-1, FLOOPY, saved and reooted.

NOW I GET THE GRUB Boot Loader with everything there!

...

Well Thanks for the help, lol, I am off to play with Ubuntu !!

---

