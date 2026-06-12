---
title: "Lenovo G570: wired connection not working with Atheros AR8152 chipset"
date: 2012-03-27
forum: Hardware
---

### Post by reeboblue on 2012-03-27
Hi all, recently picked up a Lenovo G570 and have been trying to get the wired/ethernet connection working in Ubuntu 11.10.  The laptop has a Atheros AR8152 V2 chipset in it and I did try the steps in this [other thread]("http://ubuntuforums.org/showthread.php?t=1505697&highlight=atheros+ar8152&page=26"), but it did not work.  Has anyone gotten the wired connection working on this laptop with Atheros AR8152?  If so, please help me out and let me know step-by-step the fix to get this working.

TIA :p,
Chris

---

### Post by sidzen on 2012-03-27
[SIZE=3]There exists a great resource I find myself going back to again and again.  I'll pass it on.  [***Here***]("http://www.cyberciti.biz/faq/linux-find-wireless-driver-chipset/")

[URL="http://linuxwireless.org/en/users/Download"]
http://linuxwireless.org/en/users/Download[/URL]

[https://bugzilla.redhat.com/attachment.cgi?id=355728](https://bugzilla.redhat.com/attachment.cgi?id=355728)
[/SIZE]

---

### Post by reeboblue on 2012-03-27
Thanks much for the reply sidzen!  I appreciate any help you can provide.  I did try installing the latest ccompat-wireless-2.6.tar.bz2 driver from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) already.  I tried the latest, and also a number of different drivers from that link with different build dates 2012, also from mid, late 2011.    To install I did these steps after downloading the driver *.bz2 file to my desktop:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make instal

```

None of them worked. I did notice that your link to [https://bugzilla.redhat.com/attachment.cgi?id=355728](https://bugzilla.redhat.com/attachment.cgi?id=355728) looks like a slightly different driver from the ones I've tried.  Do you think that will work?

Cheers and thank you,
Chris

---

### Post by nptuanthach on 2012-10-16
Thanks much Reeboblue!
I got the same problem with Athero AR8152/8158 but now I solved it by your way.

---

