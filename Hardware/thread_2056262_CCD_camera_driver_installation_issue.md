---
title: "CCD camera driver installation issue"
date: 2012-09-11
forum: Hardware
---

### Post by unibok on 2012-09-11
Hello.

We recently purchased a scientific Andor CCD camera including Linux drivers and SDK. They provided us with an install script with works flawlessly (i.e. no errors), however Ubuntu fails to detect the camera.

I believe that the problem is in the script itself and that certain files are not copied to correct directories. These are the default directories that the script copies the files to:
--------------------------------------
module_dir=/lib/modules/`uname -r`
rc_dir=/etc
rc_file=rc.local
hotplug_dir=/etc/hotplug
install_dir=/usr/local
udev_dir=/etc/udev
--------------------------------------
If nothing else I'm pretty sure that Ubuntu does not use Hotplug directories anymore.

Do you have any suggestions what to do before I contact support? 

Thanks allot.

p.s. I'm running Ubuntu 8.04.4 LTS (hardy) and the kernel is 2.6.24-28 (server). I can not upgrade as certain software isn't running on anything that is newer.

---

