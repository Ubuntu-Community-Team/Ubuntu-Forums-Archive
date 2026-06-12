---
title: "Inspiron 1100 as Edubuntu LTSP Client Screen Resolution"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by ashkev on 2007-08-26
I am trying to boot a Dell Inspiron 1100 as an LTSP client.  It boots, but the resolution is tiny.  I know that the resolution problem on this machine is well known, and I think I know how to fix it, for a Ubuntu installation, but since this is a terminal, I am having trouble.  I have looked at[ this thread]("http://www.mail-archive.com/edubuntu-users@lists.ubuntu.com/msg01224.html") from the Edubuntu mailing list, but it has nit helped.  I have installed the 915resolution package:

> sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/sources.list
sudo chroot /opt/ltsp/i386

apt-get update
apt-get install 915resolution

And I have tried using [this howto]("http://ubuntuforums.org/showthread.php?t=351647") to set my resolution to 1024x768.

Do I need to do something with a custom XF86config file.  If so, can someone help me with it?

I did boot the laptop using Knoppix and everything looked fine.  I will attache the xorg.conf file from that.

Thanks

---

### Post by ajgreeny on 2007-08-26
>  apt-get update
apt-get install 915resolution

I think you need to put **sudo** in front of both these commands for anything to happen.

---

### Post by ashkev on 2007-08-26
Yes, I did....sorry I didn't mention it.  The package was installed.  When I tried to boot the terminal, I got some strange patterns on the screen, but it x would not boot.  It had booted before...just in a tiny screen.

---

### Post by ashkev on 2007-08-27
can anyone help me?

---

### Post by ashkev on 2007-08-27
Should I post this in a different Forum?  Can someone tell me which forum would be best?  Maybe something having to do with LTSP?

---

