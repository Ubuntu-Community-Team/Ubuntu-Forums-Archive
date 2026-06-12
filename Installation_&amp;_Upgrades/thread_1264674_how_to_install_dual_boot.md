---
title: "how to install dual boot"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by baltadt on 2009-09-12
I have Vista already installed. I have been running 9.04 from an 8gig usb for a month now and want to dual boot now. I have already partitioned 40gigs for ubuntu but I was looking for help to make sure I don't mess up.  After I installed ubuntu on my usb drive it will not let me load windows with it in. Although if I remove the usb it loads fine. Please help me install correctly this time.

---

### Post by rob-ward on 2009-09-12
You should have no problem getting it working when it is on the hdd, just make sure your usb drive is disconnected when you install. By the sounds of it you have made a boot loader on the USB pen drive that doesn't now about windows, you shouldn't have that problem when installing on the HDD.

---

### Post by baltadt on 2009-09-12
But  when I boot from the usb it allows me to select windows vista but when it tries to load it says error 13:invalid or unsupported executable format

---

### Post by rob-ward on 2009-09-12
If you are reinstalling ubuntu on your HDD it shouldn't be a problem, however if you want to try and fix that error then this post might help you

[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

hope that helps

---

### Post by presence1960 on 2009-09-12
let's not guess at why you get error 13. we need to see exactly your setup. With your ubuntu USB plugged in boot into Ubuntu. Do this:

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by raymondh on 2009-09-12
> **rob-ward said:**
> If you are reinstalling ubuntu on your HDD it shouldn't be a problem,
EDIT : better see the boot info script first :) Also, do you have Ubuntu in your HD already?

---

### Post by baltadt on 2009-09-14
Thank you all but I solved the problem.  I just dove off the deep (kinda) and I am now dual booting Vista and Ubuntu from my hard drive and have absolutely no problem loading windows.  Should have done this a long time ago, it's sooooo much fast. Thank you all again.

---

