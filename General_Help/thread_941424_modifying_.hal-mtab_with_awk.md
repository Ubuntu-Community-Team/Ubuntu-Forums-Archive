---
title: "modifying .hal-mtab with awk"
date: 2008-10-08
forum: General Help
---

### Post by RobertWHurst on 2008-10-08
I've been tinkering trying to get my windows disc to auto-mount and I've figured it out, now I have a shell script that mounts it. I edited sudo permissions so it could run without requiring a password. ```
#!/bin/bash
sudo mkdir -p '/media/disk'
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/disk
cd /media
awk '{print '/dev/sda1	1000	0	ntfs-3g	nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8,exec	/media/disk'}'.hal-mtab > .hal-mtab
```

my problem is the bottom half, u see I'm trying to edit .hal-mtab with awk so I can unmount the drive with HAL from Nautilus or from the desktop. the problem is that awk isn't writing anything at all, the file is always empty.

---

### Post by RobertWHurst on 2008-10-11
WILL SOMEONE ANSWER ME PLEASE!!!

its like a line of code and you can make a post?

:mad:

---

### Post by iponeverything on 2008-10-11
> **RobertWHurst said:**
> I've been tinkering trying to get my windows disc to auto-mount and I've figured it out, now I have a shell script that mounts it. I edited sudo permissions so it could run without requiring a password. ```
#!/bin/bash
sudo mkdir -p '/media/disk'
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/disk
cd /media
awk '{print '/dev/sda1	1000	0	ntfs-3g	nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8,exec	/media/disk'}'.hal-mtab > .hal-mtab
```

my problem is the bottom half, u see I'm trying to edit .hal-mtab with awk so I can unmount the drive with HAL from Nautilus or from the desktop. the problem is that awk isn't writing anything at all, the file is always empty.

why awk?

```
echo "/dev/sda1   1000	0	ntfs-3g	nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8,exec	/media/disk" > .hal-mtab
```

---

### Post by RobertWHurst on 2008-10-11
ok ic thanks for helping me iponeverything

---

### Post by rolexim on 2009-04-27
> **RobertWHurst said:**
> I've been tinkering trying to get my windows disc to auto-mount and I've figured it out, now I have a shell script that mounts it. I edited sudo permissions so it could run without requiring a password. ```
#!/bin/bash
sudo mkdir -p '/media/disk'
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/disk
cd /media
awk '{print '/dev/sda1    1000    0    ntfs-3g    nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8,exec    /media/disk'}'.hal-mtab > .hal-mtab
```my problem is the bottom half, u see I'm trying to edit .hal-mtab with awk so I can unmount the drive with HAL from Nautilus or from the desktop. the problem is that awk isn't writing anything at all, the file is always empty.

RobertWHurst, you shouldn't work with HAL by hand, I hate the fact of creating a separate shell for each disk or removable device I own, try this:
[http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL)
If you have a working ntfs-3g, then you probably just have to go forward on the above URL until
"Device specific policies
NTFS write access
The good way"
and create that "20-ntfs-config-write-policy.fdi" file with the suggested XML code, you may need to change the initial numbrer (20) in case is already used by another .fdi file, restart HAL, and that's it, open Nautilus, double click on your disk icon, you'l have it mounted and /media/.hal-mtab auto updated, I also did it on a RHEL distro with success.

Hope it also work for you

---

### Post by rolexim on 2009-05-20
Hey RobertWHurst, you know what?, I just went to the website I mentioned before and the solution text was gone !!! :-k silly uhh ??

But thanks to google "cache" pages I found it again, no more to say, this is what I meant:

[FONT=Courier New][SIZE=1][B]Device specific policies
NTFS write access
The good way[/B]

If you can't write on your NTFS devices create the following file and restart hal:
File: /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi

 <?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
 <deviceinfo version="0.2">
[/SIZE][/FONT][FONT=Courier New][SIZE=1]  <device>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]    <match key="volume.fstype" string="ntfs">[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]      <match key="@block.storage_device:storage.hotpluggable" bool="true">[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]        <merge key="volume.fstype" type="string">ntfs-3g</merge>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]        <merge key="volume.policy.mount_filesystem" type="string">ntfs-3g</merge>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]      </match>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]    </match>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]  </device>[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]  </deviceinfo>[/SIZE][/FONT]  [FONT=Courier New][SIZE=1]

Note: this configuration file has been tested with hal=0.5.11 and correctly identifies/mounts (external) ntfs devices with ntfs-3g. mount should display the filesystem type as fuseblk if this configuration file is correctly detected.[/SIZE][/FONT] 

See you ):P

---

