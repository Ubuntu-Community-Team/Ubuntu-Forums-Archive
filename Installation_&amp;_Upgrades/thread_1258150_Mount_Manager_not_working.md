---
title: "Mount Manager not working"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by zenbachry on 2009-09-04
I use Mount Manager to automatically mount my other hard drive that was put in after installing of Ubuntu.

Just recently I had partitioned it. When I restarted the computer and got back to Ubuntu, I tried to reload Mount Manger to set it to automatically mount the new partions. But it wouldn't load. It would ask me for administrator password, then it would pop up in the panel, then disappear. Nothing happened. I uninstalled it, and installed it again, but same thing.  Then, just before thinking of asking for help, I had thought about opening it in the Terminal, and see what it gives me.

This is what it gives me:

```
stray@stray-desktop:~$ mountmanager
4 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/fd0" 
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sdb2" 
[I] Storage device was detected: "/dev/sdb1" 
[I] Storage device was detected: "/dev/sda5" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sdb" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/iso9660.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/udf.xml"  was successful 
[W] Parsing of  "/usr/share/mountmanager/options/ext4.xml"  was unsuccsessful 
[W] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was unsuccsessful 
Segmentation fault
stray@stray-desktop:~$ 
```

So...what's it mean and how do I fix it?

---

### Post by stlsaint on 2009-09-04
have you added the entry into fstab...there is where you may want to edit so that you can add the auto mount your drive. add a stanza to show like the rest of your drives. whatever the position of your new drive is /dev/sda etc is what you want to add to in fstab.

---

