---
title: "Dell Inspiron B130 Mini PCI Wireless Problems HELP!"
date: 2010-07-30
forum: Hardware
---

### Post by baseball1019 on 2010-07-30
I have a 2006 Dell Inspiron B130. Windows was slow and buggy on it, so I made the plunge into Ubunutu. I'm running 10.4 a few weeks after the update, my belkin wireless usb adapter seemed to stop working. It's always been a piece of junk. Instead of spending $50 on another one for this outdated system, I thought why not just get the hardware installed. So I ordered a Mini PCI card off of eBay said to work with my machine.
I installed it, BIOS seems to recognize it. I connected to the internet by ethernet for the broadcom driver ubuntu suggested I install. Everything seemed to be going well. However, there's still no wireless internet after a restart of the machine.
When I right-click on the networking status icon the drop down lists "Enable Wireless" but is grayed out.
I searched the forums and found many users having issues with the broadcom chips, but the discussion was too technical for me. 
Help Obi-Wans!

---

### Post by freedomAboveAll on 2011-05-10
I have a B130.  Installed 11.04 and both Ethernet AND Wireless were DOA/ non existent.

found this:
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fc6-zod-on-dell-inspiron-b130-wired-ethernet-problem-508656/#post2535634](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fc6-zod-on-dell-inspiron-b130-wired-ethernet-problem-508656/#post2535634)

and did this at terminal:

```

> sudo modprobe b44 
> ifup 

```
and wired networking fired up!

Doing a 
```

> sudo apt-get update
> sudo apt-get upgrade

```

next steps (for natty) ...

```

>  sudo apt-get install b43-fwcutter firmware-b43-installer

```
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

The restricted driver detection does not start up for me, so I added 'b43' to the file /etc/modules so it would load on boot.  This got wireless working at least.

---

