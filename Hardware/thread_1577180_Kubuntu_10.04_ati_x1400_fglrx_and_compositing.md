---
title: "Kubuntu 10.04 ati x1400 fglrx and compositing"
date: 2010-09-18
forum: Hardware
---

### Post by axel22 on 2010-09-18
Hello.

I own a Dell Inspiron with an ati radeon mobility x1400 graphics adapter:

```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
        Subsystem: Dell Device 2003
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at ee00 [size=256]
        Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at dfd00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon

```

I previously used Kubuntu 9.10, and then upgraded to 10.04. High resolution works and the secondary monitor works. However, after upgrading to 10.04 from 9.10 compositing no longer works.

Problems:
1) opening "Desktop" section of "Settings" crashes the application
2) invoking "fglrxinfo" outputs "Segmentation fault"
3) invoking "glxinfo" outputs:

```

brijest@Reaver:~$ glxinfo 
name of display: :0.0
Segmentation fault

```

4) invoking "aticonfig --initial" always outputs "aticonfig: No supported adapters detected"

5) I've never once observed a xorg.conf file in the etc/X11 dir:

```
brijest@Reaver:~$ ls /etc/X11/
app-defaults  default-display-manager  rgb.txt  xinit               Xreset    Xresources  Xsession.d        XvMCConfig
cursors       fonts                    X        xorg.conf.failsafe  Xreset.d  Xsession    Xsession.options  Xwrapper.config

```

I think that xorg.conf.failsafe above was generated when I was building the proprietary driver from the ATI website from scratch, but I'm not sure.


I've tried:
1) Reinstalling "fglrx" package with aptitude
2) Installing "xorg-driver-fglrx" package with aptitude
3) Building the driver from the ATI website from scratch (with Ubuntu/lucid option) and installing *.deb files obtained in this way

In each of the cases above, I've removed the old packages as instructed here:
[HTML]http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver[/HTML]

Nothing seemed to work. I can use the secondary monitor in the native res, but compositing is not supported. Is there anything that can be done?

---

### Post by axel22 on 2010-09-20
Ok, when I deinstalled fglrx and all variants completely, I could still use the external monitor, but it was full of waves and flickering. I have, however, noticed through all that flickering on the secondary monitor that compositing was actually working now. But I couldn't use the monitor.

I googled a bit. This solved the problem (read through the comments too):

[HTML]http://beyondteck.blogspot.com/2010/05/flickering-monitor-in-ubuntu-1004-for.html[/HTML]

Essentially, installing a newer version of the kernel solved the problem. I didn't have to install fglrx.

I now have compositing and the external monitor working.


P.S. If someone knows how to set the thread to SOLVED, let me know :)

---

