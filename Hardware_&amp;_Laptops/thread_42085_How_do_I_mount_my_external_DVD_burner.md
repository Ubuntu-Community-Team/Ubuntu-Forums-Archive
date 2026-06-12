---
title: "How do I mount my external DVD burner ?"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by john_walsh54 on 2005-06-16
My external firewire Lacie DVD burner is listed in device manager as DVD-RW ND-3520A as block device /dev/scd0, but I cannot find it listed in Places -- Computer. However, when I put a CD in the drive the CD-player starts playing. How do I configure ubuntu to mount it? please give extact instructions - noobie.

---

### Post by rachii on 2005-06-16
if it plays the cd player, then isnt it auto mounting when you put the cd in?

are you trying to get it listed under "places--computer"?

right click on the desktop and select open terminal.  in the terminal type```
gedit /etc/fstab
``` and copy -- paste the contents here

---

### Post by john_walsh54 on 2005-06-16
Yes, I am trying to get it listed in places - computer. I have included the fstab listing, but the CD-ROM referenced is my other cd drive!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by rachii on 2005-06-16
so now do ```
sudo gedit /etc/fstab
``` (that way you can edit it) and add your dvd device.   i am assuming your other cd drive is listed under places-computer?  if so then just copy the fstab enty for your cdrom except change it to /dev/scd0, then save, and it should come up

---

### Post by john_walsh54 on 2005-06-17
rachii
Thanks for your patience. 
The burner plays the CD, but there is no audio desktop icon and there is no "device" listed in "computer", which means I cannot access the drive via nautlius, just like I do for my other (DVD-ROM) drive.
I am not sure if I should copy the line as you suggest  because the DVD-ROM drive is read-only, while the external drive is a burner? Shurely the settings must be different?
Another strange happening is that when I put a data cd (Suse 9.2) in my external drive an icon appears on the desktop.  So, for a data cd I can access the drive via nautlius.
Sorry, I only put a data cd in the drive today - never expected it to behave differently. Its all very dodgy. What should I do?

Kind regards

John

---

### Post by rachii on 2005-06-17
thats weird it mounts for some,and not others.   it wouldnt hurt to put it in fstab, my burner and rom entries are identical except for locations.  so go ahead and try it, you can always delete it or comment it out later.
can you manually mount the driver with the mount command when it isnt a data disk?

---

### Post by john_walsh54 on 2005-06-29
I tried doing that but when I rebooted I got an error initialising Hald (Device Manager), which meant that none of my peripherials were recognised. I removed the change I made. Now, in some boots every peripherial is recognised, but in most boots nothing is recognised. The burner will only be recognised through a hotplug now. Thats why its taken me so long to get back to you.
I think I'll have to do a reinstall. I'll raise a bug for my burner. I've had enough.

---

### Post by ad noiseam on 2005-09-06
Here is how I more or less solved this problem in my case. It might help, or even work for you, who knows.

1. log-in as root user
2. go to the /media directory
3. create a new folder for your drive. For example, "dvdrom0".
4. create a link to this folder. To do this, press shift+control+left click on "dvdrom0" and drag this somewhere else in the same window.
5. rename the link to "dvdrom"

then:
6. Go to System -> Device Manager
7. Browse to find your drive
8. Click on the "Advanced" tab.
9. Look at the value of the first key, "block.device"
10. Open the terminal
11. type "sudo gedit /etc/fstab"
12. in the file that comes up, find your other CD-Rom drive (there should be listed with something like /media/cdrom)
13. copy in this line, but replace the beginning by the "node" found in Gnomebaker and the part after "/media/" by the name of the folder you created in step 3.
14. exit gedit, the terminal and the Device Manager

and finally:
15. Go to System -> Users and Groups
16. Look for user "Hal"
17. click on "Properties"
18. click on the "User privileges"
19. check "access to CD-Rom drives", "access to floppy drives", "enable access to external storage devices automatically"
20. click "Ok"

and:
21. reboot

This should work. Tell me if it did!

---

### Post by Jenda on 2005-10-07
I seem to have the same problem. There is no user called "Hal", but there is such a group. This doesn't offer me the "User privileges" tab, though.

---

### Post by djmadkins on 2005-10-07
on the bottom of the first tab in "users and groups" be sure to check the "show all users and groups" checkbox.. you will then have a user named hal and you can follow his instructions.

---

