---
title: "Messed up xorg.conf for nvidia drivers"
date: 2008-10-17
forum: General Help
---

### Post by nimonika on 2008-10-17
I did an upgrade yesterday on Hardy and found that it has completely messed up my xorg.conf with the resolution and the nvidia drivers are no longer available. The resolution is also terrible now.

Please could someone post me their xorg.conf for a wide screen sony laptop (1200x800), gb keyboard and nvidia drivers.

I have tried everything from sudo-dpkg-reconfigure to nvidia-xconfig.
One thing messes up the other. Please help!!

---

### Post by sparky-steve on 2008-10-17
Hello,

Have you read this thread:

[http://ubuntuforums.org/showthread.php?t=949407](http://ubuntuforums.org/showthread.php?t=949407)

If you follow it, it will create a working xorg for you. Works on my Vaio.

---

### Post by Elfy on 2008-10-17
It should have created a backup when it got changed. Check in /etc/X11, it should have a time stamp like xorg.conf.20080805123458 but with yesterday's date.

You can use an old backup by copying backup to xorg.conf

```
sudo cp /etc/X11/nameofbackupxorg /etc/X11/xorg.conf
```

Reboot.

---

### Post by sparky-steve on 2008-10-17
> **forestpixie said:**
> It should have created a backup when it got changed. Check in /etc/X11, it should have a time stamp like xorg.conf.20080805123458 but with yesterday's date.

You can use an old backup by copying backup to xorg.conf

```
sudo cp /etc/X11/nameofbackupxorg /etc/X11/xorg.conf
```

Reboot.

Alot of people had problems after the new kernel yesterday; it's unlikely that copying the xorg.conf file will help in this instance, though forestpixie is correct in that there should be a copy there with yesterdays timestamp.

---

### Post by Elfy on 2008-10-17
> Alot of people had problems after the new kernel yesterday;Aah - hadn't noticed that I had that kernel a while back from proposed without problemms.

Although I will say that using the direct download from nvidia could cause problems for people who aren't aware that future kernel changes would make it necessary to do so again it used to be the same with envy, but I think now it's in the repos it gets taken care of.

---

