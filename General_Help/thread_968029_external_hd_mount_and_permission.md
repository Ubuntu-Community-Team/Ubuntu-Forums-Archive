---
title: "external hd mount and permission"
date: 2008-11-02
forum: General Help
---

### Post by hndaklr8480 on 2008-11-02
hey sorry to ask so many questions.  I was given a 250g harddrive and have been able to format it and mount it.

it is mounted:
/dev/sdb1 /mnt/usb


I am able to view the file in it with filemanager, but cant write to it. I have tried chmod and it does not work

the harddrive is vfat so i know chmod doesn't work with it anyway

I have edit /etc/fstab for the automount and is reads:
/dev/sdb1 /mnt/usb  auto default 0 0

it doesn't automount 

I troubleshot this with someone on the ubuntu irc chat and we formated the harddrive fat32 so it would be compatible with window incase i was at a windows computer and wanted to access it.  we then mounted the drive and it worked, we then unmounted unpluged waited 10 sec plug back in and a window popped up labeled 250g storage device. I have changed nothing and if i unplug device i have to manualy mount again in the terminal browse filemanager to find it, and then don't have permission to move folders or files to or create folders in the directory(harddrive) please help i am frustrated with this.  I would like to be able to play with other distros and showoff linux from the harddrive to people with windows on their computers. I would like full permission to this harddrive
thanx

---

