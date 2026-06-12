---
title: "login configuration not correct"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by swong1 on 2006-01-23
Hi,

I recently upgraded from Hoary to Breezy on my laptop. It works, but there are some minor gliches. On the login screen, I get the warning message:

The configuration file contains an invalid command line for the login dialog, so running the default command. Please fix your configuration.

Can anyone help me troubleshoot? Thanks!

---

### Post by swong1 on 2006-01-24
Hi,

Can anyone help? If you could just tell me where can I find the login files, I would much appreciate it.

---

### Post by swong1 on 2006-01-24
Edit: found an earlier post with the same problem:
[http://www.ubuntuforums.org/showthread.php?t=90569&highlight=%22login+configuration%22](http://www.ubuntuforums.org/showthread.php?t=90569&highlight=%22login+configuration%22)

Acoordingly, the steps to correct this problem are:
```

ctrl-alt-f1
sudo /etc/init.d/gdm stop
sudo apt-get remove gdm --purge
sudo apt-get install gdm ubuntu-desktop xubuntu-desktop
sudo /etc/init.d/gdm start

```

Now I encounter another problem after issuing gdm stop. My laptop freezes at "checking battery state". I searched this forum for similar threads. It seems it has a conflict with nVidia driver, but I'm using ati. Another thread [http://www.ubuntuforums.org/showthread.php?t=117031&highlight=%22checking+battery+state%22](http://www.ubuntuforums.org/showthread.php?t=117031&highlight=%22checking+battery+state%22)
suggests adding the line 

Option	    "NoAccel"

in xorg.conf. But I went through a lot to install my ati driver to get 3D accelaration. Is there any other way to get around this? Thanks.

Edit: Tried this a second time. This time it worked without a glich. And I don't have the "invalid command" message on login screen anymore. Thanks!

---

