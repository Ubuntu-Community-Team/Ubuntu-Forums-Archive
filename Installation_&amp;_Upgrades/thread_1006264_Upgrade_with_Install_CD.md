---
title: "Upgrade with Install CD?"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by manoka on 2008-12-09
Hello,

Please inform me if it is possible to do an upgrade from ubuntu 7.10 to 8.10 with an 8.10 Install CD Desktop Edition by using two harddrives.

At the moment I have 7.10 installed on a 20 GB harddrive (set as master) and some data I don't care to keep on a 320 GB harddrive (set as slave).

I unplugged the 20 GB harddrive and installed 8.10 from an Install CD Desktop Edition to the 320 GB harddrive.

I would like to copy the applications and files (from the desktop and the Home Folder) from the 7.10 OS , which I am using now, to the newly installed 8.10 OS.

Then I would like to erase or format the 20 GB harddrive and transfer the 8.10 OS and the applications from the 320 GB harddrive to the 20 GB harddrive, and preferably keep the files on the 320 GB harddrive. 

Or is there an easier way to do it, except via an online upgrade?

Any foolproof detailed step by step instructions would be very much appreciated by a newbie.

manoka

---

### Post by taurus on 2008-12-09
I would format the large harddrive to ext3 filesystem.  Then, copy whatever I want from the smaller one to that larger one.  Install Intrepid on the smaller harddrive and when it's done, just copy stuff from the large harddrive over again.

Or you could make the large harddrive a new /home and transfer your $HOME from the smaller harddrive to that new /home.  When you install Intrepid, just mount the second harddrive, larger one, to /home but do not format it.

Of course, there are other ways too.

---

