---
title: "Problem after suspend/resume with option 3g driver"
date: 2010-05-03
forum: Hardware
---

### Post by lars.la on 2010-05-03
Hello.

After installing Ubuntu 10.04 i have had a problem with my 3g (12d1:1404 Huawei Technologies Co., Ltd.).
I checked some logs and it seems like modem-manager doesn't properly  release the device so the module can be removed before suspend.
The fix, at least it seems to have fixed the problem, is to add a couple of lines to: /usr/lib/pm-utils/sleep.d/55NetworkManager
In the suspend-function add the lines: 
        killall modem-manager
        rmmod option
        rmmod usbserial
under the dbus_send line.

Please leave feedback if this works for you too.

//Lars

---

### Post by lars.la on 2010-05-04
Now, when i got home from work, modem-manager was still messing with the 3g device after resume so i added a "killall modem-manager" to the resume function of /usr/lib/pm-utils/sleep.d/55NetworkManager, maybe this will fix the problem.

What could modem-manager be up to?

---

### Post by Dwaalspoor98 on 2011-06-08
Thanks a lot for sharing this :)

This is sufficient for me:
sudo bash -c 'echo "killall modem-manager" > /etc/pm/sleep.d/61modem-manager'
sudo chmod 755 /etc/pm/sleep.d/61modem-manager

---

