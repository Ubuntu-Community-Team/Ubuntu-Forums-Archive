---
title: "Mounting USB sticks as a regular user not working"
date: 2009-09-30
forum: Hardware
---

### Post by Thomas Kenobi on 2009-09-30
I have the following problem. The system won't let me mount a removable usb stick (NTFS or FAT), unless I have root privileges. This also means that auto mount isn't working and I have to resort to the console every time.

To be clear this works:
```
sudo mount /dev/sdc1
sudo umount /media/sdc1
```However when trying to do the same without root privileges I get the following:
```
mount /dev/sdc1
mount: only root can mount /dev/sdc1 on /media/sdc1
```I have checked "Users and Groups" and the option to access external storage devices automatically is enabled for my account. I also tried tampering with the authorisations gui (org > freedesktop > hal > storage > mount file systems from removable drives), but nothing worked and since I don't exactly know how things work there, I just reverted to defaults.

Any help would be most than welcome.

---

### Post by Thomas Kenobi on 2009-09-30
Solution found. I'm posting it here for anyone interested.
[http://nixcraft.com/getting-started-tutorials/446-linux-mount-usb-flash-pen-drive-normal-user.html](http://nixcraft.com/getting-started-tutorials/446-linux-mount-usb-flash-pen-drive-normal-user.html)

---

### Post by renkinjutsu on 2009-09-30
Or, you can add an alias for 'mount -o user,exec,rw' so you don't have to make an fstab entry for every device you want to mount!

---

