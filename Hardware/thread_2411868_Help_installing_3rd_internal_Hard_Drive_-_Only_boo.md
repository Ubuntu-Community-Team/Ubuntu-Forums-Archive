---
title: "Help installing 3rd internal Hard Drive - Only boots emergency mode"
date: 2019-02-04
forum: Hardware
---

### Post by marcus39 on 2019-02-04
Hi everyone.

I am running Ubuntu 18.04.1 and am attempting to install a 3rd internal hard drive. Presently, I have two 4TB drives installed. I'm not sure how my bootloader is setup (or if that is my issue here) so I'll describe best I can.

When I boot from a shutdown, I get an option about which drive I should boot from. Drive 2 or Drive 4. It's a graphical selection and looks like it is Ubuntu asking me (not my Bios screen or anything like that).

One of my drives is my main drive for the OS and the other one is just data/backup. So, I always boot from Drive 2.

When I plug in a 3rd drive, I get a 3rd option, Drive 3. If I boot from drive 2 like normal, I get a different-than-normal boot screen and it boots into a text mode ("emergency mode"), it says. From the command line, I can see all my directories and am logged in as root. 

Any idea what is going on here?

My goal is to install the 3rd drive to install and boot Windows. Ideally, I would like to accomplish this without having to do a fresh install and wipe my existing drives.

Thanks in advance for any guidance or help!

---

### Post by oldfred on 2019-02-04
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Are you changing SATA port order.
Drives are set from UEFI/BIOS by order plugged into SATA ports, if all are SATA. So SATA0 typically becomes sda.
And grub should be booting using UUID or labels, not device, so any change in drive order should not change boot.

---

### Post by marcus39 on 2019-02-05
When I unplug the new drive, everything returns to normal. 

I did not change the boot order in the UEFI, at least not on purpose, but I see what you are saying. The current drives are plugged into 3 and 4, the new one is plugged into 1. I checked after it was plugged in that the UEFI boot drive was showing the same value. I never understood what I did to cause the option at bootup where i can see 2 drives to choose from. Usually I don't do anything and it just boots from the correct one.

Here is the report.

[http://paste.ubuntu.com/p/35TY9HP5Cz/](http://paste.ubuntu.com/p/35TY9HP5Cz/)

I'll check out the link you provided.

Thanks.

[http://paste.ubuntu.com/p/35TY9HP5Cz/](http://paste.ubuntu.com/p/35TY9HP5Cz/)

---

### Post by oldfred on 2019-02-05
You are mounting you data drive using device by device like         /dev/sdb1 /media/data .
When you plug that into a lower number SATA port it then becomes sda and your mount of sdb1 should then be sdc1.

So if new drive changes drive order and becomes sdb, and it does not have a partition sdb1, yet then it will not mount and cause issues.
Using device is not recommended, just for that reason. I used to only use UUID, but now am changing to use labels. I label when partitioning and when I forget use Disks to add a label.

I have not changed my entry on this system yet:
```
# Entry for /dev/sdb6 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 noatime 0 2

```

---

### Post by marcus39 on 2019-02-10
> **oldfred said:**
> When you plug that into a lower number SATA port it then becomes sda and your mount of sdb1 should then be sdc1.
```
# Entry for /dev/sdb6 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 noatime 0 2

```

This was the problem. I just moved the old drives down the ports and put the new drive on the highest numbered sata port.

Thanks for the help!

---

