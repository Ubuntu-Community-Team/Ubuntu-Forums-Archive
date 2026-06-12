---
title: "Unmount a USB-Stick automatically"
date: 2015-11-20
forum: Hardware
---

### Post by APUboard on 2015-11-20
I'm trying to run a script on an USB automatically when mounted. The automatic mounting works.
I used a rule in udev for that. There's a action which should handle the unmounting, but it isn't working.
I know that I need to umount first, otherwise the file doesn't get saved. But I would like to just disconnect the usb and it should still write all the files on the stick.
Is this even possible or do I need to umount first?

[SIZE=1][COLOR=#C5C8C6][FONT=monospace]KERNEL!=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"sd[a-z][0-9]"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], GOTO=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"media_by_label_auto_mount_end"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Import FS infos  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]IMPORT[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{program}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"/sbin/blkid -o udev -p [COLOR=#CC6666]%N[/COLOR]"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Get a label if present, otherwise specify one  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{ID_FS_LABEL}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]!=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]""[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{dir_name}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"[COLOR=#CC6666]%E[/COLOR]{ID_FS_LABEL}"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{ID_FS_LABEL}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]""[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{dir_name}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"usbhd-[COLOR=#CC6666]%k[/COLOR]"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Global mount options  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]ACTION==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"add"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{mount_options}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"relatime"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Filesystem-specific mount options  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]ACTION==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"add"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{ID_FS_TYPE}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"vfat|ntfs"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{mount_options}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"[COLOR=#CC6666]$env[/COLOR]{mount_options},utf8,gid=100,umask=002"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Mount the device  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]ACTION==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"add"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], RUN+=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"/bin/mkdir -p /media/[COLOR=#CC6666]%E[/COLOR]{dir_name}"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], RUN+=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"/bin/mount -o [COLOR=#CC6666]$env[/COLOR]{mount_options} /dev/[COLOR=#CC6666]%k[/COLOR] /media/[COLOR=#CC6666]%E[/COLOR]{dir_name}"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Clean up after removal  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]ACTION==[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"remove"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], ENV[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]{dir_name}[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]!=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]""[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], RUN+=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"/bin/umount -l /media/[COLOR=#CC6666]%E[/COLOR]{dir_name}"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace], RUN+=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"/bin/rmdir /media/[COLOR=#CC6666]%E[/COLOR]{dir_name}"[/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]  [/FONT][/COLOR][COLOR=#969896][FONT=monospace]# Exit  [/FONT][/COLOR][COLOR=#C5C8C6][FONT=monospace]LABEL=[/FONT][/COLOR][COLOR=#B5BD68][FONT=monospace]"media_by_label_auto_mount_end"[/FONT][/COLOR][/SIZE]

---

### Post by sudodus on 2015-11-20
What do you mean by ***disconnect*** in 'I would like to just disconnect the usb and it should still write all the files on the stick'? Do you mean unplug or turn off current, or only unmount all partitions?

The output to mass storage devices is buffered. A USB stick is a kind of mass storage device. So you need to write the buffered data to the device before it is unplugged.

The command ***sync*** is doing this job. It is performed automatically by the command ***umount***.

When you run umount the USB stick will still have 'power on', while the eject command via a file browser will also turn the power off. So if you want to mount the USB stick again, you can do it after umount, but after eject you must unplug and re-plug it.

---

### Post by APUboard on 2015-11-20
So I meant unplug the usb stick, so sync is probably the thing I was looking for.

---

### Post by sudodus on 2015-11-20
If you want to unplug the USB stick I strongly recommend that you unmount (with the command ***umount***) or eject it. Do not only sync it.

---

### Post by APUboard on 2015-11-23
But sync is still better than just unplug it, right?

---

### Post by sudodus on 2015-11-23
Yes, but risky, because it can still be written to after the sync command, while umount prevents writing to it.

---

### Post by APUboard on 2015-11-23
So if I sync it like every 10 seconds the data will be still written on the stick, but maybe the 5 second between will be lost.

---

### Post by sudodus on 2015-11-23
Yes.

The problem is not only lost data, but also file corruption - for example that you write to an existing file (append data). The whole file might be hard to read. In the worst event, the whole file system might be corrupted, but if there is journaling, it should be more robust.

If you describe what you intend to do with some more details, it might be possible to find a better method.

---

