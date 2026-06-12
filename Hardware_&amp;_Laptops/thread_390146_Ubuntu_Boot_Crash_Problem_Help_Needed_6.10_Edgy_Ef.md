---
title: "Ubuntu Boot Crash Problem Help Needed 6.10 Edgy Eft"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by SFHasan on 2007-03-21
Hello All,

I am relatively a new but pretty amazed and convinced user of Ubuntu 6.10 Edgy Eft, after trying various flavours (distributions). This is by far the most user friedly release I have seen for mainstream desktop users, yet when it comes to boot crash and system errors, very little can be resolved by just a simple re-installation over the previous messed up copy on the hard disk. 

My hardware configuration is as follows ;

HP Pavillion Laptop Dv1000, Celeron 1.7 Ghz, 512MB RAM, 80GB HardDisk and the usual peripherals which are always a part of the package.

I created around 10GB of unpartitioned space and installed Ubuntu with its own automatic partitioning option of defining the root and the swap partition. Now my system was a Dual Boot with Windows XP SP2 and Ubuntu 6.10 with a GRUB selection at startup working just flawlessly. I was able to install a good bunch of all working softwares for multimedia, browsing, CD/DVD playing and burning, fonts, bluetooth and some good amount of Eye-Candy too using AIGLX and BERYL. Everything was working fine and both OS were living in peace and harmony.

And then the bad day has dawned today, as I tried to access Linux partitions from within windows. For this purpose I used the EX2IFS driver/software from [http://www.fs-driver.org]("http://www.fs-driver.org"). It was installed and working amazingly seemless with my linux partitions (which is Ext3 and the software mainly for Ext2 claims to be perfect for it too). 

But after installation of EX2IFS, when I rebooted into GRUB to get into UBUNTU, the boot process always crashes and shows the strange following message ( I have attached the screenshot as well).

```

init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS process (1880) terminated with status 1
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default process (1881) terminated with status 1
```

I tried searching around for a similiar problem with a remedy, but in vain. I am not sure that whether this problem is caused by EX2IFS access driver in Windows, since its websites says it works just great without any harm to the linux partititions. The troubleshooting section on the website has nothing much too, since I never renamed my linux partitions under windows.

I hope some help is out there, I have tried booting in the recovery mode and it freezes at the same location where the normal bootup does. I tried booting using the Live-CD, but not much of recovery options are known to me by using it.

Any help would be highly appreciated, since RE-INSTALLATION is certainly the last option I am thinking of, cause of all the nice desired customization of the system would be lost and to be done again, which is a time intensive task. :( 

Thanks in advance.

Best Regards,
S.F.Hasan

---

### Post by apjone on 2007-03-23
Hi, in ubuntu /bin/sh is not a program itself but points to either bash or dash. It looks like  your link has been removed , You need to some how run the following command (may be try recovery mode) as root

```

ln -sf /bin/bash /bin/sh

```

could try a live cd 

mount your / partion to root and try

```

ln -sf /bin/bash /mnt/bin/sh

```

again as root. This should work.

This post should have been put in general help.

---

### Post by SFHasan on 2007-03-24
Thank you ApJone,

I would have tried what you suggested, but I believe the restless soul in me couldnt wait this long for your helpful reply...heheh.

I resintalled the Ubuntu again and was able to download all the desired repositories and related stuff with a effort of 2 days.

Thank for your concern anyways, would be asking you for more help if needed in the future.

Regards,
S.F.Hasan

---

### Post by apjone on 2007-03-24
`No problem. Glad everything is back worksing (and now you have a cleaner machine). If you need any help do not hesitate to ask.

---

### Post by mathieu.lacage@sophia.inr on 2007-03-26
Actually, I encountered the exact same error message today on my ubuntu after a dist-upgrade to 7.x and it turns out that /bin/ is entirely clean if I look at it from my rescue boot...

I suspect that my only alternative is to re-install now unless someone knows of a magic apt-get command which can reinstall every package which stores files in /bin...

---

### Post by chouf on 2007-09-28
Hi all,

I have exactly the same problem.
I installed Ubuntu on my T41 IBM laptop without any problem.
The I started to install Lotus Notes 8.0 for Linux.
I followed this guide to do the setup ([http://www.glump.net/dokuwiki/howto/notes_8_on_ubuntu](http://www.glump.net/dokuwiki/howto/notes_8_on_ubuntu)).

The installation went fine, but after a reboot, Ubuntu would not load.
I'm now getting the following error message during the boot process:

```
init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2397) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2398) terminated with status 255
```

I'm a Linux newbie, but I suppose this is related to the following command I've typed in, part of the "how-to" guide linked above:

```
sudo mv /bin/sh /bin/sh.old
sudo ln --symbolic /bin/bash /bin/sh
```

then

```
sudo rm /bin/sh
sudo mv /bin/sh.old /bin/sh
```

I booted the laptop with the Live CD but now I'm stuck as I don't know what to do to repair this.

Would anyone know what to do?

Thanks in advance for your help

chouf

---

