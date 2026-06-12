---
title: "Ubuntu 16.04 USB &amp; Disc issues"
date: 2017-03-17
forum: Hardware
---

### Post by wshakes on 2017-03-17
Ubuntu 16.04, freshly installed and updated.
Dell Lattitude E6430

Upon sudo gparted, I get:
> 
Libparted Warning
The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Cancel / Ignore

I am able to hot plug recognize USB plugin and I am able to read and write-- albeit slowly, it starts out fast, but within a minute it bottlenecks around 21MB/s on my USB 3.0 port-- but I am unable to format the drive within unity file manager.

If I ignore gparted warning, USB drives are not recognized under devices.

1. Is the libparted warning serious / do I need fixingt / why can't GParted find my USB drives while Unity can?
2. How may I format my usb drives?
3. Why is USB 3.0 slow, I had this same problem with Mint and Arch. I do not have windows to troubleshoot this issue. Is it linux or my laptop and is there a workaround?

Please help me troubleshoot and I will closely follow your direction. Thank you for your time.

---

### Post by wshakes on 2017-03-17
Ubuntu 16.04, freshly installed and updated.
Dell Lattitude E6430

Trying to format USB Drive.

I am able to hot plug recognize USB plugin and I am able to read and write within unity-- albeit slowly, it starts out fast, but within a minute it bottlenecks around 21MB/s on my USB 3.0 port.

Upon format inside unity file manager I get:

> This partition cannot be modified because it contains a partition table; please reinitialize layout of the whole device. (udisks-error-quark, 11)

Now to try gparted. Upon sudo gparted I get as soon as it opens up:
> 
Libparted Warning
The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Cancel / Ignore

Upon Ignore, strangely gparted sees the device and thinks it is some how 59GB?? (It's a 16GB USB drive, and contians the image I used to install ubuntu.)

What do I do?

---

### Post by wshakes on 2017-03-17
Why did ubuntu forums create two topics after I edited. This OP is no good, see link for simpler and updated description of my problem:
[https://ubuntuforums.org/showthread.php?t=2355896](https://ubuntuforums.org/showthread.php?t=2355896)
Please use that topic ^ Thanks for any help.

---

### Post by wildmanne39 on 2017-03-17
I merged the threads for you so please stay in this thread.

Thanks

---

### Post by wshakes on 2017-03-17
> **wildmanne39 said:**
> I merged the threads for you so please stay in this thread.

Thanks you made it worse. delete the OP or edit the OP with the text from post #2

---

### Post by QIII on 2017-03-17
Please do not make demands of the Staff.

If you have an issue with the action of a Staff member, you are welcome to start a polite post for the Administrators in the [Resolution Centre]("https://ubuntuforums.org/forumdisplay.php?f=123") to help us see your point of view.

---

### Post by wshakes on 2017-03-17
> **QIII said:**
> Please do not make demands of the Staff.

If you have an issue with the action of a Staff member, you are welcome to start a polite post for the Administrators in the [Resolution Centre]("https://ubuntuforums.org/forumdisplay.php?f=123") to help us see your point of view.

Did I forget to say please? I am sorry to upset your sensibilities. Let's get real. I am concerned about clarity of the topic for future readers who may have a similar problem as mine. That is the only thing I am concerned about. If you're going to be editing other people's topics, do it right.

Gparted is working fine. It's only one USB drive I am having a problem with which previously has had a low level rewrite the wrong block size. And ubuntu is recognizing the normal USB drives just fine as well. Not sure how to properly repair this USB drive though.

I repaired the usb drive following instructions here:
[http://askubuntu.com/questions/675649/unable-to-delete-usb-drive-partitions-block-size-error](http://askubuntu.com/questions/675649/unable-to-delete-usb-drive-partitions-block-size-error)

---

