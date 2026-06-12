---
title: "How can I run the hardware autoconfiguration script from the live cd?"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by tuxcantfly on 2007-01-05
Ok, here's why I want to do this...

[http://ubuntuforums.org/showthread.php?t=305109](http://ubuntuforums.org/showthread.php?t=305109)
[https://wiki.ubuntu.com/install.exe](https://wiki.ubuntu.com/install.exe)
[https://blueprints.launchpad.net/distros/ubuntu/+spec/windows-installer](https://blueprints.launchpad.net/distros/ubuntu/+spec/windows-installer)

Essentially, what we're trying to do is provide an ubuntu installer from windows, that will require the minimal configuration and user interaction, and most user-friendliness possible. We've got most of it working already, only we're having some hardware detection issues. In particular, for some reason, xorg isn't having its resolution properly configured, and networking isn't being configured either. However, on the same computer, when booting with the live cd, both networking and resolution are properly configured

So here's what I want to do...

When the system boots the first time, I want the autoconfiguration script from the live cd to run, and automatically configure the system. Is there a particular command that can run it? I want to put it into a shell script in /etc/rcS.d that will run on the first boot and autoconfigure the hardware. So does anybody know the command to start the hardware autoconfiguration script from the livecd?

---

### Post by tuxcantfly on 2007-01-06
Ok, I figured out the command for the xorg autoconfiguration:

```
dexconf
```

Does anybody know the command for the networking autoconfiguration?

---

### Post by tuxcantfly on 2007-01-15
nevermind, I figured out how to do networking autoconfiguration:

```
dpkg-reconfigure dhcp3-client
/etc/init.d/networking restart
```

---

