---
title: "Iomega Prestige hard drive"
date: 2009-05-02
forum: Hardware
---

### Post by figi22 on 2009-05-02
I'm having trouble mounting a brand new Iomega Prestige hard drive.  The message that I get is as follows:

[COLOR="Blue"]$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1 If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shut down Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line : mount -t ntfs-3g /dev/sdb1 /media/Iomega HDD -o force
Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/Iomega HDD ntfs-3g force 0 0[/COLOR]

First of all then I tried the command line option, but that didn't work.  Then I went in and edited the fstab file to add the new line, but then I just got a message:

[COLOR="Blue"]line 12 in /etc/fstab is bad
mount: can't find /media/Iomega in /etc/fstab or /etc/mtab[/COLOR]

Any ideas?

---

### Post by taurus on 2009-05-02
1.  Connect the drive to a windows machine and use the _safely remove hardware_ (icon in the lower right corner) option to unmount it first before you remove it.

2.  Install ntfsprogs and use ntfsfix to fix it.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/Iomega
sudo mount -t ntfs-3g /dev/sdb1 /media/Iomega
df -h
```

3.  Or force mount it with

```
sudo mkdir /media/Iomega
sudo mount -t ntfs-3g /dev/sdb1 /media/Iomega -o force
df -h
```

---

### Post by figi22 on 2009-05-02
Thanks - I'm ashamed to say that I took the easy option of no. 1 while waiting for a reply.  I wish I'd tried one of the other methods to see how I got on.

Anway all OK - thanks. :)

---

### Post by giosue_c on 2009-05-16
The real problem here is that your drive is formatted with NTFS.  Why not switch to a natively supported filesystem like ext3?  gparted will take care of that for you...

---

