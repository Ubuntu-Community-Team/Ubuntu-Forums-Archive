---
title: "reinstall 7.10 w/o losing files??"
date: 2008-09-11
forum: General Help
---

### Post by eudeal on 2008-09-11
Hey need some help here! Installed ZoneMinder in Ubuntu 7.10 had to reboot a couple of days later for upgrades and now it won't start. It goes to the busy box for a while then to scripts showing ZoneMinder successfully started then stops at 'Starting Bluetooth services" even when booting from CD(CD start up does not show ZoneMinder entry). FYI-Zoneminder never would load after CL install declared it successfully installed. When I typed the IP address of the PC into Firefox a page came up that said 'your SQL server is running'. Anyone have any ideas how to get the OS started? NO luck with Safe graphics mode either. This is my workhorse computer with tons of **** on it that I can't lose. Soooo one final question is can I reinstall 7.10 over the existing version without disturbing the files? Thanks

---

### Post by Pelham123 on 2008-09-12
Summary is that your OS will not boot and hangs at 'Starting bluetooth services..."? Do you have to reset when it hangs?

Are you saying that you cannot run the LiveCD at all? And at the Grub menu, booting into recovry mode will also not work?

As for the re-install of 7.10 without losing files, I think that would depend on how the partition table was set up for your current install.

---

### Post by eudeal on 2008-09-13
not sure what you mean by 'reset'. Restart changes nothing still hangs up at 'starting Bluetooth services'.

Live CD either freezes or hangs up at same point even in safe graphics mode. Can boot to recovery mode in GRUB menu, managed to find some ZM sartup files and deleted so ZM doesn't start(tries to but can't find files) but still hangs up at good old Bluetooth. Ready to try to copy files to external HDD but reluctant because of limited CL experience.

As for partition table 320 Gb SATA HDD has 292 Gb ext3 partition 92.2 Gb in use) and 5.8 GB swap partition.  I have tried to isolate the active partition by reducing it to 120 Gb but all my partition manangers crash. Must be something else going on there.

---

### Post by Pelham123 on 2008-09-14
As you can get to a recovery console, it may be better to stop Bluetooth services from starting up at boot.

Not sure how much you know about startup scripts and their locations. All scripts are located in /etc/init.d. When the system boots the scripts run are dictated by symbolic links in /etc/rc*.d (depending on runlevel) with '*' being a number 0-6.

Have a look around the /etc/init.d and /etc/rc2.d folders and you'll see what I mean. You can stop bluetooth from starting up by renaming it:

At the command line...

cd /etc/rc2.d

sudo mv S25bluetooth s25bluetooth

It just changes the name from an uppercase 'S' to lowercase - which will stop the script being run at the default bootup runlevel. Reboot the system and let us know

Apologies for late reply

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi eudeal, I hope you can fix your existing installation, however, should you reinstall 7.10 and want to keep your desktop/files/user configurations/..., here is how I would do it :

- Assuming you have everything installed on a single partition (no separate /home partition).

- Boot the 7.10 install+live cd

- Double-click on your existing installation partition to have it mounted.

- MAKE A BACKUP ON AN EXTERNAL USB DRIVE.

- Open a terminal.

- Become root (sudo -i).

- Go to your existing installation (cd /media/something/).

- Delete everything in /media/something/ EXCEPT the /media/something/home partition (using rm -rf).

- Go to the home directories folder (cd home) and rename your existing home directory (mv youruser youruser_keepit).

- Reboot and proceed to the actual installation.

- Use manual partitionning and tell the installer NOT to format the existing partition.

- When you've installed and booted in your reinstalled system,

- Go to a console (ctrl+alt+f1), login and become root (sudo -i).

- Go to /home (cd /home).

- Make sure your old home directory belongs to you (chown -R youruser:youruser youruser_keepit)

- Remove the home directory the installer has made (rm -rf youruser).

- Replace it with your previous directory (mv youruser_keepit youruser).

- That's it, reboot, you're done.

---

