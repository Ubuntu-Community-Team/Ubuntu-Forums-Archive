---
title: "vgaswitcheroo on HP Pavilion G6 unable to edit &quot;switch&quot;-file"
date: 2011-08-05
forum: Hardware
---

### Post by dag0bert on 2011-08-05
Hello!

I am trying to get vgaswitcheroo working on a HP Pavilion G6 with Intel and Ati-Hybrid-Grafic, Ubuntu 10.04 with 3. and 2.6.37 kernel. I am not able to edit /sys/kernel/vgaswitcheroo/switch. 
"echo OFF > /sys/kernel/vgaswitcheroo/switch" gives me nothing but a untouched switch file or/and a freezing terminal. Trying to edit it with gedit gives me "no write permission" so does trying to create a file in this directory. All this i do as root means using sudo or su -i.

I tried to put in /etc/fstab
none   /sys/kernel/debug debugfs defaults 0 0
and 
debugfs /sys/kernel/debug debugfs 0 0


mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
**debugfs on /sys/kernel/debug type debugfs (rw,0)**


with no effects. While booting I get error messages similiar to "unable to create /sys/kernel/vgaswitcheroo/switch non existing directory", athough the file is existing.

What could be the reason?

Bye,
dag0

---

### Post by dag0bert on 2011-08-06
Were are all you gurus? 61 hits and no ideas? :(

---

### Post by hebetude on 2011-10-08
You don't have vgaswitcheroo 

dmesg | grep switcheroo
[    1.729536] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    1.938878] vga_switcheroo: enabled


If you see nothing, then it's not supported on your laptop.  You may also want to delete the file you're creating there, may not matter though.

---

