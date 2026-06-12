---
title: "How to use an udev rule to execute script when usb is plugged in"
date: 2015-11-23
forum: Hardware
---

### Post by APUboard on 2015-11-23
[COLOR=#333333]A script, which is located on the usb stick should be executed when the stick is plugged in.[/COLOR]
[COLOR=#333333]That's how it looks like. As much as I know everything is working except from the snippet I wrote.[/COLOR]

[COLOR=#333333]This is the part which should execute a tcppdump script:[/COLOR]
[COLOR=#333333]RUN+="/media/%E{dir_name}/[/COLOR][COLOR=#333333]autotcpdump.sh[/COLOR][COLOR=#333333]"[/COLOR]


[SIZE=1][COLOR=#333333]KERNEL!="sd[a-z][0-9]", GOTO="media_by_label_auto_mount_end"
# Import FS infos
IMPORT{program}="/sbin/blkid -o udev -p %N"
# Get a label if present, otherwise specify one
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"
# Global mount options
ACTION=="add", ENV{mount_options}="relatime"
# Filesystem-specific mount options
ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,gid=1 00,umask=002"
# Mount the device
ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}", RUN+="/media/%E{dir_name}/autotcpdump.sh"
# Clean up after removal
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /media/%E{dir_name}"
# Exit
LABEL="media_by_label_auto_mount_end"[/COLOR][/SIZE]

[COLOR=#333333]And that's the script, the while-clause is not working yet, but I'm currently using it for the echo "worked" to debug.[/COLOR]


[SIZE=1][COLOR=#333333]tcbox:/media/usbhd-sdb1$ cat autotcpdump.sh
#!/bin/sh
sdb=$(sudo cat /proc/mounts | grep sd[b-d]1 | cut -d "/" -f3)
sudo echo "worked" | sudo tee -a /media/usbhd-sd[b-d]1/test.txt
while [ "$sdb" == "sdd1" ]
do
sudo tcpdump -i eth0 -w /media/usbhd-sdd1/abfrage2.pcap -c10
echo "ok" >> /media/usbhd-sdd/test.txt
done[/COLOR][/SIZE]

[COLOR=#333333]I can execute autotcpdump manually but, so I think the fault is inside the rule.[/COLOR]

---

