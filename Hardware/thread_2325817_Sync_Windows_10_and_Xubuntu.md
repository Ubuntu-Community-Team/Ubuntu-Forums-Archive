---
title: "Sync Windows 10 and Xubuntu"
date: 2016-05-25
forum: Hardware
---

### Post by makem2 on 2016-05-25
I have a machine running Windows 10 and used by other family members. Data they produce is saved to one folder on the machine.

I have Xubuntu and want to sync the above folder with my Xubuntu from where it will then be synced to a Raspberry Pi, or, better still, sync it directly with the Rpi which is also on the same secure LAN.

I want the sync to be initiated from the Xubuntu machine.

I currently use rsync to sync the Xubuntu and Rpi but so far have been unable to add in the W10 machine.

I can browse the W10 machine from Xubuntu but not the other way round.

Can anyone put me on the right path please?

---

### Post by bashiergui on 2016-05-25
It sounds like you want to share the folder amongst all computers on your lan.

If the xubuntu machine is separate from the windows 10 machine then you can use samba to share the windows folder. 
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by makem2 on 2016-05-25
I can browse the windows folder but I cant figure out how to rsync it to the xubuntu machinefrom that machine.

The windows folder is shared.

All searches bring up linux to windows syncing from windows, not the other way round.

---

### Post by yancek on 2016-05-25
Windows is designed to NOT be able to access or read Linux filesystems.  There is third party software which 'might' work on the same machine.  If they are separate machines, you would need samba installed and configured to do what you want.

---

### Post by Mark Phelps on 2016-05-26
Is this "folder" on the Win10 machine inside the OS partition, or is it inside a separate Data partition?

If it is the former, you are risking corrupting the Windows filesystem by sharing it, regardless of what tool you use.  And if it does get corrupted, you will then NOT be able to boot Win10 -- which will make it really hard to fix.

A much SAFER alternative is to stored shared data inside a data-only Windows partition formatted NTFS.  That way, if that filesystem does get corrupted, you can easily repair that from inside Win10.

Good Luck

---

