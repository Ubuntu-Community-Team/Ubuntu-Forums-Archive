---
title: "Need Help with Dual Booting"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by abhjos on 2009-07-08
[SIZE=2]Hello Friends,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I am using Windows Vista and installing the Linux Ubuntu 9.04 on the seperate partition. The Linux installation is successful, and when I restart the system and check if my windows vista is working properly I am getting some Grub 2 error message and my windows vista is not starting, but I am able to start Linux.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Please help me with this issue as I want to use both Windows and Linux.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Hoping to get helping hand from your side.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thank you,[/SIZE]
[SIZE=2]Abhay Joshi[/SIZE]

---

### Post by joshedmonds on 2009-07-08
Go to Applications -> Accessories -> Terminal

Enter the follwing:

```
sudo fdisk -l
```

Copy and paste the output here. Please use the code tags around what you paste (see the # above the text field)

Also, please post the contents of /boot/grub/menu.lst below the words 'End Default Options' in the 'Debian Automagic Kernel List' all the way to the end of the file.

EDIT: No reply for half an hour, I'm bugging out, can someone else take this if it resurfaces.

---

