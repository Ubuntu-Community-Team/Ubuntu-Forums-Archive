---
title: "Installed 9.10 Karmic, grub still shows 9.04, boot fails"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by ManiacDan on 2009-11-02
I installed 9.10 Karmic Koala this morning through the update manager, and when the system rebooted I noticed that menu.lst seems to have been untouched.  I swear I chose "use new version" from the menu during installation, but apparently it either didn't "take" or there was a pebkac (assuming the latter).

When I select to boot into 9.04 I get a corrupted version of the 9.04 boot screen with some networking error messages along the bottom, then I get what I assume is the 9.10 boot screen (which is particularly awesome).  I can log in normally, but logging into a windowing session OR an xterm session only lasts about 30 seconds, at which point the OS seizes completely.  

Through my research it seems that I could just boot to xterm and run the grub 2.0 updater again, accepting the changes to menu.lst from the command line, but I'm afraid of doing so when the machine won't last longer than a minute.  Any suggestions?

Thanks,
Dan

P.S.  I'm stuck in XP until this is resolved, please have mercy.

---

### Post by ManiacDan on 2009-11-02
Some more research leads me to believe I can update grub2 from a liveCD.  Downloading now, I'll update the thread if it's successful.

-Dan

---

### Post by ManiacDan on 2009-11-02
I followed the instructions [here]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD"), but they seemed to have no effect.  grub-install works fine and gives no errors, but nothing happens, the original grub 1.97 boot menu (without Karmic) still appears on boot.  As far as I know I'm installing to the correct drive/partition, I uses /dev/sda3 as the mount point (it was listed as "Linux" in the output of fdisk -l, where the other two were "Swap" and "NTFS").  I also used "/dev/sda" as the install location for grub-install.  

Unless I find anything else, I'm going to have to wipe this partition and do a re-install of Karmic, which seems stupid given the problem is supposedly easily resolved.

I ran the "install ubuntu" app from the desktop of the live CD, and it recognized /dev/sda3 as having Ubuntu 9.10 on it, but I can't boot to it.  Very frustrating to see it right in front of me and not be able to get to it.

-Dan

---

### Post by oska1969 on 2009-11-02
I have the same problem!    Tryed Supergrub without any result (with my knowledge-newbe). (I usually only use supergrub to start windows.. (have windows 7, xp and ubuntu on the same harddrive and my docs and storage on another harddrive)).

Later i tryed to install ubuntu karmic from cd.. then it saw my 2 harddrives as one????   just for fun i tryed the 9.04 cd... it saw my 2 hardrives correct with all its partitions...  The mb5 checksum was ok!

---

### Post by ManiacDan on 2009-11-02
I booted into "failsafe GNOME" from the log-in screen and it failed horribly, going to a screen full of blinking special characters.

Then I booted into regular gnome...and it worked.  I still can't boot to 9.10 from GRUB, but apparently I'm now in some kind of awful hybrid of 9.04 and 9.10 with somewhat stable operations.  I'm going to try to re-install grub2 from the package manager, since I'm IN the working OS that should be enough to get it going again.  

More to follow...

-Dan

---

### Post by ManiacDan on 2009-11-02
Ok, I got grub re-installed via synaptics and now it's at least booting into 9.10 smoothly, I just need to figure out all the rest of the issues, including (but not limited to):
-Weird new fonts are blurry
-Network connections icon always shows "disconnected"
-No icons in menus
-notify-osd showing up in the middle of the screen instead of the corner
-Sound distortion
-Probably messed up additional configuration files, like the destkop prefs.

For those that are interested, this is exactly what happened and the steps I took to fix.  Some of these steps are probably unnecessary:
1)  Upgraded from 9.04 to 9.10 using the package manager.  Most likely I selected "leave the old menu.lst alone."  
2)  Rebooted, GRUB showed 9.04 only.
3)  Booted into 9.04, it attempted to load 9.10, immediately siezed and crashed.
4)  Booted to a liveCD, followed [these instructions (link)]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD"), and re-installed GRUB.  No effect.
5)  Booted into 9.04 recovery mode, rebooted.
6)  Booted back into 9.04 (with the 9.10 login screen) and selected "Failsafe GNOME" as my boot environment.  It crashed.
7)  Booted back into 9.04 (with the 9.10 login scree) and selected "GNOME" as my env.  It worked.
8)  Loaded synaptics and selected "grub-pc" for installation, which auto-removed the old grub
9)  Installed and rebooted, grub2 was available for chainloading, and both it and the original loading screen had 9.10 available.  

I hope this helps someone, don't know what else I could have done.  I'm assuming this all happened because the installer defaults to "install new files but don't allow me to boot into them," which personally I find utterly retarded.  To each his own, I guess.  I'm at least up to working quality with 9.10 today, I may have to do a complete format/reinstall later in the week if I'm unhappy with the crippled state I've left myself in.  Most of the problems can be safely ignored as they're aesthetic, but I would hate to have some kind of compatibility/security issue because of this botched update.

Marking thread closed.

-Dan

---

