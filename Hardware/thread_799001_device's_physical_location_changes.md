---
title: "device's physical location changes"
date: 2008-05-18
forum: Hardware
---

### Post by dale_nx26 on 2008-05-18
Hello, so I'm trying to automount my Windows's partition. And it works...sometimes. The thing is the partition's location changes by itself (or maybe a change in settings causes it?). For example, it used to be /dev/sda6 but changed to /dev/sdf6, and this causes it to not mount. Due to this, I can't use Rhythmbox stably (it loses music since it can't find the old directory). Any suggestions? Thanks for reading!

---

### Post by dale_nx26 on 2008-05-18
bump...

---

### Post by jocko on 2008-05-19
Instead of using device nodes (/dev/sdxY), set up your /etc/fstab to use uuid's.

To find out what uuid your drive have, first find out which device node it uses this boot:
```
sudo fdisk -l
```Then list the uuid's:
```
ls -la /dev/disk/by-uuid/

```That will give you a list with lines looking something like this:

```
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]14a06299-44fd-4ed1-b410-7257dc712731[/COLOR] -> ../../hdc1
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]15764d6b-3184-4493-b05d-1a2e8e696441[/COLOR] -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]8c2ac1b1-3989-4d21-9b61-f15efaba38f4[/COLOR] -> ../../sdb4
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]a04f0c57-2740-410e-9e82-ade225733fee[/COLOR] -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]e0e9bf70-6733-4528-8b01-1cc78c38690d[/COLOR] -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-05-18 18:05 [COLOR=Blue]f394b2f2-4d6e-40cc-a64a-9ffe04b63935[/COLOR] -> ../../sda1

```Copy the uuid (highlighted in blue) of the drive, and open up your fstab:```

sudo gedit /etc/fstab
```Find the line for your drive:
```
[COLOR=Red]/dev/sdb1[/COLOR] / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
``` and make it look something like this:
```
[COLOR=Blue]UUID=a04f0c57-2740-410e-9e82-ade225733fee[/COLOR] / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
```(just put "UUID=" followed by your unique uuid instead of "dev/sdxY" in the beginning of the line. Don't change anything else).

---

### Post by dale_nx26 on 2008-05-19
Thank you. I haven't tried this yet, but I will when I get home from the place I am right now and report back.

---

### Post by dale_nx26 on 2008-05-19
Hey, I think it definately works. Based on NTFS config tool and gparted, I can see the "node" has been changing while the partition is able to mount consistently every time I start Ubuntu. Hopefully it stays that way. Thank you very much! Another issue down, just a few more to go to make my Ubuntu perfect.

---

### Post by jklm988 on 2008-05-19
You write very well, support you![neoprene computer bags](http://www.cnprince.com/en/oem.html) [neoprene Laptop computer bags](http://www.cnprince.com/en/oem.html) [memory foam computer bags](http://www.cnprince.com/en/oem.html) [memory foam Laptop computer bags](http://www.cnprince.com/en/oem.html)

---

