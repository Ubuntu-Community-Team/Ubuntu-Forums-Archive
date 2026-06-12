---
title: "Removable Harddrive"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by aikiwaza on 2007-07-16
(Fiesty) I have a hot swappable (removable) harddrive (sata).  I am having troubles installing/mounting it.  Ubuntu can see the drive and I have been able to format and partition it (FAT32... both windows and ubuntu need to be able to see it.)  The problem is that Ubuntu won't mount it as a removable medium.  I researched several ways to mount it.  None of them have worked yet.  It only shows up as a folder (under /media/), and one that won't allow me to change permissions on it, hence I can't write anything to it.  I am new to Linux OS so any help is appreciated.

If more information is needed please let me know what and if it's not a common knowledge how to get that info.

Thanks.

---

### Post by markusf21 on 2007-07-16
try ```
sudo chown -R username:username /media/what ever its called
```
it wont help u with the mounting but but it should let u read/write to it

EDIT username = your name

---

### Post by aikiwaza on 2007-07-19
Thanks for that command... I can now write to the folder.  The only thing is that the folder isn't on the hard drive at all.  It is on the system harddrive and so doesn't really help me being there.  I don't think that my sata hd mounted because I can't find it anywhere.  Does anyone have any advice for that?

---

### Post by aikiwaza on 2007-12-26
solution: i modified the fstab file (located in /etc/fstab... use the command in terminal: sudo gedit /etc/fstab )

There is lots of documentation on how to edit fstab so I won't post any of that here.

---

