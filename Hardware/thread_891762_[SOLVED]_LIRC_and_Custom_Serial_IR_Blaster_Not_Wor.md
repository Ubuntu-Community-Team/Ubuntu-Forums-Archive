---
title: "[SOLVED] LIRC and Custom Serial IR Blaster Not Working"
date: 2008-08-16
forum: Hardware
---

### Post by Eric Boring on 2008-08-16
Hello everyone. I'm hoping someone here can help me figure this out. I am trying to get a custom-built Serial IR Blaster to transmit, but I have hit a road block. I've searched around and tried a lot, and now I am just plain confused. 

Here is what I can tell you:

If I run lsmod, I get this:

```

josh@frankendevo:~$ lsmod | grep lirc_serial
lirc_serial            16276  0 
lirc_dev               15860  2 lirc_serial,lirc_i2c

```

As far as I can tell, this seems like it should work. But when I test the device, no joy. (I've tried just using it to change channels on the set-top box, and I've tried viewing the transmitter through a digital camera.)

I'm running mythbuntu 8.04 on this machine.

If anyone can help me out with this, it would be great.

EDIT: 
OK, I started following the instructions here: [http://www.mythtv.org/wiki/index.php/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/index.php/Ubuntu_Serial_Lirc_Install)

So I install these packages:
```
josh@frankendevo:~$ sudo apt-get install lirc lirc-modules-source module-assistant
```

But when I run the reconfigure command, here is what happens:
```
josh@frankendevo:~$ sudo dpkg-reconfigure lirc-modules-source
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

```

But I never see a configuration dialog. Then when I try to edit /etc/lirc/lirc-modules-source.conf there is a file there, but it is blank.

---

### Post by Eric Boring on 2008-08-18
I think I must have posted this in the wrong forum. I'm going to close the thread and re-post it in Mythbuntu. Hope that's ok.

---

