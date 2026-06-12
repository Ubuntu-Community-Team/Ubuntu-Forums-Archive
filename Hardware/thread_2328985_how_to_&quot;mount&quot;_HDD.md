---
title: "how to &quot;mount&quot; HDD"
date: 2016-06-26
forum: Hardware
---

### Post by ryuk86 on 2016-06-26
Hello everyone, I am writing because I have a problem on my laptop. In my pc HDD it is compromised (I switched automatically upgrade from Windows 8.1 to Windows 10). I tried it with the Windows recovery tools, but I can not solve the problem. I then decided to try to access my hdd using a live version of ubuntu xubuntu-16.04-desktop-amd64.


In my pc it is detected the internal hdd, but when I click on "mount" one error that I enclose below.


[IMG]http://forum.ubuntu-it.org/download/file.php?id=20934&mode=view[/IMG]


Have I desabilitate secure boot? and try to mount again hdd? thanks a lot








[IMG]http://forum.ubuntu-it.org/download/file.php?id=20935&mode=view[/IMG]

---

### Post by weatherman2 on 2016-06-26
Secure boot has nothing to do with it.  But Windows 8/Windows 10 use something called "fast startup" which is a form of hibernation - and that means the file system as last used by Windows could be in an unstable state if you tried to access it without shutting down properly.  Sounds like you can't boot up Windows, obviously, to try to disable fast startup.

You might be able to mount the partitions read-only in a terminal window.  Try this:

Open a terminal windows (Ctrl Alt t)

When the window opens. type this command:

```
sudo mount -t ntfs-3g -r /dev/sda4 /mnt
```

If that works without returning an error, then your Windows C: should be mounted in the directory /mnt:

```
ls /mnt
```

You can navigate from the top of the filesystem to the /mnt directory (same directory where you see the top-level directories like /home /usr /tmp and /var among others).

---

### Post by oldfred on 2016-06-26
If system is UEFI, you should be able to go into UEFI or use one time boot key like f10 or f12 to get into UEFI boot menu (not grub menu) and directly boot Windows. You may need f8 to get into Windows repairs.

If BIOS system, you just about have to reinstall a Windows type boot loader with either Boot-Repair or your Windows installer or repair flash drive. After Windows fixed, reinstall grub to MBR to dual boot.

Either way you must turn off fast start up in Windows.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold

[/URL]
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]
[/URL]

---

