---
title: "Ubuntu has bricked my laptop..."
date: 2011-05-20
forum: Hardware
---

### Post by rpmmatt on 2011-05-20
Hi.
I recently tried out Ubuntu 10.04 on my Toshiba laptop. However, due to a bug with being unable to change brightness and the Laptop not recognizing DVD's/CD's properly, I decided to go back to Windows. However, because Ubuntu has screwed my DVD drive, I could only boot from a USB stick. After formatting the hard drive using the Win 7 installer I get the error that Windows cannot create a partition and I can't install. An old XP disc doesn't even recognise the hard drive at all.
Strangley, when I use the Ubuntu CD it installs fine.

What has Ubuntu done to my laptop to stop it from using any other OS????????????????????????/

Forgot to add, Laptop is a Toshiba Equium P200

---

### Post by Nerotriple6 on 2011-05-20
Probably because you have formatted the drive with a filesystem that Windows cannot recognize such as EXT4? Boot up on the live CD containing Ubuntu, locate the hard drive tool and format it as NTFS. Windows should now detect it and be able to install.

---

### Post by ivanovnegro on 2011-05-20
Im sorry to hear that but the fault was yours, you formatted apparently your total hard disk and do just what Nerotriple6 told you.
The brightness thing can be buggy thats right but with Ubuntu you should be able to use your CD/DVD drive, you have to install the Ubuntu restricted extras for codecs because Ubuntu is free software and dont ship with proprietary codecs.
You can also enable to install proprietary things from within the install process if you want to install Ubuntu again, maybe :D.

---

### Post by Grenage on 2011-05-20
Indeed, and the XP disc probably doesn't have the relevant SATA drivers, so it won't be able to see the hard disc.

---

### Post by rpmmatt on 2011-05-20
Already reformatted the disk, and even manually put a partition in using the Diskpart tool from command prompt.

---

### Post by el_koraco on 2011-05-20
Maybe you need to go to bios and change from ahci to [ide]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-7-ultimate-x64-will-not-install-in-ahci/282886d4-a614-405f-aa33-f484e7ce5e6d") mode. 

I know Windows installs sometimes have trouble with that.

---

