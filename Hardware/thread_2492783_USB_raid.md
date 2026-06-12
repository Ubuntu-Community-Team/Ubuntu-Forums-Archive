---
title: "USB raid"
date: 2023-11-22
forum: Hardware
---

### Post by rzmuda on 2023-11-22
I am creating a USB raid NAS using Ubuntu on a laptop
[https://www.microfusion.org/blog/setting-up-a-simple-nas-server-on-linux-ubuntu/](https://www.microfusion.org/blog/setting-up-a-simple-nas-server-on-linux-ubuntu/)
[https://askubuntu.com/questions/172735/how-can-i-create-a-usb-raid](https://askubuntu.com/questions/172735/how-can-i-create-a-usb-raid)

I would like to raid 2 or 4 SSDs over usb in a dock or usb adapter? Which would work better?

Would you recommend those instructions or something else?

The end result is a self made free nas

using latest lts Ubuntu

---

### Post by TheFu on 2023-11-27
DON'T USE USB for anything RAID.
You will be burned. Your data will be lost.  You still need backups for when the RAID fails, which it will.

Don't.  Just don't.

Use SATA, eSATA, SAS, Infiniband instead.

---

