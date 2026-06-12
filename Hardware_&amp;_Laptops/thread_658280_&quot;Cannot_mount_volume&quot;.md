---
title: "&quot;Cannot mount volume&quot;"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by northpig87 on 2008-01-04
Hi, I could not start my windows xp on my laptop, it keeps showing blue screen and restart the moment i load xp. so i tried the live cd (v7.10) and trying to at least move all my datas on hdd to an external usb drive.
right now (in safe graphics mode), i have ubantu running some what, i was able to view folders in my external drive, but when i tried to open "74.5GB Volume", which i assume is my hdd in the laptop, it says 

Cannot mount volume.
$LogFile indicates unclean shutdown(0,0) failed to mount '/dev'hda1': operation not supported Mounted is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown windows cleanly. Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -tntfs-3g/dev/hda1/media/disk -o force    Or add the option to the relevant row in the /etc/fstab file:         /dev/hda1/media/disk ntfs-3g default, force 0 0


ok that took a while to type lol, so yes windows xp is installed on this computer. 2, yes a external hdd is connected but it can mount that external hdd, not my internal one. and 3. what's that force option? would i lose my datas on hdd if i force it to read? 4. if i were to change the ntfs format of my internal hdd to format appropriate for ubantu to run or to mount, it probably means i would lose all my datas on that hdd after changing the format right? What can i do to retrieve my files? 

Thank you all!

oh and as i just finished typing, i realized my ubantu is frozen..lol, nothing is moving disc isn't turning, screen is still there...but ya...

---

### Post by northpig87 on 2008-01-04
as i was looking through other 'cannot mount volume" threads...i realized that...

How do you open a terminal to type all those commands others have listed to mount ntfs? lol..sorry for being so stupid...><

i looked everywhere...i remember on UNIX it's just left click on desktop and open terminal. ><

---

### Post by derkaderka on 2008-01-04
the terminal is located under application > accessories > terminal

---

