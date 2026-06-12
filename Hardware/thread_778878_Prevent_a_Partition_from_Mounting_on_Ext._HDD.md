---
title: "Prevent a Partition from Mounting on Ext. HDD?"
date: 2008-05-02
forum: Hardware
---

### Post by SendDerek on 2008-05-02
Hello,

I was hoping that there was a way prevent a partition on an Ext. HDD from mounting.  Basically, I have parted this HDD two ways: one with NTFS and the other with Ext3.  I don't want the first partition (the NTFS) to mount while in Linux.  This way, I don't have to unmount two different drives for the same one HDD.  Is there a way?

Thanks in advance,

Derek

PS.  My next question is going to be can I rename the drives?  So, "My HDD" instead of "disk-1" or "disk-2"?

---

### Post by russo.mic on 2008-05-02
Well, do you not want them to mount on start up?  that can be done by removing the partition's entry in /etc/fstab.

You could still manually mount the partition if you choose, but it wouldn't mount automatically. 

As far as renaming goes, you could rename the volume label easily enough, but not the /dev/ entry as far as I know.  Here is a link:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Hope it helps!  

Russo

---

### Post by SendDerek on 2008-05-02
Thanks very much. The renaming part helped out a lot.  

I'm still trying to figure out how NOT to mount the first partition of my Ext. HDD when I plug it in via USB.  It's not in the fstab file to edit.

---

### Post by clemmy on 2011-04-29
*I know this is a quite old thread, but I was searching on google for the same problem and this is one of the first results.. so i think this is a good place to share a solution that i've just found... (maybe it's not useful anymore for SendDerek but could be useful for others!)*

[LIST=1]
[*]plug your ext drive and check the UUID and the type of the partition that you don't want to be automatically mounted (/dev/sdb2 in this example)
```
$ sudo blkid
/dev/sda1: UUID="699a99b8-aab2-4701-a0f4-bb0fd9ec6dc9" TYPE="ext4" 
/dev/sda2: LABEL="swap" UUID="b6740a9a-f897-4f25-a73e-b1d12f0af64e" TYPE="swap" 
/dev/sda3: UUID="f51a03d8-da8a-4e09-b793-1d15eed69da5" TYPE="ext4" 
/dev/sdb1: LABEL="'M-]hM-(^X" UUID="2BC7-51A4" TYPE="vfat" 
/dev/sdb2: UUID="[COLOR="Red"]57f8f4bc-abf4-0000-675f-946fc0f9f25b[/COLOR]" TYPE="[COLOR="Blue"]ext4[/COLOR]"
```


[*] edit /etc/fstab (sudo gedit /etc/fstab) and append this at the end of the file. Replace the UUID and the TYPE according to the value you got in previous step.
```
# Prevent mounting specific partition on external hd
UUID=[COLOR="Red"]57f8f4bc-abf4-0000-675f-946fc0f9f25b[/COLOR] none [COLOR="Blue"]ext4[/COLOR] ro,noauto
```


[*]reboot
[*]enjoy :)
[/LIST]

---

