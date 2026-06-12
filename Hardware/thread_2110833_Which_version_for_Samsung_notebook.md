---
title: "Which version for Samsung notebook?"
date: 2013-01-31
forum: Hardware
---

### Post by PurushothRokr on 2013-01-31
Hi i have Samsung Notebook 3 NP505e5Z!
CPU : AMD A4 1.96GHZ (2core)
RAM : 4gb
VRAM : 1 GB AMD HD RADEON

shall i install ubuntu 12.10 32 bit or i should go for 64 bit, also i wanna utilize full hardware resource....

 Is PAE works well in 32bit, if i go for 32 bit can i utilize my 4 gb? also can it support virtualization? 
The thing which resist to go 64 bit is application compatability and availability.. please suggest me friends.... :):)

---

### Post by Warren Hill on 2013-01-31
I'd go with 32-bit

see here for a discussion 
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by furything on 2013-01-31
Borderline memory.
If you intend to add more ram assuming 4gb is not the max supported then 64bit
If max ram then I would go 32bit

---

### Post by Mark Phelps on 2013-01-31
That must not be a valid model number because a search on it brings up nothing.

You need to find out the specific Radeon chipset that laptop contains.

AMD dropped Linux driver support this last summer for Radeon chipsets of the HD 2x/3x/4x series.  IF your laptop has one of those, you would do better going with 12.04 instead of 12.10.

---

### Post by grahammechanical on 2013-01-31
Why? You do not explain why you make these recommendations. The reasons that many give for choosing 32bit Linux instead of 64bit Linux are old reasons that no longer apply.

I am using the development branch of Ubuntu 13.04 (Raring Ringtail). It has the Linux 3.8 kernel. Support for i386 or 32bit CPUs is going to be removed from the Linux 3.8 kernel.

> A Linux kernel developer has asked that support for the i386 specifications be removed from the upcoming Linux kernel 3.8 and Linus Torvalds readily agreed.

[http://news.softpedia.com/news/Linux-Kernel-3-8-Says-Goodbye-to-i386-314293.shtml]("http://news.softpedia.com/news/Linux-Kernel-3-8-Says-Goodbye-to-i386-314293.shtml")

[http://lkml.indiana.edu/hypermail/linux/kernel/1212.1/01152.html]("http://lkml.indiana.edu/hypermail/linux/kernel/1212.1/01152.html")

If your machine has a 64bit CPU and we have an excellent 64bit OS (Ubuntu) with 64 bit applications, then why not install the 64 bit Ubuntu?

For a year now the Ubuntu developers have been installing in Ubuntu Multiarch libraries that make it possible to efficiently run 32 bit applications on 64 bit Ubuntu.

> Ubuntu 11.04 introduces support for installing packages from multiple architectures on a single system. This makes a wider array of 32-bit applications available to users of 64-bit Ubuntu.

[https://wiki.ubuntu.com/MultiarchSpec]("https://wiki.ubuntu.com/MultiarchSpec")

Ubuntu no longer provides a 32 bit non-PAE version. So, 32 bit CPUs that do not have PAE support cannot run standard Ubuntu.

Since when did we start describing 4GB of RAM as 'borderline?'

Mobile phones have 64 bit CPUs and the future Ubuntu phone will be running 64 bit Ubuntu.

---

### Post by PurushothRokr on 2013-02-06
> **Mark Phelps said:**
> That must not be a valid model number because a search on it brings up nothing.

You need to find out the specific Radeon chipset that laptop contains.

AMD dropped Linux driver support this last summer for Radeon chipsets of the HD 2x/3x/4x series.  IF your laptop has one of those, you would do better going with 12.04 instead of 12.10.

Model No: AMD HD RADEON 6480G
Yes i'm heard so. Thanks for reply:)

---

### Post by Yellow Pasque on 2013-02-06
Use 64-bit, especially if you want to use VM's.

---

### Post by PurushothRokr on 2013-03-23
Hi Guys,  i tried ubuntu-12.10-desktop-i386 on my laptop  it got stuck on the installation logo after sometime,
then i have tried ubuntu-12.10-desktop-amd64 it also failed.


When i see by pressing ESC i got this


Starting enable remaining boot time encrypted block devices         [OK]
Stopping enable remaining boot time encrypted block devices        [OK]




Then cursor appear after stuck.......

---

