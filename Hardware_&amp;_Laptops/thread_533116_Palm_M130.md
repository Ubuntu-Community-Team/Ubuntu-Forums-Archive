---
title: "Palm M130"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by dgrafix on 2007-08-23
Thought id take another cracjk at getting my palm to work, 
/dev/pilot does not exist. However, i can see dev4.3_ep00 appears when i press the sync button, but it will not allow the . and _ characters into the pilot location.

How do i turn /dev/usbdev4.3_ep00 into /dev/pilot 

and will this be the same even if the usb devices change position etc?

---

### Post by linuxwizard on 2007-08-24
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

---

### Post by cefola on 2008-01-09
My system is Debian of which Ubuntu is based.
My solutiom is follows:
1.   change to root
2.   as root run:
      mknod /dev/ttyUSB0 c 188 0     # found these statements on other forum
      mknod /dev/ttyUSB1 c 188 0     # found these statements on other forum
      mknod /dev/pilot c 188 0            #  added this statement based on above info
      chmod 666 /dev/pilot                 #  added this statement based on above info
3.  Connect Palm M130 via USB port
4.  Change settings in Evolution to connect via   /dev/pilot
5.  Push button on cradle
6.  Evolution syncs !

Hope this helps

Ray

---

### Post by cuddy on 2008-06-28
Hi,
As a complete beginner you have lost me on 'change to root'. Please could you point me in a direction to find out about this.
Thanks,
Cudddy.:confused:




> **cefola said:**
> My system is Debian of which Ubuntu is based.
My solutiom is follows:
1.   change to root
2.   as root run:
      mknod /dev/ttyUSB0 c 188 0     # found these statements on other forum
      mknod /dev/ttyUSB1 c 188 0     # found these statements on other forum
      mknod /dev/pilot c 188 0            #  added this statement based on above info
      chmod 666 /dev/pilot                 #  added this statement based on above info
3.  Connect Palm M130 via USB port
4.  Change settings in Evolution to connect via   /dev/pilot
5.  Push button on cradle
6.  Evolution syncs !

Hope this helps

Ray

---

### Post by firefeather on 2008-06-28
> **cuddy said:**
> Hi,
As a complete beginner you have lost me on 'change to root'. Please could you point me in a direction to find out about this.
Thanks,
Cudddy.:confused:

He basically means that those are administration commands and require a special command to make them work.

To do this, you would type "sudo " (without the quotes) before each command. **However**, be careful when you do this, because running commands with sudo can break your system or destroy your data if you aren't careful.

EDIT: I should follow up on that; cefola is saying that you should run these in the Terminal (Applications -> Accessories -> Terminal). Because you should always understand to some degree what a command is doing, you can check out the commands by using the "man" command (short for "manual"), like so:

```
man mknod
```

This will tell you what mknod does. You can then replace "mknod" with "chmod".

---

### Post by cuddy on 2008-07-19
Many thanks. I have submerged myself in a couple of books/primers on Linux and now begin to understand something of what you are saying. It's a steep curve. Thank you for your patience.
Cuddy.

---

### Post by cuddy on 2008-07-20
Hi,
I tried the commands.responses:
after the first command I was asked for my password, then - 
sudo: mknod/dev/ttyUSB0: command not found
sudo: mknod/dev/ttyUSB1: command not found
sudo: chmod: cannot access /dev/pilot: No such file or command.

Gnome did seem to begin to respond on sync but then nothing.

I tried with Kpilot and used the wizard: 
Kpilot cannot yet syncronise the addressbook with Evolution, so the addressbook conduit was disabled.
When syncing the calendar od to-do list using Kpilot please quit Evolution before the sync, otherwise you will lose data.

Ah well, try again perhaps?

Cuddy.

---

