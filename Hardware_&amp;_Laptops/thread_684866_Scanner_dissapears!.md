---
title: "Scanner dissapears?!"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Sain on 2008-02-01
I have finally set up my scanner (hp 2400) after a year or so I searched drivers for it... Now I have different problem: Scanner works perfect using Xsane after installation, however Xsane fails to recognize him after few restart or something. I haven't really figured out what is the cause of this, but I'm unable to use scanner afterwards..

scanimage -L gives:
```
scanimage: symbol lookup error: /usr/lib/sane/libsane-hp2400.so.1: undefined symbol: sanei_usb_init

```

Then I just reinstall drivers, and everything works again... Installation procedure and drivers can be found at [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php). Scanner is HP scanjet 2400. It is officially unsupported by Sane project, but drivers on that page are working.

I would be very grateful if someone can look into this and shed some light on problem... Scanner is the only part of my hardware that wasn't working on Linux and I was so happy when I got it to work.

---

### Post by citral on 2008-03-24
The problem is that the patch for libsane in the fix is not up to date. Ubuntu uses newer libsane.

In the file is explained how to solve it: 

> 
    The hp2400 driver contains only HP authored code and depends on 
    the SANE library for some functions.  Unfortunately, libsane.so
    lacks the sanei_usb module.  To add this module,
        1) Obtain the SANE distribution from [www.sane-project.org](www.sane-project.org).
        2) add "sanei_usb.lo" to the "EXTRA" line in backend/Makefile.in:

EXTRA = sane_strstatus.lo ../sanei/sanei_init_debug.lo ../sanei/sanei_config.lo ../sanei/sanei_usb.lo

        3) follow the SANE README build and instructions.  This sequence of
           instructions appears to install in /etc/sane.d and /usr/lib:
                cd sane-backends-1.0.??
                configure --prefix=/usr --sysconfdir=/etc
                make
                su
                make install



Use the instructions on [https://help.ubuntu.com/community/UpdatingADeb?highlight=%28deb%29](https://help.ubuntu.com/community/UpdatingADeb?highlight=%28deb%29) to custom compile the package.

I would give you my resulting .deb file, but debi needs the compiled source tree along with it?

This got me thinking to perhaps file a bug to include the required makefile switch by default...

Regards,
Hugo

---

### Post by Sain on 2008-05-13
I haven't looked at this thread for a while.... 
I made a little shell script that automatically installs drivers and then runs Xsane. It all happens in a fraction of a second, so you don't even notice the difference. It wasn't the most elegant solution I guess, but it worked.

Unfortunately that was on Gutsy, and doesn't work on Hardy anymore (returns "segmentation fault"). So I guess I finally give up on HP 2400 and Ubuntu. 

It's still hard to believe that these are fully functional drivers that work... until I restart my computer!?!

---

### Post by bobandiara on 2008-05-14
Hello, there.
I'm running Hardy Heron right now, and I own a HP 2400. I installed the above mentioned driver, it worked. Then, I rebooted my machine. When I tried to run *scanimage -L*, it returned the "segmentation fault" error. 
I reinstalled the driver, and it worked for me, which makes me think I will have to reinstall it every time I need to use the scanner. Now, I'm curious to try this solution. I'll post here if anything happens. Thanks for the info!

---

### Post by Sain on 2008-07-10
Why doesn't Sane finally add support for HP 2400? Driver obviously exist, so how hard would it be to add it by default? 
This patching, hacking and everything is just too much... :(

---

### Post by mjuhasz on 2008-07-14
The instructions in the driver package are not valid anymore. I was not able to compile libsane package in hardy with usb support. I managed to compile it in gutsy but not in hardy so do not stress yourself if it fails.
Here is the solution I found. Follow the instructions in the driver package and install the driver accordingly. It will work but the solution is not permanent (might stop working after reboot).
The trick: backup libsane.so.1.0.19 and rename libsane.so.1.0.14 from the HP2400 driver to libsane.so.1.0.19.
If you replace the libsane.so.1 symlink so that it points to libsane.so.1.0.14 instead of libsane.so.1.0.19 it will work only until the next call to ldconfig which might happen even on the next reboot or on package update/installation. ldconfig fixes the libsane.so.1 symlink and it will point again to libsane.so.1.0.19 which of course will not work. That is why simply replacing the symlink is not enough: it will sooner or later point to the new driver instead of the good old one.

Something like:

cd /usr/lib
# create backup
cp libsane.so.1.0.19 ~/libsane.so.1.0.19
# replace original file with the one from the driver
sudo mv libsane.so.1.0.14 libsane.so.1.0.19

I have only an HP2400 scanner so I do not mind replacing the new sane file with the old one.

---

