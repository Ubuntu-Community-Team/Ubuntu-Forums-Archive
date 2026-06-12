---
title: "PM991a Device Update"
date: 2022-05-15
forum: Hardware
---

### Post by lofftjm2 on 2022-05-15
I just installed Ubuntu on a Dell XPS 8940.  I've updated everything from the command line via

apt update
apt dist-upgrade

As of this moment there are no updates from apt pending.

In the "Ubuntu Software" application there is on update still pending, listed under "Device Firmware", called "PM991a Device Update".  This appears to be firmware for the internal Nvme SSD where the OS is installed.

Is this update a dependable process?  I don't want to brick a brand new machine.

---

### Post by #&amp;thj^% on 2022-05-15
I find it very dependable, note: in my use.
```
sudo service fwupd start
```
Once the daemon is running, check if there are any firmware updates available.

```
sudo fwupdmgr refresh
```
The output should look like this:
```

Fetching metadata https://cdn.fwupd.org/downloads/firmware.xml.gz
Downloading&#8230;                         [****************************]
Fetching signature https://cdn.fwupd.org/downloads/firmware.xml.gz.asc
```
After this, run the firmware update:
```

sudo fwupdmgr update
```
I do it by CLI, I don't use software managers

---

### Post by lofftjm2 on 2022-05-16
Thanks for the information.  Worked perfectly.

---

