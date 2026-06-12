---
title: "Zyxel M-102, need help with install"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by jaa1180 on 2007-09-21
I have a Dell D820 and using a Zyxel M-102 PCMCIA card for wireless. 
Currently the laptop is dual booting with Winders XP Pro and Ubuntu 7.04.

I have not found any documentation on making this wireless card work. 
Any suggestions?

---

### Post by jaa1180 on 2007-09-26
Anyone???

---

### Post by dingobytes on 2008-05-13
A few months to late, but I was able to install the ZyXEL M-102 PCMCIA WiFi device on an old computer for my daughter. I am new to Ubuntu and have gotten my daughter using it, so she decided she would install (Ubuntu 8.04) on an old laptop she was using.

I tried several searching Synaptic Package Manager for ZyXEL, ndiswrapper, Atheros and a few other things related to the CardBus. I was able to use a 3Com PC Card with XJack Connector to get a wired connection, so I knew the PCMCIA slot was working.

Try using the following instructions in a terminal:

One of the items I read was that other ndiswrapper drivers may cause some issues, so I went ahead and removed all ndiswrappers using the following command in the terminal.

```
for dr in $(ndiswrapper -l | grep -o "\w* :" | grep -o "\w*" ); do sudo ndiswrapper -e $dr; done
```

I did a quick check to make sure the ndiswrappers were all removed by running...

```
ndiswrapper -l
```

If by chance you have any ndiswrapper drivers remaining, you can remove them by running the following command for each one (driver should be replaced with the driver name):

```
sudo ndiswrapper -e (driver)
```

Now you need to grab the M-102 window drivers or more specifically the inf file...

```
wget http://us.zyxel.com/upload/download_library/M-102\ Drivers.zip
```

Once the download completes, you just need to unzip the files...

```
unzip M-102\ Drivers.zip
```

Now change your directory to the M-102 Drivers Directory...

```
cd M-102\ Drivers
```

Finally you can install the device using the following...

```
sudo ndiswrapper -i net5513.inf
```

You should get a reply that it was installed...

> installing net5513...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64

That should do it. If your CardBus is in the slot, you should now be able to connect to WiFi devices.

If this helps anyone else out, be sure to post that it helped so others don't have to search for hours/days looking for a resolution! Thanks to user bmartin for his post relating to this.

---

### Post by thehurley on 2008-05-30
hello,

I tried dingobytes instructions, all seemed to go ok but once I've finished, the m102 card doesn't seem to power on.  The same card works perfectly in the same laptop under Windows XP.  Is there another step I'm missing?

ty.


```

thehurley@laptop:/media/disk/hardware/zyxel/m102/drivers$ ls -lA
total 372
-rwxrwxrwx 1 root root 358464 2005-09-13 09:59 ar5513.sys
-rwxrwxrwx 1 root root   7994 2005-12-29 01:51 net5513.cat
-rwxrwxrwx 1 root root  11045 2005-12-28 11:00 net5513.inf

thehurley@laptop:/media/disk/hardware/zyxel/m102/drivers$ sudo ndiswrapper -i net5513.inf 
installing net5513 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64

thehurley@laptop:/media/disk/hardware/zyxel/m102/drivers$ ndiswrapper -l
net5513 : driver installed
	device (168C:0020) present

```

---

### Post by thephotoman on 2008-05-31
thehurley: Could I get the output of this command:

```
lsmod | grep ndiswrapper
```

---

### Post by thehurley on 2008-05-31
ok, with the help of photosinensis/thephotoman, I got this working.

```

thehurley@laptop:~$lsmod | grep ndiswrapper
thehurley@laptop:~$

```

... nothing was returned.  photosinensis then told me to issue the following:

```

thehurley@laptop:~$sudo modprobe ndiswrapper

```

Immediately the lights on the card powered on, and all available wireless networks were detected.  Now running lsmod again looks good...

```

thehurley@laptop:~$lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,ohci_hc

```

---

