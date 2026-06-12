---
title: "Ubuntu 7.10 software RAID compatible?"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by Kivech on 2008-02-12
Like the title says.

I have a Gigabyte GA X38-DQ6 motherboard that comes with RAID, but is officially software raid.

I would like to use RAID 1 on my system, but does Ubuntu support that?

I'm preparing myself for a full migrate from Vista, but want to figure all potential hurdles out in advance. Rather safe then sorry.

Thanks for your replies in advance.

Kivech

---

### Post by damien_d on 2008-02-12
short answer:
sudo apt-get install mdadm
man mdadm 

long answer:
I've just migrated from fedora where the raid support seems a little better.
What I had in my system was that I had the OS installed on its own hard drive /dev/hda and then /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 setup as RAID 5 and mounted as /home because that was the data I wanted to protect.

IF I remember correctly, creating a RAID array was something like:

$ sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

This will return almost instantly - a backgorund process will do the work

I rebooted, for some reason, but I can't remember why.

You can monitor the progress with:

$ watch cat /proc/mdstat 

It can take several hours.

Once it's done, format the /dev/md0 with your choice of file system.

Actually installing ubuntu on the raid is not something I have done.  Fedora's installer gives you an option to do so.  One would hope that ubuntu is just as easy.

---

### Post by chrisdeckard on 2008-02-12
Ubuntu's installer (at least the server install) lets you setup software RAID and LVM devices.  It works quite well.

If Linux sees the hard drive, it's compatible with Linux software RAID.  It won't matter what motherboard, drive controller, or hard drive you have.

-Chris

---

### Post by Kivech on 2008-02-12
Great Chris, that's all I needed to know! :)

---

