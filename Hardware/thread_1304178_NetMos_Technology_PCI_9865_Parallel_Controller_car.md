---
title: "NetMos Technology PCI 9865 Parallel Controller card install how-to for Ubuntu"
date: 2009-10-29
forum: Hardware
---

### Post by joecrow on 2009-10-29
NetMos Technology PCI 9865 Parallel Controller card install how-to for Ubuntu

Just wanted to share this with folks installing a pci to parallel controller card with a NetMos 9865 chip. After  Googling, I found a lot of folks out there with the same problem I had when trying to install this puppy. So, after finding a solution, I decided to come here and post what I found for others to read and hopefully solve their problem. So, here goes nothing.

I do not have a parallel port on my computer so I bought a cheap card on Ebay. It is a no name card that came with a cdrom and a Linux driver called msc9865_Linux. I couldn't "Make" or "compile" anything from the driver. The instructions were to vague and after googling, it seems the driver was too old and the manufacturer stopped supporting it. I eventually found a tutorial by Lazly at [http://lazly.hu/q/netmos-technology-pci-9865-parallel-controller-install-howto-ubuntu-904-english](http://lazly.hu/q/netmos-technology-pci-9865-parallel-controller-install-howto-ubuntu-904-english) which worked for me. It was not very detailed but I managed. Even though it is already in English, I modified and rewrote it here so it makes more sense and added more details.

Im using ubuntu 8.10 but this will work with 9.04 and others. As I explained above, I too tried to install an old printer with a parallel card and was going around in circles with the driver and installation instructions. I googled 'til my fingers were raw and still nothing. However, the following how-to solved my problem without using any driver!

First, make sure your system "sees" the card with the following:
    $ sudo lspci
      ...
      03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller
      ...
Scroll down until you see something similar to the above. As you can see, my system sees the card and identified the parallel port. By the way, there were two serial ports listed on the same card. Which I will not be using. Anyway,...

    $ sudo cat /proc/ioports | grep parport
      <nothing>

    $ sudo modprobe -r lp
    $ sudo modprobe -r parport_pc

    $ sudo lspci -v
       ...
       03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at e000 [size=8]
    I/O ports at d800 [size=8]
    Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
    Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [48] Power Management version 2
       ...
Note the I/O port above listed as being at e000. It will probably be different on yours. In the following command replace mine with whatever yours may be.

    $ sudo modprobe parport_pc io=0xe000
    $ sudo modprobe lp

    $ sudo /etc/init.d/cups restart

At this point, my printer started printing so I stopped, but you may need to install your printer drivers. If that is the case, Use the official Ubuntu printer setup GUI.

Before you reboot your system, you still need to edit a couple of files so you can keep printing when the system is restarted. The first file, has to be created and the info added to it. The second file should already exist so you just need to add the line to it. So go ahead and create the file "parport_pc" in the directory as indicated below. Then edit it with your fav text editor. I used Nano in my examples.

    $ sudo nano /etc/modprobe.d/parport_pc
    options parport_pc io=0xe000

Once the file "parport_pc" is created and the option above is added, edit the next file to make sure it all works after rebooting.
    $ sudo nano /etc/modules
    ...
    parport_pc
    lp
    ...

That's all. I've been using Ubuntu for a year now and love it but I'm not an expert so maybe other here can further help you along. I hope this method helps others. Later, JoeCrow

---

### Post by pmorton on 2009-11-05
Well, I never.
That's the quickest solution to anything I've ever found on a forum. Four minutes and sorted. First search for help, as well, and only a week after you'd posted it.

Great post. Thanks!

---

### Post by joecrow on 2009-11-07
You are welcome. I am glad someone was helped. :D

---

### Post by maanafzal on 2012-04-18
Hey 
Do you have some procedure for serial port. I am using PCI Serial card and its not working with my system. 
Please help me out in this issue.

---

