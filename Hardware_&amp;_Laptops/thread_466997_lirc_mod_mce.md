---
title: "lirc_mod_mce"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by bodine on 2007-06-07
need help installing windows media center edition wireless keyboard and remote on ubuntu feisty. 
I have downloaded lirc_mod_mce from: 
[http://sourceforge.net/projects/mod-mce](http://sourceforge.net/projects/mod-mce)
but need help compiling/installing. I have searched the web and  looked on many forums but without any luck.

thanks in advance, bodine.

---

### Post by kombipom on 2007-06-24
I'm in the same position, I downloaded it, uncompressed it, went into the directory and typed make, there were no errors, just some warnings, but nothing happened, nothing in dmesg to suggest anything.  I also can't get the remote to work with lirc.  I have followed the instructions on help.ubuntuforums when I start lircd no /dev/liec0 or similar is created and irw just returns to the prompt.:(

---

### Post by kombipom on 2007-06-24
I've got it working!

A quick HOW-TO before I forget

This assumes that you haven't installed lirc yet.If you have you need to remove the usbmce/usbmce2 modules

1.Install the lirc packages
         sudo apt-get install lirc lirc-modules-source 

2. Uncompress the downloaded tar file
        tar -xf lirc_mod_mce-0.1.4.tar.bz2

3. The version of lirc_mod_mce is slightly incompatable with the version of lirc in Feisty but all you have to do is swap a header file:
        copy /src/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.h into te directory with your lirc_mod_mce source files in.

4.  type "make" (without quotes) in the lirc_mod_mce directory, this should compile the code to produce a .ko file.

4. copy the .ko file to /lib/modules/2.6.20-16-generic/misc (change the kernel name to match yours if different)

5. type sudo depmod -a

6. Unplug and re-insert the USB reciever and it should work, if not, try a re-boot.

I just cobbled this together from info on the Sourceforge pageand it worked for me.

Kombipom

---

### Post by bmilleker on 2007-10-31
How did you get around these errors when loading your module?

```
[  435.472898] lirc_mod_mce: Unknown symbol lirc_get_pdata
[  435.472988] lirc_mod_mce: Unknown symbol lirc_unregister_plugin
[  435.473312] lirc_mod_mce: Unknown symbol lirc_register_plugin

```

I am running fiesty as well.

---

### Post by bmilleker on 2007-11-01
Solution here [http://ubuntuforums.org/showthread.php?t=592057](http://ubuntuforums.org/showthread.php?t=592057)

---

