---
title: "DWL-AG132 + ndiswrapper + edgy"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by OldGaf on 2007-01-15
Hi all,

First I would like to say AHHHHHHHHHHHHHHHHHH ](*,) 

OK..... I am trying to get my DWL-AG132 to play nice with Edgy using ndiswrapper.

I have a fresh install of edgy and dist-upgrade done.
I am using ndisrapper 1.34
This is the process I follow:

1.Make sure I have the headers:

2.Grab the latest version of Ndiswrapper: 
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

3.Go to the downloaded file and extract it:

4.Change to that directory:

5.Once in the source-directory run:
make distclean

6.Then run:
make

7. As root, run:
make install

8. Then run the following to install the drivers (put in the full path)
ndiswrapper -i neta5agu.inf

$ ndiswrapper -l 

Installed ndis drivers:
neta5agu                driver present, hardware present

$ lsusb
Bus 005 Device 005: ID 2001:3a01 D-Link Corp. [hex]

$ ndiswrapper -d 2001:3a01 neta5agu
$ ndiswrapper -m 
$ sudo depmod -a
$ sudo modprobe ndiswrapper

ndiswrapper -l
neta5agu : driver installed
        device (2001:3A01) present

All this works the first time and I am able to activate and surf the net........

BUT....... as soon as I reboot the box, it will not work. I can't even see the device. No matter what I do, I am unable to get it to work again. I have un-installed the drivers and run "make un-install, removed all evidence and re-installed.... no good. The only thing I can do is install the OS again and repeat the above procedures, but again it only works until I reboot.

The only thing I noticed is that the device number was 2001:3a00 on one install, and the device changed to 2001:3a01 on boot. I un-installed the driver and put it back with the right number (which it accepted) but it still would not work or show up.

ANY help would be GREATLY appreciated.

updated and moved to network / wireless area........ sorry.

---

