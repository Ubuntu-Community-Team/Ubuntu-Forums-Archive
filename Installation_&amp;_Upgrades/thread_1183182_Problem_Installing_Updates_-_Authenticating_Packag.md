---
title: "Problem Installing Updates - Authenticating Packages"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by igfud on 2009-06-09
Hello,

I'm using Ubuntu 9.04.  Every time I try to install updates when the window opens showing currently available updates, I receive a window telling me to complete a "partial upgrade."  (I'm not sure why this is necessary, because I installed 9.04 from a CD and so there shouldn't be any newer version to upgrade to, although maybe I don't fully understand the message).  After clicking on this, I receive the following error:

> 
It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.The listed package is libdb4.3.  After clicking on "Close" the update manager does not reopen and I am not prompted to update until the next reboot.

There used to be two packages listed with the error, but now there is only one.  What might be the cause of this?  I wouldn't mind so much, except that it won't allow me to install any updates until this issue is resolved.  I've had this problem for the last few weeks.

I have attached an image of the error message.

Thanks,
igfud

---

### Post by wpshooter on 2009-06-09
Have you tried changing to a different Ubuntu server ?

---

### Post by igfud on 2009-06-10
I went ahead and tried sudo apt-get install libdb4.3 and it seemed to work fine.  I opened the update installer and proceeded through the partial upgrade.

Everything seemed to work fine.  Once the installer closed, it reopened saying there was a partial upgrade.  I tried to install the updates, but the previous set of updates had disabled my wireless internet access so I rebooted the computer.  Upon rebooting the computer the Ubuntu grub entry had disappeared leaving only the memtest.

Currently I'm using the LiveCD.  How might I fix the grub menu (or possibly an additional problem with the installation)?  I tried the instructions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but only the memtest is showing on the grub menu.

I've also seen a couple sites recommending the use of grub-install.  I mounted the partition that contains my installation and tried sudo grub-install /media/disk (such that the full path would be /media/disk/boot/grub).
This was the output of grub-install:

```
Probing devices to guess BIOS drives. This may take a long time.
Format of install_device not recognized.

```

Any ideas why Ubuntu might have disappeared from menu.lst, and how I might be able to fix this?

Thanks,
igfud

---

### Post by igfud on 2009-06-12
bump :(

I could definitely reinstall without losing anything, but what fun is that?  I'm more interested in why it disappeared from GRUB (or menu.lst).

Thanks,
igfud

---

