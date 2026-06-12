---
title: "installing drivers"
date: 2008-07-31
forum: Hardware
---

### Post by Auxilio on 2008-07-31
Hi. I'm new to both the forms, and linux. I wanted it because I was tired of PC, and don't really have the money to dish out for a nice Mac. Also my friend said linux was really neat to use, and I kinda wanted to start learning programming/code. So I got this laptop, it's an MSI, and my friend told me that I should look for my own graphics and mobo drivers, but I can't find them ANYWHERE. Also, they're not listed under the unrestricted/restricted drivers. Do I need to download these drivers? Also, in the hardware drivers section, it has listed the "Atheros Hardware Access Layer (HAL) and "Support for Atheros 802.11 wireles LAN cards." do I need to find drivers for these? or are they working fine? Also, my wireless is not working properly, is this why? I'm really sorry that I'm this behind, but I gotta learn.

---

### Post by jimv on 2008-07-31
Generally the only drivers you need to worry about are for your graphics card and network cars....and even then, only if they aren't working correctly.  Ubuntu has drivers for tons of hardware included with it.

---

### Post by Auxilio on 2008-07-31
So I'm guessing that my network drivers aren't working properly, but what about my graphics drivers? How can I tell if they're not working properly? Also, how can I try to install games? I mean, obviously, sticking them in the drive and installing won't work, right? So how do I get them to work? I heard something about WINE, is that what I need?

---

### Post by Auxilio on 2008-07-31
Ok, so I found drivers for my network card, but it's this thing called Madwifi, and it has a whole bunch of files in it, rather than just an installer. Now, I realize that with linux, I'm not going to get an installer a lot of the time, but I would like to learn how to install this properly. It has a file called install, but it's very confusing and I don't really get it. Can anyone help me with this?

---

### Post by evets25 on 2008-08-01
As opposed to the windows way, you should only install drivers manually if your hardware does not work at all. (i.e.: your Linux distro doesn't come with the driver) However, chances are, if Ubuntu doesn't come with a driver for a particular device, then there IS no Linux driver at all for that device. 

Installing drivers manually in Linux is not the same as in windows. You (generally) don't download a setup file and run it. (It's the same way with software too) 

So unless you know what you're doing, and there's a specific problem with a specific piece of hardware that you're trying to fix, don't install additional drivers! It will inevitably confuse your computer and cause unnecessary problems. 

If you are having specific problems with a particular piece of hardware, then give us some more info and we can help you out, such as 
- particular model/brand of your computer
- what piece of hardware you are having problems with, and what specific model/brand it is (be specific as possible) 

There are different commands that you can run to find out about your hardware if necessary, like 

```
uname -r
lspci
lshw
lsusb
ifconfig
```

These will tell you about, in order, your kernel version, any PCI devices, all hardware, any usb devices, any network devices.

---

