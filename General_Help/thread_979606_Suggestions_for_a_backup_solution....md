---
title: "Suggestions for a backup solution..."
date: 2008-11-12
forum: General Help
---

### Post by trekrem on 2008-11-12
I've been looking into a good solution for the following situation...To simplify:

I have a laptop, a dock for the laptop and an external hard drive connected to the dock. When the laptop is in use it is removed from the dock, when the laptop is not in use it is docked. Here is what I am looking to do...

When I dock the laptop, and the external hard drive mounts I would like to automatically incrementally backup the contents of the laptop hard drive to the external hard drive. After the backup is completed (successfully or unsuccessfully) I would like it to shut down or possibly suspend the laptop.

I have a few years experience using linux, and now use it as my primary operating system, I am familiar with using cron/crontab, but haven't had much experience with rsync.

(GUI solutions are out of the question.)

Thank you in advance for any help/suggestions.

---

### Post by kaptengu on 2008-11-12
I think the best way would be to write a udev-rule. Something like this perhaps:
[http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion...-529113/](http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion...-529113/)

---

### Post by trekrem on 2008-11-12
Thank you, if the udev script works that would solve running the script automatically upon the drive being mounted...

As for the actual rsync script, I have been looking over the man page for rsync and can figure that out, the only issue remaining would be having the machine shut down or possibly suspend after the script has completed. (No specific time the laptop would be docked, so a cron job probably wouldn't work.)

---

### Post by justleen on 2008-11-12
bash scripts are run line-by-line. So if you have a line with the rsync command, and a line below that to shutdown, it will wait for the rsync to finish, then try to shutdown.

---

### Post by trekrem on 2008-11-12
Excellent, thanks justleen, this should work out nicely then...Thanks for the help.

(This thread will be marked solved after the solutions are tested and confirmed working.)

Again thank you kaptengu and justleen.




In the mean time, any tips for the rsync script would be very helpful...Looking to have maybe 7 separate daily incremental backup folders and 1 full current backup folder.

---

### Post by kaptengu on 2008-11-12
Maybe the script could look something like this:
```

#!/bin/bash
NOW=`date '+%Y-%m'-%d_%H:%M`
mkdir -p /media/usb/backup/{current,old/$NOW}
rsync -av --delete /home/user/ /media/usb/backup/current
cp -al /media/usb/backup/current /media/usb/backup/old/$NOW
#for DELDIR in "$(find /media/usb/backup/old -maxdepth 1 -type d -mtime +7)"
#do
#rm -rf $DELDIR
#done
shutdown -h now

```

---

### Post by kaptengu on 2008-11-12
Try to modify this:
[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

---

### Post by m_l17 on 2008-11-12
For incremental backups I use rsnapshot:

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

[http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html]("http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html")

---

