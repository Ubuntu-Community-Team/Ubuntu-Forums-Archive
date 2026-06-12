---
title: "writing iso files"
date: 2008-11-20
forum: General Help
---

### Post by hirohitosan on 2008-11-20
Hi there.
I have a USB pen drive with 2 partitions on it. One is a normal disk and the other is a CD-rom like disk. I mean when I insert in my USB drive it is mount like a CD. Can I write on that virtual CD an ISO image?

And generaly how can I burn an ISO image on a pen drive?

Thanks

---

### Post by malachi on 2008-11-20
I'm not sure what you mean in your first question, but you can burn an ISO to a USB drive using [Unetbootin]("http://unetbootin.sourceforge.net/"). 

Homepage: **_[http://unetbootin.sourceforge.net]("http://unetbootin.sourceforge.net/")_**

You can download the Ubuntu version [**_here_**]("http://unetbootin.sourceforge.net/unetbootin-i386-latest.deb").

---

### Post by tom66 on 2008-11-20
You could extract the ISO using Archive Manager, then copy it across to the relevant partition(s). But I'm not sure this is what you want. Please note though; it won't preserve boot sector information so it won't make the drive bootable.

---

### Post by john183 on 2008-11-20
I am gonna take a stab in the dark and guess that your usb drive is a "U3 smart" enabled drive. The "cd" portion of that drive is not writable. and to use that drive to make a bootable usb thumb drive you would have to take to "U3" software off. I have had to do that to 3 different drives to to use them the way that i wanted to.

Removal of the U3 software must be done in windows. For more information on that subject go to:
[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

As for making a Ubuntu LiveUSB drive, that information can be found in great detail here in the forums.

---

### Post by hirohitosan on 2008-11-22
> **john183 said:**
> As for making a Ubuntu LiveUSB drive, that information can be found in great detail here in the forums.

can you point where I can find?

thx

---

### Post by john183 on 2008-11-22
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[http://ubuntuforums.org/showthread.php?t=515574](http://ubuntuforums.org/showthread.php?t=515574)

Hope this helps. post back if this works or you need any other help

---

