---
title: "[HOWTO]  Netgear ReadyNAS and Ubuntu"
date: 2011-12-24
forum: Hardware
---

### Post by ionospheric on 2011-12-24
This Howto explains how to access the ReadyNAS shares with Ubuntu.

- Install Samba file system
```
sudo apt-get install smbfs
```

- Allow netbios name resolution (so you can reach shares through a name rather than IP address)
```
sudo gedit /etc/nsswitch.conf
```

- In this file, change line
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
  to
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

- then install winbind
```
sudo apt-get install winbind
```


- Create directories necessary for permanent mount:
```
sudo mkdir /mnt/NAS
sudo mkdir /mnt/NAS/media
```

- Make yourself the owner of the mount point
```
sudo chown -R myusername:myusername /mnt/NAS/media
```

- Store login credentials on your system
```
sudo mkdir /root/credentials
sudo mkdir /root/credentials/NAS
```

- Create a credentials file
```
sudo gedit /root/credentials/NAS/media
```

- In this file, add the two lines
```
username=media
password=******
```
(using the password that you gave the share on the NAS)

- Edit fstab to add the mount information
```
sudo gedit /etc/fstab
```

- add the line
```
//nas-02-48-AD/media    /mnt/NAS/media     cifs uid=1000,umask=000,noperm,noserverino,nogroup,rw,credentials=/root/credentials/NAS/media,iocharset=utf8 0 0

```
Notes: - nas-02-48-AD is the network name of the NAS
       - noperm circumvents permission problems
       - noserverino solves a problem with Thunderbird
       - add noauto if you don't want the share to be mounted automatically
       - the credentials file saves you from showing your password in the fstab

- Then mount the share
```
sudo mount /mnt/NAS/media
```

Helpful links:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=814298]("http://ubuntuforums.org/showthread.php?t=814298")
[http://ubuntuforums.org/showthread.php?t=88206]("http://ubuntuforums.org/showthread.php?t=88206")

---

### Post by dirktanyan on 2012-01-08
Very nice!

---

