---
title: "Usb ports do not appear in my Virtualbox machine"
date: 2010-06-09
forum: Hardware
---

### Post by sgb77 on 2010-06-09
Hello,
I have read a lot of post similar to this problem where the usb ports settings in virtualbox is greyed out. However my problem is that I don't even see the usb category in my virtual machine.

I have added the following fix that worked for the issue when the category is greyed out ( nothing changes for my case)
```
sudo nano -w /etc/fstab

Enter this in your fstab under all of the rest of the lines, make sure you do not edit anything BESIDES adding this new line.

Reboot and see how well it works.

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

I am kind of new to the virtualbox in linux world, so any help would be greatly appreaciated.

I am running Ubuntu 9.10 in a Dell vostro 1000, amd 32 bit.

Thank you.

---

### Post by C.S.Cameron on 2010-06-09
As I understand USB drives don't work with Vbox OSE.
Try the full version from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).
(even then I find USB support a bit touchy).

---

### Post by sgb77 on 2010-06-11
Thank you,
I was not aware there were different versions of virtual box. Thanks a lot for the help

---

### Post by cfhowlett on 2010-06-11
After setting up your vm's, make sure you set up the "Guest Additions".  Download the user manual for the vbox site for more.

---

