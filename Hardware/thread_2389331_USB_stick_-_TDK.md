---
title: "USB stick - TDK"
date: 2018-04-15
forum: Hardware
---

### Post by dee119 on 2018-04-15
):P Hi - have just downloaded a live iso Distro onto a 32Gb TDK usb stick.

At the moment the live Distro will play OK,  but I am now unable to add any
addition read-only files to the USB stick for the grand children to understand
what to do..

Have tried to change the permissions to the USB drive sd/b  via #sudo chmod

 but I keep getting the message #Read-only file system cannot
change permission.

Anyone help me understand where I am going wrong on this please.

Thank you for any input.

---

### Post by oldfred on 2018-04-15
The standard live installer is Read-only as it is a replacement for a DVD and configured the same. It is not set up to be modified.

If you want to use live installer a little be more and save some data, but still cannot update installer itself, you want what is called a persistent install.
That provides separate space for data. I think it is limited to 4GB and with your large flash drive you need added partition(s).

       Persistent  install
[URL="https://help.ubuntu.com/community/mkusb/persistent"]https://help.ubuntu.com/community/mkusb/persistent
      [/URL]
 [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) 
    
[URL="https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752"]https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752
      [/URL]
 [http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal]("https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752")


With larger flash drive, you also can do a full Ubuntu install, it will not be as fast as an install to internal drive, but is functional. You install from a smaller flash drive which just needs to be 2GB or more to the larger flash drive like you would install to any external drive. UEFI or BIOS makes a difference, though.

---

### Post by dee119 on 2018-04-16
:D Hi OldFred - thank you so much for your reply to my question on the USB stick.

Have had a quick look at the information and the link pages you suggested ,  but will
 need to re-read a few times to get acquainted with every thing. 

Thank you again and am most grateful for your help and advice,  that's what I do
love about this forum,  all the knowledge and help of the members. 

Will spend some time getting everything up and running, but for now will
post that the question has been Solved.

Best wishes and thanks - Dee

---

### Post by dee119 on 2018-04-16
Now Solved

---

### Post by slickymaster on 2018-04-16
> **dee119 said:**
> Now Solved

Being so, please mark the thread as solved. Follow the link in my signature if you don't know how to do it.

---

### Post by dee119 on 2018-04-16
:) Thank your slickymaster for your heads up on my lack of knowledge on the solved tag.

Best wishes - Dee

---

