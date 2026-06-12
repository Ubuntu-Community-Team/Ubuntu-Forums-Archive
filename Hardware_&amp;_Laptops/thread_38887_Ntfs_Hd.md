---
title: "Ntfs Hd"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by blasmat on 2005-06-02
I currently run Mandrake 10.1 and have run a lot of distros in the past and am very interested in running Ubuntu. I have downloaded and installed Hoary, but found quickly that it doesn't see my NTFS Hard Drive! That's my data drive, I need the info on it, so I reinstalled Mandrake. Any idea what's up?

---

### Post by somuchfortheafter on 2005-06-02
google search turned this up first.. it should be of some assistance
[http://www.techspot.com/vb/all/windows/t-850-Using-NTFS-partitions-as-normal-User.html](http://www.techspot.com/vb/all/windows/t-850-Using-NTFS-partitions-as-normal-User.html)

---

### Post by shakin on 2005-06-02
[QUOTE=blasmat]I currently run Mandrake 10.1 and have run a lot of distros in the past and am very interested in running Ubuntu. I have downloaded and installed Hoary, but found quickly that it doesn't see my NTFS Hard Drive! That's my data drive, I need the info on it, so I reinstalled Mandrake. Any idea what's up?[/QUOTE]

I'm sure it can see the drive, but it doesn't automatically mount it. You will want to add an fstab entry to see the drive. Since you're on Mandrake right now, open /etc/fstab and copy out the line for that drive. Save it and paste it into your fstab on Ubuntu, making sure to create the right directory locally (eg. /media/windows).

Of course, you can only safely read from NTFS. I suggest installing captive-ntfs (should be in the Ubuntu repositories), which will use the Windows-native dlls for NTFS so you can read and write to that drive.

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=blasmat]I currently run Mandrake 10.1 and have run a lot of distros in the past and am very interested in running Ubuntu. I have downloaded and installed Hoary, but found quickly that it doesn't see my NTFS Hard Drive! That's my data drive, I need the info on it, so I reinstalled Mandrake. Any idea what's up?[/QUOTE]
 Did you try instructions at 
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

?

---

