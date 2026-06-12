---
title: "dual monitor and freezes @ splash screen"
date: 2012-01-06
forum: Hardware
---

### Post by MyD0j0 on 2012-01-06
Hi and thanks for any help.  I know this is a little long winded, but all I can do is tell you what I did to get to a frozen splash screen that doesn't respond to either ctrl-alt-F1 or ctrl-alt-backspace.
 
I have a HP Pavilion dv9008nr with NVIDIA GeForce Go 6150 (UMA) running Ubuntu 11.10 64bit and also use the HP xb3000 expansion base connected to a second monitor and usb kb/mouse (KVM is passed through a Belkin FIDL102U--a dual port KVM switch with audio and usb support and built in cabling). All updates are current as of today, at about 1:00 PM central time.
 
After the system updates, I used the nvidia settings to setup dual monitors and rebooted.  I had to reboot several times to play with the twin view vs. extended desktop because I was having trouble getting the display up on both monitors--twin view solved this issue with the exception of missing the launcher on the primary display. 
 
I also had to play with booting into the normal ubuntu vs. ubuntu 2d desktops because I was having trouble with non-responsive launcher buttons and washed out desktop background (ubuntu 2d solved this issue)--in order to reboot to fix I had to use the esc and tab keys.
 
After disconnecting the laptop from the expansion base (and therefor the 2nd monitor), I could not get the desktop to display the launcher as if it never left the dual monitor mode and began rebooting several times trying the ubuntu and ubuntu 2d desktop modes to try to get the launcher back.  Eventually, the machine just froze at the splash screen as soon as it appeared.
 
I know you gurus have work-arounds galore to get a system back up and running--how do I get mine restored?!?!
 
 
PS.  I know--bad timing, but my backup server is down because I'm migrating it from FreeNAS to Ubuntu server...I never would have expected this to cause an entire lack of boot-ability; I don't have backups of backups...

---

### Post by MyD0j0 on 2012-01-07
bump for some serious help, plz

---

### Post by MyD0j0 on 2012-01-07
After getting the boot repair tool as explained here: [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation)
 
I now have two boot info logs, one for pre-boot repair:
 
[http://paste.ubuntu.com/796669/](http://paste.ubuntu.com/796669/)
 
and one post boot repair:
 
[http://paste.ubuntu.com/796678/](http://paste.ubuntu.com/796678/)
 
 
The repair process did not fix the problem but I have no idea how to interpret the boot info output to see what my next steps should be.  If someone could take a look and offer some suggestions, I'd appreciate it!

---

### Post by MyD0j0 on 2012-01-11
finally figured this out; the system was mounting read only so I couldn't restore the xorg.conf file from the backup I had, but now I finally got in read/write and was able to restore the backup.

---

