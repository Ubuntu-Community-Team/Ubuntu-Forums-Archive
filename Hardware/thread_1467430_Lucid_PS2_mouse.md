---
title: "Lucid PS/2 mouse"
date: 2010-04-30
forum: Hardware
---

### Post by Devilman13 on 2010-04-30
After updating to Lucid, my PS/2 mouse no longer works on a Dell Optiplex. Unplugging and re-plugging, restarting, etc do not fix. USB mouse works fine.

---

### Post by sioc on 2010-05-01
Same problem for me !

Just updated from 9.10 to 10.4, and my PS/2 mouse won't run.
I plugged a USB mouse, and this one works fine, but I would like to make my old PS/2 work too...

I saw some various bugs around there that seems related to that, but I'm not sure it's exactly the same... ?

[http://ubuntuforums.org/showthread.php?t=1442724](http://ubuntuforums.org/showthread.php?t=1442724)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542848)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/555169](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/555169)

Wait & see...

---

### Post by maxol on 2010-05-12
Same problem here.

After upgrading to Lucid my Dell C610 laptop doesn't recognise my PS2 mouse. However by unplugging and then replugging the mouse it will work.

Still a pain though.

---

### Post by Devilman13 on 2010-05-29
That didn't work for me. It doesn't matter how I re-plug the mouse, it refuses to work. Anyone know another solution or read somewhere that this will be fixed?

---

### Post by lidex on 2010-05-31
What is the output of these commands:
```
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

Then try this:
```
sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients
```

**Reboot**

---

### Post by JRBASTIEN on 2010-06-18
> **lidex said:**
> What is the output of these commands:
```
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

Then try this:
```
sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients
```

**Reboot**


I can confirm that this command works.  I had the same problem on Lucid (not after an upgrade. The mouse just stopped working for no reason).  Runing this code fixed my problem.  Thank you.

---

