---
title: "Installed Vista after ubuntu"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by RastaManPower on 2009-08-07
hello guys i jsut installed vista and now i cant boot into ubuntu. how can i fix the bootloader? i am new to ubuntu and dualboots. anyone can help me configure grub again?

---

### Post by Mighty_Joe on 2009-08-07
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by merlinus on 2009-08-07
Boot from live cd, open a terminal, and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

Remove the cd and restart.

---

### Post by RastaManPower on 2009-08-07
ok guys i will try now and let you know if i got it to work or not. thank you

---

### Post by RastaManPower on 2009-08-07
i have tryed what you told me...still nothing..i se grub loading but then it gives like an error that i have no time to read and boots into vista...

---

### Post by merlinus on 2009-08-07
Post results of

```
sudo fdisk -l
```

---

### Post by ajgreeny on 2009-08-07
What did you actually use for the command ```
setup (hd0)
``` because it should normally be exactly that, not the number from the previous command.  (hd0) will normally put grub on the windows disk MBR, which is the easiest way to do things.  When the machine begins to start grub, try hitting any key which may mean the error message is retained on screen and you can tell us exactly what it said.  If that is no help boot to the live CD again and run ```
sudo fdisk -l
``` to see what your partition layout is like, or use gparted and send a screenshot of that if you prefer, it can sometimes be more helpful.  It would also be useful to see your ubuntu install's /boot/grub/menu.lst, so mount the ubuntu partition using the live CD, navigate to the /media/**ubuntupartition**/boot/grub/menu.lst and copy it here.

---

