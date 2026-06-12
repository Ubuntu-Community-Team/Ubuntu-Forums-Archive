---
title: "cdrom link broken"
date: 2008-07-01
forum: Hardware
---

### Post by boho103 on 2008-07-01
Just got this strange error today, my cdrom drive has been working fine, I'm using ubuntu 8.04 hardy. I've used my cdrom drive multiple times so I know it works, but today after I unmounted an image, [about 50 minutes after I unmounted the image]and then I went to /media folder and realized that my cdrom link is broken! Whats going on and is there any ideas on how to fix it? I googled it and nothing helpful showed up. I put in a cd and it says unable to mount disk-name or whatever, I get that with every disk I put in : /, I also can't mount normal iso images either. When I get the unable to mount disk error it comes up with this in details. "mount: mountpoint /media/cdrom0 does not exist." It does in fact recognize the disks though, it even shows up with the disk names, I just can't open them : /

---

### Post by ajopaul on 2008-07-01
did u try after a reboot, is this device present /dev/cdrom ?

---

### Post by boho103 on 2008-07-02
yes there is a link called cdrom at /dev/cdrom
there isn't a folder, its just some sort of link
and yeah I've tried rebooted multiple times : /

---

### Post by boho103 on 2008-07-02
fixed!
I did sudo mkdir /media/cdrom0
and sudo mkdir /media/cdrom
and the cd worked!
hehehe I think I accidently deleted the folders >.<

---

